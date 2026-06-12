---
title: "Printing Sequence of Character with Single Space"
date: 2012-11-16
forum: Programming Talk
---

### Post by 1991sudarshan on 2012-11-16
How to print a sequence of characters with single space or tabs  when the printf command is used in this way ? 

```
#!/bin/bash
for ((x=1;x<=1391;x+=1)); 
do
echo `printf "%08d" $x`.pdf ;
done

```I want the bash to print the output like this 

```
00000001.pdf 00000002.pdf 00000003.pdf  .......
```

---

### Post by steeldriver on 2012-11-16
I don't think you need the 'echo' in there, that will always add the newline - and your format specifier needs to be a string not an integer (you are printing the whole name, not just the $x) - after that, you can just use a literal space as the separator

```
$ for ((x=1;x<=1391;x+=1));  do printf "%08s " $x.pdf ; done
```However the built-in sequence syntax would be neater imho:

```
$ for f in {00000000..00001391}.pdf; do printf "$f "; done
```

---

### Post by Vaphell on 2012-11-16
```
echo {0000000..00001391}.pdf
```
what do you need it for?

---

### Post by 1991sudarshan on 2012-11-16
> **steeldriver said:**
> I don't think you need the 'echo' in there, that will always add the newline - and your format specifier needs to be a string not an integer (you are printing the whole name, not just the $x) - after that, you can just use a literal space as the separator

```
$ for ((x=1;x<=1391;x+=1));  do printf "%08s " $x.pdf ; done
```However the built-in sequence syntax would be neater imho:

```
$ for f in {00000000..00001391}.pdf; do printf "$f "; done
```

Thank you SO Much, that solves the problem.

---

### Post by 1991sudarshan on 2012-11-16
> **Vaphell said:**
> ```
echo {0000000..00001391}.pdf
```what do you need it for?

For combing a **Chinese Hakka to English Dictionary** which I downloaded from the internet. The Dictionary has around 1391 pages. Unfortunately . I got 1391 pdf files. So I  wanted to combine it. 

Anyways, you idea too worked , Thank you so much.

---

