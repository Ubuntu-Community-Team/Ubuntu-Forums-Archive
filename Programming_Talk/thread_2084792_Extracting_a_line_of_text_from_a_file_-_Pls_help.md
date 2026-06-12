---
title: "Extracting a line of text from a file - Pls help"
date: 2012-11-16
forum: Programming Talk
---

### Post by scar1 on 2012-11-16
Hi everyone,

Wonder if anyone can help me with a situation I am in where I would like to extract some data from a very large text file.

I have a text file which has lots of info I am interested in however lots of rubbish to. I noticed that the lines of text I am interested in has a "*" at the end of that line and that is the very last character of that line. 

I am familiar with programming however not so familiar with using bash scripts to do this. I have done some reading and I think the logic would be to use GREP & sed to find the line that has "*" and then extract that line only to an output file.

Im not sure on the syntax or how can apply this, can anyone possibly help me here, would be appreciated.

Thanks
Steve

---

### Post by dargaud on 2012-11-16
```
grep "*$" YourFile
```

---

### Post by Vaphell on 2012-11-16
> and then extract that line only to an output file.

```
grep "*$" YourFile > output.file
```

---

### Post by cortman on 2012-11-16
Quick sed:

```
sed '/.*[^\*]$/g' > results
```

I recommend using grep:

```
grep "^.*\*$" my_file > results
```

EDIT:

Forgot that quoting takes away *'s special character status- just

```
grep "*$" my_file > results 
```

will work fine.

---

### Post by scar1 on 2012-11-18
Thanks very much for the quick responses...
when investigating further I have actually found the last character of the line I require is "Q" and also I need to export that line and the whole line above it.

I hope that makes sense, once again any help is much appreciated.

Thanks
Scar1

---

### Post by steeldriver on 2012-11-18
You can add a -Bn switch to get n lines of before context (similarly -An for n lines of after context or -Cn for context either side of the matching lines)

```
$ grep **-B1** 'Q$' *yourfile*
```

---

### Post by scar1 on 2012-11-18
Brilliant! Will let you know how I get on.

---

