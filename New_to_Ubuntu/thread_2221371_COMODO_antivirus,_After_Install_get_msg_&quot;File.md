---
title: "COMODO antivirus, After Install get msg &quot;Filesystem filter driver is not loaded&quot;"
date: 2014-05-01
forum: New to Ubuntu
---

### Post by parker-hugh on 2014-05-01
Installed Lubuntu 14.04 on hp530 notebook.
Installed COMODO 
Start Comodo and shield is red with following message:

Filesystem filter driver is not loaded!
(B) Run Diagnostics
so I run diagnostics and get following message:

The diagnostics utility has found some problems with your installation.
Would you like to fix them?
(B) OK
after I click OK, I get message: 

The kernel module 'avflt.ko' appropriate for your current kernel version does not exist, please run
/opt/COMODO/post_setup.sh to install it. Then run
"/etc/init.d/cmdavd restart" command to restart your cmdavd service.
(B) OK

I managed to install COMODO successfully on another newer pc on Linux  Mint 13 xfce. So I know the software is ok, does this version of linux have an older kernel?

This is the same issue as found here at forums.comodo .... [http://bit.ly/1iEI0qv](http://bit.ly/1iEI0qv)

this link suggested downloading an unofficial driver from here ... [http://www.bondoffamily-net.com/~kinta-chan/techknow/Linux/RedirFS/src/driver.tar]("http://http://www.bondoffamily-net.com/~kinta-chan/techknow/Linux/RedirFS/src/driver.tar")

My question is, is this the correct solution? is it safe to copy and replace the driver? if so, how can I do this using the terminal?

this is the path of the new driver       /home/hugh/Dropbox/Linux/COMODO_AV_LINUX/Driver/New/driver.tar
this is the path of the existing driver /opt/COMODO/driver.tar

I am a noobie to linux so if it is safe to do this, what would be the correct syntax to use in a terminal window?

many thanks for any help, it would be much appreciated

regards,

Hugh

---

### Post by whitesmith on 2014-05-01
You simply don't need any AV software in Ubuntu (or any other *nix) unless you mess around with Windows stuff in Wine. But even if you do, avoid installing/using as su and you'll be fine without anti-virus "protection," which *nix doesn't need because it is designed to keep bad-karma stuff confined to a sandbox (your home directory). Also, AV software slows things down to a crawl. Most modern viruses are too complex to be caught be Comodo or its cohorts. You might consider a hosts file that turns away sites known for bad behavior. A good sample--intended for Windows but usable without modification in Ubuntu--may be found here: [http://msmvps.com/blogs/hostsnews/default.aspx](http://msmvps.com/blogs/hostsnews/default.aspx). Cheers.

---

### Post by ian-weisser on 2014-05-01
> **parker-hugh said:**
> This is the same issue as found here at forums.comodo .... [http://bit.ly/1iEI0qv](http://bit.ly/1iEI0qv)

this link suggested downloading an unofficial driver from here ... [http://www.bondoffamily-net.com/~kinta-chan/techknow/Linux/RedirFS/src/driver.tar]("http://http://www.bondoffamily-net.com/~kinta-chan/techknow/Linux/RedirFS/src/driver.tar")

My question is, is this the correct solution? is it safe to copy and replace the driver? if so, how can I do this using the terminal?

Is the correct solution to download *totally untrusted code* from some *random site off the internet* and insert it into your kernel so it is immune to all Linux filesystem, application, networking, and other built-in protections?

No. I think it's not the correct solution at all.

---

### Post by Ubi_one_2014 on 2014-05-01
remove comodo, and install clamav and clamtk

virus signatures are automaticly updated by freshclam

---

### Post by sammiev on 2014-05-01
I prefer [Bitdefender]("https://help.ubuntu.com/community/BitDefender") as clamav  is well known for false positives. I had Bitdefender find unwanted items which is great as I share items and files with Window users.

---

### Post by parker-hugh on 2014-05-02
Thanks **whitesmith** for your feedback, I have heard that you don't need antivirus on Linux. But there are some people who say that you could be affected by a virus, I'm not sure which view is the correct one.

So  was thinking best play safe as the laptop is for my sister and I wanted to make sure that she was fully protected while online, she has used windows xp up till now, but she needs something else since this is no longer supported, therefore Lubuntu was my first choice for an old notebook.

I was thinking of installing Avast and run it once a week as a safety precaution. would that be a good option? I think this one only runs manually, but that would not be too much of an overhead on the laptop 

Also see that **sammiev** recommends Bitdefender, so would be a good alternative? does this one only run manually?

**Ubi_one_2014**, you mentioned clamav and clamtk, what is the difference between these two?  is there a gui version available? does this one also run manually?

Thanks again for your responses. 

Hugh

---

### Post by LastDino on 2014-05-02
Clamtk is GUI front end for Clamav. And unless you run server, avoid such a hassle of anti-virus. I've found out that best way to go about this is use some bootable tool which can scan your PC for virus and not need you to install it on Linux OS. There are anti virus solutions who provide that facility.

---

### Post by parker-hugh on 2014-05-02
Thanks **Goten0007**, good advice. I will look into that now and will come back and let you know what I have found out. Meanwhile if anyone has any experience of a bootable method, please let me know. regards, Hugh

---

### Post by Ubi_one_2014 on 2014-05-02
yes, clamtk is the gui for clamav, what i use also on kubuntu 14.04

for my debian server i have installed clamav as well. I use it in combination with proftpd server

i find it a very convienient AV

---

