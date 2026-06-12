---
title: "Using bash to obtain numbers in diffreent lines"
date: 2014-01-27
forum: Programming Talk
---

### Post by Muriel_Gros-Baltha on 2014-01-27
Hello,

I have a file containing many lines of that type :
KE340296.1    823    .    G    A    61.72    .    AC=1;AF=0.042;AN=24;BaseQRankSum=1.327;ClippingRankSum=-0.175;DP=45;FS=0.000;InbreedingCoeff=-0.1226;MLEAC=1;MLEAF=0.042;MQ=36.73;MQ0=0;MQRankSum=1.126;QD=12.34;ReadPosRankSum=-0.476    GT:AD:DP:GQ:PL    0/0:4,0:4:12:0,12,128    0/0:1,0:1:3:0,3,34    0/0:7,0:7:21:0,21,197    0/0:2,0:2:6:0,6,68    0/0:3,0:3:9:0,9,79    0/0:7,0:7:21:0,21,1940/0:1,0:1:3:0,3,37    0/0:2,0:2:6:0,6,78    0/1:2,3:5:44:95,0,44    0/0:4,0:4:12:0,12,142    0/0:2,0:2:6:0,6,66    0/0:3,0:3:9:0,9,97

How can I grep the number that followed DP in column 8 ?
What I would like is for each line, grep the number following DP and put that number in a list so that I can latter make a graph of the distribution.

Thanks a lot for your help,

Muriel

---

### Post by ofnuts on 2014-01-27
> **Muriel_Gros-Baltha said:**
> Hello,

I have a file containing many lines of that type :
KE340296.1    823    .    G    A    61.72    .    AC=1;AF=0.042;AN=24;BaseQRankSum=1.327;ClippingRankSum=-0.175;DP=45;FS=0.000;InbreedingCoeff=-0.1226;MLEAC=1;MLEAF=0.042;MQ=36.73;MQ0=0;MQRankSum=1.126;QD=12.34;ReadPosRankSum=-0.476    GT:AD:DP:GQ:PL    0/0:4,0:4:12:0,12,128    0/0:1,0:1:3:0,3,34    0/0:7,0:7:21:0,21,197    0/0:2,0:2:6:0,6,68    0/0:3,0:3:9:0,9,79    0/0:7,0:7:21:0,21,1940/0:1,0:1:3:0,3,37    0/0:2,0:2:6:0,6,78    0/1:2,3:5:44:95,0,44    0/0:4,0:4:12:0,12,142    0/0:2,0:2:6:0,6,66    0/0:3,0:3:9:0,9,97

How can I grep the number that followed DP in column 8 ?
What I would like is for each line, grep the number following DP and put that number in a list so that I can latter make a graph of the distribution.

Thanks a lot for your help,

Muriel

Technically, you don't want to grep the number (because you don't know it...) you want to extract it. You can use sed to replace the whole line by just the sequence of digits that follows "DP=":
```

sed -re 's/.*DP=([0-9]+).*/\1/'

```

---

### Post by Muriel_Gros-Baltha on 2014-01-27
This works perfectly thanks a lot for your help !

Can you however explain me why there is \1 ???
If I understand well, you start by s for saying that a regex is following.
Then you take every number following DP and before the next dot. But what is the end ?
Thanks !!

And sorry for not using the good word (extract, grep...) I'm new in this type of thing ! (But I love it !!)

---

### Post by Lars Noodén on 2014-01-27
\1 refers to the first subexpression in the pattern.  It is what is between the parenthesis, in this case the first set is the only set since there is only one set of parenthesis in the  pattern.

[http://www.grymoire.com/unix/sed.html](http://www.grymoire.com/unix/sed.html)

---

### Post by ofnuts on 2014-01-27
> **Muriel_Gros-Baltha said:**
> This works perfectly thanks a lot for your help !

Can you however explain me why there is \1 ???
If I understand well, you start by s for saying that a regex is following.
Then you take every number following DP and before the next dot. But what is the end ?
Thanks !!

And sorry for not using the good word (extract, grep...) I'm new in this type of thing ! (But I love it !!)
Not really. In slow motion:

[LIST]
[*]s/something/something else/ is thr "substitute" command in sed, everything that mactches "something" is replaced by "something else"
[*]Of course a frequent usage is to use a regular expression for "something"
[*]Parentheses in the regular expression delimit "groups" that act a bit like variables that are assigned what has been matched by the part of the regexp between the parentheses (here the string of digits after "DP=")
[*]\1...\9 in the second part are references to these groups/variables set while matching the first part
[*]The '.*' before and after match anything  so this whole thing reads:
[LIST]
[*]in each line, take any sequence of characters, then "DP=", then a sequence of digits, then any other sequence of characters
[*]replace that (which is the whole line) by just the sequence of characters
[/LIST]
[/LIST]
 
Google around for more info on "regular expression". If you want the fast track from noob to regexp guru, read: the ["Owl book"]("http://www.amazon.com/Mastering-Regular-Expressions-Jeffrey-Friedl/dp/0596528124/"). A very easy read...

---

### Post by Muriel_Gros-Baltha on 2014-01-27
OK thanks a lot for the explanation !

However, I have problem in extracting what follows AC and AF.
Indeed, if I do : 
sed -re 's/.*AC=([0-9]+).*/\1/'
and 
sed -re 's/.*AF=([0-9]+).*/\1/'

I extract what follows MLEAC and MLEAF !
I tried to put ; before but it doesn't work.

For AC, I found a way. I extract the 8th column using awk.
And I use ^ since AC is at the beginnign of the line.
But what I obtain is not only the numbers, I have "AC=5".
But I replaced AC= by nothing with sed and it worked.
However, that's a lot of steps while I am sure that a simple one is possible !

For AF, I tried this :
sed -re 's/^AC=([0-9]+).*.*AF=([0-9]+).*/\2/'
However, I obtain just 0, since the numbers are decimal, but I also need those decimals !!

And I also tried with BaseQRankSum or ClippingRankSum.
I believe there is also problem with decimal and also negative numbers ???

Can't I just say that I want to replace everything until ;"EXP=decimal number" and everything that follows by this decimal number ?

I just borrowed at the library the book you advice and will try to find a way !

Muriel

---

### Post by steeldriver on 2014-01-27
Can you repost your data between CODE tags please? it's hard to see what the format really is

If it really is columnar or delimited data there may be more robust ways to parse it

---

### Post by Muriel_Gros-Baltha on 2014-01-27
My data look that way :

```
KE340296.1    823    .    G    A    61.72    .     AC=1;AF=0.042;AN=24;BaseQRankSum=1.327;ClippingRankSum=-0.175;DP=45;FS=0.000;InbreedingCoeff=-0.1226;MLEAC=1;MLEAF=0.042;MQ=36.73;MQ0=0;MQRankSum=1.126;QD=12.34;ReadPosRankSum=-0.476    GT:AD:grin:P:GQ:razz:L     0/0:4,0:4:12:0,12,128    0/0:1,0:1:3:0,3,34    0/0:7,0:7:21:0,21,197     0/0:2,0:2:6:0,6,68    0/0:3,0:3:9:0,9,79     0/0:7,0:7:21:0,21,1940/0:1,0:1:3:0,3,37    0/0:2,0:2:6:0,6,78     0/1:2,3:5:44:95,0,44    0/0:4,0:4:12:0,12,142    0/0:2,0:2:6:0,6,66     0/0:3,0:3:9:0,9,97
```

Actually, the 8th column started with AC and finishes with ReadPosRankSum=-0.476.

To wotk more easily, I extracted the 8th column but there is probably another way !

---

### Post by Vaphell on 2014-01-27
[noparse]```

```[/noparse] not [noparse]> [/noparse]
code uses monospace font, doesn't affect whitespaces and doesn't put emoticons in (=preserves original format with indentation and stuff)

---

### Post by Muriel_Gros-Baltha on 2014-01-27
Sorry, I didn't know how to do, I changed it above ;)

---

### Post by Vaphell on 2014-01-27
i don't know what you need exactly, but awk is definitely the way to go.

example
```
$ awk '{ n=split($8, arr, "[;=]"); for(i=1; i<n; i+=2){ print $1 ": " [COLOR="#0000FF"]arr[i][/COLOR] "=" [COLOR="#008000"]arr[i+1][/COLOR] }; }' data.txt
KE340296.1: [COLOR="#0000FF"]AC[/COLOR]=[COLOR="#008000"]1[/COLOR]
KE340296.1: [COLOR="#0000FF"]AF[/COLOR]=[COLOR="#008000"]0.042[/COLOR]
KE340296.1: [COLOR="#0000FF"]AN[/COLOR]=[COLOR="#008000"]24[/COLOR]
KE340296.1: [COLOR="#0000FF"]BaseQRankSum[/COLOR]=[COLOR="#008000"]1.327[/COLOR]
KE340296.1: [COLOR="#0000FF"]ClippingRankSum[/COLOR]=[COLOR="#008000"]-0.175[/COLOR]
KE340296.1: [COLOR="#0000FF"]DP[/COLOR]=[COLOR="#008000"]45[/COLOR]
KE340296.1: [COLOR="#0000FF"]FS[/COLOR]=[COLOR="#008000"]0.000[/COLOR]
KE340296.1: [COLOR="#0000FF"]InbreedingCoeff[/COLOR]=[COLOR="#008000"]-0.1226[/COLOR]
KE340296.1: [COLOR="#0000FF"]MLEAC[/COLOR]=[COLOR="#008000"]1[/COLOR]
KE340296.1: [COLOR="#0000FF"]MLEAF[/COLOR]=[COLOR="#008000"]0.042[/COLOR]
KE340296.1: [COLOR="#0000FF"]MQ[/COLOR]=[COLOR="#008000"]36.73[/COLOR]
KE340296.1: [COLOR="#0000FF"]MQ0[/COLOR]=[COLOR="#008000"]0[/COLOR]
KE340296.1: [COLOR="#0000FF"]MQRankSum[/COLOR]=[COLOR="#008000"]1.126[/COLOR]
KE340296.1: [COLOR="#0000FF"]QD[/COLOR]=[COLOR="#008000"]12.34[/COLOR]
KE340296.1: [COLOR="#0000FF"]ReadPosRankSum[/COLOR]=[COLOR="#008000"]-0.476[/COLOR]

```

8th column gets sliced on ; and =, storred in array arr, and then the (name, value) pairs are printed out on separate lines.

---

### Post by ofnuts on 2014-01-27
> **Muriel_Gros-Baltha said:**
> OK thanks a lot for the explanation !

However, I have problem in extracting what follows AC and AF.
Indeed, if I do : 
sed -re 's/.*AC=([0-9]+).*/\1/'
and 
sed -re 's/.*AF=([0-9]+).*/\1/'

I extract what follows MLEAC and MLEAF !
I tried to put ; before but it doesn't work.

For AC, I found a way. I extract the 8th column using awk.
And I use ^ since AC is at the beginnign of the line.
But what I obtain is not only the numbers, I have "AC=5".
But I replaced AC= by nothing with sed and it worked.
However, that's a lot of steps while I am sure that a simple one is possible !

For AF, I tried this :
sed -re 's/^AC=([0-9]+).*.*AF=([0-9]+).*/\2/'
However, I obtain just 0, since the numbers are decimal, but I also need those decimals !!

And I also tried with BaseQRankSum or ClippingRankSum.
I believe there is also problem with decimal and also negative numbers ???

Can't I just say that I want to replace everything until ;"EXP=decimal number" and everything that follows by this decimal number ?

I just borrowed at the library the book you advice and will try to find a way !

Muriel
The general solution is to prefix the names you search by '\W' which means "anything but a word letter (A-Z,a-z,0-9,and underscore). Then "\WAC" cannot be matched in "MLEAC" because the "E" is a word letter.

So for "AC": (btw, there is no ";" there):
```

's/.*\WAC=([0-9]+).*/\1/'

```

Then for MLEAC:
```

's/.*\WMLEAC=([0-9]+).*/\1/'

```

But if you need to extract each field it may be more efficient to do everything in one pass if the data file is big. But we can't make useful suggestions if we don't know the bigger picture.

---

### Post by drmrgd on 2014-02-08
A bit late to the party, but in case the OP is still reading this, thought I would offer a suggestion.  What you seem to be working with is a VCF file.  It may be a lot easier to parse the file with VCF Tools instead of manually pulling data out.  For example, I think you can pull out the data you want, plus the variant position and allele information in this way:

```

vcf-query <input_vcf_file> -f '%CHROM:%POS\t%REF\t%ALT\t[%DP]\n'

```

I might not have that format quite correct since I don't have your VCF in front of me.  But, at any rate, you can pull out the data you want with regexes and such as others have suggested, but in the end VCF Tools is set up better to parse these files than home brew methods and once you figure out how to use the tool, I think you'll find it much easier too.

**edit**: I see you want more fields and thought I would post a real world example.  Suppose you have a VCF file with information like this (from Ion Torrent sequencing data):

```

chr1     11194505        .       T       C       14.9    PASS    AO=14;DP=350;FAO=14;FDP=350;FR=.;FRO=336;FSAF=6;FSAR=8;FSRF=132;FSRR=204;FWDB=0.0886193;FXX=0;HRUN=1;LEN=1;MLLD=286.784;QD=0.170289;RBI=0.0886574;REFB=-0.000686145;REVB=0.00259716;RO=336;SAF=6;SAR=8;SRF=132;SRR=204;SSEN=0;SSEP=0;SSSB=0.0324758;STB=0.535304;TYPE=snp;VARB=0.0206353;OID=.;OPOS=11194505;OREF=T;OALT=C;OMAPALT=C   GT:GQ:DP:FDP:RO:FRO:AO:FAO:SAR:SAF:SRF:SRR:FSAR:FSAF:FSRF:FSRR  0/1:14:350:350:336:336:14:14:8:6:132:204:8:6:132:204

```

In order for me to get the data I usually like to have for some of my analysis, I extract:

CHROM
POS
REF
ALT
FILTER
FR
GTR
GT
FDP
FRO
FAO

So, I could run this command:

```

$ vcf-query test.vcf -f '%CHROM:%POS\t%REF\t%ALT\t%FILTER\t%INFO/FR\t[%GTR\t%GT\t%FDP\t%FRO\t%FAO]\n'

```

which will generate output that looks like this:

```

chr1:11194505   T       C       PASS    .       0/1     T/C     350     336     14
chr1:11259281   T       G       PASS    .       0/1     T/G     6       3       3
chr1:11288758   G       A       PASS    .       1/1     A/A     1918    0       1918
chr1:11301714   A       G       PASS    .       1/1     G/G     1996    0       1996
chr2:47630550   C       G       PASS    .       0/1     C/G     1386    474     912
chr2:47635722   AT      A       NOCALL  .,PREDICTIONSHIFTx0.490781      ./.     ./.     981     981     0
chr2:47639587   GA      G       NOCALL  .,PREDICTIONSHIFTx0.349565      ./.     ./.     833     833     0
chr2:47641560   A       T       NOCALL  .,PREDICTIONSHIFTx0.452707      ./.     ./.     1313    1313    0

```

You can see it's a lot easier than manually parsing the whole file, and if you wanted, you can call that from a perl script that will go even further to calculate VAF or to filter out variants that you don't want to see (e.g. variants that didn't pass filter).

---

