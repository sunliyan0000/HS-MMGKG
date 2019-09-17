# HS-MMGKG
# Introduction
HS-MMGKG is a new multi-objective heuristic optimization methodology for detecting genetic interactions. In HS-MMGKG, we use harmony search with five objective functions to improve the efficiency and accuracy. A new strategy based on p-value and MDR is adopted to generate more reasonable results. The Boolean representation in BOOST is modified to calculate the five functions rapidly. These strategies take less time complexity and have higher accuracy while detecting the potential models. We compared HS-MMGKG with CSE, MACOED and FHSA-SED using 26 simulated datasets. The experimental results demonstrate that our method outperforms others in accuracy and computation time. It is anticipated that our proposed algorithm could be used in GWAS which is helpful in understanding disease mechanism, diagnosis and prognosis. The article is at http://www.eurekaselect.com/171466/article.
# Uploaded files
/code/lib contains all dependency packages of HS-MMGKG.<br>
/code/src contains all source code of HS-MMGKG.<br>
/code/target contains a compiled jar file which is generated by using /code/build.sh.<br>
/code/build.sh is the script which can complie the source code of HS-MMGKG on linux.<br>
/code/run.sh is some examples which utilize HS-MMGKG to detect epistaitc interactions in the example GWAS files in /data.<br>
/data/simulated_data contains 26 zip files. They are the 26 simulated datasets used in the article for HS-MMGKG.<br>
/data/example.tped and /data/example.tfam is an example of real GWAS data containing only 1000 SNPs. More details about the tped and tfam format is at http://www.cog-genomics.org/plink/1.9/formats#tped.<br>
/data/example.txt is an exmaple of simulated data containing 1000 SNPs.<br>
# Compilation
cd /code
bash build.sh
# run
cd /code
\#\#Run a graphical interactive interface and it supports multiple threads.<br>
java -jar /target/hs-mmgkg.jar<br>
\#\#Detect epistatic interactions in /data/example.txt.<br>
java -cp target/hs-mmgkg.jar:target/lib/commons-io-2.5.jar:target/lib/commons-math3-3.6.1.jar main.Command -file /data/example.txt -order 2 -hms 5 -hmcr 0.8 -par 0.4 -tmax 400000 -fold 5 -ishow 4000 -nshow 4 -pvalue 0.05 -nsolution 40<br>
\#\#Detect epistatic interactions in /data/example.tped and /data/example.tfam.<br>
java -cp target/hs-mmgkg.jar:target/lib/commons-io-2.5.jar:target/lib/commons-math3-3.6.1.jar main.Command -file /data/example.tped -order 2 -hms 5 -hmcr 0.8 -par 0.4 -tmax 400000 -fold 5 -ishow 4000 -nshow 4 -pvalue 0.05 -nsolution 40<br>
# parameters

parameter|default value|description
----|----|----
file|null|The path of the input GWAS file. If the path end with ".tped" or ".tfam", HS-MMGKG will load the GWAS file as it is a real GWAS data. Otherwise, it load the file as it is simulated.
order|2|The order of the reported epistatic interactions.
hms|5|Harmony memory size for the Harmony Search.
hmcr|0.8|Harmony memory considering rate for the Harmony Search.
par|0.4|Pitch adjusting rate for the Harmony Search.
tmax|-1|The maximum iteraction for the Harmony Search. -1 means the Harmony Search will never stop for the number of iterations.
fold|5|The fold of cross validation used in MDR.
ishow|4000|After each ishow iterations, HS-MMGKG displays echoes.
nshow|4|The number of displayed harmonies.
pvalue|0.05|The threshold of pvalue.
nsolution|40|The number of reported epistatic interactions.
