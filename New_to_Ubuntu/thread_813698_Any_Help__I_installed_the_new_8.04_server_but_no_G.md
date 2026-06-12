---
title: "Any Help?  I installed the new 8.04 server but no GUI.."
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Linuxwho? on 2008-05-31
Hi All,

I am a new idiot and just beginning Ubuntu and Linux for that matter.  I read the online docs and tried a search here on GUI first..

I installed 8.04 desktop on my laptop as a trial and a GUI came up and all, pretty cool.  So I used another server of mine and installed the server version successfully but I wanted GUI with the  option of using the prompt as well.  Do I have to install the GUI as some sort of an add-in on the server version?  If so can anyone tell me how?  Thanks in advance experts!! - signed new Linux/ubuntu moron.

---

### Post by sam_delta on 2008-05-31
in simplier terms , i believe that 

ubuntu Desktop = ubuntu server + GUI

for your server you can install a gui by typing with an internet connection
for gnome
```
sudo apt-get install ubuntu-desktop
```if you prefer kde ```
sudo apt-get install kubuntu-desktop
``` or if you prefer Xfce ```
 sudo apt-get install xubuntu-desktop
```

just install 1 of them, the one you prefer (as you already installed ubuntu on your other machine, your most likely be already familiarilzed with gnome which is ubuntu desktop)
sam

---

### Post by ramjet_1953 on 2008-05-31
Webmin is probably a good choice for a GUI server admin package.
It is much lighter than XFCE or the like.

[http://www.webmin.com/](http://www.webmin.com/)

Regards,
Roger :cool:

---

### Post by bobbocanfly on 2008-05-31
Ideally you wouldnt have a GUI on a server but if you do want one I wouldnt recommend downloading one of the *-desktop packages. These come with things like CD burning and Instant Messaging, which i doubt you need on the server. If you want a minimal GUI environment you should look at installing Fluxbox or Openbox. They use up very little RAM but give you all the functionality you should need with a servers GUI.

---

### Post by Linuxwho? on 2008-05-31
You guys are awesome!  Thank you!!:)

---

### Post by avtolle on 2008-05-31
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) is a link to a Wiki article you might find helpful in installing a GUI atop the server.

---

### Post by Linuxwho? on 2008-05-31
Thanks.  VERY helpful.  It is quite amazing after coming from a windoze environment that I can choose from multiple GUI's at any time!

---

### Post by Xiong Chiamiov on 2008-05-31
> **Linuxwho? said:**
> Thanks.  VERY helpful.  It is quite amazing after coming from a windoze environment that I can choose from multiple GUI's at any time!
You can in Windows too, to some extent with things like ShellOn.  I used it to boot bbLean for me, while my mother got plain old Explorer as her shell.

Reiterating what someone else said, don't install the *-desktop packages, but rather the *-core ones.  You don't need all the extra apps that come with those, but just the desktop environment.

---

