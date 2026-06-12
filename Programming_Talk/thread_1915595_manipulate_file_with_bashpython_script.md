---
title: "manipulate file with bash/python script"
date: 2012-01-26
forum: Programming Talk
---

### Post by abraxas334 on 2012-01-26
Hi, I am trying to manipulate a file, which is a mix of text and numbers.
To be precise it requires the alteration of the third column, provided that the line starts with a number. My first approach was using sed, but there i was just looking for numbers in general and thus would change all the number in that particular line. 
How can I tell sed to only change the character in the 3rd column. My current script looks like this:
[PHP]
#!/bin/bash
file="./dynamin_dimer_fg_Protein_chain_B1.itp"
for ((i=1; i<=6; i++))
do
k=`expr $i - 5 + 741`
#echo $k
#echo $i
sed -i  '1,8379{25}s/     '$i' /     '$k' /g' $file
done
vi $file


[/PHP]


An expert of the file looks like this:

```

;       Command line was:
;       pdb2gmx -f dynamin_dimer_phfitted.pdb -o dynamin_dimer_fg.gro -p dynamin_dimer_fg.top -ignh
;
;       Force field was read from the standard Gromacs share directory.
;

[ moleculetype ]
; Name            nrexcl
Protein_chain_B     3

[ atoms ]
;   nr       type  resnr residue  atom   cgnr     charge       mass  typeB    chargeB      massB
; residue   6 MET rtp MET  q +1.0
     1         NL      6    MET      N      1      0.129    14.0067   ; qtot 0.129
     2          H      6    MET     H1      1      0.248      1.008   ; qtot 0.377
     3          H      6    MET     H2      1      0.248      1.008   ; qtot 0.625
     4          H      6    MET     H3      1      0.248      1.008   ; qtot 0.873
     5        CH1      6    MET     CA      2      0.127     13.019   ; qtot 1
     6        CH2      6    MET     CB      2          0     14.027   ; qtot 1
     7        CH2      6    MET     CG      3      0.241     14.027   ; qtot 1.241
     8          S      6    MET     SD      3     -0.482      32.06   ; qtot 0.759
     9        CH3      6    MET     CE      3      0.241     15.035   ; qtot 1
    10          C      6    MET      C      4       0.45     12.011   ; qtot 1.45
    11          O      6    MET      O      4      -0.45    15.9994   ; qtot 1
; residue   7 GLU rtp GLU  q -1.0
    12          N      7    GLU      N      5      -0.31    14.0067   ; qtot 0.69
    13          H      7    GLU      H      5       0.31      1.008   ; qtot 1



```
So basically I am trying to manipulate the column headed resnumber, so that the counting starts at 1 and not 6. The file is obviously too large in order to do this manually.


The solution does not have to be bash (awk sed whatever), any suggestions are greatly appreciated.
Thanks for the help.

---

### Post by Vaphell on 2012-01-26
```
awk 'BEGIN { OFS="\t" }
     $1 !~ /[0-9]+/{ print }
     $1 ~ /[0-9]+/{ $3=$3-5; print }' in.txt
```
formatting may be off a bit

---

### Post by ofnuts on 2012-01-26
The sed solution:
```
sed -re 's/^(\s+[0-9]+\s+\w+\s+)'$i'/\1'$k'/' < data
```basically you create a regexp that matches

[LIST]
[*]start of line
[*]spaces
[*]digits
[*]more space
[*]word characters
[*]some more space
[*]your number
[/LIST]
and you replace it with:

[LIST]
[*]all the above minus your number (what is inside the parens in the first member replaces the '\1' in the second)
[*]whatever you need to replace your number with
[/LIST]

---

### Post by Vaphell on 2012-01-26
heh, i figured out pretty much the same sed solution, but dumped it because who knows how many $i's there would be. Running sed 1000 times for 1000 different integers would not be so cool.
Also I see a minor caveat: $i needs to be followed by another space segment, otherwise $i=1 will match any 1[0-9]+
i suggest ```
's/^(\s+[0-9]+\s+\w+\s+)'$i'**(\s+.*)$**/\1'$k'**\2**/'
```

---

### Post by ofnuts on 2012-01-27
> **Vaphell said:**
> heh, i figured out pretty much the same sed solution, but dumped it because who knows how many $i's there would be. Running sed 1000 times for 1000 different integers would not be so cool.
Also I see a minor caveat: $i needs to be followed by another space segment, otherwise $i=1 will match any 1[0-9]+
i suggest ```
's/^(\s+[0-9]+\s+\w+\s+)'$i'**(\s+.*)$**/\1'$k'**\2**/'
```
I wondered too... but you can have set run mutilple s/// commands in one pass... the only real advantage of awk here is that if you can compute the substituted value from within awk things remain simple.

---

### Post by fra11 on 2012-01-27
Hi all,
actually it was me having this problem and I had a colleague of mine posting the question for me as I didn't have an account before. So I tried the sed command in a .sh script as I needed to make the change recursively

[PHP]
#!/bin/bash
file="./file to change"
for ((i=6; i<=9; i++))
do
k=`expr $i - 5 + 741`
#echo $k
#echo $i
sed -re 's/^(\s+[0-9]+\s+\w+\s+)'$i'(\s+.*)$/\1'$k'\2/' < $file
done
vi $file
[/PHP]

but iti is printing the file unchanged 4 times on the screen and not changing the original file $file as I wanted. :confused:
Can you help me with that? 
Thanks

---

### Post by fra11 on 2012-01-27
Ps I have tried also the awk script with the same result. :cry:

Ps2 I know that in the script I have posted before it doesn't just do $i - 5, that is just because I actually have to apply the same concept to 2 files, one has to start from 1 and the other from 741...

thanks again and please please help me!!!![-o<

---

### Post by Vaphell on 2012-01-27
how is awk line not working?
i copied your data into in.txt
output of slightly modified command
```
$ awk -v n=-5 'BEGIN { OFS="\t" }
     $1 !~ /[0-9]+/{ print }
     $1 ~ /[0-9]+/{ $3=$3+n; print }' in.txt

...
[ atoms ]
;   nr       type  resnr residue  atom   cgnr     charge       mass  typeB    chargeB      massB
; residue   6 MET rtp MET  q +1.0
1	NL	1	MET	N	1	0.129	14.0067	;	qtot	0.129
2	H	1	MET	H1	1	0.248	1.008	;	qtot	0.377
3	H	1	MET	H2	1	0.248	1.008	;	qtot	0.625
4	H	1	MET	H3	1	0.248	1.008	;	qtot	0.873
5	CH1	1	MET	CA	2	0.127	13.019	;	qtot	1
6	CH2	1	MET	CB	2	0	14.027	;	qtot	1
7	CH2	1	MET	CG	3	0.241	14.027	;	qtot	1.241
8	S	1	MET	SD	3	-0.482	32.06	;	qtot	0.759
9	CH3	1	MET	CE	3	0.241	15.035	;	qtot	1
10	C	1	MET	C	4	0.45	12.011	;	qtot	1.45
11	O	1	MET	O	4	-0.45	15.9994	;	qtot	1
; residue   7 GLU rtp GLU  q -1.0
12	N	2	GLU	N	5	-0.31	14.0067	;	qtot	0.69
13	H	2	GLU	H	5	0.31	1.008	;	qtot	1

```
maybe you need to add 567?
```
$ awk -v n=567 'BEGIN { OFS="\t" }
     $1 !~ /[0-9]+/{ print }
     $1 ~ /[0-9]+/{ $3=$3+n; print }' in.txt

...
[ atoms ]
;   nr       type  resnr residue  atom   cgnr     charge       mass  typeB    chargeB      massB
; residue   6 MET rtp MET  q +1.0
1	NL	573	MET	N	1	0.129	14.0067	;	qtot	0.129
2	H	573	MET	H1	1	0.248	1.008	;	qtot	0.377
3	H	573	MET	H2	1	0.248	1.008	;	qtot	0.625
4	H	573	MET	H3	1	0.248	1.008	;	qtot	0.873
5	CH1	573	MET	CA	2	0.127	13.019	;	qtot	1
6	CH2	573	MET	CB	2	0	14.027	;	qtot	1
7	CH2	573	MET	CG	3	0.241	14.027	;	qtot	1.241
8	S	573	MET	SD	3	-0.482	32.06	;	qtot	0.759
9	CH3	573	MET	CE	3	0.241	15.035	;	qtot	1
10	C	573	MET	C	4	0.45	12.011	;	qtot	1.45
11	O	573	MET	O	4	-0.45	15.9994	;	qtot	1
; residue   7 GLU rtp GLU  q -1.0
12	N	574	GLU	N	5	-0.31	14.0067	;	qtot	0.69
13	H	574	GLU	H	5	0.31	1.008	;	qtot	1

``` adding **> out.txt** at the end will redirect this output to file

---

### Post by fra11 on 2012-01-27
Well I've copied my file in in.txt, then created a .sh script with your commands

[PHP]
#!/bin/bash
awk -v n=-736 'BEGIN { OFS="\t" }
     $1 !~ /[0-9]+/{ print }
     $1 ~ /[0-9]+/{ $3=$3+n; print }' in.txt
vi in.txt
[/PHP]

and if I run the .sh script it prints in the terminal the file in.txt without changing it for many times and then it opens the file which hasn't been changed.
where am I wrong?

---

### Post by fra11 on 2012-01-27
Ehi I might have solved the problem by myself. I just needed to add where to write the file :)
Thanks a lot!!!:D

However I have noticed that the script will do the change for all the lines. How can I tell it to do it only in a certain range of lines?
Thanks

---

### Post by Vaphell on 2012-01-27
[http://en.wikipedia.org/wiki/AWK#Built-in_variables](http://en.wikipedia.org/wiki/AWK#Built-in_variables)

NR counts processed records (lines)/is a current record number, so you can do something like
```
awk 'NR==3 || NR>10 { $3=$3+5; print }'
```
to limit operation only to (row = 3) or (row > 10)
you need to figure out the range and update the filter part where currently 'is digit/is not digit' test is performed, eg
```
NR>10 && NR<30 && $1~/[0-9]+/{ $3=$3+n; print }'
```

---

