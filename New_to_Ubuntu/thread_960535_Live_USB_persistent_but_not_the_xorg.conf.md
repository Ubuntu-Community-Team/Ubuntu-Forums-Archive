---
title: "Live USB persistent but not the xorg.conf"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by aimpau on 2008-10-27
Every time I boot my Xubuntu Hardy USB with my friend's laptop, I always have to type:

1. sudo nvidia-xconfig
2. startx

I removed the gdm btw.

The above commands are needed so that I can change the desktop resolution by using nvidia-settings. However, when I reboot, everything persists except the xorg.conf. It always gets rewritten. Is there a workaround for this? If none, is the xinit.rc in a persistent LiveUSB, persistent? Anyone can help in a temporary workaround?

Thanks!

---

### Post by aimpau on 2008-10-30
sudo bump

---

### Post by C.S.Cameron on 2008-10-30
I understand that /etc/X11/xorg.conf is not located in a persistent folder or partition, (casper-rw or home-rw).
A full install to the flash drive will make a flash drive that works just like a HDD install.

---

### Post by Mr. Picklesworth on 2008-10-30
> **C.S.Cameron said:**
> I understand that /etc/X11/xorg.conf is not located in a persistent folder or partition, (casper-rw or home-rw).
A full install to the flash drive will make a flash drive that works just like a HDD install.

Keep in mind, though, that using the flash drive like that means Ubuntu will do a lot more writing to the drive, which will drain its life fairly quickly as opposed to the Live USB thing.

---

### Post by snowpine on 2008-10-30
> **Mr. Picklesworth said:**
> Keep in mind, though, that using the flash drive like that means Ubuntu will do a lot more writing to the drive, which will drain its life fairly quickly as opposed to the Live USB thing.

Please quantify "drain its life fairly quickly"... Days? Weeks? Months? Years?

---

### Post by C.S.Cameron on 2008-10-30
I have a flash drive that I have been using with full install for over a year, (and it still has 4 left on the guaranty).

I think this one should be sent to Myth Busters as I have never heard of it actually happening.

A persistent install writes to the USB also.

---

### Post by aimpau on 2008-10-31
I actually would like to second that. I have an 8 yr old Apacer 256mb and I've formatted it a lot of times, written tons of data and even converted it to Damn Small Linux then to Puppy then back to DSL. Still working in top shape as of now.

Anyways, I was expecting that since it is a Live USB, it SHOULD not have a persistent xorg.conf to maintain compatibility with other computers. How can I edit my xinit?

---

### Post by Fosite on 2008-11-02
[I]I also had this problem, but created a pretty basic workaround.

After setting up your correct xorg.conf back it up. [/I]
sudo nvidia-xconfig
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.nvidia

*then write a simple script to reset your xorg config:*
echo "cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf" > resetNVXorgConf
sudo mv resetNVXorgConf /etc/init.d/ 
sudo chmod +x /etc/init.d/resetNVXorgConf

[I]then link it into runlevel2 so it starts just before X. (S29)
[/I]
sudo ln -s ../init.d/resetXorgConf S29resetXorgConf

*works for me.*

---

### Post by aimpau on 2008-11-03
If it's Linux, it will work for anyone. :)

Thanks for sharing valuable knowledge! :)

edit:
Btw, how do I disable to feature or do I just reconfigure in displayconfig-gtk if its a different PC altogether?

I noticed that you just registered so you can answer my concern. Thanks!

---

### Post by octaedro7 on 2009-03-29
> **Fosite said:**
> [I]I also had this problem, but created a pretty basic workaround.

After setting up your correct xorg.conf back it up. [/I]
sudo nvidia-xconfig
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.nvidia

*then write a simple script to reset your xorg config:*
echo "cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf" > resetNVXorgConf
sudo mv resetNVXorgConf /etc/init.d/ 
sudo chmod +x /etc/init.d/resetNVXorgConf

[I]then link it into runlevel2 so it starts just before X. (S29)
[/I]
sudo ln -s ../init.d/resetXorgConf S29resetXorgConf

*works for me.*

Fosite: I've tried to follow (what I understood of) your directions to no avail.
Could you please give a more detailed step by step guide to accomplish it?
Would be highly appreciated.

---

### Post by tonidekohlanta on 2009-08-04
Hello everybody,
I revive this old thread because it's the only place where I found a good and easy solution to the xorg.conf issue on USB key persistent Ubuntu.
The given solution has small mistakes so I would like to correct them for everyone else. After installing nvidia packages in synaptic:
# nvidia-glx 
# nvidia-kernel-common 
# linux-restricted-modules-(your-kernel-version)

The good instructions are, as typed in terminal:

sudo nvidia-config
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.nvidia
echo "cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf" > resetNVXorgConf
sudo mv resetNVXorgConf /etc/init.d/
sudo chmod +x /etc/init.d/resetNVXorgConf
sudo ln -s /etc/init.d/resetNVXorgConf etc/rc2.d/S29resetNVXorgConf

The last line is were there were mistakes, as the link file we create has to be in rc2.d folder to be launchable during boot, and there also was a name mistake. I put all instructions just to give the complete solution.
I hope it will help some people.
Toni

---

