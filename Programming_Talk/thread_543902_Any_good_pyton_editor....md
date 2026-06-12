---
title: "Any good pyton editor..."
date: 2007-09-05
forum: Programming Talk
---

### Post by Majorix on 2007-09-05
...that is available on the repos or as a deb package?

SPE doesn't work with me for some reason even though I would love it to.

So any other good alts?

---

### Post by steve.horsley on 2007-09-05
I normally use gedit or geany.

---

### Post by Majorix on 2007-09-05
They don't do automatic indentation though do they?

---

### Post by Mirrorball on 2007-09-05
Eclipse + Python plugin, Komodo Edit, kate...

---

### Post by nanotube on 2007-09-05
i like scite, and pype. these both do indentation and code folding. geany.. i think it does auto indent too?

---

### Post by Acglaphotis on 2007-09-05
SciTE FTW!

---

### Post by gnuman on 2007-09-05
DrPython is currently my favorite.

---

### Post by pmasiar on 2007-09-05
IDLE is the simple one. 

Any decent programmer's text editor should recognize Python: SciTE is the fast and universal one. Kate, Gnome editor - all will work.

For IDE, use Eric if you cannot use SPE. 

What errors SPE reports?

---

### Post by Majorix on 2007-09-06
I will try scite since so many recommend it.

And SPE reports this:
```
majorix@gaul:~$ spe

Spe Warning: Spe was developped on wxPython v2.6.1.0., but v2.8.4.0. was found.
If you experience any problems please install wxPython v2.6.1.0.


SPE v0.8.2.a (c)2003-2005 www.stani.be

If spe fails to start:
 - type "python SPE.py --debug > debug.txt 2>&1" at the command prompt
   (or if you use tcsh: "python SPE.py --debug >& debug.txt")
 - send debug.txt with some info to spe.stani.be[at]gmail.com
 
Blender support disabled (run SPE inside Blender to enable).

Encrypted debugging disabled. 
  If you prefer encrypted debugging, install the "Python Cryptography Toolkit"
  from http://www.amk.ca/python/code/crypto

Launching application...
majorix@gaul:~$ 

```

---

### Post by pmasiar on 2007-09-06
> **Majorix said:**
> 
And SPE reports this:
```
majorix@gaul:~$ spe

Spe Warning: Spe was developped on wxPython v2.6.1.0., but v2.8.4.0. was found.
If you experience any problems please install wxPython v2.6.1.0.

```

Well, SPE detected wrong version of wxPython and suggested what to do. So I am not sure where is the problem. Did you tried installing SPE with matching version of wx, and it did not worked still? How did you installed it: manually, or using Synaptic?

---

### Post by Majorix on 2007-09-06
I installed it from Synaptic.

But  don't you find it odd that I need an older version of software just to make spe work? Can't they just recompile their code or something to make it work with newer versions? Or is the project abandoned?

---

### Post by pmasiar on 2007-09-06
> **Majorix said:**
> I installed it from Synaptic.

But  don't you find it odd that I need an older version of software just to make spe work? Can't they just recompile their code or something to make it work with newer versions? Or is the project abandoned?

No, I don't find it odd that software works with some version of library and not with other. What new features do you miss?

I have no clue but I assume that some wxPython API changed and it is hard to maintain compatibility.

I installed by Synaptic too and it worked just fine, so you did something differently.

---

### Post by stani on 2007-09-17
> **Majorix said:**
> I installed it from Synaptic.

But  don't you find it odd that I need an older version of software just to make spe work? Can't they just recompile their code or something to make it work with newer versions? Or is the project abandoned?
A quick visit to the spe website ([http://pythonide.stani.be](http://pythonide.stani.be)) would show that the project is not abandoned at all. The time I have available for SPE, I devote to development rather then packaging. If you use ubuntu, you can easily install the latest version of SPE if you follow the instructions on the "download (subversion)" link. Just open a terminal in the folder where you want to download SPE :
```
sudo apt-get install subversion
svn checkout svn://svn.berlios.de/python/spe/trunk/_spe
```Do not rename the _spe folder. You can start SPE with a shortcut or in the terminal by:```

python your_folder/_spe/SPE.py
```This version of SPE is the one I use and develop myself on Ubuntu, which is SPE preferred platform. I strongly recommend not using the version in synaptic, but in subversion.

Good luck!
Stani

---

### Post by Majorix on 2007-09-18
Ok stani, thanks a lot for personally coming and replying in the thread, I really appreciate that :)

I will try the subversion, and let you know how it went.

---

### Post by stani on 2007-09-18
Of course don't forget to uninstall first your previous version of SPE first! Offtopic: if you need to batch resize/rotate images, you could try my new software: [http://photobatch.stani.be](http://photobatch.stani.be) (free download link below).

Stani

---

### Post by CostaRica on 2007-09-21
> **stani said:**
> Just open a terminal in the folder where you want to download SPE :
```
sudo apt-get install subversion
svn checkout svn://svn.berlios.de/python/spe/trunk/_spe
```Do not rename the _spe folder. You can start SPE with a shortcut or in the terminal by:```

python your_folder/_spe/SPE.py
```

Good luck!
Stani

I did what you (Stani) said, but now i can not find the file or run SPE!  I searched in the file system, in my home folder and it is not there, although I tried to install it again and says I already have the newest version (I completely uninstalled the repo version before).

---

### Post by UbuWu on 2007-09-21
> **stani said:**
> The time I have available for SPE, I devote to development rather then packaging.
This version of SPE is the one I use and develop myself on Ubuntu, which is SPE preferred platform. I strongly recommend not using the version in synaptic, but in subversion.


It would help if you officially release a new version of spe. Usually the latest stable version of software is in the ubuntu archives, not the current subversion snapshot.

---

### Post by pmasiar on 2007-09-23
OTOH, if developer has time pressures, i prefer to use time on features and committing them to SVN, and not waste precious time on packaging. There **is** SPE in repos, packaged by MOTU. If you need something better, maybe you wanna help with it?

---

### Post by sacherjj on 2007-09-25
I like Scribes.  I am using it more and more for all my program editing on python and more.

---

