---
title: "Terminal appears instead of ubuntu desktop at boot up"
date: 2013-07-02
forum: New to Ubuntu
---

### Post by michaelas on 2013-07-02
I made a mistake the other day when I was trying to install a codec for Rythmbox, which it turns out I didn't need to do. But I went to the forum page at the address listed below, and followed the sudo command to install the **restricted extras pack**, using the terminal screen, which I guess should not have done. Now every time I boot up, I get the terminal instead of the normal ubuntu desktop. It requires a login and password, and then awaits a command. 
When this happens I have been able to **ctrl-alt-delete** to reboot, and sometimes I get the old desktop back, but not always.

So:

How to I get to the desktop from the terminal? or

How do I remove the installed restricted extras package? or

How do I get my computer to boot to the desktop as before instead of the terminal?


I hope this is clear. I'm in unfamiliar territory here.

Here is the forum page I was on.
[http://ubuntuforums.org/showthread.php?t=1326307](http://ubuntuforums.org/showthread.php?t=1326307)

Re: Rhythmbox and missing Windows Media Audio Codec

install the ubuntu restricted extras pack.

this is the command I used:
*sudo apt-get install ubuntu-restricted-extras*

It took a long time, and I received no verification that it was finished so I interrupted the process after a half hour and shut down the computer. After that, then the problems started. Any suggestions?   :confused:

---

### Post by ryan516 on 2013-07-02
Don't ever interupt a file like that! It will tell you when it's done when it says User@ComputerName. As for your issues, I'd go into the DE(Desktop Enviornmen) and transfer all your files you need backed up into Ubuntu One or something, then reinstall Ubuntu. That's what I'd reccomend.

---

### Post by deadflowr on 2013-07-02
You can try fixing any broken packages
```
sudo apt-get -f install
```

You can also try restarting the xserver
```
sudo service lightdm restart
```

See if either of those help get to the desktop.

---

### Post by michaelas on 2013-07-02
Thanks. I tried the code 

sudo service lightdm restart

and it did get me back to the desktop. Yay. But upon reflection, I think I'll make a fresh start and reinstall.
It's the only way to be sure.
Thanks for the help. A Lesson learned! ;)

---

### Post by Zill on 2013-07-02
> **michaelas said:**
> ...It took a long time, and I received no verification that it was finished so I interrupted the process after a half hour and shut down the computer. After that, then the problems started...
It really isn't a good idea to interrupt a software installation process.  This can leave packages in an "unknown" state and so it is then necessary to fix the broken packages as advised.

As I recall, [ubuntu-restricted-extras]("http://packages.ubuntu.com/lucid/ubuntu-restricted-extras") includes some packages that have restrictive license agreements and it is therefore necessary to specifically agree to these EULAs before all the packages can be installed.  Unless things have changed with later versions, after starting to install ubuntu-restricted-extras, a terminal window will automatically open up showing the [EULA]("http://askubuntu.com/questions/16225/how-can-i-accept-microsoft-eula-agreement-for-ttf-mscorefonts-installer").  You then need to move the cursor with the "tab" key to the "OK" at the end of the agreement and hit "space" or "Enter".  Installation should then proceed and complete normally.

---

### Post by Valiid on 2013-07-02
> **deadflowr said:**
> You can try fixing any broken packages
```
sudo apt-get -f install
```

You can also try restarting the xserver
```
sudo service lightdm restart
```

See if either of those help get to the desktop.
I have the same problem this guy is having... sort of. I can get to this text Ubuntu using the recovery mode startup, but cannot get the desktop. I have tried these codes. Is there anything else you think can help me? (My post [here]("http://ubuntuforums.org/showthread.php?t=2159144"))

---

### Post by deadflowr on 2013-07-02
> **Valiid said:**
> I have the same problem this guy is having... sort of. I can get to this text Ubuntu using the recovery mode startup, but cannot get the desktop. I have tried these codes. Is there anything else you think can help me? (My post [here]("http://ubuntuforums.org/showthread.php?t=2159144"))

I posted a link to psychocats tutorial on getting back to pure kubuntu on the thread you have.
Hopefully it might help.
Don't know for sure though.
Good luck.

---

