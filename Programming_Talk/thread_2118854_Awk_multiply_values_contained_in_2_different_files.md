---
title: "Awk multiply values contained in 2 different files"
date: 2013-02-22
forum: Programming Talk
---

### Post by YoYoMoMo on 2013-02-22
Hi Everyone !

I have two files with the same configuration
and I want to multiply corresponding values and write the result in a file.
Let say 2 header lines and then lines of values (with not constant number of columns):

```

more file1.txt -->
BLABLABLA
BLABLABLA
1 2 3 4
1 2 3
1 2
1 2 3

``````

more file2.txt -->
BLABLABLA
BLABLABLA
2 2 2 2
2 2 2
1 1
1 1 1

```I want to have this results:
```

more file3.txt -->
BLABLABLA
BLABLABLA
2 4 6 8
2 4 6
1 2
1 2 3

```
Anyone has an idea ? Thanks in advance,
Y.

---

### Post by schragge on 2013-02-22
In awk, try to read the contents of each file into its own array, then in the END clause, multiply elements of two arrays in a loop.

[highlight]Update.[/highlight]
If there were only one column in each file, I'd suggest something like
```

[color=green]$[/color] cat file1.txt
15
8
92
53
[color=green]$[/color] cat file2.txt
96
30
34
86
[color=green]$[/color] paste -d\* file[12].txt|bc
1440
240
3128
4558

```

---

### Post by steeldriver on 2013-02-22
Hello and welcome

You could also try a 'while... read' loop in bash instead of awk

```
while read -u3 -a vals1; read -u4 -a vals2
do
*  your math on the array values *
done 3< file1.txt 4< file2.txt
```There may be a neater way to do it with an associative array instead of separate arrays for the two file inputs

---

### Post by YoYoMoMo on 2013-02-22
Thanks a lot for your answers.
This is a good basis for the beginning of my program.

---

### Post by ofnuts on 2013-02-22
[http://stackoverflow.com/questions/11160145/merge-two-files-in-linux-with-different-column](http://stackoverflow.com/questions/11160145/merge-two-files-in-linux-with-different-column)

---

### Post by steeldriver on 2013-02-22
I kind of assumed this was homework, but if not

```
while read -u3 -a line1; read -u4 -a line2
do 
    for (( i=0; i< ${#line1[@]}; i++ ))
        do printf "%d " $(( ${line1[i]} * ${line2[i]} ))
    done
    printf "\n"
done 3< file1.txt 4< file2.txt
0
0
2 4 6 8
2 4 6
1 2
1 2 3

```The extra zeros are because I didn't bother to strip the header lines, probably extra credit to be had for checking that the ith value of the second array exists as well

---

### Post by Vaphell on 2013-02-23
in case of awk i'd try something like this:
```
paste file1 file2 | awk '{ for(i=1;i<=NF/2; i++) printf("%d ", $i*$(i+NF/2)); printf("\n"); }'
```
*paste *to put columns next to each other, and then in awk for every row multiply i-th element by (i+NF/2)-th element

---

### Post by YoYoMoMo on 2013-03-06
Thanks a lot Vaphell, it works very well !
I have just added a if condifition because of the header.

```

paste $filein1 $filein2 | awk ' BEGIN {begdata=0}{ 
                if ((NR>2 && NF==12) || begdata==1) { 
                  for(i=1;i<=NF/2;i++) {  
                     printf(" %12.5E",$i*$(NF/2+i)); 
                  } 
                  printf("\n");  
                   begdata=1;
                 } 
                else
                 {
                   print substr($0,0,length($0)/2)
                 }
               }' > $fileout
```

---

### Post by schragge on 2013-03-06
Well, I guess to get rid of headers, this would be enough:
```
[COLOR=red]head -2 file1;[/COLOR] paste file{1,2} | awk '[COLOR=red]NR>2[/COLOR] {c=NF/2; for(i=0;i++<c;) printf "%d%s", $i*$(i+c), i<c?" ":"\n"}'
```

---

