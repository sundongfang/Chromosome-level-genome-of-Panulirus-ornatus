# Chromosome-level-genome-of-Panulirus-ornatus
## Genome Assembly Steps, Software Types and Software Parameters
### Step 1: Assemble contig sequence
The pacbio platform was used for sequencing, and the amount of third generation data was measured to be 292.02G, 
with a coverage depth of 115.67× (calculated according to the genome size of 2524.70M predicted by SURVEY). 
Using all third generations of data, preliminary assembly was performed using falcon software to obtain the contigs sequence of the genome.

```
Software: wtdbg
Version: 2.5
Parameters: ND0.20_NL2304_NM200_WS0.05_WE3_TAIL9216
max_depth = 50
node-drop=0.25,0.20
node-len=1024,1536,2048
node-max=200
brute_force=1
kmer=21
```

### Step 2 : Perform three-generation error correction on the genome
Using all the third generations of data, use arrow software to perform third generations of error correction on the contigs sequence of the genome, and get the genome sequence after error correction.
 ```  
Software: ARROW
Version: Smrtlink_8.0
Parameters: Default parameters
```
### Step 3: Second-generation error correction of the genome
Pair end sequencing was performed by Illumina Hiseq sequencing platform, and the total sequencing volume obtained was 182.90G with a coverage depth of 72.44×. Using pilon software, the genome was subjected to second generation error correction.
```
Software: pilon
Version number: pilon-1.22
Parameters: Default parameters
```
### Step 4: Mount the chromosome
According to the 456.71G Hi-C data obtained from sequencing, the contigs/scaffolds sequences obtained from assembly were uplifted to the chromosome level using all-hic software to obtain the chromosome genome.
```
Software : all.hic
Parameters :
break=N
CLUSTER=73
filter=yes
MaxLinkDensity=3
longest_=800
enz=mboI
format_=Sanger
NonInformativeRatio=0
shortest_=150
minREs=50
fill=yes
```
