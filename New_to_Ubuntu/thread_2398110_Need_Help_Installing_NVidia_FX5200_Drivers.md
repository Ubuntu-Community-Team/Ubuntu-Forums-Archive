---
title: "Need Help Installing NVidia FX5200 Drivers"
date: 2018-08-07
forum: New to Ubuntu
---

### Post by geford211 on 2018-08-07
Hello all.

My PC is a 2001 Computer with an AMD XP 2000+ Processor, 512 MB of RAM, and a 80 GB HDD.

It formerly ran Windows XP fine. However, with the deprecation of Windows XP, I was motivated to switch to Lubuntu. The Hard Drive was DBAN'd (wiped) and Lubuntu was installed.

I recently acquired an AMD FX5200 AGP card for my machine, it is currently removed, because the graphics drivers on LUBUNTU do not support that specific graphics card.

I **do not** have **Internet Access** on the Lubuntu machine, and am currently posting this from another machine with internet access. Due to circumstances, it is impossible to connect an ethernet plug.

I am attempting to install the NVidia 5 FX drivers, which amazingly, were available for linux computers, however, after typing 

```
cd/home/user/Downloads

chmod +x NVIDIA-Linux-x86-173.14.39-pkg1.run

sudo ./NVIDIA Linux x86-173.14.39.pkg1.run
```

Through the LDXE Terminal

it would return an error message box requesting me to install binutils.

I have obtained the binutils 2.31 tar.xz package from this computer, and transferred it over to the linux PC via USB, but I do not understand how to install it into the Lubuntu computer.

Remember. I cannot CONNECT THAT COMPUTER TO THE INTERNET. It is out of the question!

Is there any way to install binutils from the .tar.xz package?

Thanks.

And Geez.... nobody told me that installing linux were this complicated! I regret having given linux a try, and am contemplating switching back to windows XP.

---

### Post by Autodave on 2018-08-07
Linux is quite easy to install.....provided you have internet access. When you install any package, there are dependencies (extra files that are needed to make something work) that need to be installed. Whereas Windows gives you a whole bunch of files to cover just about any possibility, Linux only gives you what you need. (You may have noted the very small size of your Lubuntu install.

Hopefully someone will be able to help you, but I have no idea how to do what you want to do w/o internet access.

What driver are you trying to install and where did you get it from?

---

### Post by Yellow Pasque on 2018-08-07
The Nvidia 173.xx driver is EOL and won't work on modern versions of Ubuntu (the Xserver version is not new enough). It's a dead end.

> the graphics drivers on LUBUNTU do not support that specific graphics card.
False. The best driver available ("nouveau") should used by default. If you have a problem with it, give more details on your issue.

---

### Post by NM5TF on 2018-08-08
> **Temüjin said:**
> The Nvidia 173.xx driver is EOL and won't work on modern versions of Ubuntu (the Xserver version is not new enough). It's a dead end.


[COLOR="#FF0000"]False. The best driver available ("nouveau") should used by default[/COLOR]. If you have a problem with it, give more details on your issue.

+1

nvidia has dropped support for it's older graphics cards...when Xorg-server changed to v1.20 the legacy nvidia drivers no longer work....go with nouveau....

tommy

---

