---
title: "Avoid your program to look ugly if requires root privileges?"
date: 2010-06-13
forum: Programming Talk
---

### Post by hakermania on 2010-06-13
I have developed a program that does things that require root privileges, so in its desktop shortcut I created I added the 'gksu' to the 'Exec='. Now every time I run it it asks for administrator password and runs perfectly! The problem is that when it is running like this looks very ugly, every visual effect disappears and the window looks like it comes from Windows 98 or something like that (yiak). I've wasted really much time in this program. Can you help me fix this, or find another way to run the program with root privileges but not to look so ugly.
To understand look how it looks when normal user runs it (and the prog doesn't work):
[IMG]http://i45.tinypic.com/e6dd82.png[/IMG]
And that's how when is run with root privileges(and the prog work because it requires root privileges):
[IMG]http://i47.tinypic.com/2dj2grl.png[/IMG]
[CENTER]***_Thx for any answers or help!_***
[/CENTER]

---

### Post by simeon87 on 2010-06-13
> **hakermania said:**
> I've wasted really much time in this program

+1, given that you could have used this time constructively for a program that actually benefits others.

---

### Post by ad_267 on 2010-06-13
Usually this is because you're using a gtk theme from your users home directory rather than one installed system wide. If you use a theme installed system wide or symbolically link your .themes directory from /root you shouldn't have this problem.

It looks like you're using the default Ubuntu theme in that screenshot though, is that correct?

---

### Post by hakermania on 2010-06-13
Yes, I am using the default theme. My though is that people that'll take this prog will find it too ugly too, and i cannot make them link anything... :(

---

### Post by James78 on 2010-06-13
Generally what I do is something like gksudo gnome-control-center, then I edit the preferences for the root account, themes, etc, then they display perfectly.

P.S. Nice program. It'd be nicer if your program asked for the administrator password when it starts itself up though right? That way users won't have to add gksu or anything else to a shortcut.

---

### Post by SledgeHammer_999 on 2010-06-13
> **James78 said:**
> ...It'd be nicer if your program asked for the administrator password when it starts itself up though right? That way users won't have to add gksu or anything else to a shortcut.

That's what gksu does.

---

### Post by James78 on 2010-06-13
I meant program it INSIDE the program, so it doesn't have to be added to a shortcut. ;) Just like synaptic and other programs.

---

### Post by d3v1150m471c on 2010-06-13
why not just modify some launch commands.
IE:
```

echo "password" | sudo -S command

```You could have the program store the user's password when asked for it upon its initial installation and have it append a variable in the coding that could be piped to sudo instead of dealing with gksu.
Of course you might want to encrypt wherever the variable is stored or something of the like. hope that helps... Freakin' cool app btw.

A better idea might be to have an input space on the application that the password could be entered to.

---

### Post by SledgeHammer_999 on 2010-06-13
> **James78 said:**
> I meant program it INSIDE the program, so it doesn't have to be added to a shortcut. ;) Just like synaptic and other programs.

That's one possibility. But synaptic doesn't do it. Open this file a take look-->/usr/share/applications/synaptic.desktop

---

### Post by James78 on 2010-06-13
> **SledgeHammer_999 said:**
> That's one possibility. But synaptic doesn't do it. Open this file a take look-->/usr/share/applications/synaptic.desktop
I know. It was just an example though. :)

---

### Post by nvteighen on 2010-06-13
Well, there's the new authentication system in GNOME in which a button is provided to gain/drop root privileges (e.g. in Date & Time settings). I'm not sure how that works, but there it is.

---

### Post by trent.josephsen on 2010-06-13
Here's my question:  Why are you running the entire thing as root if only parts of it require root privileges?  You should run all the boring and nonessential stuff, like creating a GUI and changing settings, in user mode, and become root only when you need to -- that's a fundamental security rule.  Like, say, Aptitude, which lets you search for packages and schedule things in user mode, and become root only when you're ready to apply changes (unfortunately it doesn't use sudo, so won't work if you don't have a root password set).

I don't know whether that would be a major overhaul of your program or not.  If you're just calling other programs behind the scenes, adding "sudo -S" to the front and piping in the password should do it (haven't tried it myself).  If you're interacting with the hardware directly it may be more involved (but shouldn't be too bad if it's written modularly).

---

### Post by sisco311 on 2010-06-13
> **nvteighen said:**
> Well, there's the new authentication system in GNOME in which a button is provided to gain/drop root privileges (e.g. in Date & Time settings). I'm not sure how that works, but there it is.

+1 

It's called PolicyKit.

[http://hal.freedesktop.org/docs/polkit/](http://hal.freedesktop.org/docs/polkit/)

> **trent.josephsen said:**
> Here's my question:  Why are you running the entire thing as root if only parts of it require root privileges?  You should run all the boring and nonessential stuff, like creating a GUI and changing settings, in user mode, and become root only when you need to -- that's a fundamental security rule.  Like, say, Aptitude, which lets you search for packages and schedule things in user mode, and become root only when you're ready to apply changes (unfortunately it doesn't use sudo, so won't work if you don't have a root password set).



+1

---

### Post by StephenF on 2010-06-13
There is a program called gtk-chtheme that you can run as root to set the desired gtk theme for the root user.

---

### Post by hakermania on 2010-06-13
the app with a new look is now available in 
```
http://rapidshare.com/files/398621645/CrackWifiMachine.tar.gz
```
only for educational purposes of course!
[IMG]http://img189.imageshack.us/img189/2617/screenshotcrackwifimach.png[/IMG]
@[d3v1150m471c]("http://ubuntuforums.org/member.php?u=979822")
Too few people will trust your system. I use gksu...
@[SledgeHammer_999]("http://ubuntuforums.org/member.php?u=76221")
Yes, you are right, when I realized that I was fool to make a program like this I remembered Synaptic and I go checked his shortcut, and then discovered gksu...
@[James78]("http://ubuntuforums.org/member.php?u=672443")
I don't know how to do your suggestion, give some C++ code


PS.Be nice with the prog and me, I am only 15....Let me now if it looks ugly when is run by root, i changed some settings in my system and all look like the picture now, but let me now.....:P
Oh, and run ./make as simple user....

---

### Post by hakermania on 2010-06-13
> **trent.josephsen said:**
> Here's my question:  Why are you running the entire thing as root if only parts of it require root privileges?  You should run all the boring and nonessential stuff, like creating a GUI and changing settings, in user mode, and become root only when you need to -- that's a fundamental security rule.  Like, say, Aptitude, which lets you search for packages and schedule things in user mode, and become root only when you're ready to apply changes (unfortunately it doesn't use sudo, so won't work if you don't have a root password set).

I don't know whether that would be a major overhaul of your program or not.  If you're just calling other programs behind the scenes, adding "sudo -S" to the front and piping in the password should do it (haven't tried it myself).  If you're interacting with the hardware directly it may be more involved (but shouldn't be too bad if it's written modularly).
all of the program's features require root privileges. it would be annoying for every button you pressed a pop-up was appearing requesting your passwd. it was something I would like to avoid :)

---

### Post by Finalfantasykid on 2010-06-13
A little off topic, but you mentioned that no one would use the program if it looked like the theme was from win 98.  I think what is equally important though is to have a good GUI design.  Take a look at this document [http://pages.cpsc.ucalgary.ca/~saul/hci_topics/powerpoint_presentations/grapical_design.ppt](http://pages.cpsc.ucalgary.ca/~saul/hci_topics/powerpoint_presentations/grapical_design.ppt) .  Many of the components in your program are placed without much thought on a reason for them to be placed there.

---

### Post by hakermania on 2010-06-13
> **Finalfantasykid said:**
> A little off topic, but you mentioned that no one would use the program if it looked like the theme was from win 98.  I think what is equally important though is to have a good GUI design.  Take a look at this document [http://pages.cpsc.ucalgary.ca/~saul/hci_topics/powerpoint_presentations/grapical_design.ppt]("http://pages.cpsc.ucalgary.ca/%7Esaul/hci_topics/powerpoint_presentations/grapical_design.ppt") .  Many of the components in your program are placed without much thought on a reason for them to be placed there.
Thx for your link, I'll check this, but I have to tell you that my app looks like it is from win98 because it is run with root privileges, something necessary! So, I can generally change the look of my app, but not the look of the 90s xD

---

### Post by trent.josephsen on 2010-06-13
> **hakermania said:**
> all of the program's features require root privileges. it would be annoying for every button you pressed a pop-up was appearing requesting your passwd. it was something I would like to avoid :)

A GUI is a feature, and it doesn't require root privileges, which was my point.

But my idea was to ask for the password once (on startup) and store it against future use.  Not the greatest, but short of splitting the entire thing into daemon and client processes and implementing authentication of clients, it's the most secure solution I can see.  In my experience, poorly written GUI apps are the most prone to misbehavior -- better that happen to a regular user than to root.

sudo's timeout scheme suggests a possibly more robust solution.

---

### Post by nvteighen on 2010-06-14
> **sisco311 said:**
> +1 

It's called PolicyKit.

[http://hal.freedesktop.org/docs/polkit/](http://hal.freedesktop.org/docs/polkit/)


Thanks. It seems an interesting API worth to explore... (the question is... when? I got no time! :()

---

### Post by hakermania on 2010-06-14
> **trent.josephsen said:**
> A GUI is a feature, and it doesn't require root privileges, which was my point.

But my idea was to ask for the password once (on startup) and store it against future use.  Not the greatest, but short of splitting the entire thing into daemon and client processes and implementing authentication of clients, it's the most secure solution I can see.  In my experience, poorly written GUI apps are the most prone to misbehavior -- better that happen to a regular user than to root.

sudo's timeout scheme suggests a possibly more robust solution.
hm...I see, can you tell me how to pipe out the passwd?
I mean, ok, the user runs make, his passwd is asked and stored in a folder...Then how do I connect this file with this app and every time it runs the authentication is being done automatically??

---

### Post by SledgeHammer_999 on 2010-06-14
> **hakermania said:**
> hm...I see, can you tell me how to pipe out the passwd?
I mean, ok, the user runs make, his passwd is asked and stored in a folder...Then how do I connect this file with this app and every time it runs the authentication is being done automatically??

You do realize that this is bad practice and may create a huge security hole on your user's machine, right? Furthermore this kind of practice could classify your app as malware.

---

### Post by trent.josephsen on 2010-06-14
> **hakermania said:**
> hm...I see, can you tell me how to pipe out the passwd?
I mean, ok, the user runs make, his passwd is asked and stored in a folder...Then how do I connect this file with this app and every time it runs the authentication is being done automatically??

No, no.  At startup, not compilation.  Store the password in a temporary variable.  This isn't necessarily the best idea either, but orders of magnitude better than trying to save it on a hard drive.

Alternatively, you could let sudo decide (set SUDO_ASKPASS to a password-asking tool of your choice and use the -A switch to sudo).  That way you only have to enter the password once per timeout period.

The most secure way would be to make sure that the user has access to the necessary hardware without having to become root.  I don't know how complicated that would be for your program.

---

### Post by nvteighen on 2010-06-14
Can I ask what exactly is what requires root privileges?

Also, be aware that your application may be illegal in some countries even if used for educational purposes.

---

### Post by jwbrase on 2010-06-14
Frankly, I think the "Windows 98" look is much better than the Ubuntu default...

---

