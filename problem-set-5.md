
#Stefan Haugen
# Overview
For this problem set you will write a series of python programs to perform
sequence analysis tasks. Please edit this document to include your answers and
include your scripts in your pull request.  

## Problem 1
Write a python program that reports the number of intervals for each
chromosome in a bed file. Write the program as a python script named
``problem_1.py``. 

Execute your program on the ``data-sets/bed/lamina.bed`` file:

```bash
python3 problem_1.py 



from collections import Counter

counts = Counter()

for line in open('/Users/stefanhaugen/temp/data-sets/bed/lamina.bed'):

if line.startswith('#'): continue

fields = line.split('\t')

chrom = fields[0]

counts[chrom] += 1

##there must be a better way to sort dictionaries here...

for chrom, count in counts.items():
	sortme = [(v,k) for k,v in counts.items()]
	sortme
	sortme.sort()
	sortme.reverse()
	
print(sortme[0][1])
```

Which chromosome has the most intervals?
``problem_1.py``

## Problem 2
Write a python program that parses a fastq file and determines the total number
of ``C`` bases in the fastq. Write the program as a python script named
``problem_2.py``.

Execute your program on the ``data-sets/fastq/SP1.fq`` file.

```bash

python3 problem_2.py SP1.fq

import sys
from collections import Counter

filename = sys.argv[1]

count = 0

bases = Counter()

for line in open('~/temp/data-sets/fastq/SP1.fq'):
	line = line.rstrip()
	if count == -:
		name = line
		count += 1
		
	elif count == 1:
		seq = line
		count += 1
		
	elif count == 2
		 count += 1
		 
	elif count == 3:
		qual = line
		count = 0
		
		for base in seq:
			bases[base] += 1
			
print(bases['C'])

```

What is the total number of ``C`` bases?
``problem_2.py``

## Problem 3:
Write a python program that parses a fastq file and determines the most
common 6-mer (aka hexamer) sequence at the 5' and also the 3' end of each read. 
Write the program as a python script named ``problem_3.py``

```
python3 problem_3.py

for i in range(0, line.length-1):

     if (line.length-1) - i >= 6:

           hexamer = line[i] line[ i+1] line[ i+2] line[i+3] line [i+4] line [i + 5]

            aka_hexamers_5[hexamer] +=1

```

```

What is the most common hexamer at the 5' end?
``write your answer here``

What is the most common hexamer at the 3' end?
``write your answer here``

## Problem 4:

The ``pysam`` package makes it easy to parse through a ``bam`` file
and extract important attributes. For this problem write a python program
named ``problem_4.py`` that parses a bam file and reports the following metrics: 
    
1. The total number of alignments on the positive and the negative strand. 
Use the Sam Flag attribute to determine if the alignment is on the forward or reverse
strand. 16 indicates an alignment on the reverse strand and 0 defines positive 
for this experiment. (hint: use the ``.flag`` attribute of an ``AlignedSegment``). More
information about these Flags in section 1.4 of the SAM [specification](http://samtools.github.io/hts-specs/SAMv1.pdf) 
    
2. The total number of alignments with no mismatches and the number of alignments
with more than zero mismatches. The NM tag records the edit distance between
the sequence and the reference. (hint: use the ``.get_tag()`` method to extract
the ``NM`` tag value). 

FYI to view the contents of a bam file as plain-text, use samtools view:

```bash
samtools view file.bam | less
```

How many positive strand aligned reads are there?
``your answer here``

How many negative strand aligned reads?
``your answer here``

How many alignments with no mismatches?
``your answer here``

How many alignments with more than zero mismatches?
``your answer here``

