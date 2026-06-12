---
title: "exe?"
date: 2017-06-27
forum: New to Ubuntu
---

### Post by alexkoganov on 2017-06-27
soooo iam in  linux for a couple of days and ian trying to understand something.
i win when i am downloading a app there is a simple exe file to install the app and a checkbox that asks me if i wand a desktop shortcut.
well i downloded a ssh client (putty) ,unzipped it  and what the hell i am suppose to do from here (scr shot attached).
and after install it what about the desktop shorcut?

tnx

---

### Post by cc1984 on 2017-06-27
Linux doesn't use .exe files. Not sure which distro you are using but in Ubuntu we don't usually download apps like that, instead we install apps from the Ubuntu repositories (there are exceptions to this of course). This can be done through the command line with the apt command or through a GUI like Software Center. Also in Linux, Putty isn't necessary as you can make an ssh connection in a terminal. Here is an example:

```
ssh username@ipaddress
```

---

### Post by alexkoganov on 2017-06-27
and still :).

---

### Post by QIII on 2017-06-27
Hello!

"and still" what?

From your image, it appears that you are running as root.  You shouldn't do that!  Ubuntu does not have root enabled by default for a reason.

Are you asking about installing PuTTY on your Ubuntu machine?  It appears that you have downloaded the source code, which means it will have to be compiled/built.  This is not always an easy task for a beginner.

---

### Post by oldos2er on 2017-06-27
Please tell us which version of Ubuntu you're running. 

Meanwhile here's some info on installing software: [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by CatKiller on 2017-06-27
You don't need to run .exe files. You don't need to install PuTTY.

PuTTY is a tool for Windows to make it do the things that Linux can do. Linux can already do the things that Linux can do.

As cc1984 has already told you, if you want to SSH to somewhere, you use the ssh command.

---

### Post by HermanAB on 2017-06-28
Howdy,

Welcome to the Linux experience.

Linux and BSD systems do things differently from Windows.  Do not download random programs off the internet.  

There is a special software installer (Ubuntu Software Center or Synaptic Package Manager) on your system, which will get and install programs for you very easily - including PuTTY - from the Canonical Ubuntu servers.

---

### Post by Bucky Ball on 2017-06-28
You can install Putty directly from the official Ubuntu repositories (Software). You should look there first before grabbing things randomly from elsewhere. Linux is not Windows. ;)

> **CatKiller said:**
> You don't need to install PuTTY.

PuTTY is a tool for Windows to make it do the things that Linux can do. Linux can already do the things that Linux can do.

Firstly, Putty is NOT a Windows-only program. It is cross-platform and runs natively in Linux (it's in the repos). Secondly, there is no good reason why you would not install Putty for the task. A very handy tool for communicating remotely with other machines. 

There is more than one way to 'kill a cat' when it comes to SSH. Whatever suits. Just pointing out that what you have stated regarding Putty is incorrect. It is cross-platform, install if it suits the purpose. Absolutely no reason not to (I use Putty regularly to communicate with my Raspberry Pi as it is quick and easy and that's on Ubuntu). ;)

---

