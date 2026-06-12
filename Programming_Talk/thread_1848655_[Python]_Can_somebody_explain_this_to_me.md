---
title: "[Python] Can somebody explain this to me???"
date: 2011-09-22
forum: Programming Talk
---

### Post by Dhiraj Thakur(Invincible) on 2011-09-22
```

>>> a = 1
>>> b = 1
>>> b is a
True
>>> a = 6000
>>> b = 6000
>>> b is a
False
 
```

---

### Post by JDShu on 2011-09-23
Interesting.

After I did some experimentation, it appears that when you assign a name to an integer between 0 and 256 inclusively, Python assigns predetermined memory locations that contain that integer to the name. For numbers over 256, Python seems to create a new memory location and fill it with the desired number, before pointing the name to that memory location.

I suspect that this behavior is unique to cpython and isn't something you should rely on as it probably works differently in other Python implementations.

---

### Post by Aprile79 on 2011-09-23
Talking about python can somebody help me with my script?
 
Hi I am busy working with biological sequences, but I am having some problems. 
Let's say that I want to compare two dna sequences i.e
seq1='ATGGAGGCAATGGCGGCCAGCACTTCCCTGCCTGACCCTGGAGACTTTGACCGGAACGTG
CCCCGGATCTGTGGGGTGTGTGGAGACCGAGCCACTGGCTTTCACTTCAATGCTATGACC
TGTGAAGGCTGCAAAGGCTTCTTCAGGCGAAGCATGAAGCGGAAGGCACTATTCACCTGC
CCCTTCAACGGGGACTGCCGCATCACCAAGGACAACCGACGCCACTGCCAGGCCTGCCGG
CTCAAACGCTGTGTGGACATCGGCATGATGAAGGAGTTCATTCTGACAGATGAGGAAGTG'

seq2='ATGGAGGCAATGGCGGCCAGCACTTCCCTGCCTGACCCTGGAGACTTTGACCGGAATGTG
CCCCGGATCTGTGGGGTGTGTGGAGACCGAGCCACTGGCTTTCACTTCAATGCTATGACC
TGTGAAGGCTGCAAAGGCTTCTTCAGGCGAAGCATGAAGCGGAAGGCACTATTCACCTGC
CCCTTCAATGGGGACTGCCGCATCACCAAGGACAACCGGCGCCACTGCCAGGCCTGCCGG
CTCAAACGCTGTGTGGACATCGGCATGATGAAGGAGTTCATCCTGACAGATGAGGAAGTG
CAGAGGAAGCGGGAGATGATCCTGAAGCGGAAGGAGGAGGAGGCCTTGAAGGACAGTCTG
CGGCCCAAGCTGTCTGAGGAGCAGCAGCGCATCATTGCCATACTGCTGGACGCCCACCAT
AAGACCTACGACCCCACCTACTCCGACTTCTGCCAGTTCCGGCCTCCAGTTCGTGTGAAT
GATGGTGGAGGGAGCCATCCTTCCAGGCCCAACTCCAGACACACTCCCAGCTTCTCTGGG
GACTCCTCCTCCTCCTGCTCAGATCACTGTATCACCTCTTCAGACATGATGGAC---TCG'

Thus my aim is to identify variations between those two sequences in term of codons, and the position in which the changed codon falls. Then I want to know the amino acid product related to that codon. Any helps?
this is what I done so far but I cannot see exactly want I want:

def sequence_compare(seq_a, seq_b):
len1= len(seq_a)
len2= len(seq_b)
mismatches = []
for pos in range (0,min(len1,len2)) :
if seq_a[pos] != seq_b[pos]:
mismatches.append('|')
else:
mismatches.append(' ')
print (seq_a)
print (mismatches)
print (seg_b)
sequence_compare(seq_a,seq_b)

Basically I would like to see something like: ATC-ATT and the related amino acid changed.

any suggestions??

---

### Post by ofnuts on 2011-09-23
> **Aprile79 said:**
> Talking about python can somebody help me with my script?
 
Hi I am busy working with biological sequences, but I am having some problems. 
May I suggest starting another thread for this?

---

### Post by nvteighen on 2011-09-23
> **Dhiraj Thakur(Invincible) said:**
> ```

>>> a = 1
>>> b = 1
>>> b is a
True
>>> a = 6000
>>> b = 6000
>>> b is a
False
 
```

Very roughly, the 'is' operator compares the memory locations of some object. Doing this on unmutable data types (like integers) yields undefined behavior and it's quite nonsensical to do so, because... well... them being unmutable makes it completely irrelevant to know whether 1 is stored at the same place or not (in the case of a, b), because all you care about is that their value is 1.

Instead, 'is' is more useful for mutable data structures, lists and classes mostly, because for them equality of value does not imply identity. E.g. if you have two objects A and B of class C, they may at some point have the same values... but are they the same object? Are two Volkswagen Polo cars the same object? So, when you not only want to know whether two objects are the same in value, but you want to be sure that two variables are pointing to the very same object, you should use 'is'.

> **Aprile79 said:**
> Talking about python can somebody help me with my script?


Please, start a new thread and use the [NOPARSE]```

```[/NOPARSE] tags to include code.

---

