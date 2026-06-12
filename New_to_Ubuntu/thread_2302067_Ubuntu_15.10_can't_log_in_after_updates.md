---
title: "Ubuntu 15.10 can't log in after updates"
date: 2015-11-07
forum: New to Ubuntu
---

### Post by Wawrzyn on 2015-11-07
Hey. Im new to Ubuntu. I got a prompt that some software updates are available so i installed them, and then restarted the computer like i was asked.
The problem is that i can't log in anymore. As soon as i type in my password, i get a black screen for a split second with these lines:
```

fsck from util-linux 2.26.2
/dev/sdb5: clean, 338599/2681728 files, 3928098/10727936 blocks

```
And then i return to login screen. Yes im typing correct password. 
I've looked around on internet and i tried doing some of the things that experts recommend:
CTRL + ALT + F1, then login. Then all of the solutions require apt-get commands, but another problem is that i have no internet anymore for some reason.
So i tried reconnecting to my wifi in the command line:
```

nmcli c up id my_network_name

```
But i got a message saying that there is no suitable device to do that with.
I really don't know what to do at this point. Does anyone know what i can do to fix this? I will happily provide more info if i can access it from command line and without internet which i dont have.

---

### Post by CitadelUniversal on 2015-11-07
Could you bring up the history of what was installed? Its located at /var/log/apt/history.log - also are you aware of dpkg-reconfigure command line tool it should reconfigure any bad updates or if you've rebooted while updating it should finish the updates off....

---

### Post by Wawrzyn on 2015-11-07
Thank you for your answer. I tried using the dpkg-reconfigure tool but i dont know the name for the update to use it. I also looked for the update log and this is the complete update log from the update that broke everything. I hope a picutre is ok, its a lot to retype: [http://i.imgur.com/4mZ6xZX.jpg](http://i.imgur.com/4mZ6xZX.jpg)

---

### Post by ajgreeny on 2015-11-07
Try ```
sudo dpkg --configure -a
```

---

### Post by Geoffrey_Arndt on 2015-11-07
Based on your prior thread, can you elaborate how your upgraded from 15.04 to 15.10?    Was it a full reinstall from media, or an online upgrade via Software Updater?   Just trying to get a sense for why your system is so screwed up after running it for so short a time.

---

### Post by Wawrzyn on 2015-11-07
I get dpkg: error: unknown option --reconfigure.

EDIT: And i didnt updtate from 15.04, i downloaded clean 15.10 image and installed that instead

EDIT 2: One dangerous thing i did is that after i installed it, i expanded the partition afterwards effectively moving the beginning of the partition. I read that this could mess up the bootloader if i move the beginning too far, but everything worked fine after the expansion. I dont know if this could have anything to do with this problem. Otherwise i dont know anything else i could have done to cause this.

---

### Post by ajgreeny on 2015-11-07
> **Wawrzyn said:**
> I get dpkg: error: unknown option --reconfigure.

EDIT: And i didnt updtate from 15.04, i downloaded clean 15.10 image and installed that instead

EDIT 2: One dangerous thing i did is that after i installed it, i expanded the partition afterwards effectively moving the beginning of the partition. I read that this could mess up the bootloader if i move the beginning too far, but everything worked fine after the expansion. I dont know if this could have anything to do with this problem. Otherwise i dont know anything else i could have done to cause this.
Sorry, that's a typo.  It should be either ```
sudo dpkg --configure -a
``` or
```
sudo dpkg-reconfigure -a
```I mixed up spaces and dashes needed.

---

### Post by Wawrzyn on 2015-11-07
Second one doesn't work and the first one does nothing. Does you have some idea what might be wrong so i can do some serching myself?

---

### Post by Akul_Penugonda on 2015-11-08
Hey, have you tried starting an x server in tty1? Like do ctrl-alt-f1 on startup, then type "startx", then right click, choose "Open terminal", then type "unity" (or whatever desktop environment you want). Then you have a gui again, which might make it easier to troubleshoot the wifi issue/whatever else is going on.

---

### Post by Wawrzyn on 2015-11-08
I searched the internet back and forth, tried everything with no avail. Fortunately all i had there is a bunch of code backed on git. So i formatted everything and reinstalled ubuntu. One thing for sure, im never installing updates again.

Im going to be honest, i switched to ubuntu beacuse i wanted to have a clean system where i can code in peace but the last couple days have been nothing but solving problems that just keep coming up. I dont know if its me messing up or what, but so far i followed trusted tutorials and stuff keeps going south. I really want to make this work, but there is only so many times im going to reinstall everything.

Neverthelesd thank you very much for trying tl help, I really appreciate it.

---

