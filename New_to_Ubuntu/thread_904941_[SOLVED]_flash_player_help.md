---
title: "[SOLVED] flash player help"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by Thr33finger on 2008-08-29
So i think it's the flash player which I have an issue with. But what is happening is basically every site i go to the banner's and other graphics have a grey play button on them and won't play or activate until i click on them. I'm pretty sure it's the flash player I chose or something along those lines(lol and of course sorry I cannot remember which one i chose, all i remember is my choices I believe were gnash, adobe and something else), but have searched around and cannot find out a way to uninstall the one I chose or change the settings or something like that. Can anyone help me?

---

### Post by SunnyRabbiera on 2008-08-29
well what do you have installed right now?
If you need normal flash we can help you get it.

---

### Post by ad_267 on 2008-08-29
That sounds like it could be the flashblock plugin for firefox. Go to Tools - Add-ons - Extensions and disable flashblock if it's there.

---

### Post by Thr33finger on 2008-08-31
Ok, as in firefox I do not have flash block in there. also according to firefox I have shockwave installed. basically i'm hoping it is shockwave which is causing my issue. So how do i go about uninstalling shockwave and installing something else?


Thanks in advance

---

### Post by jemate18 on 2008-08-31
> **Thr33finger said:**
> So i think it's the flash player which I have an issue with. But what is happening is basically every site i go to the banner's and other graphics have a grey play button on them and won't play or activate until i click on them. I'm pretty sure it's the flash player I chose or something along those lines(lol and of course sorry I cannot remember which one i chose, all i remember is my choices I believe were gnash, adobe and something else), but have searched around and cannot find out a way to uninstall the one I chose or change the settings or something like that. Can anyone help me?

Hi. this is what to do to install flash player
These are the steps on how to install adobe flash player 9.
1. Applications -> Accessories -> Terminal
2. Assuming you have downloaded your adobe flash player from the adobe website [the tgz verions ]on your desktop which is
```
/home/[name]/Desktop/install_flash_player_9_linux.tar.gz
```

type this on your terminal
```
cd ~/Desktop
```
then
```
tar -xf install_flash_player_9_linux.tar.gz
```

3. A new directory named install_flash_player_9_linux will be created that is
```
/home/[name]/Desktop/install_flash_player_9_linux
```

4. type
```
cd ~/Desktop/install_flash_player_9_linux
```

5. type
```
./flashplayer-installer
```

6. Then you will be prompted about the installation
7. Close any browser
8. Press Y for the question asked about the "proceed with the installation" question.
9.restart firefox, or just open it.
10. ENJOY

I hope this help. Make sure to mark this thread SOLVED if you have been able to do what you want and dont forget to THANK the people who helped you.

I hope this helps

jemate18

---

### Post by jemate18 on 2008-08-31
> **Thr33finger said:**
> So i think it's the flash player which I have an issue with. But what is happening is basically every site i go to the banner's and other graphics have a grey play button on them and won't play or activate until i click on them. I'm pretty sure it's the flash player I chose or something along those lines(lol and of course sorry I cannot remember which one i chose, all i remember is my choices I believe were gnash, adobe and something else), but have searched around and cannot find out a way to uninstall the one I chose or change the settings or something like that. Can anyone help me?

Did you try the solution I have posted above?

Mark this thread SOLVED "https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are able to do what you intend to do and DONT FORGET to THANK the people who HELPED YOU by clicking the "thanks" button

Hope this helps.

jemate18

---

### Post by joshsmith on 2008-08-31
it is bad advice to leave the repo managed version of flash, to switch to the custom downloaded one

the problem the original poster is suffering from is that they didnt install adobe flash, but rather the swfdec package

the solution:
go into synaptic package manager and remove swfdec-gnome swfdec-mozilla pacakges

then go onto youtube, when prompted click to add the missing plugins, and this time choose the adobe flash plugin

(if you have problems with sound at any point, also install the package libflashsupport)

---

### Post by gjoellee on 2008-08-31
> **jemate18 said:**
> Hi. this is what to do to install flash player
These are the steps on how to install adobe flash player 9.
1. Applications -> Accessories -> Terminal
2. Assuming you have downloaded your adobe flash player from the adobe website [the tgz verions ]on your desktop which is
```
/home/[name]/Desktop/install_flash_player_9_linux.tar.gz
```type this on your terminal
```
cd ~/Desktop
```then
```
tar -xf install_flash_player_9_linux.tar.gz
```3. A new directory named install_flash_player_9_linux will be created that is
```
/home/[name]/Desktop/install_flash_player_9_linux
```4. type
```
cd ~/Desktop/install_flash_player_9_linux
```5. type
```
./flashplayer-installer
```6. Then you will be prompted about the installation
7. Close any browser
8. Press Y for the question asked about the "proceed with the installation" question.
9.restart firefox, or just open it.
10. ENJOY

I hope this help. Make sure to mark this thread SOLVED if you have been able to do what you want and dont forget to THANK the people who helped you.

I hope this helps

jemate18

let me make that easier for you :) Download the .deb file form my website, here is the direct link to download
[http://www.kshoster.net/downloadfiles/flashplugin.deb](http://www.kshoster.net/downloadfiles/flashplugin.deb)

---

### Post by jemate18 on 2008-08-31
> **gjoellee said:**
> let me make that easier for you :) Download the .deb file form my website, here is the direct link to download
[http://www.kshoster.net/downloadfiles/flashplugin.deb](http://www.kshoster.net/downloadfiles/flashplugin.deb)

deb files make life easier than tar balls do. But if you get to know both ways, then you'll gain a lot because not all software or applications have .deb equivalent, sometimes you have to deal with .tgz downloads

If you have opt to download the .deb file from
```
http://www.kshoster.net/downloadfiles/flashplugin.deb
```

Please do these steps. Assuming you have downloaded it in your desktop
1. Application -> Accessories -> Terminal
2. You should be root
```
sudo su [password]
```
3. type
```
cd ~/Desktop
```
4. type```
dpkg --install flashplugin.deb
```
or
```
dpkg -i flashplugin.deb
```
5. Enjoy

Mark this thread SOLVED "https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are able to do what you intend to do and DONT FORGET to THANK the people who HELPED YOU by clicking the "thanks" button on the lower right "medal icon" for their help and useful post

jemate18

---

### Post by aysiu on 2008-08-31
> **joshsmith said:**
> it is bad advice to leave the repo managed version of flash, to switch to the custom downloaded one

the problem the original poster is suffering from is that they didnt install adobe flash, but rather the swfdec package

the solution:
go into synaptic package manager and remove swfdec-gnome swfdec-mozilla pacakges

then go onto youtube, when prompted click to add the missing plugins, and this time choose the adobe flash plugin

(if you have problems with sound at any point, also install the package libflashsupport) I second this advice.

There's no point in asking the OP to install Flash if another plugin is conflicting with it.

Let's see if SWFdec or Gnash is installed first.

---

### Post by silkstone on 2008-08-31
I see no advantage in installing Flash Player 9 manually instead of simply using Synaptic to install flashplugin-nonfree from the repos. That way you will get updates automatically.

The most reliable version of Flash Player seems to be Flash 10 beta 1, but I'm not sure where you can download that from now. The latest version (Flash 10 rc) runs into problems because of a bug in xulrunner which causes Firefox to segfault. If you can find the beta 1 version of Flash 10, follow the method under 'Troubleshooting - Adobe Flash Player' towards the end of this post...

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Thr33finger on 2008-09-01
Hey,
Thanks for all your suggestions and help. Joshsmith thanks. i forgot what it was I loaded first. The swfdec-mozilla. i already had abode installed just never uninstalled swf through synaptic. It is working now. though. Again thanks for the help.

---

