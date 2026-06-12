---
title: "Stopping lxdm crashes my laptop"
date: 2011-12-13
forum: New to Ubuntu
---

### Post by Rogs128 on 2011-12-13
Good morning all
 
I have an old Dell Latitude C800 with ATI Mobility graphics. As it was running badly under Windows XP I decided to give Lubuntu a go and installed the Lubuntu 11.10.
 
However this caused the split/fuzzy screen problem. I found a 'cure' for this in doing
 
sudo service lxdm stop
 
sudo Xorg -configure
 
edit xorg.config and move to /etc/X11
 
sudo service lxdm start
 
Unfortunately I only get as far as trying to stop lxdm. The screen clears and then shows a few lines of text very quickly, clears again and I am left with a flashing _ in the top left corner.
 
From here I can do nothing other than reboot my laptop.
 
I previoulsy had Linux Mint 11 with LXDE running along side Windows XP and this fix worked first go. I was only trying Lubuntu 11.10 as it worked faster off the LiveCD than Mint did off the HDD!
 
So any suggestions as to what might be happening when I stop the service or if there is an alternative method that I can use to set the xorg.conf would be most welcome as I am feeling I have bitten off more than I should have:(

---

### Post by gastly on 2011-12-13
Are you running those commands from a tty or from within lxde (lxterminal)?
If you are running those while running lxde then surely that will cause your desktop to close as lxdm starts your desktop environment and if you stop lxdm it will take your desktop environment down with it. The commands you posted are meant to run from a tty.

Do this, press **Ctrl+Alt+F2**. This will cause you to shift to tty2 and you will be presented with a console where you will be asked to login. From there type the commands and it should all be fine :)

---

### Post by Rogs128 on 2011-12-13
Thanks for the reply....
Sorry I forgot to say I was booting into the normal desktop and then CTRL+ALT+F1 to get to some sort of command line session.
 
I'll give CTRL+ALT+F2 ago when I get home tonight and let you know what happens.

---

### Post by Rogs128 on 2011-12-13
Ok

So I have now tried Ctrl+Alt+F2

Unfortunatley I now get the following:

* Starting AppArmor Profiles      [OK]
* Setting Sensors Limits           [OK]
Checking for running unattended-upgrades:
* Starting NTP Server ntpd        [OK]
* Starting Bluetooth                  [OK]

Below that is a flashing cursor and nothing else happens...... 

Does anyone have any suggestions as to what might be happening or what I can do?  Or should i just give up with Lubuntu and is there another similar distro that might actually work??


Thanks

Roger

---

### Post by Rodney9 on 2011-12-13
This may help - 

[http://ubuntuforums.org/showpost.php?p=11398602&postcount=35](http://ubuntuforums.org/showpost.php?p=11398602&postcount=35)


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by Rogs128 on 2011-12-14
Thanks for all the help
 
I have now got Lubuntu working well.
 
To do this I used Ctrl+ALt+F1 to go to tty an used the sudo service lxdm stop this seemed to crash the system
 
Out of interest I then did Ctrl+Alt+F2.  I was then put into tty2 in which I was able to create xorg.conf, edit it and move it to /etc/X11
 
A quick reboot and there is Lubuntu in all it's glory :P
 
My laptop is rejuvenated and I am a happy bunny again
 
Not sure why this worked, but very glad it did!

---

### Post by amjjawad on 2011-12-14
First of all, Hello and Welcome to Ubuntu Forum :)

Second of all, thank you for choosing and using Lubuntu. You did the right choice, no doubt about it.

As for your issue, I'm afraid it's a bit beyond my experience because I haven't faced any issue similar to yours. Usually, I build my experience either by testing new stuff or trying to break things or some other time dig to find some problems/bugs :)
I like to jump where my experience fits more. However, I'll do my best to help.

I see you managed to fix the issue and I also see you are not sure what happened and why it's working now? :)

My guess is, it's a graphics issue.

There are couple of questions that will make everything clear. If you don't mind, have a look at my signature and check "How to write an informative and detailed thread".

There are some questions that I'd like to ask you so we could help each other and help everyone that might run into the same :)

If you are not willing to go through this, I totally understand :)

Thank you!

By the way, as my friend Rodney pointed out, please check Lubuntu One Stop Thread (on my signature too). It has many useful information, general information that might be useful for you :)

---

### Post by Rogs128 on 2011-12-15
Thanks for the reply and offer of further help.
 
When I get home I will try some of the commands from your thread and post up the details (hardware spec etc)
 
I think you are right that it is graphics issue as the ATI mobility GPU does seem to cause problems as I've found from abit of web research.
 
My next step was going to be to try and install a different graphics driver, but as I have a working laptop maybe I should be just happy with that :D
 
Roger

---

### Post by amjjawad on 2011-12-15
> **Rogs128 said:**
> Thanks for the reply and offer of further help.
You are most welcome, Roger :) we are all here to help you and also to learn in the process, this is why Lubuntu One Stop Group has been created and that's why me and Rodney are members in that group :)

 
> When I get home I will try some of the commands from your thread and post up the details (hardware spec etc)
Take your time, we are here :)
 
> I think you are right that it is graphics issue as the ATI mobility GPU does seem to cause problems as I've found from abit of web research.
Yes, I've seen some issues with ATI.

---

