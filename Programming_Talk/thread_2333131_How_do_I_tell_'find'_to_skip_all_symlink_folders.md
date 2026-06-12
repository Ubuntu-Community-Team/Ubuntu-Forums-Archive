---
title: "How do I tell 'find' to skip all symlink folders?"
date: 2016-08-07
forum: Programming Talk
---

### Post by Paddy Landau on 2016-08-07
This must have been answered somewhere, but Google as I might, I cannot find the answer.

According to the [COLOR=#696969][FONT=lucida console]find[/FONT][/COLOR] manual, you can use [COLOR=#696969][FONT=lucida sans unicode]-P[/FONT][/COLOR] (which is default anyway) to prevent it from following symlinks.

But, this applies only to flies. What I want is for [COLOR=#696969][FONT=lucida console]find[/FONT][/COLOR] to not follow any folders that are symlinks.

For example, suppose the folder structure is as follows.
```
.
&#9500;&#9472;&#9472; folderA
&#9474;   &#9500;&#9472;&#9472; folderAA
&#9474;   &#9492;&#9472;&#9472; folderAB
&#9500;&#9472;&#9472; folderB
&#9474;   &#9500;&#9472;&#9472; folderBA
&#9474;   &#9492;&#9472;&#9472; folderBB
&#9492;&#9472;&#9472; linkToOutside -> /somewhere/else/outsideA/

```I want to use [COLOR=#696969][FONT=lucida console]find[/FONT][/COLOR], but tell it to search only [COLOR=#696969][FONT=lucida console]folderA[/FONT][/COLOR] and [COLOR=#696969][FONT=lucida console]folderB[/FONT][/COLOR], and exclude folder [COLOR=#696969][FONT=lucida console]linkToOutside[/FONT][/COLOR] (because it is a symlink).

I have tried the following options but to no avail:
```
find -P -xdev '!' -type l
```
How do I tell [COLOR=#696969][FONT=lucida console]find[/FONT][/COLOR] to skip all symlink folders?

---

### Post by vasa1 on 2016-08-07
> **Paddy Landau said:**
> ... I have tried the following options but to no avail:
```
find -P -xdev '!' -type l
``` ...

Just to request a clarification.

Why use **'!'** instead of just **!**?

---

### Post by vasa1 on 2016-08-07
If I look in /usr/local, I see:```
07:13 PM /usr/local $ ls -AlF
total 32
drwxr-xr-x 2 root root 4096 Feb 11 18:20 bin/
drwxr-xr-x 2 root root 4096 Jul 23  2014 etc/
drwxr-xr-x 2 root root 4096 Jul 23  2014 games/
drwxr-xr-x 2 root root 4096 Jul 23  2014 include/
drwxr-xr-x 4 root root 4096 Apr 20 14:52 lib/
lrwxrwxrwx 1 root root    9 Nov 14  2014 man -> share/man/
drwxr-xr-x 2 root root 4096 Jul 23  2014 sbin/
drwxr-xr-x 9 root root 4096 Apr 20 15:17 share/
drwxr-xr-x 2 root root 4096 Jul 23  2014 src/
07:14 PM /usr/local $ 
```

If I'm in /usr/local and run```
find -L . -type d
``` I get```
07:14 PM /usr/local $ find -L . -type d
.
./etc
./bin
./sbin
./lib
./lib/python2.7
./lib/python2.7/dist-packages
./lib/python2.7/site-packages
./lib/python3.5
./lib/python3.5/dist-packages
./games
./share
./share/xml
./share/xml/schema
./share/xml/misc
./share/xml/declaration
./share/xml/entities
./share/fonts
./share/applications
./share/ca-certificates
./share/sgml
./share/sgml/dtd
./share/sgml/misc
./share/sgml/declaration
./share/sgml/stylesheet
./share/sgml/entities
./share/man
./share/emacs
./share/emacs/site-lisp
**./man**
./src
./include
07:14 PM /usr/local $ 
```But if I run```
find . -type d
```I get```
07:16 PM /usr/local $ find . -type d
.
./etc
./bin
./sbin
./lib
./lib/python2.7
./lib/python2.7/dist-packages
./lib/python2.7/site-packages
./lib/python3.5
./lib/python3.5/dist-packages
./games
./share
./share/xml
./share/xml/schema
./share/xml/misc
./share/xml/declaration
./share/xml/entities
./share/fonts
./share/applications
./share/ca-certificates
./share/sgml
./share/sgml/dtd
./share/sgml/misc
./share/sgml/declaration
./share/sgml/stylesheet
./share/sgml/entities
./share/man
./share/emacs
./share/emacs/site-lisp
./src
./include
07:17 PM /usr/local $ 
```In other words, the **man** folder isn't listed.

---

### Post by steeldriver on 2016-08-07
The default behaviour (without the -L command line option) should not *descend into* linked directories e.g. given

```

$ tree -l .
.
&#9500;&#9472;&#9472; folderA
&#9474;   &#9500;&#9472;&#9472; folderAA
&#9474;   &#9492;&#9472;&#9472; folderAB
&#9500;&#9472;&#9472; folderB
&#9474;   &#9500;&#9472;&#9472; folderBA
&#9474;   &#9492;&#9472;&#9472; folderBB
&#9492;&#9472;&#9472; linkToOutside -> ../somewhere/else/outsideA/
    &#9492;&#9472;&#9472; somefile

7 directories, 1 file

```

then
```

$ find .
.
./folderB
./folderB/folderBB
./folderB/folderBA
./folderA
./folderA/folderAA
./folderA/folderAB
./linkToOutside

```

whereas

```

$ find -L . 
.
./folderB
./folderB/folderBB
./folderB/folderBA
./folderA
./folderA/folderAA
./folderA/folderAB
./linkToOutside
./linkToOutside/somefile

```

(note the additional result [FONT=courier new]./linkToOutside/somefile[/FONT])

If you don't want to even *list* links, you can do

```

$ find . ! -type l
.
./folderB
./folderB/folderBB
./folderB/folderBA
./folderA
./folderA/folderAA
./folderA/folderAB

```

---

### Post by Paddy Landau on 2016-08-08
> **vasa1 said:**
> If I look in /usr/local, I see&#8230;
> **steeldriver said:**
> The default behaviour (without the -L command line option) should not *descend into* linked directories&#8230;
@vasa1 and @steeldriver, thank you for your responses.

I am utterly befuddled.

I get the same responses as you with your examples. But &#8212; which is the reason why I posted &#8212; it doesn't work on my home folder!

My home folder has two symbolic links:
```
$ ls -ld li* Pl*
lrwxrwxrwx 1 paddy paddy 20 Aug  8 15:47 linkToOutside -> /home/paddy/outsideA
lrwxrwxrwx 1 paddy paddy 37 Jun  6  2014 PlayOnLinux's virtual drives -> /home/paddy/.PlayOnLinux//wineprefix/
```
Yet [FONT=&amp][COLOR=#696969]find[/COLOR][/FONT] always descends into that folder. (Many output lines omitted for readability.)
```
$ find [a-z]*/ -xdev -maxdepth 2 '!' -type l -print
           :          :          :          :
linkToOutside/
linkToOutside/outsideAA
linkToOutside/outsideAB
           :          :          :          :
PlayOnLinux's virtual drives/
PlayOnLinux's virtual drives/default
PlayOnLinux's virtual drives/Quicken
PlayOnLinux's virtual drives/Quicken/dosdevices
PlayOnLinux's virtual drives/Quicken/drive_c
           :          :          :          :
```
Why does this command descend into the symlinks? What am I missing? (I feel truly stupid!)

---

### Post by sudodus on 2016-08-08
I made a symbolic link from my home folder to a subdirectory in my 'data' partition

```
ln -s /media/multimed-2/test/test0/ test0
```

I tried the following command

```
find ~ -ls | grep '/test0 '
```

and it finds only the link itself, does not descend into it, while your command (translated to look at test0) lists the content.

```
find [a-z]*/ -xdev -maxdepth 2 '!' -type l -print |grep test0
```

I suggest that you simplify your command :-)

---

### Post by steeldriver on 2016-08-08
Agree with the above - I think it's because you're telling it to find **within **folders matching [a-z]*/ (one of which is the linked directory)

In other words, the point at which 'find' starts to do its thing, you are already the other side of the symlink

---

