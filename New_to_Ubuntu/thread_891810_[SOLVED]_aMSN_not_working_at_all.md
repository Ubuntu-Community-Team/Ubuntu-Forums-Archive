---
title: "[SOLVED] aMSN not working at all"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by unknown user on 2008-08-16
[B]I have been using aMSn and I really think it is good.  However, the last few times I have come to use it, it has not been able to connect.  I have put my username and password in and the bar keep on going from side to side but never connects

I know thi has been addressed before but not sure how to do what is said as I am really new here.

Can anyone help please with easy to follow steps[/B]

---

### Post by Sorivenul on 2008-08-16
First make sure you have all your updates install.  If you do, uninstall aMSN completely and reinstall using the package from the aMSN website or getdeb.  From my understanding they recently upgraded their protocol and those with the old versions are having connection issues.  

[http://www.getdeb.net/app/aMSN]("http://www.getdeb.net/app/aMSN")
[http://www.amsn-project.net/linux-downloads.php]("http://www.amsn-project.net/linux-downloads.php")

---

### Post by zzHanks on 2008-08-16
Thank you for the links. 

I installed the deb package without uninstalling the previous version. Works smooth.

---

### Post by unknown user on 2008-08-17
[B]Thanks for the link, will try shortly.

Just one thing how do I know if to go for the 32 or 64 bit download?[/B]

---

### Post by peakshysteria on 2008-08-17
No need to shout man. And it might be better if you told us what version of Ubuntu you are running in the first post.```
cat /etc/lsb-release
```
Then it's easier to help. Msn has update a bit of their code. Amsn seems to be the only one affected. Other IM's should work fine. Have you tried that just to rule it out? An update for the latest version should already be available via synaptic. If not download the latest installer from the Amsn site. If that give doesn't help try to enable hardy-proposed and it all should be good.

---

### Post by stijngysemans on 2008-08-17
you can also try "emesene"
you can install this using applications > add/ remove programs

---

### Post by unknown user on 2008-08-18
[FONT="Verdana"]Hay peakshysteria I was not shouting in my reply, I just like messing around with the formatting of my message, see what nice effects I can get.
I will have a look at it tonight as do like aMSN.
Will also have a look at emesene, cheers.

zzHanks said that he installed the deb fine over the top of his existing version and it worked fine.  Can anyone give me any tips on doing this, thanks guys.[/FONT]

---

### Post by zzHanks on 2008-08-18
> **unknown user said:**
> [FONT=Verdana]
zzHanks said that he installed the deb fine over the top of his existing version and it worked fine.  Can anyone give me any tips on doing this, thanks guys.[/FONT]
It's probably safer to uninstall the previous version through Synaptic and then download the deb file from [http://www.getdeb.net/app/aMSN](http://www.getdeb.net/app/aMSN) (select 32 or 64 bit, depending on your computer) Install and you should be done.

Hope that helps.

---

### Post by unknown user on 2008-08-18
[FONT="Verdana"]Great guys I have now got it working by downloading the 32 bid deb one, works a treat again.
Can you give me any clues on setting up the account to allow me to click on my message icon and open it up?[/FONT]

---

### Post by gjoellee on 2008-08-18
I think I know why this happened:
MSN have just changed the server in some kind of way, and therefore old versions of, AMSN, Emesene, Pidgin etc... may not be able to connect

---

### Post by zzHanks on 2008-08-18
> **unknown user said:**
> [FONT=Verdana]Great guys I have now got it working by downloading the 32 bid deb one, works a treat again.
Can you give me any clues on setting up the account to allow me to click on my message icon and open it up?[/FONT]
That's good 

Are you talking about a launcher (shortcut) on the desktop?

If so: Right-click on the desktop > Create Launcher. Name it something like aMSN, then the command is just **amsn** and then the optional comment.

You can also add this to the panel.

---

### Post by unknown user on 2008-08-19
[FONT="Verdana"]Hi zzHanks, nope I mean the one when you open aMSn towards the top of the box, below your status, it tells you if you have any emails.  If you click on this, it tried to open your hotmail email account.

When I click on it I get the message that aMSn could not perform this request and to check my settings.

Hope this explain, cheers.[/FONT]

---

### Post by zzHanks on 2008-08-19
[quote=unknown user][FONT=Verdana]...I mean the one when you open aMSn towards the top of the box, below your status, it tells you if you have any emails.  If you click on this, it tried to open your hotmail email account.

When I click on it I get the message that aMSn could not perform this request and to check my settings.[/FONT][/quote]
Now I know what you're talking about (The skin that I use made it disappear, I think).

I don't think I have the solution, but have you tried **Change Account Information** under the Personal tab in Preferences?

---

### Post by unknown user on 2008-08-19
[FONT="Verdana"]Thanks for that I will try it tonight when I get home and hopefully it will work.  It would be smashing if I can sort this out.  

It is funny the more I sort out my Ubuntu to how I want it, the more I do not want to touch my dirty windows system:):)[/FONT]

---

### Post by SuperSonic4 on 2008-08-19
Type "firefox $url" in the preferences, such as I have done in the screenshot

---

### Post by zzHanks on 2008-08-19
[quote=unknown user]It is funny the more I sort out my Ubuntu to how I want it, the more I do not want to touch my dirty windows system:):)[/quote]
That's how it works.
 
I think SuperSonic4 has the solution.

---

### Post by unknown user on 2008-08-19
Cool that works a treat and now it opens up my message box, I have to log in with my password but can cope with that unless you guys know how to set up so it will log me in straight away

---

