---
title: "HOWTO: Disable the NTP sychronization process during usplash."
date: 2005-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Muhammad on 2005-10-15
Many people have reported that NTP Synchronization slows down or lags the booting process, I thought I might as well post a mini-HOWTO. :)

[list]**System -> Administration -> Synaptic**[/list]

[list]Click Search and type "ntpdate" in the search box.[/list]

[list]Right-click and choose "Mark for Removal"[/list]

NOTE:This will also remove the Ubuntu-minimal, but don't worry, it won't cause harm .

**_Alternate Method:_**

```
sudo apt-get remove ntpdate
```

Congratulations, the NTP will never cause you annoyances again!

---

### Post by LaSSarD on 2005-10-15
If you don't want it to be permanent, you can just remove its executable permission:
sudo chmod -x /etc/init.d/ntpdate

---

### Post by jobezone on 2005-10-17
In Gnome, you can also deactivate it going to the menu option System -> Administration -> Services

---

### Post by oblib on 2005-10-20
Another, less "removing" solution is to use the following command, given all over the forums:

```
sudo update-rc.d -f ntpdate remove
```

That just removes it from startup. Worked for me!

---

### Post by bam on 2005-10-21
thanks worked well, the one above me :)

---

### Post by LaSSarD on 2005-10-21
nice one oblib, very chic way :D

---

### Post by mlomker on 2005-10-22
I'd recommend downloading the **bum** package.  It is a lot easier than update-rc.d or any other method.

---

### Post by hesee on 2005-10-22
[QUOTE=oblib]Another, less "removing" solution is to use the following command, given all over the forums:

```
sudo update-rc.d -f ntpdate remove
```

That just removes it from startup. Worked for me![/QUOTE]

Strange thing happened when I did like that: during next boot the boot process stopped and computer power went down. When this happened, last line was: calculating module dependencies...    I had to boot failsafe, and put ntpdate back to be able to normal boot (this ntpdate fails, btw. That was the original reason to remove it...)

---

### Post by brj on 2005-10-28
[QUOTE=jobezone]In Gnome, you can also deactivate it going to the menu option System -> Administration -> Services[/QUOTE]

deactivating the service didn't help :( ubuntu still tries to to sync the clock during boot.

---

### Post by RSX311 on 2005-10-28
I removed ntupdate but it removed ubuntu-minimal with it, why does it do that?  I was afraid it might of affected something else so I did apt-get install ubunutu-minimal and it installed ntupdate back again.  Anybody know why?

---

### Post by mlomker on 2005-10-28
That's a metapackage, so you can safely remove it.  That being said, there's no reason to remove ntpdate.  You can just disable it using **bum**, as previously mentioned.

---

### Post by manicka on 2005-10-28
**BUM** is available in universe

sudo apt-get install bum 

lol

---

### Post by emendelson on 2005-10-28
Another easily reversible way to do this is

```
cd /etc/rcS.d
sudo mv S51ntpdate _S51ntpdate

```

If you ever want it back, just rename the file.

---

### Post by brj on 2005-10-29
[QUOTE=mlomker]That's a metapackage, so you can safely remove it.  That being said, there's no reason to remove ntpdate.  You can just disable it using **bum**, as previously mentioned.[/QUOTE]
i can install and even run **bum**. but i must admit, i'm not able to enable the startup script **ntpdate** nor any other script :(

---

### Post by Miciomiao on 2009-10-21
Guess what?
/etc/network/if-up.d/ntpdate
-_________-'
Can't they just leave the clock alone?

---

