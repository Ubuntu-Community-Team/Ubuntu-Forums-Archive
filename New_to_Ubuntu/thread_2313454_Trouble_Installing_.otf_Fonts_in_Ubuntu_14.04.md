---
title: "Trouble Installing .otf Fonts in Ubuntu 14.04"
date: 2016-02-12
forum: New to Ubuntu
---

### Post by 12 leaders on 2016-02-12
Hello everyone,

I recently bought a Chromebook and I'm running Ubuntu 14.04 on it using Crouton.

The work I intend to do on this device involves extensive typing and the use of unique fonts. Some of those fonts are .ttf, while others are .otf. I've had no issues installing the former, but I have been unable to install any of the .otf fonts. I've tried extensively, but nothing seems to help.

If anyone could assist me with this I'd greatly appreciate it. 

Thanks.

---

### Post by coldraven on 2016-02-12
Try this:
[http://askubuntu.com/questions/18357/how-to-install-otf-fonts](http://askubuntu.com/questions/18357/how-to-install-otf-fonts)

---

### Post by 12 leaders on 2016-02-12
I actually tried that earlier. I was able to generate the "opentype" folder in the fonts folder. I then copied and pasted the fonts into that new folder. Afterward, I used Terminal to refresh the font cache. Unfortunately, it's still not working.

Please see attached photos:

[IMG]http://i67.tinypic.com/11w61zc.png[/IMG]

[IMG]http://i65.tinypic.com/33o44qs.png[/IMG]

---

### Post by coldraven on 2016-02-13
I'm not an expert on fonts, I was intrigued and did a bit of searching. However the last response in the link I posted was this:
> Using the standard library on Linux, the OTF fonts don't loads. Must install addictive library based on your system configuration, libotf for example.

I just used the Synaptic Package Manager to browse for libotf and am now slightly confused, there seems to be both libotf0 and libotf-bin. Not sure which one you need :(

Selecting libotf-bin results in it automatically selecting libotf0 as a dependency, so my guess is to do the following and then you'll get both. They are only very small files so that should not create any problems. 

```
sudo apt-get install libotf-bin
```


I just tried it and the install is only 270kb. I don't have any OTF fonts to test this. See below

```
sudo apt-get install libotf-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done

The following extra packages will be installed:
  libotf0
The following NEW packages will be installed
  libotf-bin libotf0
0 to upgrade, 2 to newly install, 0 to remove and 3 not to upgrade.
Need to get 75.2 kB of archives.
After this operation, 270 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ wily/main libotf0 amd64 0.9.13-1ubuntu1 [44.2 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ wily/universe libotf-bin amd64 0.9.13-1ubuntu1 [31.0 kB]
Fetched 75.2 kB in 0s (112 kB/s)     
Selecting previously unselected package libotf0:amd64.
(Reading database ... 368809 files and directories currently installed.)
Preparing to unpack .../libotf0_0.9.13-1ubuntu1_amd64.deb ...
Unpacking libotf0:amd64 (0.9.13-1ubuntu1) ...
Selecting previously unselected package libotf-bin.
Preparing to unpack .../libotf-bin_0.9.13-1ubuntu1_amd64.deb ...
Unpacking libotf-bin (0.9.13-1ubuntu1) ...
Setting up libotf0:amd64 (0.9.13-1ubuntu1) ...
Setting up libotf-bin (0.9.13-1ubuntu1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...


```

Edit: downloaded an OTF font, unzipped it to my home folder, then used the following command and the font is now working in LibreOffice
```
sudo cp QumpellkaNo12.otf /usr/share/fonts/opentype/
```

Edit2: If after unzipping to your home folder you can just double click the OTF file and the Font viewer/installer will open.
Then if you click the install button (top right) the font will be available but I don't know where it puts it. It does not appear in /usr/share/fonts/opentype
Maybe someone else can tell us.

---

### Post by 12 leaders on 2016-02-13
Thanks to your help, I finally was able to get it to work! :D :D :D

I really appreciate your patience and persistence.

---

### Post by coldraven on 2016-02-13
> **12 leaders said:**
> Thanks to your help, I finally was able to get it to work! :D :D :D

I really appreciate your patience and persistence.

No problem, I learned something too. Prior to this I didn't know about otf fonts, it's been years since I did any DTP.

---

### Post by 12 leaders on 2016-02-13
I work as a translator so I can't do without them.
Do you happen to know if RTL fonts are supported natively in Libre Office or is there a command I need to run to set it up?

---

### Post by coldraven on 2016-02-14
Well I just learned what RTL means :)
This seems to be what you need to do, it's shown for a Mac but I presume it will work on any platform.
In Ubuntu the LibreOffice settings are found under Tools>Options>Language Settings>Languages

[http://alefba.us/libreoffice-arabic-persian/](http://alefba.us/libreoffice-arabic-persian/)

---

### Post by 12 leaders on 2016-02-15
I was actually unfamiliar with the acronym myself until saw it being used on multiple forums. :)

Thanks again for your help!

---

### Post by coffeecat on 2016-02-15
> **coldraven said:**
> 
Edit2: If after unzipping to your home folder you can just double click the OTF file and the Font viewer/installer will open.
Then if you click the install button (top right) the font will be available but I don't know where it puts it. It does not appear in /usr/share/fonts/opentype
Maybe someone else can tell us.

If you install a font this way, it's installed locally to your home folder in ~/.local/share/fonts/ . A few releases ago, it went into ~/.fonts/ but I'm fairly sure 14.04 uses ~/.local/share/fonts/ - 15.10 certainly does.

Advantages: quick and easy with no terminal commands. You don't have to refresh the font cache. No messing about with permissions or sudo. 

Disadvantage: the font is available to that account holder only, not system-wide.

---

### Post by coldraven on 2016-02-15
> **coffeecat said:**
> If you install a font this way, it's installed locally to your home folder in ~/.local/share/fonts/ . A few releases ago, it went into ~/.fonts/ but I'm fairly sure 14.04 uses ~/.local/share/fonts/ - 15.10 certainly does.

Advantages: quick and easy with no terminal commands. You don't have to refresh the font cache. No messing about with permissions or sudo. 

Disadvantage: the font is available to that account holder only, not system-wide.

Thanks for clearing that up. I had looked in vain for ~/.fonts and that explains it's absence. I must improve my find/locate skills :)

---

