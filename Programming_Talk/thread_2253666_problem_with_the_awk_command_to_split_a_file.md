---
title: "problem with the awk command to split a file"
date: 2014-11-21
forum: Programming Talk
---

### Post by tho4 on 2014-11-21
[SIZE=2][FONT=arial]Hello,

From a fasta file as follows:

>species_1
ATTGCTCGAT
>species_2
TCGTCTAAGT
>species_3
TTCAACATGG

I want to generate individual files as follow:

file_1:
>species_1
ATTGCTCGAT

file_2:
>species_2
TCGTCTAAGT

file_3:
>species_3
TTCAACATGG

I am trying to use the following command (source: [http://stackoverflow.com/questions/21476033/splitting-a-multiple-fasta-file-into-separate-files-keeping-their-original-names):](http://stackoverflow.com/questions/21476033/splitting-a-multiple-fasta-file-into-separate-files-keeping-their-original-names):)

[/FONT][/SIZE]
[SIZE=3][FONT=arial]awk '/^>chr/ {OUT=substr($0,2) ".fa"}; {print >> OUT; close(OUT)}' [/FONT][/SIZE][SIZE=3][FONT=arial]Input_File

but it doesn't work for me, and I do not really understand the syntax here. Could someone be of help? Is there a direct way to do it with csplit? Because I currently use csplit and then rename the output, but this is not optimal.

Thank you[/FONT][/SIZE]

---

### Post by Vaphell on 2014-11-21
```
$ cat src.txt
>species_1
ATTGCTCGAT
>species_2
TCGTCTAAGT
>species_3
TTCAACATGG
$ while read ln; do [[ ${ln:0:1} = '>' ]] && file=${ln#?}.fa; echo "$ln" >> "$file"; done < src.txt
$ ls
species_1.fa  species_2.fa  species_3.fa  src.txt
$ cat species_1.fa
>species_1
ATTGCTCGAT
```

---

### Post by tho4 on 2014-11-24
Thanks a lot !

---

### Post by steeldriver on 2014-11-24
... if you did want to use awk, then maybe something like

```

awk -vOFS='\n' '/^>species/ {split($1,a,"_"); getline data; print $0,data >> "file_"a[2]".fa"}' input_file

```

---

