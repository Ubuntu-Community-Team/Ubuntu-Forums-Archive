---
title: "On the road to..."
date: 2012-09-18
forum: New to Ubuntu
---

### Post by Arthur Livingston on 2012-09-18
« I first met Dean not long after my wife and I split up. »

hi,

Ok yes I am new on this road. But I believe that sharing ideas and a computer running on a **just working** version of Linux can potentially make the world a better place. So two days ago I decided to try my hand at all this, thinking that it would be easy for me as it should be for the world to embrace it. Geek friend of mine was supposed to help but the stoner was more of a loudmouth than a helper. Since a new thread can potentially bring some others pass through the first step - that is not get discouraged when knocking head on walls - I will try to bring this to its happy end and write my journey for the world to read. Characters met on this road will surely make it unroll it to a new day if Linux really is the San Fran of operating systems as people say...

Here's the ride:

- Dell Optiplex 760, initially running Vista, 2 HDD, Win 7 on one and Ubuntu on the other;
- ATI Radeon 3450 HD suspected of creating conflict with 'Buntu.

[LIST=1]
[*]First downloaded the wubi.exe on Ubuntu website. Ended up with a blinking white depressive underscore.
[*]Figured out how to change the boot order of the Dell, burned Ubuntu 12.04 to a cd and fired up.
[*]Ended up with another depressive underscore blinking white into the night of the dark screen.
[*]Ended up with another depressive underscore blinking white into the night of the dark screen.
[*]Pressed a key when two white images appeared at the bottom of the screen after booting from cd. Got to a page where F6 led to the ability to mark a X on each of the following: «acpi=off», «noapic» and «nomodeset». Installed Ubuntu this way,  brought it to a party and drank and danced all night like beat kids do in these sweet sixties - told myself that it was great and decided to go on with this if the plan could work.
[*]Next day decided to replace the driver as soon as I could find one that was open enough. Had to cheat on Ubuntu to make it start by pressing E at what they call the «Grub screen», that led me to remove «quiet splash $vt_handoff» and replace it with «acpi=off». I was on saddle, winding like a bullet through the red and purple plains.
[*]Went to ATI website and downloaded the Linux drivers. Went to the System Settings and tried authenticating or installing the drivers: 
- «ATI/AMD proprietary FGLRX graphics driver (post-release updates)» failed to install; 
-  «ATI/AMD proprietary FGLRX graphics driver» ...it was written at the bottom that I need to restart, but restarting let to a dark brown screen...
[/LIST]

I'm now like Sad Sal waiting for a fix.

**What do you think?**

Arthur

---

### Post by newb85 on 2012-09-18
From the sticky [Suggestions on how to get your support questions answered as quickly as possible]("http://ubuntuforums.org/showthread.php?t=1422475")

> 4. Make the title of your thread meaningful and concise. 

> 9. Don't ramble. Some background information on your problem is necessary, but try to keep all the information in your post relevant to your problem.

If you describe what you've done with your computer and omit the parts about your geek friend, your party life, beating your kids, and your poetic license, someone might take the time to help you.

---

### Post by QIII on 2012-09-18
For many users, the fglrx-updates (Post release updates) version does not work.  For many users, the GUI "Additional drivers" method of installation does not work.

If you can manage to stumble back on to the Rocky Road to Dublin without too much difficulty,  see the Community ATI Driver wiki in my signature.

Look for the section "Using the Ubuntu repositories (alternate command line method)".

---

### Post by vasa1 on 2012-09-18
> **newb85 said:**
> ...
If you describe what you've done with your computer and omit the parts about your geek friend, your party life, beating your kids, and your poetic license, someone might take the time to help you.

Absolutely agree. I If I were king of the world, I'd lock such posts up where no one would have to waste time reading them. OP should get a blog for the other stuff and just post the simple request here.

Unfortunately, there are people who stuff their posts with stuff that isn't just relevant to the support they seek.

---

### Post by Arthur Livingston on 2012-09-18
sorry. plain basics, w/o poetry:

Dell Optiplex 760, Ubuntu
ATI Radeon 3450 HD

works ok with «acpi=off», «noapic» and «nomodeset», installed Ubuntu this way

starts good when removing «quiet splash $vt_handoff» and replacing it with «acpi=off»

doesn't work with ATI Linux drivers
- «ATI/AMD proprietary FGLRX graphics driver (post-release updates)» failed to install; 
- «ATI/AMD proprietary FGLRX graphics driver» not working neither

is there a simple package to make it work? anything simple?

---

### Post by Arthur Livingston on 2012-09-18
putting in another video card might be a solution... 
wich one should work and will it work?
(considering that this definitely seems to be a video card driver problem)

---

### Post by QIII on 2012-09-19
Did you attempt to reinstall using the method I suggested?

---

### Post by Arthur Livingston on 2012-09-19
hi [QIII]("http://ubuntuforums.org/member.php?u=628170")

No I did not yet. I lack the time to understand the methods and all. For now it is really not my thing to try to understand all of that.

If Linux really is a game of messing with drivers I am backing off. As you might have seen, my natural interests are somewhere else.

If the same thing happens when I had the firewire card and hard drive that I already have, then I will hit a wall and not do what already urges...

But I am not totally dropping the ball yet, I will try to take the time to use your method in the next days.

Thank you, the others can go back to what they do best, whatever that is.

By the way, excerpts and poetic influence from the first post were from Jack Kerouac's On the road. I wanted to make it a nice & useful thread. Sorry to break the square, here is not the place for that.

A.

---

### Post by Arthur Livingston on 2012-09-19
*when I _***add***_ the firewire card...

---

