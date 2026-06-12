---
title: "OS Updates Won't Download/Install"
date: 2018-03-27
forum: New to Ubuntu
---

### Post by shanasman450 on 2018-03-27
I'm showing to have an os update and when I click install a loading bar appears on the install button, gets to about 1/4 then quits and I'm told to check my internet connection. Anyone else have this issue? Also, what is the difference between using the Ubuntu Software application to download/install updates and using sudo apt-get update?


PS. I have made sure I'm connected at the time of installation and I have tried restarting the computer.

---

### Post by wildmanne39 on 2018-03-27
*Thread moved to **New to Ubuntu, a more appropriate forum**.*

---

### Post by QIII on 2018-03-27
Hello!

Which release of Ubuntu are you using?

Would you please use the terminal and issue the following:

```
sudo apt-get update
```

Please post the results.

---

### Post by shanasman450 on 2018-03-27
I'm using 16.04

Here's the terminal output. [https://drive.google.com/file/d/1k2j8wYnj00D-IA0vo4ilCLzOr_derW0e/view?usp=sharing](https://drive.google.com/file/d/1k2j8wYnj00D-IA0vo4ilCLzOr_derW0e/view?usp=sharing)

---

### Post by Geoffrey_Arndt on 2018-03-28
Have you tried to change the download server?   Note you can use Synaptic to select a new server - - then be sure to reload the package db.

---

### Post by Impavidus on 2018-03-28
The difference between Ubuntu Software and the terminal is here that the terminal is less intuitive to use, but gives finer control and better error messages.

Now that you ran apt-get update succesfully, try```
sudo apt-get dist-upgrade
```That will try to download and install the updates, including packages not previously installed.

Besides, you can copy-paste terminal output into a forum post, enclosed in code tags. That's more convenient than a screenshot.

---

### Post by monkeybrain20122 on 2018-03-29
> **shanasman450 said:**
> I'm showing to have an os update and when I click install a loading bar appears on the install button, gets to about 1/4 then quits and I'm told to check my internet connection. Anyone else have this issue? Also, what is the difference between using the Ubuntu Software application to download/install updates and using sudo apt-get update?


PS. I have made sure I'm connected at the time of installation and I have tried restarting the computer.

Maybe you can change the server in software & update.

Maybe your DNS or firewall settings. I am having the same issue and only intermittently and only to some sites (e.g skype repo) since we changed ISP at home, since I share WIFI with people upstairs and have no access to the router I have no idea what is going on, but 100% sure it is the ISP, when I take my laptop to work or anywhere else and before they changed ISP I never had problems. 

Yes, sudo apt-get gives you fine grain control IF you know all the options and the package names (if you try to install) the Software centre on the other hand doesn't show you a lot of useful information (and nowadays I think installs snap packages if they are available,e.g vlc but snap is experimental and often don't work very well) A happy medium is synaptic package manager, it has a gui, very good search facility, it gives you a lot of fine grain control without you having to memorize a bunch of command line gibberish. You can install it either with the software centre or 

```
sudo apt install synaptic
```

---

