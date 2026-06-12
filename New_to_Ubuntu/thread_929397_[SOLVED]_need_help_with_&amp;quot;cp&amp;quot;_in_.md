---
title: "[SOLVED] need help with &amp;quot;cp&amp;quot; in terminal"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by twitch2197 on 2008-09-25
I'm trying to copy a bunch of audio/video codecs (located at home/Desktop/all-20061022) to a folder i created at usr/local/lib/codecs.
I read the man pages and I still don't understand why the terminal tells me "usr/local/lib/codecs: no such file or directory" or "cp: omitting directory 'Desktop/all-20061022'"
is ```
cp Desktop/all-20061022/ usr/local/lib/codecs
```
correct?
can someone help clear this command up?

---

### Post by tjwoosta on 2008-09-25
> 
I'm trying to copy a bunch of audio/video codecs (located at home/Desktop/all-20061022) to a folder i created at usr/local/lib/codecs.
I read the man pages and I still don't understand why the terminal tells me "usr/local/lib/codecs: no such file or directory" or "cp: omitting directory 'Desktop/all-20061022'"
is
Code:

cp Desktop/all-20061022/ usr/local/lib/codecs

correct?
can someone help clear this command up? 


try 

```
cp ~/Desktop/all-20061022 /usr/local/lib/codecs
```

---

### Post by jerome1232 on 2008-09-25
assuming you are in your home directory when doing this, that should be /usr/local/lib/codecs


if you don't lead the path with a '/' it looks in your current directory, so it thinks your are trying to copy those files to ~/usr/local/lib/codecs

---

### Post by twitch2197 on 2008-09-25
> **tjwoosta said:**
> try 

```
cp ~/Desktop/all-20061022 /usr/local/lib/codecs
```
I got this in response to that
```
cp: omitting directory `/home/twitch/Desktop/all-20061022'
```

---

### Post by jerome1232 on 2008-09-25
If you want to copy the contents of a directory you need to copy recursivly with the -r option, also you are going to need root access to copy to /usr so

```
sudo cp -r ~/Desktop/all-20061022 /usr/local/lib/codecs
```

edit: lol forgot the -r switch in my command, thatnks for pointing that out AndrewTheArt

---

### Post by twitch2197 on 2008-09-25
> **jerome1232 said:**
> If you want to copy the contents of a directory you need to copy recursivly with the -r option, also you are going to need root access to copy to /usr so

```
sudo cp ~/Desktop/all-20061022 /usr/local/lib/codecs
```
Thanks, that worked. I didn't think about the -r option, and i'd tried with sudo already. thanks for clearing it up!

---

### Post by AndrewTheArt on 2008-09-25
> **jerome1232 said:**
> If you want to copy the contents of a directory you need to copy recursivly with the -r option, also you are going to need root access to copy to /usr so

```
sudo cp ~/Desktop/all-20061022 /usr/local/lib/codecs
```

You mean

```
sudo cp -R ~/Desktop/all-20061022 /usr/local/lib/codecs
```

---

### Post by tjwoosta on 2008-09-25
nevermind...

glad you got it figured out

---

### Post by jerome1232 on 2008-09-25
Yeah lol I forgot the -r switch in my command, I fixed it now.

:lolflag:

---

