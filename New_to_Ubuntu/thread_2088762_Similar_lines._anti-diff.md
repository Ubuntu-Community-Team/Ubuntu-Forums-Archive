---
title: "Similar lines. anti-diff?"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by honeybear on 2012-11-27
Hi, 

Under bash, I have a string that contains:

```
4357
4352
54354
345623
2345
65678
```



```

3758
69756
2478
54354
345623
09634
234532
65478
```

How to output into a variable the similar ones? In this example, would be :

```
echo $mysamenumbers
54354
345623
```


Any help would be welcome.

---

### Post by Vaphell on 2012-11-27
define similar. "you know it when you see it" doesn't cut it
either way i don't think it's easy

---

### Post by drmrgd on 2012-11-27
Is $mysamenumbers supposed to be a list or array, or is it supposed to be a string with linebreaks?  Also you said that you have two 'strings' with those numbers.  Do you mean 'strings' or are they files?  

A crude, quick, and dirty way (depending on what your final goal is) might be to use 'comm' to assign similar strings to the variable:

```
$ cat file1.txt 
4357
4352
54354
345623
2345
65678
$ cat file2.txt 
3758
69756
2478
54354
345623
09634
234532
65478
$ mysamenumbers=$(comm -12 <(sort file1.txt) <(sort file2.txt))
$ echo $mysamenumbers 
345623 54354
```

If you need a more elaborate solution, then a full on script to read the data into an array and compare the elements would have to be done I think.

---

