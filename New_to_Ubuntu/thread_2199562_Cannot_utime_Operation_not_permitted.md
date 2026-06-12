---
title: "Cannot utime: Operation not permitted"
date: 2014-01-14
forum: New to Ubuntu
---

### Post by ebarongo82 on 2014-01-14
I have downloaded the pal2nal package but I am not permitted to do anything on it. I cannot even delete it to start afresh. What is the way forward? 


edson@samsung:~$ wget [http://www.bork.embl.de/pal2nal/distribution/pal2nal.v14.tar.gz](http://www.bork.embl.de/pal2nal/distribution/pal2nal.v14.tar.gz)
--2014-01-14 22:29:47--  [http://www.bork.embl.de/pal2nal/distribution/pal2nal.v14.tar.gz](http://www.bork.embl.de/pal2nal/distribution/pal2nal.v14.tar.gz)
Resolving [www.bork.embl.de](www.bork.embl.de) ([www.bork.embl.de](www.bork.embl.de))... 194.94.44.35
Connecting to [www.bork.embl.de](www.bork.embl.de) ([www.bork.embl.de)|194.94.44.35|:80](www.bork.embl.de)|194.94.44.35|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17031 (17K) [application/x-gzip]
Saving to: ‘pal2nal.v14.tar.gz’

100%[======================================>] 17,031      12.0KB/s   in 1.4s   

2014-01-14 22:29:53 (12.0 KB/s) - ‘pal2nal.v14.tar.gz’ saved [17031/17031]

edson@samsung:~$ tar vxzf pal2nal.v14.tar.gzpal2nal.v14/
pal2nal.v14/pal2nal.pl
tar: pal2nal.v14/pal2nal.pl: Cannot open: File exists
pal2nal.v14/for_paml/
pal2nal.v14/for_paml/test.cnt
tar: pal2nal.v14/for_paml/test.cnt: Cannot open: File exists
pal2nal.v14/for_paml/test.codeml.ori
tar: pal2nal.v14/for_paml/test.codeml.ori: Cannot open: File exists
pal2nal.v14/for_paml/test.tree
tar: pal2nal.v14/for_paml/test.tree: Cannot open: File exists
pal2nal.v14/test.aln
tar: pal2nal.v14/for_paml: Cannot utime: Operation not permitted
tar: pal2nal.v14/test.aln: Cannot open: File exists
pal2nal.v14/README
tar: pal2nal.v14/README: Cannot open: File exists
pal2nal.v14/test.nuc
tar: pal2nal.v14/test.nuc: Cannot open: File exists
tar: pal2nal.v14: Cannot utime: Operation not permitted
tar: Exiting with failure status due to previous errors

---

### Post by oldos2er on 2014-01-14
What does the README say?

---

### Post by ebarongo82 on 2014-01-14
You mean the contents of README?


```
PAL2NAL is a program that converts a multiple sequence alignment
of proteins and the corresponding DNA (or mRNA) sequences into
a codon-based DNA alignment. The program automatically assigns
the corresponding codon sequence even if the input DNA sequence
has mismatches with the input protein sequence, or contains UTRs,
polyA tails. It can also deal with frame shifts in the input
alignment, which is suitable for the analysis of pseudogenes.
The resulting codon-based DNA alignment can further be subjected
to the calculation of synonymous (Ks) and non-synonymous (Ka)
substitution rates.


#-----------#
# Reference
#-----------#

If you use PAL2NAL, please cite the following paper:

  - Mikita Suyama, David Torrents, and Peer Bork (2006)
    PAL2NAL: robust conversion of protein sequence alignment into
    the corresponding codon alignments.
    Nucleic Acids Res. 34:W609-W612.


#-------#
# Files
#-------#

The distribution version should contain the following files:

    README                 - This document
    pal2nal.pl             - The script (version 14) (written in Perl)
    test.aln               - test data (protein alignment)
    test.nuc               - test data (DNA sequences)

    for_paml (directory)
      test.cnt             - control file for codeml
      test.tree            - tree file used for codeml
      test.codeml.ori      - an example of codeml output


#-------#
# Usage
#-------#

Usage:  pal2nal.pl  pep.aln  nuc.fasta  [nuc.fasta...]  [options]

    pep.aln:     protein alignment either in CLUSTAL or FASTA format

                 - works not only a pairwise alignment but also
                   the alignment with more than 2 sequences.

                 - if there are frame shifts in your alignment,
                   you have to specify those positions by numbers:
                   for example '2' in the alignment means that
                   there are only two bases (i.e. one base deletion)
                   (see 'test.aln').


    nuc.fasta:   DNA sequences
                 (single multiple fasta format file,
                  or may be separated files)

    Options:

       -h            Show help

       -output (clustal|paml|fasta|codon)
                     Output format, default = clustal

       -blockonly    Show only user specified blocks
                     '#' under CLUSTAL alignment (see example)

       -nogap        remove columns with gaps and inframe stop codons

       -nomismatch   remove mismatched codons (mismatch between
                     pep and cDNA) from the output

       -codontable (1(default)|2|3|4|5|6|9|10|11|12|13|14|15|16|21|22|23)
                     NCBI GenBank codon table
                     1  Universal code
                     2  Vertebrate mitochondrial code
                     3  Yeast mitochondrial code
                     4  Mold, Protozoan, and Coelenterate Mitochondrial code
                        and Mycoplasma/Spiroplasma code
                     5  Invertebrate mitochondrial
                     6  Ciliate, Dasycladacean and Hexamita nuclear code
                     9  Echinoderm and Flatworm mitochondrial code
                    10  Euplotid nuclear code
                    11  Bacterial, archaeal and plant plastid code
                    12  Alternative yeast nuclear code
                    13  Ascidian mitochondrial code
                    14  Alternative flatworm mitochondrial code
                    15  Blepharisma nuclear code
                    16  Chlorophycean mitochondrial code
                    21  Trematode mitochondrial code
                    22  Scenedesmus obliquus mitochondrial code
                    23  Thraustochytrium mitochondrial code

       -html         HTML output (only for the web server)

       -nostderr     No STDERR messages (only for the web server)



    - The correspondence of IDs between pep.aln and nuc.fasta is
      automatically checked:
        - If you use the same IDs in both pep.aln and nuc.fasta,
          the sequences don't have to be in the same order.
        - If not, the order of the sequences in pep.aln and nuc.fasta
          has to be the same.

    - IDs in pep.aln are used in the output.


Example:  pal2nal.pl  test.aln  test.nuc  -output paml  -nogap


#---------------------------------#
# How to calculate Ks, Ka values?
#---------------------------------#

To calclate Ks, Ka values, you need the codeml program, which
is included in the PAML package. You can download PAML from

  [http://abacus.gene.ucl.ac.uk/software/paml.html](http://abacus.gene.ucl.ac.uk/software/paml.html)

As an example, a control file (test.cnt) and a tree file (test.tree)
are in the "for_paml" sub-directory.

These control file and tree file are designed for the 'test' data
used in PAL2NAL.

Example:

   pal2nal.pl  test.aln  test.nuc  -output paml  -nogap  >  for_paml/test.codon

   cd for_paml

   codeml  test.cnt

     You can find the output of codeml in "test.codeml".
     Ks, Ka values are very end of the output file.
     Just for comparison, there is a sample output file, "test.codeml.ori".
```

---

### Post by oldos2er on 2014-01-14
I added code tags to your post to make it a bit easier to read. See [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode) for more about that.

So the Usage section tells you how to run the program. For specialized software like that you're more likely to get help with it by contacting its developers, rather than these forums. Just a thought.

---

### Post by spjackson on 2014-01-14
Are you trying to extract the tar onto a non-Linux filesystem e.g. USB drive or a mounted Windows partition? If so, try extracting it onto a Linux filesystem.

---

### Post by ebarongo82 on 2014-01-15
> **spjackson said:**
> Are you trying to extract the tar onto a non-Linux filesystem e.g. USB drive or a mounted Windows partition? If so, try extracting it onto a Linux filesystem.

 The tar is onto linux filesystem. The  log implies the copy exists and can't be overwritten. I resolved to delete everything up and re-install. But the directory containing the package seems to be locked (there is even a lock signal over the folder) so any operation on the files within is not permitted.

---

### Post by ebarongo82 on 2014-01-15
> **spjackson said:**
> Are you trying to extract the tar onto a non-Linux filesystem e.g. USB drive or a mounted Windows partition? If so, try extracting it onto a Linux filesystem.

The issues are now solved. It was something to do with changing the permission mode and so it is okay now. 

```
 sudo chmod -R 777 pal2nal.v14
```

---

