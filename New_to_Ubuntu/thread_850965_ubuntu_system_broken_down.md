---
title: "ubuntu system broken down"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by lyni on 2008-07-06
I downloaded a package thru the synaptic manager. once it finished it advised me to restart the computer, which I did. after that I have not been able to get past the desktop. I have turned the computer on and off several times. sometimes the top and bottom panels appear and sometimes they don't. sometimes the Applications etc titles come up sometimes they don't. sometimes firefox webbrowser and email icon come up sometimes they don't. when they do come up if I click on them the whole desktop freezes up. and I turn the computer off and start again. how can I get past the desktop and use my computer? will I have to reinstall ubuntu? and if so how do I do that?
thank you for any advice.

---

### Post by sayakb on 2008-07-06
Can you login to the failsafe session?
At the login prompt (gdm), press F10 and click **Select session** and click **Failsafe Gnome**.
Click **Just for this session** when prompted to.
If it logs in, create a new user from System->Administration->Users and groups and see if you can log into the new account.

---

### Post by lyni on 2008-07-06
thank you for your reply. I tried your suggestion but it did not work. after clicking on Failsafe GNOME it did not give me the option of going to 'just this session'. a box came up which said 'This is the Failsafe GNOME session. you will be logged into the 'Default' session of GNOME without the startup scripts being run. This should be used to fix problems in your installation'.

when I got to the desktop I tried clicking on 'system' but the desktop was frozen I couldn't click on anything.
any more suggestions appreciated.
lyni

---

### Post by BGFG on 2008-07-07
Hi I recently had a somewhat similar problem, but in my case i dad un-installed something important. 
When you restart your machine, at the login prompt select options, and ensure that you have the GNOME session as your default. (this worked for me, i had somehow switched my default login session to X i think)

I not that then if you remember the package you installed, you could use the failsafe session and the command

```
sudo apt-get remove 

```

to remove it and hopefully regain system functionality.

Good Luck.

---

### Post by lyni on 2008-07-07
I just tried your suggestion BGFG several times. unfortunately it didn't work. I got to the desktop and was able to click on Applications>Accessories>Terminal. after that the desktop freezes up again.
is there anything else I can try?

---

### Post by sirgogo on 2008-07-07
I suggest you boot, then hit Control+Alt+F1. Then go:
```
sudo touch /forcefsck
```

Let your compy reboot, then tell me what results you get. I suspect hard disk problems. Perhaps there is also a permissions breach. That happened to me a couple times when I was being smart with linux-- the only solution would then be to reinstall. So just try the fsck first.

---

### Post by lyni on 2008-07-07
sirgogo,thank you for your suggestion. I just tried it but unfortunately it still hasn't worked. it gave me a lot of info about the programs being free software and Ubuntu giving no warranty and to access official documentation go to help.ubuntu.com.
it just kept going -desktop $. each time I put in sudo touch /forcefsck it just kept going back to desktop $.
is there anything else I could try to get past the desktop?

---

### Post by hyper_ch on 2008-07-07
what package did you install?

---

### Post by Sef on 2008-07-07
What version of Ubuntu are you running?

---

### Post by lyni on 2008-07-07
I have ubuntu 8.04. the package I installed was ubuntustudio from the synaptic manager.

---

### Post by lyni on 2008-07-07
I still do not have a solution to the above problem. does anyone have any other suggestions please?

---

### Post by boblemur on 2008-07-07
do u keep your /home and ur / separate?? or are they on the same partition?

because you should try keep them separate if possible, incase you do things like what you did... and their is no easy solution...

you should write urself a script that installs all ur programs that u use...

and id say just reformat if you have them separate because /home keeps all ur settings anyways

---

### Post by lyni on 2008-07-07
no I don't have a separate partition. so how do I get past the desktop to get in to anything? or do I just have to somehow uninstall ubuntu and reinstall? and just lose what I have?

---

### Post by boblemur on 2008-07-07
no in grub you can select the second option, and that will take you to a root console...

and you can run terminal commands from their.

also are you using compiz? or metacity? if ur using compiz, try dropping back to metacity

you could try reinstalling gnome desktop... but im not sure if that would work... but if you are dual booting, you can mount ur ntfs partition in the recovery terminal and then copy all the files u need across

---

### Post by boblemur on 2008-07-07
also you should go into grub on your normal boot entry and press e ( to edit) then delete the last entry the quiet one... and also edit the long one and remove slash and quiet from the end of it

dont worry these changes are only tmp so once you finish press b and it will boot

that will show all the boot log to you....

and you may see something fail to load... although it can go past very quickly

---

### Post by lyni on 2008-07-07
no I don't have compiz or metacity. can you explain what you said about grub please. I am totally new to all this and I need step by step instructions because I do not understand all these terms. I downloaded ubuntu 8.04 2 weeks ago and I am trying to get my head around all this new terminology.

---

### Post by hyper_ch on 2008-07-07
I would uninstall ubuntu studio and also uninstall ubuntu-desktop (have a look at [http://www.psychocats.net](http://www.psychocats.net) at the "pure" entries, there you'll find all packages belonging to ubuntu-desktop) and then I would reinstall the ubuntu-desktop.

---

### Post by boblemur on 2008-07-07
lol ok, sorry about that...

grub is ur boot loader and you have like the normal ubuntu the default one then the recovery one under it...

if you select recovery it will take you to a root terminal... just a black screen and the prompt...which you can use if you destroy you desktop or your graphics ( like uv done)

metacity and compiz are both window managers, metacity is what you will be using if you dont know which you are using...

compiz does all the cool looking effects that you might see on youtube or what have u...

do you have a windows parition installed... because if you do it will make backing up a lot easier...

also im not sure what you have done... but you could read up about the ubuntu studio package and see what things it installs when you select it...

do you rember the EXACT package name? because when i look in synaptic there is like 20 ubuntustudio things in there....

it may be something that got replaces ( some graphics thing ) because when you install things, sometimes others need to be installed first... and sometimes things need to be removed and replaced

something that works may have been replaced with something that wont work on your hardware...so as much detail as to the steps u did when you broke it... would be alot of help...

---

### Post by sayakb on 2008-07-07
Press Ctrl+Alt+F1 at gdm (login prompt)
Type in at the terminal:
```
sudo apt-get remove ubuntustudio-desktop
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by BGFG on 2008-07-07
Hey Lyni, check these two threads. They also had ubuntustudio problems. But i believe you may have to use the failsafe session to execute.

[http://ubuntuforums.org/showthread.php?t=468549](http://ubuntuforums.org/showthread.php?t=468549)

[http://ubuntuforums.org/showthread.php?t=782467](http://ubuntuforums.org/showthread.php?t=782467)

The post above also seems like the best course.

---

