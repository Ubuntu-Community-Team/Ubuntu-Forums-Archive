---
title: "how do you know when there are updates to ubuntu? you run the updater every day?"
date: 2017-06-07
forum: New to Ubuntu
---

### Post by ronjjjg8885 on 2017-06-07
tnx

---

### Post by LastDino on 2017-06-07
[https://wiki.ubuntu.com/SoftwareUpdates](https://wiki.ubuntu.com/SoftwareUpdates)

Check the part and familiarize with checking update automatically.

Personally, and I'm sure lot of people here run 

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

On versions before 16.04 and on later
```
sudo apt update && sudo apt upgrade && sudo apt dist-upgrade
```

on daily basis, rendering gui package manager useless. 

You can also achieve good results from Synaptics.

---

### Post by Tadaen_Sylvermane on 2017-06-07
After much research on how often to reboot, how often to update I settled on once every 2 weeks. I do my laptop, server, lxd containers and ltsp chroots at the same time.  I do this typically on Sunday morning, takes less than a half hour usually to get through all of it. After doing all of this the laptop and server get rebooted and I leave them alone until 2 weeks later on Sunday morning. This is mostly due to my laziness. 

I don't see the need to update daily. While it may be dumb I figure 2 weeks is often enough when combined with the security by obscurity philosophy. I don't have much of an attack vector on my network here at home so I don't really worry about it to much. I also don't need to always have the absolute latest version of things. As long as it works and I get my work done, or in the case of the server everyone has access to their media and tv (through mythtv-backend) then I don't even think about it.

---

### Post by Tadaen_Sylvermane on 2017-06-07
Wouldn't let me edit original post. In a nutshell don't try to always be on top of it. If it pops a notification go for it, or set a schedule to check manually. Can't go wrong either way.

---

### Post by sp40140 on 2017-06-07
The default setting in standard Ubuntu install is to check for updates daily.
Weather you should change it or not, or when to install the updates depends on the purpose of the computer, how handy you are with linux and how much time you have and peripherals you have connected to your machine, etc.

---

### Post by ronjjjg8885 on 2017-06-09
wait a moment.
are you saying the the Software Updater isn't a good tool?

do you type this whole and long update command each day?

---

### Post by sp40140 on 2017-06-09
You don't have to. Software updater is good enough. And even then you can dump all these commands in a shell script and set it to run everyday.

---

### Post by LastDino on 2017-06-09
And if you use this command at least ones, you can next time navigate to it with arrow keys when you open the terminal. Usually that is like 2-3 presses away even for me.

---

### Post by vasa1 on 2017-06-09
Or make an alias?

---

### Post by LastDino on 2017-06-09
Very easy how to on alias

[http://www.hostingadvice.com/how-to/set-command-aliases-linuxubuntudebian/](http://www.hostingadvice.com/how-to/set-command-aliases-linuxubuntudebian/)

Detailed info page
[http://www.linfo.org/alias.html](http://www.linfo.org/alias.html)

---

### Post by oldos2er on 2017-06-09
I run ```
up
``` about once a day. ```
alias up='sudo apt update && sudo apt full-upgrade'
``` I don't use Update Manager or anything like that, always found it annoying.

---

### Post by mörgæs on 2017-06-09
> **LastDino said:**
> And if you use this command at least ones, you can next time navigate to it with arrow keys when you open the terminal. Usually that is like 2-3 presses away even for me.

+1 

It's also a good way to get to learn the command line. If you have copy-pasted a useful command (say, the update commands mentioned here) into the terminal it's easy to recycle it: Just give the command *history*, and your... well, history appears. If the command you need is number 25, you recycle it by giving the command *!25*

---

