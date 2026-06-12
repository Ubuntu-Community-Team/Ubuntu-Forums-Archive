---
title: "How I got Dreamweaver 8 + Fireworks 8 to work!"
date: 2006-09-27
forum: Outdated Tutorials &amp; Tips
---

### Post by LetsLinux on 2006-09-27
I'm fairly new to linux - and as I am in the middle of switching completely from Windows XP to Ubuntu, there are some programs that I simply can't live without. "Sure" you might say, "There are alternatives!" True there are some alternatives - but they simply aren't good enough, at least not compared to Fireworks and Dreamweaver to some extend. So I started snooping around, since I wanted these to work in Linux - but obviously they do not work using Wine I found out. It wouldn't even begin to install.

**However** there is a way - it's long, tough and diehard - but I actually managed to have both programs work like a charm. This is how I did it. :KS 

I first ran through [**this**]("http://www.ubuntuforums.org/showthread.php?t=149585") post here at UbuntuForums.org. When I was done here, I found a great website telling exactly how to do it. I will link to it later - but I will take bit's an pieces from it - since there was a lille overkill when speaking of information.

Anyway - here I go. (Make sure Wine is installed and working. The .wine directory has to be there)

[LIST=1]
[*]Make a proper installation of Dreamweaver and Fireworks in Windows XP (I know it sucks - but that's the way it is. :rolleyes: )
[*]Return to Linux (yeehaa)
[*]Copy the *Macromedia*-folder from the *c:\program files* to  */home/**<name>**/.wine/drive_c/Program Files*
[*]Copy the *Macromed*-folder from *c:\windows\system32* to */home/**<name>**/.wine/drive_c/window/system32* (yes it's called Macromed without the *ia*-part)
[*]Copy the *Macromedia*-folder from *c:\documents and settings\all users\application data* to */home/**<name>**/.wine/drive_c/Window/profile/all users/*
[*]Copy the *Macromedia*-folder from *c:\program files\common files* to */home/**<name>**/.wine/drive_c/Program Files/Common Files/*
[/LIST]

The cherry on the top of it all is the **gdiplus.dll** file, which you have to download from [here]("http://www.dll-files.com/dllindex/dll-files.shtml?gdiplus") and copy to */home/**<name>**/.wine/drive_c/window/system32*

I did this - and it worked the first time. However, if you experience problems - you might read the [whole article]("http://bkcreation.info/Blog_Macromedia8OnWine.html") on how to do it. It might be as helpful to you as it was to me.

Good luck with the installation.

Jonas :D

---

### Post by ethan@xmlstandards.org on 2006-09-27
I realise your desire to continue using the same tools you have become accustomed to on the Windows platform, and that some of the alternatives for Linux are not as polished or perhaps as complete as the Windows options, however if you really are committed to migrating desktops (I have just done this recently) then you really should reconsider looking at other alternatives that might provide what you are looking for (don't just limit yourself to what the default repositories provide - try GnomeFiles.org).

For myself I have moved my office workstation to Ubuntu, running only what I need for web application development. I have a really well customized setup now and probably only miss Microsoft Outlook, but since I can always use webmail (Exchange) then I can still stay up to date. I don't really like OpenOffice so I choose Gnumeric and AbiWord instead, also look at Google Spreadsheet and Google Wrtitely as online alternatives.

Listen dude, Dreamweaver really sucks (been using it since version 3.0), have you tried Eclipse yet? Try out the Web Tools Platform. As for Fireworks, I love that tool too, however I have yet to come across a task I cannot complete using the GIMP. Give them a try if you can.

Please ignore my comments if they don't really apply to your particualar needs, ultimately you'll use what you find to be most productive, just give all of Linux a chance. It took me nearly six months to migrate fully from Windows.

At first I had to run Windows with VMware installed and start up a virtual machine from within Windows, then I learned how to perform a proper dual boot setup that enabled me to boot into Linux and still access "My Documents" from Ubuntu (same disk right?) then I realised that I hadn't booted into Windows for over a month. So I took the leap and have now only Linux installed on my machine and never want for Microsoft. Hopefully never again.

Very seriously. Linux makes you a better person.

Good luck

Ethan Cane

---

### Post by LetsLinux on 2006-09-28
Hi Ethan,

Thank you for your comments. It's always good that not everybody agrees on everything - it would be way to dull - and never expans ones horizon. 

I for one loves the simple setup in OpenOffice and I believe their spreadsheets to be very suitable for my needs. Next edition might be able to beat Excel I hope. It runs faster than MS Office. I haven't tried Gnumeric but AbiWord reminds be too much of WordPro, which I grew to dislike a lot.

Talking about mailing programmes, well Outlook was good for me (personally) however I never used the calendar tool - as my cellular did that for me as well as my time-manager. Thunderbird suits my needs with reading and writing mails - as I don't spend much time with that when I'm off work - but I haven't tried Evolution. Is that something you can recommend?

I have found software outside the standard repository that comes with Ubuntu. But I must confess, GIMP simply doend't do it for me. I have been working with Fireworks since number 4 - and simply got the hang of it and right now, I don't want to change that. However GIMP seems to be updated frequently, so I can't say that I don't want to switch to that yet. However, I need to feel good around it before I switch. And having bought Fireworks - I might just want to have my moneys worth! :-)

I understand what you say about Windows and the My Documents thing. Using NTFS-3g for Linux I managed to be access (read and write) my Windows partition as well. I hardly use Windows anymore, I guess it's only there by habit. ](*,) 

You're right, using Linux makes things a bit easier and more bright!

---

### Post by Josh1 on 2006-09-28
Actually dreamweaver does not "suck", its the industry standard, and everyone uses it.
By the way, nice guide, though I could swear i've seen it around somewhere, since this is the way I did it :D.

---

### Post by LetsLinux on 2006-09-28
I also like Dreamweaver :-)

By the way, yes I got the link from here as well - but it was do difficult to find. Now at least I got "Dreamweaver" "How" and "Fireworks" so it would be easier to find by doing a seach! :-)

---

### Post by Josh1 on 2006-09-28
Uploaded a screenshot to my site:
[http://josh.bur.st/ubuntu/images/dreamweaver.png](http://josh.bur.st/ubuntu/images/dreamweaver.png)

edit:
By the way i had to import the regkey for dreamweaver.

---

### Post by MKR. on 2006-09-28
> **Josh1 said:**
> Actually dreamweaver does not "suck", its the industry standard, and everyone uses it.
By the way, nice guide, though I could swear i've seen it around somewhere, since this is the way I did it :D.

It's a matter of taste. :P

Industry standard doesn't equate to "best for everyone". Maya and 3dsmax are industry standard for CGI,  but I find them to be painful to use, and stick to blender + wings.

Dreamweaver's functionality is mirrored in the form of several applications, but the convergence that comes from Dreamweaver is nice.

If I hadn't already become accustomed to all the editors I use, I would definately use this guide to get Dreamweaver working. :P

---

### Post by ethan@xmlstandards.org on 2006-09-28
Just pitching back in for five minutes.

I work in the industry, for a top 10 agency in fact in the heart of London, and in my experience Dreamweaver is far from being an industry standard. It is just the best tool around with which we have been lumbered by Macromedia/Adobe.

Honestly, not wishing to get off topic here, but sit down and try to install Eclipse (preferably the Web Tools) and get it setup correctly.

Depeding upon your needs (I am a ColdFusion/XML/XSLT/Oracle developer) install the plugins you need to be productive. There are hundreds available.

Give it a whirl and you'll honestly see why it beats Dreamweaver hands down. I know where you are coming from with your responses. I too used and swore by Dreamweaver until I found Eclispe (just like finding Jesus - :) -). My main gripe is down to all the little wizards and stuff it throws at you to code applications. I mean learn how to do that stuff by hand. This is my whole point about Linux making you a better person. You are truly exposed to your environment and have to learn how to do low level tasks.

Tools like Dreamweaver and Windows in general hide that sort of stuff from you, keeping you dumb and constrained to their way of doing things.

Long story short...

Install Eclipse, (do not take my word for it - ask a friend or someone you work alongside), and then create a simple project, move around the workspace and take a look at all the options it provides. It really is a powerhouse IDE, and here to stay.

Ethan Cane

PS.

If you feel like following up this discussion then I'll send you my address and we can step outside and do this thing. Biatch!

---

### Post by jcrnan on 2006-09-28
letslinux: If I were gay I would marry you :D

This is so awsome, I love dreamweaver and now I actualy can run it properly ^^ weeeeeeeeee

---

### Post by Josh1 on 2006-09-28
> **ethan@xmlstandards.org said:**
> Just pitching back in for five minutes.

I work in the industry, for a top 10 agency in fact in the heart of London, and in my experience Dreamweaver is far from being an industry standard. It is just the best tool around with which we have been lumbered by Macromedia/Adobe.

Honestly, not wishing to get off topic here, but sit down and try to install Eclipse (preferably the Web Tools) and get it setup correctly.

Depeding upon your needs (I am a ColdFusion/XML/XSLT/Oracle developer) install the plugins you need to be productive. There are hundreds available.

Give it a whirl and you'll honestly see why it beats Dreamweaver hands down. I know where you are coming from with your responses. I too used and swore by Dreamweaver until I found Eclispe (just like finding Jesus - :) -). My main gripe is down to all the little wizards and stuff it throws at you to code applications. I mean learn how to do that stuff by hand. This is my whole point about Linux making you a better person. You are truly exposed to your environment and have to learn how to do low level tasks.

Tools like Dreamweaver and Windows in general hide that sort of stuff from you, keeping you dumb and constrained to their way of doing things.

Long story short...

Install Eclipse, (do not take my word for it - ask a friend or someone you work alongside), and then create a simple project, move around the workspace and take a look at all the options it provides. It really is a powerhouse IDE, and here to stay.

Ethan Cane

PS.

If you feel like following up this discussion then I'll send you my address and we can step outside and do this thing. Biatch!

OK, I installed it by synaptic and all the other needed things to run it, but Now I can't find it in Applications.. Any idea on where it is :P?
P.S:
It seems that eclipse is really good in your point of view, and before bashing a product I like to use it for a bit and see how well it performs.

---

### Post by LetsLinux on 2006-09-29
> **jcrnan said:**
> letslinux: If I were gay I would marry you :D

Ha ha ha... Not quite the reaction I hoped for, but anyway, good it worked for you. Macromedia makes excellent programmes, so why throw them away just because you change OS! :mrgreen: 



> **ethan@xmlstandards.org said:**
> 
Tools like Dreamweaver and Windows in general hide that sort of stuff from you, keeping you dumb and constrained to their way of doing things.


Ha ha ha... I agree. I do most of the programming via a text editor. So I actually don't use Dreamweaver that much - but it has a great CSS editor included! :-D 

> **ethan@xmlstandards.org said:**
> 
Install Eclipse, (do not take my word for it - ask a friend or someone you work alongside), and then create a simple project, move around the workspace and take a look at all the options it provides. It really is a powerhouse IDE, and here to stay.


Haven't heard about it - I might have to install it and give it a try!

---

### Post by rejser on 2006-10-27
Installed once before using this guide, everything worked fine. But installed a new harddrive and reinstalled as my old harddrive where quite tired and made funny noices.
When I start I get a message saying something is wrong with the software, please reinstall (the windows version works fine, Wine is version 0.9.22)

If I look in the terminal it says:
"*fixme:win:EnumDisplayDevicesW ((null),0,0x34f7c4,0x00000000), stub!*"
Which don't say me anything.

Any idea, I've gotten so comfy with dw so it feels like betreyal to use anything else.

---

### Post by mrojas73 on 2006-10-28
I like dreamweaver for html and php.  Can you do both with eclipse or it is just for java stuff?

---

### Post by logik-bomb on 2006-10-28
> **rejser said:**
> Installed once before using this guide, everything worked fine. But installed a new harddrive and reinstalled as my old harddrive where quite tired and made funny noices.
When I start I get a message saying something is wrong with the software, please reinstall (the windows version works fine, Wine is version 0.9.22)

If I look in the terminal it says:
"*fixme:win:EnumDisplayDevicesW ((null),0,0x34f7c4,0x00000000), stub!*"
Which don't say me anything.

Any idea, I've gotten so comfy with dw so it feels like betreyal to use anything else.

Same problem here :|

Help us, plz !
thanks

---

### Post by rejser on 2006-11-01
Could we have some wine-version info for those with working. I used to have working but not after reinstall. Don't remember which wine-version I ran.

tried .22 .23 and .24 without success.

---

### Post by dr.drake on 2007-01-03
> **ethan@xmlstandards.org said:**
> 
 ..As for Fireworks, I love that tool too, however I have yet to come across a task I cannot complete using the GIMP. Give them a try if you can...


I have a similar issue.
I was hooked on my Microsoft Image Composer :shock:  that I got for free some years ago, and I've been using it for all my website developingneeds _because it's so simple_.
recently I bought an macBook to have a portable protools studio (yes I know of the linux alternatives, but most pro recording studio's don't, so I really do need protools) and finally discovered Fireworks. it is almost the Image Composer replacement I was looking for on the mac.

I am still looking for a Linux version of one of the two, or something that works the same.
I have tried GIMP a couple of times, but eventhough it is a really good photoshop type of program, the functionality is not the same as in Fireworks or Image Composer.
the easy drag and drop of those two is what I need. in GIMP or PS the layers are too far away to select and everything you do is made a new layer, while in FW or IC it is a simple question of click it and it's selected because they are all on the same level.

I must say that I still prefer IC over FW because I can drag and move the outlines of my workspace any way I want, which makes it easy to create a small thing outside the workspace, outline it, and safe it for further use, after which I go back to the original workspace.
it is also handy when you made a whole layout, but still want to move everything to the left a bit... you don't: you just move the workspace borders to the right ;)

so...
who do we speak to to get these things ported, stolen or rewritten to/for linix??

---

### Post by Darkstar0082 on 2007-02-09
I must admit that I am new to the whole linux environment but I can say that I am glad that my curiosity had led me to try ubuntu. I dual boot with XP only because I still use Dreamweaver 8, Fireworks 8, and Flash 8. I've tried the whole copy folders to linux idea and I even copied the regedit key. I still haven't got it to work without crashing so I am going to do it all over again and see if I can finally get it installed and working properly. I want to just erase my XP partitions completely off of my laptop and be a linux user for life! Bluefish is OK but it doesn't compare to Dreamweaver. Screem lacks the functionality of a complete editor. NVU was a great idea and has a lot more potential but still dreamweaver 8 had it beat in productivity. Fireworks was just my favorite tool hands down and Gimp is also a great program but I am just used to FW8. If you have the money (or hacking abilities) I would recommend the whole Macromedia bundle of web dev programs because they are just killer applications for developing high quality sites. I am going to try eclipse because I haven't yet tried it. Ethan seems to know what he is talking about so I think it's worth a shot.

---

### Post by Dylnuge on 2007-02-09
This should help:

[http://blog.publicidadpixelada.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/](http://blog.publicidadpixelada.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/)

It worked for me. Studio 8 Professional is a great suite of apps (although with the recent Adobe takeover, I am wondering how much more like GoLive Dreamweaver will be, how much more like Illustrator Fireworks will be, and so on).

EDIT:
Sorry, I clicked on the post in recent posts and thought it was a question. Never mind.

---

### Post by geovino on 2007-03-06
Is Eclipse a web editor or what? I'm open to new web editors and I've been looking for one that I can use instead of Dreamweaver. So far I've liked Quanta.

What are your thoughts?

---

