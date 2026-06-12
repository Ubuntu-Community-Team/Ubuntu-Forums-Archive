---
title: "Some Questions About Ubuntu (11.10)"
date: 2011-12-17
forum: New to Ubuntu
---

### Post by ExpDisease on 2011-12-17
Hi Guys,

I recently installed ubuntu 11.10 to my notebook and I have some questions. 

- Are there any real,true,working screen brightness applets or something like that

- I need a shortcut for opening activities panel.

---

### Post by lolpenguin on 2011-12-17
> **ExpDisease said:**
> - I need a shortcut for opening activities panel.

Welcome to the Ubuntu community forums.

What is the "activities panel"? Is it the dash (Ubuntu logo button) or "Activities" (GNOME Shell)? Both of these are opened with the Super key, the key with the Windows logo on it.

---

### Post by Basher101 on 2011-12-17
If you ask for any screen brightness applets, i assume you are using a laptop. My next assumption would be that your Brightness arrow keys (FN + UP or FN + DOWN) do not work. If that is the case i know how to fix it with editing just two files.

edit: found my old post with the fix. I will just paste it here > type in a terminal: ```
sudo gedit /etc/rc.local
``` and there you will see at the very most bottom a red colored [COLOR="Red"]EXIT[/COLOR]. Just above that "exit" type the command ```
setpci -s 00:02.0 F4.B=00
``` and save the settings. Next file you will have to edit is your Grub config file. Type into a terminal ```
sudo gedit /etc/default/grub
``` there you will see different settings. Now look for the line that looks like this: [QUOTE]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and add "acpi_osi=Linux" at the end so that the line looks like this after editing:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="Green"]acpi_osi=Linux[/COLOR]"

this should fix your problem. the only thing that got BROKEN is the indicator app that shows you that "bar" of the brighntess and that it is reversed (UP arrow increses brightness and DOWN decreses the brightness). But this is a price i gladly pay to change the brightness. 

If you do not want to make those "permanent" changes, you can also just adjust it by command with ```
sudo setpci -s 00:02.0 F4.B=[COLOR="Red"]XX[/COLOR]
``` where in XX you replace it with HEX code (reaching from 00 = 0 ([COLOR="DarkOrange"]brightest[/COLOR]) to FF = 255 ([COLOR="Navy"]darkest[/COLOR]))



regards.



p.s. you may have to update your grub with```
sudo update-grub
``` for the changes to take effect[/QUOTE]

---

### Post by ExpDisease on 2011-12-17
@lolpenguin

Yes I'm using gnome3. Thanks for that.

@Basher101

Thank you for your help.I'm trying that now. 

In the command it says:

xperimental@experimental-RV420-RV520-RV720-E3530-S3530:~$ sudo setpci -s 00:02.0 F4.B=FF
[sudo] password for experimental: 
setpci: Warning: No devices selected for "F4.B=FF".

---

### Post by xile101 on 2011-12-18
Hey all im new here! i signed up just after i googled this subject and found Basher101's easy to follow instructions.

I would also like to ask for some help with the brightness setting. 

im using a laptop asus UL30A2 and the Fn+brightness up/down work but if i press the brightness down (only does this with down) too many times (past the lowest on the bar that is displayed) it seems to lock up and it wont let me adjust it anymore but after a few mins it all of a sudden changes.  

also another weird thing is in windows, the brightness can go really low and i always used to keep it on the lowest because having it too bright strains my eyes and also i want it to save some battery life. 

also yet another weird thing is that when i press the brightness all the way up, it the bar only shows half way and it wont go up anymore.

i tried this command in the terminal and it works but only for a few seconds then it reverts back to the brightness setting it was on because i entered the command.
> sudo setpci -s 00:02.0 F4.B=01

also I have done everything that Basher101 wrote and nothing went wrong but nothing has changed :(.

I was originally hoping to find a brightness applet when i searched for this because that is what i used in the previous linux distros i used before ubuntu 11.10 but i guess they completely removed applets :(.

any help with these problems would be very much appreciated.

---

### Post by lolpenguin on 2011-12-19
If you need support please post **in a new thread** instead of adding to current threads. They become clogged.
Yes, I know I sound like a moderator...

---

### Post by xile101 on 2011-12-20
Thank you Basher101!!  after i tried it the first time nothing happened but after my sis used the guest account and then restarted the computer the screen went fully black at the login screen so i went into recovery mode and i was about to delete that file and put the backup i made there but then i realised it turned black cuz it was set to 00. i changed it to 05 and updated grub then booted and it worked!  sure the brightness up/down keys dont work anymore but this is much better cuz i have more control over how bright i want it using the terminal command and it doesnt reset and go back to the previous brighness, it stays at the brightness setting i give it. so ty ty ty :D

also sorry about clogging your post lolpenguin.  I didnt think it would be a problem since i had a related issue but had it been something completely different, i definitly would have made a new thread.

---

