---
title: "Updating Ubuntu- IBM T40"
date: 2013-09-02
forum: New to Ubuntu
---

### Post by rainerfeyer on 2013-09-02
Hello All,

Newbie here for sure - love your forum!

Just installed Ububtu 11 on my IBM T40 - runs very well, but states it is not supported anymore and asks to be updated.
I am afraid that an update would cripple my T40 which does not have High Memory support (can't remember the term but sounded like PSA - and I know it has nothing to do with the prostate).

Thanks in advance,

Rainer

---

### Post by whitesmith on 2013-09-02
Open a terminal (Ctrl-Alt-T) and copy and paste this into it ```
df -lh /
``` This will give used and available memory. Post the result for our inspection. My 12.04 LTS takes up only 6.1 GB. You should really be on this version to be assured of support until 2017.

---

### Post by steeldriver on 2013-09-02
^^^ that's disk space, not memory

rainerfeyer, I guess you are probably referring to [PAE]("https://help.ubuntu.com/community/PAE") <-- lots of info there, including options for lighter weight desktops which may be more suitable for slower machines with lower amounts of RAM (I have an old X30 btw)

---

### Post by rainerfeyer on 2013-09-02
TY Both!

PAE - that's it! I will do some reading at the link you provided - tried an install of U12 first, but system hung repeatedly, so I figured it's not for this T40.

My current status shows:  Memory 495.9   Processor Intel Pentium M 1500MHz    32bit, 36 gig disk space

---

### Post by Jonathan Precise on 2013-09-02
> **rainerfeyer said:**
> Hello All,

Newbie here for sure - love your forum!

Just installed Ububtu 11 on my IBM T40 - runs very well, but states it is not supported anymore and asks to be updated.
I am afraid that an update would cripple my T40 which does not have High Memory support (can't remember the term but sounded like PSA - and I know it has nothing to do with the prostate).

Thanks in advance,

Rainer

Ubuntu 11.04 and 11.10 are **E*O_L_***s (have reached their **E**nd-***O***f-_***L***_ife)

Always: **_BACKUP YOUR DATA!_**
[HR][/HR]Recommended: install Lubuntu-fake-PAE 13.04. Install options: "Upgrade Ubuntu 11.xx to Lubuntu 13.04". Follow the instructions.
[HR][/HR]Not recommended: in the terminal, type:
```
gksudo gedit /etc/apt/sources.list
```

Edit as follows:
> ... [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) ...

to:
> ... [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) ....

---

### Post by mörgæs on 2013-09-02
If the PAE-workaround is too cumbersome you can also install the non-PAE version of Bodhi. See the link in my signature.

---

### Post by rainerfeyer on 2013-09-02
Jonathan,where would I find the instructions for the update? Would that go through the Software Manager?
Also, will not give up this time - Will never use Win8 so I am starting to get used to Linux with a couple of non-essential laptops.

---

### Post by rainerfeyer on 2013-09-02
I tried a couple of versions: Xubuntu and PCLinuxOS - Xubuntu was too confusing in the beginning - could not figure how to mount a Network Windows drive. PCLinuxOS seemed 'Nice', but I could not get used to the software updater.
Did try the newer version of Ubunto, but after 5 hours install it was still crawling along.

---

### Post by whitesmith on 2013-09-02
> **steeldriver said:**
> ^^^ that's disk space, not memory[snip]
If the OP has enough RAM to run v11* he certainly has enough to run v12* so disk space--secondary memory--becomes an issue...just to dot the Is and cross the Ts.

---

### Post by rainerfeyer on 2013-09-02
Hmm - not sure if I should try again with Ubuntu 12? Maybe I had a bad disk? Would it be best to get-app (trying to show I know something, which is nothing) or go from DVD again?

---

### Post by mörgæs on 2013-09-03
Please run

```
sudo lshw -sanitize > lshw.txt
```

and post lshw.txt in CODE tags.

---

### Post by sudodus on 2013-09-20
Instead of updating and upgrading, backup your personal data and make a fresh installation, because it is much easier. Try either of

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE) or [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971")

---

### Post by amjjawad on 2013-09-20
> **rainerfeyer said:**
> Hello All,

Newbie here for sure - love your forum!

Just installed Ububtu 11 on my IBM T40 - runs very well, but states it is not supported anymore and asks to be updated.
I am afraid that an update would cripple my T40 which does not have High Memory support (can't remember the term but sounded like PSA - and I know it has nothing to do with the prostate).

Thanks in advance,

Rainer

Hello and welcome!

PAE:
[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

Ubuntu Wiki - PAE:
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

Fake PAE:
[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

I'd suggest using Lubuntu 12.04 but I know someone here will strongly disagree with this suggestion so to save time, without going to deep technical discussion and endless argument, you may want to tell us what exactly are you going to use that machine for?

I have a P4 machine with less than 512MB RAM and 40GB IDE HDD, sitting 1.5m away from me, has two systems: Ubuntu 10.04 and Lubuntu 12.04 and I am not using this machine for daily tasks, I keep it just to play with it whenever I'm bored as I love Ubuntu 10.04 a lot. I do know that both versions are technically outdated but because I know what I am doing with that machine, I would worry less whether the version is supported or not.

Ubuntu 10.04 EOL:
[http://fridge.ubuntu.com/2013/05/10/ubuntu-10-04-lucid-lynx-desktop-end-of-life-reached-on-may-9-2013/](http://fridge.ubuntu.com/2013/05/10/ubuntu-10-04-lucid-lynx-desktop-end-of-life-reached-on-may-9-2013/)

Does 12.04 LXDE have LTS?
[http://askubuntu.com/questions/237077/does-12-04-lxde-have-lts](http://askubuntu.com/questions/237077/does-12-04-lxde-have-lts)

Lubuntu vs Ubuntu:
[https://wiki.ubuntu.com/Lubuntu#Lubuntu_VS_Ubuntu](https://wiki.ubuntu.com/Lubuntu#Lubuntu_VS_Ubuntu)

---

