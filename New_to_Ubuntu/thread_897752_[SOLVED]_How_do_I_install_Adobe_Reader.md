---
title: "[SOLVED] How do I install Adobe Reader?"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by aspergerian on 2008-08-22
I want some features in Adobe Reader 8.1.2, features not in Evince. I have enough HD space for this.

acroread 8.1 downloaded into:
`AdobeReader_enu-8.1.2-1.i486.tar.gz'

and did so via:
/home/usr$ sudo wget [http://ardownload.adobe.com/pub/adobe/reader/unix/8.x/8.1.2/enu/AdobeReader_enu-8.1.2-1.i486.tar.gz](http://ardownload.adobe.com/pub/adobe/reader/unix/8.x/8.1.2/enu/AdobeReader_enu-8.1.2-1.i486.tar.gz)

Several questions:

1. What directory ought acroread be installed into? Into usr?

2. What command(s) lines ought I use to extract and to install `AdobeReader_enu-8.1.2-1.i486.tar.gz' ?

3. What directory ought I be in when I do the extract and install commands?

Thank you.

running a 901 ASUS with 8.04.1 via array.org

---

### Post by Iandefor on 2008-08-22
Will getting it from [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") work? Just enable the Medibuntu repository and install the package named acroread. Medibuntu has the version you're looking for.

---

### Post by aloshbennett on 2008-08-22
It really doesnt matter which directory you install it into, as long as you have it in your classpath. As a practise, I would install it into /opt/adobereader.

To extract the files, use 'tar -xvzf AdobeReader_enu-8.1.2-1.i486.tar.gz'
Mostly you would be presented with an install.sh or something similar.

---

### Post by tangibleorange on 2008-08-22
the following commands will do as suggested by **Iandefor** (assume you are using hardy, if not, substitute hardy for your dist.):

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install acroread mozilla-acroread acroread-plugins
```

---

### Post by BGFG on 2008-08-22
> **aspergerian said:**
> I want some features in Adobe Reader 8.1.2, features not in Evince. I have enough HD space for this.

acroread 8.1 downloaded into:
`AdobeReader_enu-8.1.2-1.i486.tar.gz'

and did so via:
/home/usr$ sudo wget [http://ardownload.adobe.com/pub/adobe/reader/unix/8.x/8.1.2/enu/AdobeReader_enu-8.1.2-1.i486.tar.gz](http://ardownload.adobe.com/pub/adobe/reader/unix/8.x/8.1.2/enu/AdobeReader_enu-8.1.2-1.i486.tar.gz)

Several questions:

1. What directory ought acroread be installed into? Into usr?

2. What command(s) lines ought I use to extract and to install `AdobeReader_enu-8.1.2-1.i486.tar.gz' ?

3. What directory ought I be in when I do the extract and install commands?

Thank you.

running a 901 ASUS with 8.04.1 via array.org

Well as far as i know you don't have to select an install directory. All linux programs have a specific directory hierarchy so installations are standard. ( The higher ups may be able to change install directories be generally we don't need to)

As for the tar.gz file you should be able to right click and extract it with Ubuntu's default archiving tool. Once you do, in the folder should have a readme with installation instructions.

But generally, once you extract the tar.gz file, you can navigate to it in the terminal, say i put the file on the desktop :
```

$ cd Desktop/AdobeReader_enu-8.1.2-1.i486

```
once you get to the folder you can the execute the commands:
```

./configure

make

make install

```

So it would look like this:

```

~$ cd Desktop/AdobeReader_enu-8.1.2-1.i486 $ ./configure

~$ cd Desktop/AdobeReader_enu-8.1.2-1.i486 $ make

~$ cd Desktop/AdobeReader_enu-8.1.2-1.i486 $ make install

```

But definitely check out the enclosed readme.

---

### Post by aysiu on 2008-08-22
> **tangibleorange said:**
> the following commands will do as suggested by **Iandefor** (assume you are using hardy, if not, substitute hardy for your dist.):

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install acroread mozilla-acroread acroread-plugins
```
Another vote for using Medibuntu.

Why make it painful by compiling it from source?

---

### Post by BGFG on 2008-08-22
> **aysiu said:**
> Another vote for using Medibuntu.

Why make it painful by compiling it from source?


Cause it fun :)
But for newer guys, you are definitely correct...

---

### Post by Majorix on 2008-08-22
> **aysiu said:**
> Why make it painful by compiling it from source?

I don't think you are compiling here, as you don't have the sourcecode for Adobe Reader. But still it's good practice to download off the repos, as it is easiest to update when time comes.

---

### Post by aspergerian on 2008-08-23
Thnx to all who replied. I downloaded from Adobe, found that their tar.gz didn't work well (wouldn't install for me) but Adobe's deb version worked well, tho' it's built to install into opt. I would have preferred a directory with more space, but accepted opt. My Adobe Reader 8.1 is working well.

---

