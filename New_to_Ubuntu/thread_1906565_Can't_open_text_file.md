---
title: "Can't open text file"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by hdanap on 2012-01-09
Hi all,

Well I have messed up my system and I want to reinstall ubuntu, but when I transfer my files to a usb device all my text files will not open, it says something about character encoding, that I cant access the file.

When i type command:

file filename.txt, 

it tells me the file is binary file even though I know I used the default character code for gedit (UTF- 8

I have tried using Gvim, Geany, nano, Vim to access the file but still a no no.

No I can't reinstall ubuntu cos the fies seem like they can't be accessed.

Is there any way to access my files, I mean anyway, cos I have so much work stored that I really need . I mean my next rent and meals depend on these text files.

Advise Please

---

### Post by cortman on 2012-01-09
What does

```
cat filename.txt
```

give you?

If you can read the output, you can redirect it to a new file with

```
cat filename.txt > newfile.txt
```

---

### Post by hdanap on 2012-01-09
> **cortman said:**
> What does

```
cat filename.txt
```give you?

If you can read the output, you can redirect it to a new file with

```
cat filename.txt > newfile.txt
```

cat will not read the file as well, I tried that yesterday and just did again, still a no no.

I read somewhere that I could use a hex editor but when I open it with I think blessed hex editor, it just opens up with a buch of zeros all over and really dont know what to do with the zeros it provides.

Thanks

---

### Post by cortman on 2012-01-09
You didn't encrypt the files, did you? What exactly did you do to your system to mess it up? It may have an effect on what to do about your files.

---

