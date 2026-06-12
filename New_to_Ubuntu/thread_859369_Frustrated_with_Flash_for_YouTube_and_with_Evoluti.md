---
title: "Frustrated with Flash for YouTube and with Evolution"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by pommyjohn on 2008-07-14
I was keen to give Ubuntu Linux a trial but my experience has been far from satisfactory.It is definately not for the none computer whiz.I have a good basic knowledge but have been unable to install a flash browser to view the likes of UTube.The problem appears to be widespread if you Google Ubuntu flash but no one appears to have the answer.I have the latest Ubuntu installed on a brand new Hard drive ,no other OS on the drive .I have run sudo removeflash and reinstalled many times.
Thenh I have a problem with Evolution, I cannot get addresses to appear in the "to" pull down box although all addresses appear in the contact list and the address book is set as default (again this problem appears to be widespread on google)
I will give it a few more attempts and then it is back to  user friendly XP

---

### Post by TSS on 2008-07-14
> **pommyjohn said:**
> I was keen to give Ubuntu Linux a trial but my experience has been far from satisfactory.It is definately not for the none computer whiz.I have a good basic knowledge but have been unable to install a flash browser to view the likes of UTube.The problem appears to be widespread if you Google Ubuntu flash but no one appears to have the answer.I have the latest Ubuntu installed on a brand new Hard drive ,no other OS on the drive .I have run sudo removeflash and reinstalled many times.
Thenh I have a problem with Evolution, I cannot get addresses to appear in the "to" pull down box although all addresses appear in the contact list and the address book is set as default (again this problem appears to be widespread on google)
I will give it a few more attempts and then it is back to  user friendly XP

The YouTube issue should be a fairly easy fix.  This should get the job done: [http://www.psychocats.net/ubuntu/flash#installing](http://www.psychocats.net/ubuntu/flash#installing)

With respect to Evolution, I don't really know, because I don't use it.  One of the great things about Ubuntu is the wide range of choices you have.  Install Thunderbird (sudo apt-get install mozilla-thunderbird) and give that a try!

---

### Post by philinux on 2008-07-14
Either use synaptic package manager. System>Admin menu.
Install ubuntu-restricted-extras


Or use the terminal Accesories menu

sudo apt-get install ubuntu-restricted-extras

---

### Post by LowSky on 2008-07-14
or go to add/remove and installl ubuntu restricted extras.... three ways to install something is pretty user friendly to me

Oh and Thunderbird is better in my opinion than evolution minus the exchage support but only businesses need that.. i just wish both programs could minimized to the tray natively. Alltray is great but doens't work well with Compiz-Fusion.

---

### Post by DJ_Peng on 2008-07-14
> **TSS said:**
> With respect to Evolution, I don't really know, because I don't use it.  One of the great things about Ubuntu is the wide range of choices you have.  Install Thunderbird (sudo apt-get install mozilla-thunderbird) and give that a try!
Just one problem: If you have Evolution set up you have to import all of the data from Evolution to Thunderbird. I can't say for that direction but going from Thunderbird to Evolution was a bit of a pain in my rear getting all of my email carried over.

Dorry, pommyjohn, but I haven't even tried that yet to know how well it (doesn't?) work.

> **LowSky said:**
> Oh and Thunderbird is better in my opinion than evolution minus the exchage support but only businesses need that.. i just wish both programs could minimized to the tray natively. Alltray is great but doens't work well with Compiz-Fusion.
I have an even better reason to switch to Evolution, as an end user and not as a business. Since I switched to Evolution I can finally sync the calendar to my PDA without jumping through hoops or duplicating data on multiple calendars.

---

### Post by LowSky on 2008-07-14
But seriosuly how many people have a PDA anymore,  AND Thunderbird has a plugin called lightning that makes up for the loss

This is just like the amorok vs exaile, banshee, etc.. soo many choices

I would hope some of these programs will merge together to give us end users  some better apps. Just like compiz and beryl

---

### Post by pommyjohn on 2008-07-14
Thanks for the help guys I am at work now and away from my Linux computer but will try your recommendations tonight and report back
Thanks in anticipation of success

---

### Post by Hendrixski on 2008-07-14
> **pommyjohn said:**
> Thanks for the help guys I am at work now and away from my Linux computer but will try your recommendations tonight and report back
Thanks in anticipation of success

Yeah, Flash in Ubuntu is easy, in fact installing any software in Ubuntu is brain-dead simple. It's all in the package manager that the guys above described.  One button installs usually too.

Today just installed GRails at work on a coworkers Windows box and I nearly got an ulcer, I had to set system variables, and reboot and... oh my god. It's just so much more difficult than when I installed it through the package manager.  one click and bang. Yeah, I use linux at work. :-)

---

### Post by pommyjohn on 2008-07-15
I must admit that I am now getting more frustrated with this,I can see that Adobe flash is installed by checking Synaptic.When i select any Utube video the screen turns black for a split second then just a blank white screen.
I have a cd from Linux NZ and a brand new hard drive with no other Os installed ,am I asking too much for an installation without any problem ?
Should I run the cd install again?

---

### Post by pommyjohn on 2008-07-15
TSS I tried your link but never got the missing plug in screen ,probably because the plugin ain't missing

---

### Post by whitethorn on 2008-07-15
what browser are you using?

---

### Post by Sealbhach on 2008-07-15
Hi,

I would recommend following all the instructions here:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

to sort out your flash problem.


.

---

### Post by DJ_Peng on 2008-07-15
> **LowSky said:**
> But seriosuly how many people have a PDA anymore,  AND Thunderbird has a plugin called lightning that makes up for the loss

This is just like the amorok vs exaile, banshee, etc.. soo many choices

I would hope some of these programs will merge together to give us end users  some better apps. Just like compiz and beryl
Actually it's not just PDA's, it's also smart phones. And Lightning doesn't sync to mobile platforms without a third-party, Windows-only solution. 

Personally, I know when I'm trying to find an answer that prompts other software options I'd rather try to get it resolved with the program I already use, especially when it as as much personal data as a web browser or an email client, before I try a different program. I'm not fussing, just saying. And some of us are disappointed enough by the choices made in Firefox 3 that we're not that eager to see what happens when Thunderbird 3 comes out. So far it was looking good when I made the switch to Evolution, but Mozilla software is no longer my first choice for a task anymore after my experience getting Firefox 3 out of beta.

---

### Post by pommyjohn on 2008-07-15
Problem all fixed ,it was caused by Gnash, once I removed this everything worked fine

---

