---
title: "Jumped right in....complete noob"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by Lars75 on 2012-01-11
Ok, so I have Windows on three laptops at my house, and the kids have 2 MBPs from school.  The laptops belonging to the wife and kids are virus magnets.  I have been hearing about Linux and decided last night to make the leap.  I installed Ubuntu 11.10.  now I have problems.

1.  I installed Openoffice 3.3, but cannot figure out how to get it going.  I am a college student and use Word a lot.  I am also an Excel junkie.  

2.  My mouse jumps when I hover over a close button or try to copy and paste something.  

3.  Finally, now that I got Linux, what am I supposed to do with it?  Are there guides written for this?

I have spent several hours reading forums and posts to solve these problems.  I have been working on Windows since 1994.  I have torn a few apart and replaced parts as needed.  i have also built a few basic web pages in html.  So I am not a complete computer idiot.  I just do not know where to go from here.  I know you guys get a lot of questions, but I would really appreciate it if someone could point me in the right direction. i have been wanting to make the jump to Linux for a while, but felt a bit intimidated.  

Thank you!

---

### Post by Lars75 on 2012-01-11
2.  I fixed the mouse.  It was a surface issue.

---

### Post by mjitkop on 2012-01-11
Welcome, Lars75.

1. To start OpenOffice, move your mouse all the way to the left of the screen and click on the Ubuntu logo at the top of the launcher. In the search box, start typing "open office" and you should be able to click on it when it appears. Once the application is open, right click on its icon in the launcher (left of the screen) and select "Keep in launcher". The next time you want to start the application again, simply click on its icon in the launcher (bar on the left of the screen).

2. Sorry, I don't know about your mouse issue.

3. As a starting point, I would suggest this link:
[https://help.ubuntu.com/11.10/ubuntu-help/index.html](https://help.ubuntu.com/11.10/ubuntu-help/index.html)

Good luck. :D

----

Glad to see you figured out your mouse issue. :)

---

### Post by kaldor on 2012-01-11
Welcome to Linux :-) 

First, the default LibreOffice suite is largely the same as OpenOffice.org. LibreOffice also has some improved MS Office compatibility- I'd ignore OO.o.

For your last question, that largely depends on what you want to do. Any examples?

---

### Post by Lars75 on 2012-01-11
mjitkop...Ty for the link it looks helpful.  

Kalador, I want to create an environment on it that my wife and 3 kids can use and keep it pretty idiot proof for them.  When they mess something up on Windows I usually know how to fix it.  do I have to working about them breaking Linux?  They play mostly Facebook games, surf the web, and listen to music (the usual stuff).   I do a lot of papers.  I am also looking to type in Ancient (Attic) Greek, with a polytonic keyboard.

---

### Post by IWantFroyo on 2012-01-11
> **Lars75 said:**
> mjitkop...Ty for the link it looks helpful.  

Kalador, I want to create an environment on it that my wife and 3 kids can use and keep it pretty idiot proof for them.  When they mess something up on Windows I usually know how to fix it.  do I have to working about them breaking Linux?  They play mostly Facebook games, surf the web, and listen to music (the usual stuff).   I do a lot of papers.  I am also looking to type in Ancient (Attic) Greek, with a polytonic keyboard.

Open the "Keyboard" settings app, go to the Layouts tab, and then you can add keyboard layouts. If it isn't installed, search the Ubuntu Software Center for it.

If you really need to, you can use ibus as well. This will allow you to use input methods that are not supported with normal keyboards (like Japanese and Chinese, although I don't think you need this for Greek).

As for them breaking Linux, don't worry about it. Just don't tell them the root (system) password (so they'll come to you if they need help - the most common way to break a Linux installation is when you follow faulty directions), and use common sense.
Also, Linux is thankfully immune to Facebook game viruses in general. You may need to install ubuntu-restricted-extras for MS fonts, Java, and Flash, though before everything works.

---

### Post by kaldor on 2012-01-11
> **Lars75 said:**
> Kalador, I want to create an environment on it that my wife and 3 kids can use and keep it pretty idiot proof for them.  When they mess something up on Windows I usually know how to fix it.  do I have to working about them breaking Linux?  They play mostly Facebook games, surf the web, and listen to music (the usual stuff).   I do a lot of papers.  I am also looking to type in Ancient (Attic) Greek, with a polytonic keyboard.

The best idea for that would be to create separate accounts for your wife and kids, while leaving yourself as the administrator (super user). You can restrict them from doing system-affecting tasks (such as installing software) etc. This will prevent them from altering other users' files as well. If you want more help regarding this, then feel free to ask. 

Make sure you have a lot of the essentials ready to go so that they have no reason to tinker with stuff. You should install the *ubuntu-resticted-extras* package, which contains Flash, Java, and other multimedia codecs which might be desired by your family. I'd also greatly recommend installing VLC media player and using that instead of the default- I have much better luck with it. Remember, all of this can be found in the Ubuntu Software Centre.

Regarding the Greek keyboard layout, you can choose to add the Greek layout in the keyboard settings. Open the System Settings application by clicking the gear icon on the top right of the desktop, and navigate to Keyboard. In the layout tab you should be able to add the Greek Polytonic layout (see screenshot attachment). Note that I'm using an older version of Ubuntu, so the process to this might be slightly different.

Have fun :)

Edit: Above poster seems to have beat me to it :)

---

### Post by jmate24 on 2012-01-11
> **Lars75 said:**
> Ok, so I have Windows on three laptops at my house, and the kids have 2 MBPs from school.  The laptops belonging to the wife and kids are virus magnets.  I have been hearing about Linux and decided last night to make the leap.  I installed Ubuntu 11.10.  now I have problems.

1.  I installed Openoffice 3.3, but cannot figure out how to get it going.  I am a college student and use Word a lot.  I am also an Excel junkie.  

2.  My mouse jumps when I hover over a close button or try to copy and paste something.  

3.  Finally, now that I got Linux, what am I supposed to do with it?  Are there guides written for this?

I have spent several hours reading forums and posts to solve these problems.  I have been working on Windows since 1994.  I have torn a few apart and replaced parts as needed.  i have also built a few basic web pages in html.  So I am not a complete computer idiot.  I just do not know where to go from here.  I know you guys get a lot of questions, but I would really appreciate it if someone could point me in the right direction. i have been wanting to make the jump to Linux for a while, but felt a bit intimidated.  

Thank you!

Open Office is not supported in Ubuntu 11.10 however Libre Office will install if you install the Open Office packages from Synaptic or the Software center.

p.s. 

I use Lubuntu and I like Abiword better than Libre Office.
I also use my computer as a media center and Network File Server and Samba Server.

---

### Post by grahammechanical on 2012-01-11
Have you found the Ubuntu Desktop Guide? Here is a link:

[https://help.ubuntu.com/11.04/ubuntu-help/index.html]("https://help.ubuntu.com/11.04/ubuntu-help/index.html")

It is installed on your system. You find it by opening the Dash (click the Ubuntu icon at the top of the Launcher on the left) and typing help.

As for getting Greek, go to System Settings under the power cog icon (top right) and open Keyboard Layout. Click the plus ( + ) button and choose Greek (polytonic) and click Add. You will get a keyboard icon in the top panel from which you can select between English and Greek. The Options button will let you set a keyboard short cut for switching between keyboard layouts.

Regards.

---

### Post by Lars75 on 2012-01-12
wow, Ty for all the help.  I got the Greek Polytonic keyboard to work with accent marks in Libreoffice.  That was thanks to the help page posted.  This took me eight hours to do in MS Word.  

I am going to set my self up as Admin on my families other laptops.

Google and forums are helping me with a lot of my problems.  

I have managed to make my number pad move my pointer instead of type numbers (like I like it to do).  I have found several fixes for this, but they all seem to include one basic problem.  
They tell me to go to:
"System->Preferences-> Keyboard" then it says that "in the dialogue box".  
When I open "System Settings" I see nothing that says "Preferences".  If I open my "Home" folder and go to "System" there, I see nothing that says "Preferences".  I have tried to do this is both Ubuntu and Gnome (not sure why I have Gnome, but a lot of websites mention it, so I got it).  If I go straight from System Settings to Keyboard, I do not see a dialogue box.

---

### Post by kaldor on 2012-01-12
Starting last April, Ubuntu has been using its own custom UI on top of Gnome. Before that, it looked like [this]("http://upload.wikimedia.org/wikipedia/commons/9/9d/Ubuntu_10.04_screenshot.png"). Note the three categories on the top left- the guides are most likely referencing the old appearance.

Most of these options can now be found under System Setting in the top right menu :-)

---

### Post by Lars75 on 2012-01-12
kk, TY.  This means that every time I search a fix I need to be specific to 11.10 then.

Ok the setting was in universal settings.  I had problems with a jumpy mouse earlier, and one that wouldn't scroll earlier.  I think I got it all under control now.  
I appreciate everyone's help and input.

---

### Post by kaldor on 2012-01-12
> **Lars75 said:**
> Ok the setting was in universal settings.  I had problems with a jumpy mouse earlier, and one that wouldn't scroll earlier.  I think I got it all under control now.  
I appreciate everyone's help and input.

Glad to see we helped :)

---

### Post by Lars75 on 2012-01-13
I am trying to customize my desktop.  I have found several useful pages to help me do this.  Most of them refer to the Gnome Tweak Tool.  When I go to the software page, it says I have it installed.  However, I cannot find it in dash.  I can find the Ubuntu Tweak tool.  Do these conflict like Libreoffice and OOo?  Are you allowed to have both at the same time?



Note:  I am keeping all my post in one thread because I refer back to them in case I forgot something.   Is this acceptable, or are new threads required for each question?

---

### Post by mastablasta on 2012-01-13
it is better to open a new thread for new issue with a propper title. That way person that knows the answer to the topic can pop in and reply. "Jumped right in... complete noob" is a poor description of a problem. More info on this here: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
 
you can follow your threads if you click "search->find all your threads" (menu in forums in upper right corner of forums).
 
customisation in Unity is limited (at the moment). i hope you didn't find some sites for the old interface (which had a lot of customisaiton options). still Ubuntu tweak should be in the menu if it is installed. if you can't find it try to hit alt+f2 and then run it from there.
 
 
By the way don't want to confuse you or anything but did you know that there are other desktop environments availble in Ubuntu (besides the default Gnome with Unity Interface). For example Kubuntu (with the KDE environment that has look & feel of Windows), Xubuntu (with XFCE that is very customizable and has the look of old 2.3 Gnome environment). As a bonus XFCE uses much less system resources than the other two (about 110MB for the OS at idle). The fourth and youngest family member is Lubuntu. It uses LXDE and is really light on system resource. as in 80MB for the OS on idle. But still you can see it is young. however excelent choice for old maschines with low ram. since Unity is very new all others have more customisations options. Unity will be a bit more customizable with the next long term support (LTS) release comming out in April.
 
I am only menitoning these desktop environments (DE) since you are in customisation mode :-)

---

### Post by Lars75 on 2012-01-13
You just mentioned a lot of things there.  Kubuntu, Lubuntu, and Xbuntu.  I have seen these names kicked around a bit. I have a few thoughts/questions.

1.  My laptop is screaming fast.  So not to worried about overtaxing it.

2.  Are these (Kubuntu, Lubuntu, and Xbuntu) different OS from Ubuntu, or would they run in Ubuntu?

If I decided to run one of these would I have to uninstall Ubuntu?  I can already boot to Windows 7 or Ubuntu.  

3.  Which is the easiest for a person with 0% Linux experience to use? I am not familiar with Gnome 2.3 or other older versions.  

4.  I am looking for something stable, secure, easy to use/learn, and customize.  I like to play Facebook Games, I like Libreoffice, and so far I love Linux.  

5.  Am I asking the right questions or are there other factors I need to consider.

---

### Post by nothingspecial on 2012-01-13
Hi Lars75, welcome to the forums :)

> **Lars75 said:**
> 



Note:  I am keeping all my post in one thread because I refer back to them in case I forgot something.   Is this acceptable, or are new threads required for each question?

For each question you have, please start a new thread. You will get better help if you choose a succinct title that describes your issue. Someone who knows the answer is more likely to have a look rather than at a thread titled "New to linux" or similar.

Also someone else searching for the same solution is more likely to find your thread.

gnome-tweak-tool is listed as "Advanced Settings" in the dash btw.

---

### Post by satanselbow on 2012-01-13
> **Lars75 said:**
> 
I am going to set my self up as Admin on my families other laptops.


That is an excellent policy that I implement myself round the house ;) The same can be done on any Windows machines you may have left as well. Pays dividends when one of the kids (read "usually the wife") follows a rogue ad banner :D

If you are feeling really adventurous later you can set them all up to be remotely administrated from the comfort of your own machine ;)

---

