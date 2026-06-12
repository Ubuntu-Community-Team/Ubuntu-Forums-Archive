---
title: "Wget"
date: 2009-12-14
forum: Programming Talk
---

### Post by Slaktarn on 2009-12-14
Hay Wget is relly good and have many options

But one option i don´t find is

Ignore empty folder is there any option like thats

-m/-mirror dosen´t work i have allredy test it

Thx
Slaktarn

---

### Post by Rany Albeg on 2009-12-14
Good morning,

What do you mean by 'ignore empty folders' can you be more specific and maybe give a sample of you code?

Have a nice day.

---

### Post by Slaktarn on 2009-12-14
> **Rany Albeg said:**
> Good morning,

What do you mean by 'ignore empty folders' can you be more specific and maybe give a sample of you code?

Have a nice day.

Exaclty what i mean, If folder is emty don´t download the folder if its something in it download it and the folder... 

I use wget -r -A "*.exe" [http://localhost/test/](http://localhost/test/)

Life if its 

/test/A/test.exe
/test/B/ and this folder is empty it download it anyways and store it but i will not have it if it not contain .exe file

---

### Post by Arndt on 2009-12-14
> **Slaktarn said:**
> Exaclty what i mean, If folder is emty don´t download the folder if its something in it download it and the folder... 

I use wget -r -A "*.exe" [http://localhost/test/](http://localhost/test/)

Life if its 

/test/A/test.exe
/test/B/ and this folder is empty it download it anyways and store it but i will not have it if it not contain .exe file

Empty folders don't waste much time or space. You can remove them afterwards.

---

### Post by Slaktarn on 2009-12-14
We maybe talk about 10,000 - 100,000 folders

---

### Post by Arndt on 2009-12-14
> **Slaktarn said:**
> We maybe talk about 10,000 - 100,000 folders

How big a proportion are empty?

---

### Post by SeanHodges on 2009-12-14
> **Slaktarn said:**
> We maybe talk about 10,000 - 100,000 folders

I don't think wget provides this functionality for you, but you shouldn't need it anyway.

Directories are very small, it shouldn't take long to download them. You can then post-process the output directory using the following command:

```
find -depth -type d -empty -exec rmdir {} \;
```

This should delete all the empty directories. You have the added benefit of having more control over which directories get ignored that way as well.

---

### Post by tturrisi on 2009-12-14
download the site contents then cd to the main dir and do:
```
find . -type d -exec rmdir {} \;

```

---

### Post by xifer on 2009-12-14
> **Slaktarn said:**
> We maybe talk about 10,000 - 100,000 folders

do you need the directory names?  Need to do it in 2 steps if so.
Otherwise you might use the -nd option - multiple occurrences of the same file name can be made unique.

---

### Post by Slaktarn on 2009-12-15
> **xifer said:**
> do you need the directory names?  Need to do it in 2 steps if so.
Otherwise you might use the -nd option - multiple occurrences of the same file name can be made unique.

Yeh i need the dirnames :(

---

### Post by Slaktarn on 2010-01-29
Hay everyone its me again :)

If i have and just will download from that dir and don´t get redirection to the main folder after it downloaded from that one how do i do that?

[PHP]wget -r -A "*.rar" -A "*.bin" -A "*.exe" http://somesite:80/somedir/somedir/[/PHP]

Mvh Slaktarn

---

### Post by SeanHodges on 2010-01-29
> **Slaktarn said:**
> Hay everyone its me again :)

If i have and just will download from that dir and don´t get redirection to the main folder after it downloaded from that one how do i do that?

[PHP]wget -r -A "*.rar" -A "*.bin" -A "*.exe" http://somesite:80/somedir/somedir/[/PHP]

Mvh Slaktarn

Can you give an example of what you're trying to do? It might just be me, but I don't understand a word of what you've just written there.

---

