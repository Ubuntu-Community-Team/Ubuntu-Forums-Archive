---
title: "Editing Files Thourgh A Script"
date: 2007-10-03
forum: Programming Talk
---

### Post by 1337455 10534 on 2007-10-03
Hi, I am working on a script that needs to edit the /etc/apt/sources.list file. It's in Python, but BASH commands will work with the os mod, so... Could someone tell me how to do this?? I don't want to create a file with the same name, it wouldn't work (like, Update Manager won't recognize it...) so can someone tell me how to do this?
Thank you..

is it like:
os.system("echo $") something?? :help:

---

### Post by Wybiral on 2007-10-03
Python has file IO built in, do some googling on "open" and  "write".

No need to use the "os" module for simple file IO.

---

### Post by 1337455 10534 on 2007-10-03
Operation  	Interpretation
output = open('/tmp/spam', 'w') 	Create output file ('w' means write).
input = open('data', 'r') 	Create input file ('r' means read).
S = input.read( ) 	Read entire file into a single string.
L = input.readlines( ) 	Read entire file into list of line strings.
output.write(S) 	Write string S into file.
output.writelines(L) 	Write all line strings in list L into file.
output.close( ) 	Manual close (done for you when file collected).
[http://www.onlamp.com/pub/a/python/excerpt/PythonPocketRef/index.html](http://www.onlamp.com/pub/a/python/excerpt/PythonPocketRef/index.html)

SO, would I use L = input.readlines( ) to edit the /etc/apt/sourceslist?? How? replace "L" with the my filepath?

---

### Post by Wybiral on 2007-10-03
If you're trying to write to a file, it's simple...

```

fp = open("file", "w")
fp.write("Hello World!")
fp.close()

```

Be aware that this will OVERWRITE everything that was in the file.

To append data to the file, open it with "a" instead of "w".

---

### Post by ghostdog74 on 2007-10-03
what are you actually trying to do ? show what you want to edit from the /etc/apt/sources.list file!

---

### Post by 1337455 10534 on 2007-10-05
Replace the default with:
```

# http://3v1n0.tuxfamily.org/blog/?page_id=13
# This list contains (apt) repos for "getting". Hahaha. DON'T MESS WITH IT!!! grr.. grrr... 

# Ubuntu supported packages (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://archive.ubuntu.com/ubuntu feisty-security main restricted
deb http://archive.ubuntu.com/ubuntu feisty-proposed main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-proposed main restricted

# Ubuntu community supported packages (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://archive.ubuntu.com/ubuntu feisty-security universe multiverse
deb http://archive.ubuntu.com/ubuntu feisty-proposed universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-security universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-proposed universe multiverse

# Ubuntu backports project (GPG key: 437D05B5)
deb http://mi.mirror.garr.it/ubuntu feisty-backports main restricted universe multiverse
deb-src http://mi.mirror.garr.it/ubuntu feisty-backports main restricted universe multiverse

# CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu servers.
# RealPlayer10, Opera, VmWare Server and more to come.)
deb http://archive.canonical.com/ubuntu feisty-commercial main

# Seveas' packages (GPG key: 1135D466)
# GPG key-file: http://mirror.ubuntulinux.nl/1135D466.gpg
deb http://mirror.ubuntulinux.nl feisty-seveas all
deb-src http://mirror.ubuntulinux.nl feisty-seveas all

# The Opera browser (packages) (GPG key: 6A423791)
deb http://deb.opera.com/opera etch non-free

# Google picasa packages (GPG key: 7FAC5991)
deb http://dl.google.com/linux/deb/ stable non-free

# Medibuntu (Multimedia, Entertainment & Distraction In Ubuntu - ex Penguin Liberation Front)
# GPG key-file: http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

# The repository from Kubuntu Germany
# GPG key-file: http://archive.czessi.net/ubuntu/kczessi.gpg
deb http://archive.czessi.net/ubuntu feisty main restricted universe multiverse preview
deb-src http://archive.czessi.net/ubuntu feisty main restricted universe multiverse preview

# Achim's Unofficial 'feisty' Kubuntu packages
# GPG key-file: http://www.mpe.mpg.de/~ach/ach-gpg.asc
deb http://www.mpe.mpg.de/~ach/kubuntu/feisty ./
deb-src http://www.mpe.mpg.de/~ach/kubuntu/feisty ./

# Ubuntu feisty University Klagenfurt packages
# GPG key-file: http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub
# $ sudo apt-key add uniklu-debuild.pub 
#   uniklu:         backports and new packages
#   uniklu-intern:  not freely redistributable (jvm), or modified packages
#   uniklu-testing: packages not ready for general use
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ feisty uniklu
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ feisty uniklu-intern
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ feisty uniklu-testing
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ feisty uniklu
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ feisty uniklu-intern
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ feisty uniklu-testing

# MythTV Repository for Ubuntu Linux (GPG key: 80DF6D58)
deb http://home.eng.iastate.edu/~superm1 feisty all
deb-src http://home.eng.iastate.edu/~superm1 feisty all

# Ubuntu repository for Screenlets (GPG key: F854AFD7)
# GPG key-file: http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
deb-src http://hendrik.kaju.pri.ee/ubuntu feisty screenlets

# Subpixel Font rendering packages (GPG key: 937215FF)
# Improved fonts on LCDs - WARNING: May violate some patents
# GPG key-file: http://www.telemail.fi/mlind/ubuntu/937215FF.gpg
deb http://www.telemail.fi/mlind/ubuntu feisty fonts main
deb-src http://www.telemail.fi/mlind/ubuntu feisty fonts main

# Skype packages
deb http://download.skype.com/linux/repos/debian/ stable non-free

# Linux2Go Ubuntu Packages (GPG key: E8BDA4E3)
deb http://www.linux2go.dk/ubuntu feisty main
deb-src http://www.linux2go.dk/ubuntu feisty main

# Asher256's Repository
deb http://asher256-repository.tuxfamily.org edgy main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french

# Tvfreeplayer Packages (GPG key: )
# GPG key-file: http://www.tvfreeplayer.com/linux/falcon/tvfreeplayer.gpg
deb http://www.tvfreeplayer.com/linux/falcon feisty all
deb-src http://www.tvfreeplayer.com/linux/falcon feisty all

# gnomemeeting - ekiga (GPG key: 52ABFCB1)
deb http://snapshots.ekiga.net/ubuntu/ feisty main
deb-src http://snapshots.ekiga.net/ubuntu/ feisty main

# Cinelerra Feisty packages
deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/ ./

# Cafuego's feisty Stuff: Broadcom firmware, google-earth, secondlife (GPG key: 969F3F57)...
deb http://au.ubuntu.cafuego.net feisty-cafuego all
deb-src http://au.ubuntu.cafuego.net feisty-cafuego all

# Debuntu Ubuntu feisty packages
# GPG Key: http://repository.debuntu.org/GPG-Key-chantra.txt
deb http://repository.debuntu.org/ feisty multiverse
deb-src http://repository.debuntu.org/ feisty multiverse

# Morgoth Repository (GPG key: 7E2E4741)
# Provides Monkey's Audio, xmms pugins, vlc plugins, gqview, audacius, audacity...
# GPG key-file: http://morgoth.free.fr/files/morgoth-signkey.gpg.asc
deb http://morgoth.free.fr/ubuntu feisty-backports main
deb-src http://morgoth.free.fr/ubuntu feisty-backports main

# Musicbrainz Repository
# GPG key-file: http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/public.key
deb http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu feisty musicbrainz
deb-src http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu feisty musicbrainz

# The Ubuntu NLP Repository (GPG key: 8ABD1965)
# GPG key-file: http://cl.naist.jp/~eric-n/ubuntu-nlp/8ABD1965.gpg
deb http://cl.naist.jp/~eric-n/ubuntu-nlp feisty all
deb-src http://cl.naist.jp/~eric-n/ubuntu-nlp feisty all

# Ubuntu System Administrator packages (GPG key: 2F306651)
# GPG key-file: http://ubuntu.moshen.de/2F306651.gpg
deb http://ubuntu.moshen.de feisty multimedia misc
deb-src http://ubuntu.moshen.de feisty multimedia misc

# The Consciousness Repository (GPG key: DD385D79)
# GPG key-file: http://debs.peadrop.com/DD385D79.gpg
deb http://debs.peadrop.com feisty all
deb-src http://debs.peadrop.com feisty all

## Swiftfox (enhanced Firefox for linux) packages
deb http://getswiftfox.com/builds/debian unstable non-free
deb http://getswiftfox.com/builds/debian/trunk unstable non-free

# Sonnes repository (aMule AdunanZa, Audacious)
deb http://adurepo.altervista.org/ubuntu feisty all
deb-src http://adurepo.altervista.org/ubuntu feisty all

# darkmagez repository: rhythmbox and newer gtk (GPG key: A3012FB3)
# GPG key-file: http://mirror.randumb.org/darkmagez/repo/A3012FB3.gpg
deb http://mirror.randumb.org/darkmagez/repo feisty-darkmagez multimedia-experimental #core-experimental
deb-src http://mirror.randumb.org/darkmagez/repo feisty-darkmagez multimedia-experimental #core-experimental

# FoLKeN 'Repozytorium' (GPG key: 6FB65A0F)
deb http://deb.svx.pl/ feisty main universe bleeding
deb-src http://deb.svx.pl/ feisty main universe bleeding

# Mez's Repository (GPG key: 6AAAA569)
# GPG key-file: http://apt.sourceguru.net/6AAAA569.gpg
deb http://apt.sourceguru.net feisty all
deb-src http://apt.sourceguru.net feisty all

# Ryan Kavanagh's packages (GPG key: 02544D0E)
# GPG key-file: http://packages.ryanak.ca/02544D0E.gpg
deb http://packages.ryanak.ca ryan-feisty all
deb-src http://packages.ryanak.ca ryan-feisty all
deb http://archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main
#AUTOMATIX REPOS END

```

---

### Post by 1337455 10534 on 2007-10-11
Ok, thx, I see this:
> 
```

fp = open("file", "w")
fp.write("Hello World!")
fp.close()

```

But will putting the name of the file guarantee that Python will find it?? Don't you need to give a filepath somewhere?
That, and I want to put more than 1 line of text in my file; more like 200... Do I use the %n to do so?
```

list = open("sources.list", "w")
list.write("#repo %n repo2 %n repo3 ") # ad infinitum
list.close

```
Thanyou very much!!

---

### Post by Wybiral on 2007-10-11
> **1337455 10534 said:**
> Ok, thx, I see this:

But will putting the name of the file guarantee that Python will find it?? Don't you need to give a filepath somewhere?
That, and I want to put more than 1 line of text in my file; more like 200... Do I use the %n to do so?
Thanyou very much!!

You should give it the full path or a relative path.

You can use "\n" to generate a newline.

---

### Post by 1337455 10534 on 2007-10-11
Is this final?
```

list = open("/etc/apt/sources.list", "w")
list.write("#repo \n repo2 \n repo3 ") # ad infinitum
list.close

```

---

### Post by 1337455 10534 on 2007-10-11
I read somewhere that filepath slashes must be written twice; is it true?
Like:
list = open("//etc//apt//sources.list"
...
??

---

### Post by Wybiral on 2007-10-11
Looks fine, except the slashes are backwards (on the newline characters).

---

### Post by 1337455 10534 on 2007-10-11
ok
\n
for newline

---

### Post by Wybiral on 2007-10-11
You should play around with it in a junk file before writing it to your actual source.list to make sure it's going to produce the results you want.

---

### Post by 1337455 10534 on 2007-11-06
I've been messing around with an empty file, and cant get it to read a string...
How do I open a .txt, read the one and only string in it, and save the string as a variable?
```

# all of the following fail
# 1
S = list.open("/home/family/Desktop/Operations","r")
print S
# 2
S = open.read("/home/family/Desktop/Operations")
print S

```

---

### Post by 1337455 10534 on 2007-11-06
```

>>> a = open("/home/family/Desktop/Operations")
>>> text = input.read()
>>> print text
1234

```
It worked the first time, but fails now! Please help!

---

### Post by 1337455 10534 on 2007-11-06
Nvm; it works now:
```

operation = open("/home/family/Desktop/Operations")
branch = operation.read()
print branch

```
OOP baffles me :(/

---

### Post by nhandler on 2007-11-06
Also, to answer one of your previous questions in case someone else runs into this problem, you do not need //. If I had to guess, the guide you were reading was written for windows. In windows, \ is used instead of /. I don't know about python, but in perl (which is pretty similar), \ is used to escape characters. So putting \home just means you're escaping the h. To actually use the \, you need to escape it. Thus, you get \\.

---

### Post by 1337455 10534 on 2007-11-06
Thx Cheater!
edit>> srry for being spammish

---

### Post by 1337455 10534 on 2007-11-21
```

Traceback (most recent call last):
  File "/home/family/Desktop/iLinux.py", line 283, in <module>
    x86gutsyrepos()
  File "/home/family/Desktop/iLinux.py", line 80, in x86gutsyrepos
    list = open("/etc/apt/sources.list","w")
IOError: [Errno 13] Permission denied: '/etc/apt/sources.list'

```
Not allowed to write to the sources.list. Anyone know ho to bypass or get permission?

---

### Post by soluphobe on 2007-11-21
What about if you run the program from the terminal with sudo?  Does that grant you access?

---

### Post by geirha on 2007-11-21
I'm not sure I understand what you actually want to do. Do you want to add several extra repositories to the sources.list?

If so, I would rather just create new files in "/etc/apt/sources.list.d/". These will be read as if they were part of sources.list. So for instance, the opera repository you could add as /etc/apt/sources.list.d/opera.list with the content:
```

# The Opera browser (packages) (GPG key: 6A423791)
deb http://deb.opera.com/opera etch non-free

```

---

