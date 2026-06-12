---
title: "[SOLVED] Python Question"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by theragingking on 2008-08-01
Hey all. 

Two posts in one day. Can you tell I'm in the middle of recovering from a clean re-install? :p

Anyhoo, I'm trying (and succeeding, for the most part) to get Morrowind (including Tribunal and Bloodmoon) and a number of mods there for working in Cedegan. While working on this, I came across a mod manager called "Wrye Mash Mod Launcher" that I very much want to try out, but it's built in python and I can't seem to get it running. [This page]("http://cedegawiki.sweetleafstudios.com/wiki/Morrowind") says that it's a tricky install, and mentions something about running a version of python in win98 mode (under Issues, fourth bullet-point), but for the life of me I can't figure this out.

Can someone maybe take a look at this, explain to me what needs doing here?

Thanks for your time!

TRK~

---

### Post by kestrel1 on 2008-08-01
Could be wrong, but looks like a Windows version, hence win98 mode. I would think this relates to Win XP comaptibility mode.

---

### Post by theragingking on 2008-08-01
Kinda figured that from how it was archived; I've yet to come across any program geared toward linux what's been a .zip. Either way, I don't know what to do with the darn thing >.<

Any advice?

---

### Post by theragingking on 2008-08-01
Still looking for help here. Anyone? I can't figure this out by myself.

---

### Post by kestrel1 on 2008-08-02
Have you tried configuring Wine? 
Go to Applications - Wine - Configure Wine & under the Applications tab there is a setting at the bottom that allows you to choose the appropriate Windows Version. I think that is where you will need to change it to Windows 98. Then run the program.

---

### Post by theragingking on 2008-08-02
Actually I'm pretty sure it means running it from the command line in win98 mode using cedega, it being a windows gaming environment emulator et al. I did get that far at least.

I tried this after finding syntax, which btw, was like trying to find a needle in a heystack:

```
cedega -winver win98 -install python-2.5.2.msi
```

And I get this error in return:

```
ERROR: The -install command requires at least a Game Name and Setup EXE Name.
```

So, I'm closer, but I still need help from someone on this.

---

### Post by kestrel1 on 2008-08-02
Sorry, totally forgot about Cedega being an emulator.
It looks like Cedega wants an EXE file not an MSI.
I found this on another site about installing MSI's:
> To install .msi (Microsoft Installer) files get [http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe](http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe) and install it with the command You can install Windows Installer by typing $ cvscedega instmsia.exe Now type $ cvscedega msiexec /i somefile.msi and the application will be installed.
This was the site:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=howto%20cedega%20cvs](http://www.linux-gamers.net/modules/wiwimod/index.php?page=howto%20cedega%20cvs)

---

### Post by theragingking on 2008-08-02
Ah! Much thanks, I shall try this and report back.

---

### Post by theragingking on 2008-08-04
I finally got it working, do largely in part to my own dinking. But I couldn't have gotten anywhere without the link you posted, Kestral, so much thanks for that!

The tutorial I finally found was here:

[http://www.cedega.com/forum/viewtopic.php?t=9212](http://www.cedega.com/forum/viewtopic.php?t=9212)

Essentially, do what he says but use your Morrowind paths instead of Oblivion. It'll work out just fine ^.^

THanks for the help!
TRK~

---

### Post by theragingking on 2008-08-04
And by the by, you were right: it all came down to wine >.<

---

### Post by kestrel1 on 2008-08-04
Glad you managed to get things working. At least I was a little help :)

---

