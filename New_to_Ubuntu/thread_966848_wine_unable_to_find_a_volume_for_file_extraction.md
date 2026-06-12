---
title: "wine unable to find a volume for file extraction"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by lance bermudez on 2008-11-01
wine tells me ¨Unable to find a volume for file extraction. Please verify that you have proper permissions.¨ What do I do now?

---

### Post by taurus on 2008-11-01
Sounds like a permission problem to me.  What exactly did you try to run?

---

### Post by lance bermudez on 2008-11-01
i did like the beginner man told me to do. I installed wine and winde-dev with synaptic. then i right click on the program I wanted to install then did the open with ¨wine program Loader¨ to install my program. It has worked in the past but this time it does not want to work.

---

### Post by lance bermudez on 2008-11-01
if i do it from the command line using
lance@bermudez:~$ sudo wine *.exe
wine: /home/lance/.wine is not owned by you

and if i do the same command without the sudo I get the same error i was getting from the top

---

### Post by taurus on 2008-11-01
Is the program in your $HOME, /home/lance?  What if you just run it like

```
wine **filename**.exe
```
Replace the **filename** with the actual name of the file.

Otherwise, you can change the ownership of /home/lance/.wine again with

```
sudo chown -R lance:lance /home/lance/.wine
wine **filename**.exe
```

---

### Post by lance bermudez on 2008-11-01
yes the file i´m trying to install is in my home dir of /home/lance/file.exe

---

### Post by lance bermudez on 2008-11-03
I downloaded the new debs from winehq for wine and wine-dev at
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
things seem to be working so far the way I want. Thank you all for you help.

---

### Post by byakuray on 2009-06-01
I have the same problem but I did not understand how to solve it. Because of I don't find a C++ free and visual compiler different to Microsoft Visual C++ Express, I'll have to install it.
Please, somebody tell me about a way to install Microsoft Visual C++ Express on Ubuntu Hardy i386 or about a different free program that is visual too.

---

### Post by knifemonk on 2009-07-06
i use winetricks to install any microsoft redistributable files.

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by Tyler Oderkirk on 2009-08-11
Knifemonk is correct; winetricks version 20090809 provides a workaround for the Wine bug [0] that the original poster encountered. The bug was fixed in Wine 1.1.7 but Jaunty's repositories provide 1.0.1.

[0] [Windows Installer 3.1 cannot install because of non-standard drive labeling]("http://bugs.winehq.org/show_bug.cgi?id=5351")

---

### Post by Hemppainen on 2010-03-18
I got this same problem when I was installing dotnet30. I read lots of forum posts and do everything that was said there, but nothing helped.

I use NFS to share my home directories from my file server and this was the problem. I logged to file server and ran installation there. It made the volume problem disappear.

---

### Post by sandyd on 2010-03-18
in the latest version of winetricks...
```

winetricks volnum
```

---

### Post by ubuntubrian on 2010-03-31
I ran ```
sh winetricks volnum
```

and got the reply that drive \C was renamed. will this have any effect on any other wine stuff?

---

### Post by score100 on 2010-04-19
same problem here with dotnet 30 (.NET 3.0 Frameworks), using winetricks. "unable to find a volume for file extraction" - so apparently the bug isn't solved yet, because I got the latest wine-version and karmic 9.10.

EDIT: The latest stable version that you usually get from the software center does have the bug, but getting one of the newer development versions (for example 1.1.43 ) it doesn't happen anymore.

---

