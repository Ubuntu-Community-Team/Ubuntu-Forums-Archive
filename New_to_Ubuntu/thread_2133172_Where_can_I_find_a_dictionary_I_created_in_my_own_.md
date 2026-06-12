---
title: "Where can I find a dictionary I created in my own computer?"
date: 2013-04-07
forum: New to Ubuntu
---

### Post by BSG Fan on 2013-04-07
My question is not about the Spanish language. My question is about the location of where is the following:

I created it because the Spanish dictionary I use is very incomplete, so I created an alternated one. and I know where to find it in the document: Options = language Settings = Writing Aids = User-defined dictionaries. 
Great.


**But**, 
what if I want to copy and paste that book or folder (in a CD, etc) because my computer get crashed sometimes and once again I have to create my alternate dictionary and that take me hours to add one by one.

so, the only question I have is:

where I can find it specifically? In Fyle System? Home? Where exactly?  The name of the file is Luis [Espanol] [All]

Note: in the past I have searched for it (with over 300 words I added) but the file was too small (kb), why?

Thank in advance.

BSG Fan

---

### Post by BSG Fan on 2013-04-07
Please see the pic attached.

---

### Post by BSG Fan on 2013-04-07
and le's suppose I can backup it.... then, how or where I can paste it again (in case the computer is reformatted again) so it can work again as before?

---

### Post by BSG Fan on 2013-04-11
any idea where is it? I tried to fiond it in temp, etc, but there is nothing.
help.

---

### Post by fyfe54 on 2013-04-11
I have a spell check dictionary in LibreOffice for family names etc that are correct but not in any other dictionary.  
The file is standard.dic and is located here:  /home/USER/.config/libreoffice/4/user/wordbook

You can right click on the wordbook folder and sync with Ubuntu One.  I just tried it - works fine.

---

### Post by BSG Fan on 2013-05-13
Hello Fyfe54
Thank you for the reply. I was not here to check it in time.

Since I installed the new Ubuntu (12.04) now I can not find the /home/USER/.config/libreoffice/4/user/wordbook to check that.
I will keep trying.

---

### Post by BSG Fan on 2013-05-15
> **BSG Fan said:**
> Hello Fyfe54
Thank you for the reply. I was not here to check it in time.

Since I installed the new Ubuntu (12.04) now I can not find the /home/USER/.config/libreoffice/4/user/wordbook to check that.
I will keep trying.

No, Fyfe54,
I did the search but I could not find the file I created.
You can see the picture.

Where is my file-dictionary?

---

### Post by Vaphell on 2013-05-15
your personal customizations are always somewhere in your home dir, /usr is for standard stuff that comes with installation.

run **find ~ -iname '*.dic'**

---

### Post by BSG Fan on 2013-05-15
> **Vaphell said:**
> your personal customizations are always somewhere in your home dir, /usr is for standard stuff that comes with installation.

run **find ~ -iname '*.dic'**

Okay, Vaphell, I got it the difference between /usr and what I created.

I did the terminal and I got a list of dictionaries, and the one I want.
/home/Pito/.config/libreoffice/3/user/wordbook/**Pito [Español**].dic

But, I still can not find it manually looking for .config, or libreoffice, or wordbook.

What I am doing wrong??

it is a hidden file or something??

---

### Post by BSG Fan on 2013-05-15
> **Vaphell said:**
> your personal customizations are always somewhere in your home dir, /usr is for standard stuff that comes with installation.

run **find ~ -iname '*.dic'**

Vaphell!
You are a hero!

I found it by making visible the hidden files ;)
It was invisible in my Home folder!

I followed your instructions step by step and I found it FINALLY!

You are my hero! jejeje

Thank you.

So, this thread was solved thanks to Valphell  and the original help of fyfe54.

:popcorn:

---

### Post by fyfe54 on 2013-05-15
BSG Fan,
I'm glad you found the answer.

---

