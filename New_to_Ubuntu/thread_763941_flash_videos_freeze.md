---
title: "flash videos freeze"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by Doormat on 2008-04-23
I have an issue when playing flash videos (youtube for example). Every 2 seconds to video freezes and I have to manually seek to another point and it plays for another 2 seconds. So essentially the videos are unplayable. Is there a good way to fix this? Running 8.04 64 bit

2nd question: Will the non-beta version update through the updater or do I need to reinstall ubuntu when 8.04 full is released?

---

### Post by riven0 on 2008-04-23
You may want to re-install flash manually. It could be there was problem with the installation. So, [go here and download the flashplayer in tar.gz format]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BUIGP") to your Desktop. Now, open the terminal and copy and paste these commands one by one:
[B]
rm -r ~/.mozilla/plugins/libflashplayer.so[/B]

**cd ~/Desktop**
[B]
tar zxvf install_flash_player_9_linux.tar.gz[/B]

**cd install_flash_player_9_linux**

**./flashplayer-installer**

And follow the directions from there. 

As for your second question, you'll be able to upgrade fine without a re-install. In fact, there is supposed to be some flash fix in the repository, so you may want to upgrade before re-installing flash and see if that fixes the problem.

---

### Post by Doormat on 2008-04-23
couldn't find directory on first command and:

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

on the final command

---

### Post by riven0 on 2008-04-23
Oh, I see you're using the 64bit. Alright, then, I'm not very knowledgable about this, but have a look at the end of this page, where it says *Using nspluginwrapper for flash*. That's supposed to be the fix if you're using the 64bit Firefox. 


[AMD64/FirefoxAndPlugins]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?action=show&redirect=FirefoxAMD64FlashJava")

---

### Post by sojusnik on 2008-04-28
Same problem of freezing here...

---

