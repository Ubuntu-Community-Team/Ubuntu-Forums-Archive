---
title: "Installing winrar through terminal"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by ubunt2guy on 2008-09-30
-i d/l the WinRar (linux x64 version) tar.gz 

-extracted to my desktop

-changed directory into rar folder

-typed sudo apt-get install (everything went fine with that)

-typed make and got this

kevin@kevin-laptop:~/Desktop/rar$ make
mkdir -p /usr/local/bin
mkdir -p /usr/local/lib
cp rar unrar /usr/local/bin
cp: cannot create regular file `/usr/local/bin/rar': Permission denied
cp: cannot create regular file `/usr/local/bin/unrar': Permission denied
make: *** [install] Error 1


I don't know what to do. I checked this [https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo") and still a little confused.

any help would rock

---

### Post by Titan8990 on 2008-09-30
Any particular reason for winrar? Is there something that the default archive manager can not do?

Try:

sudo make


Edit: Also, do you have the 64bit version on Ubuntu?

---

### Post by MusicMastaMike on 2008-09-30
There's a much easier solution:

```
sudo apt-get install rar unrar
```

---

### Post by chlorinekid on 2008-09-30
personally i use 'unrar' to handle rar files...

```
sudo apt-get install unrar
```

added support for rar files for me. i'm sure i had some problems opening them with 8.04 'out-of-the-box'

---

### Post by chlorinekid on 2008-09-30
heh snap :)

---

### Post by ubunt2guy on 2008-09-30
> **chlorinekid said:**
> heh snap :)

huh?

---

### Post by ubunt2guy on 2008-09-30
> **Titan8990 said:**
> Any particular reason for winrar? Is there something that the default archive manager can not do?

Try:

sudo make


Edit: Also, do you have the 64bit version on Ubuntu?

actually i don't know what I was thinking.  I saw the .rar file and thought I had to get winrar.  I guess I'm still in Windows mode.  Thanks.

---

