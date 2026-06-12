---
title: "installing gimpshop"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by zaklinux on 2008-06-10
Installed Gimpshop using instructions from the following website: 

[http://delirial.com/archives/howto-gimpshop-on-ubuntu/](http://delirial.com/archives/howto-gimpshop-on-ubuntu/)

Running *gimp* I get the following error: 

[I]/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory
[/I]

To resolve issue tried running: 
[I]
sudo apt-get install libgimpprint-dev[/I]

but this is what I got: 
[I]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgimpprint-dev[/I]

Any suggestions ?

---

### Post by littletinman on 2008-06-10
[http://plasticbugs.com/?page_id=294](http://plasticbugs.com/?page_id=294)


Look for the deb file and install it that way. it should work. let me know if it doesn't.

---

### Post by zaklinux on 2008-06-10
Thanks littletinman for helping me out.

Removed aforementioned installation of Gimpshomp by selecting it for complete removal using Synaptic Manager.

Downloaded and double clicked on th deb file you suggested The Package Installer said that package was installed.

Ran gimp from applications menu > gimp still looks the same.

Ran gimp from terminal > gimp still looks the same and I can see the same error message in terminal as before 

[I]/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory
[/I]

---

### Post by kleo skywalker on 2008-06-21
> **zaklinux said:**
> Downloaded and double clicked on th deb file you suggested The Package Installer said that package was installed.

Ran gimp from applications menu > gimp still looks the same.

I have the same problem. I installed GIMPshop from that link on a fresh install of Hardy, but GIMP looks the same - the "shop" part is missing. Anyone know how to fix this?
Thanks.

---

### Post by kleo skywalker on 2008-06-22
> **kleo skywalker said:**
> I have the same problem. I installed GIMPshop from that link on a fresh install of Hardy, but GIMP looks the same - the "shop" part is missing. Anyone know how to fix this?
Thanks.

Update: I tried to open GIMP from the terminal - just to say if there were any messages or some such, and it does open up as GIMPshop, but I still get this message:
> /usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory
(gimp:8020): LibGimpBase-WARNING **: gimp: wire_read(): error
Also, I can't open GIMP from the menu, or by right-clicking an image - nothing happens.
This is not good, I was using GIMPshop in Gutsy and was hoping to use it on Hardy without any problems.
Any ideas?

---

### Post by kleo skywalker on 2008-06-24
bump

---

### Post by webofunni on 2008-06-24
Hi,

  Try "gimp-gutenprint". 

```
apt-get install gimp-gutenprint
```

---

### Post by webofunni on 2008-06-24
Fixed the error "/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries:" using following steps : 

```

#wget http://nchc.dl.sourceforge.net/sourceforge/gimp-print/gimp-print-4.2.7.tar.gz
#tar zxvf gimp-print-4.2.7.tar.gz
#cd gimp-print-4.2.7/
#./configure
#sudo make
#sudo make install

```

  Got an error saying lex not found when "./configure" script executed. Fixed that using " apt-get install flex".

---

### Post by kleo skywalker on 2008-06-25
> **webofunni said:**
> Hi,

  Try "gimp-gutenprint". 

```
apt-get install gimp-gutenprint
```

Thanks, but this made no difference. And I'm not surprised - this is a print plugin for GIMP, isn't it? Doesn't seem very related to my problem.

Any more ideas, anyone?

---

### Post by kleo skywalker on 2008-06-30
bump

---

### Post by kleo skywalker on 2008-07-06
bump!

---

### Post by alzie on 2008-07-06
I just downloaded and installed Gimpshop using the site that littletinman said and it seems to have installed fine.

I left the existing Gimp in place when I installed.

I would try removing Gimpshop,  install gimp from the repositories then install Gimpshop again.

I hope this helps

My install looks this the one here:  [http://www.ubuntugeek.com/howto-install-gimpshop-in-ubuntu-hardy.html](http://www.ubuntugeek.com/howto-install-gimpshop-in-ubuntu-hardy.html)

---

