# MetaGLMBench
Benchmarking DNA Language Model on Metagenomics Tasks

## Datasets

### CAMI 2

https://github.com/CAMI-challenge/second_challenge_evaluation

### Real Samples


## Preprocess
 ```
find . -mindepth 2 -name "*.fasta" -exec cat {} + > sample_0.fna

bowtie2-build sample_0.fna sample_0_index

bowtie2 -x sample_0_index \
        -1 Sample_0_illu_1.fq \
        -2 Sample_0_illu_2.fq \
        -S sample_0_unsorted.sam \
        --threads 50 \
        --very-sensitive

samtools view -bS sample_0_unsorted.sam | samtools sort -@ 10 -o sample_0.sorted.bam
 ```

## Evaluation

### CheckM2

https://github.com/chklovski/CheckM2 

 ```
# default is *.fna
checkm2 predict --threads 50 --input ./genome  --output-directory ./genome_checkm2_results

# add +x fasta if data format is *.fasta
checkm2 predict --threads 50 --input ./genome -x fasta --output-directory ./genome_checkm2_results
 ```
### CheckM

https://github.com/Ecogenomics/CheckM

 ```
checkm lineage_wf -t 8 -x fa /home/donovan/bins /home/donovan/checkm

checkm lineage_wf --genes -t 8 -x faa <bin folder> <output folder>
 ```

### AMBER

https://github.com/CAMI-challenge/AMBER

> Only CAMI Golden Standard Sample can be evaluated by AMBER

 ```

 ```
