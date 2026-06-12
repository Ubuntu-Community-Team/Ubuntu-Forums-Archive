---
title: "Ubuntu with Xfce or Xubuntu? 14.04"
date: 2015-04-25
forum: New to Ubuntu
---

### Post by Shugs81 on 2015-04-25
Hi peeps

Back again for another swing at ubuntu... lol... could never seem to get to grips enough to stick with it but having a mess around i'm really liking 14.04 and have a few questions...

Firstly... Really don't like unity... have zero clue why... tried it for a bit... didn't get on with it...  so I installed Xcfe and like how smooth it is and like the panels etc... seem to be able to use the terminal too... which i couldn't get past fedora commands before just seems a load easier... even tho it's never changed!!! who knows???!?!?

anyway.. current using a 32gb usb stick to test it out... so it does run a bit jerky and stuff... I wanted to ask a couple of questions before I get started with ditching fedora...

firstly... is there a way to just copy the install from the usb stick to the ssd I'm using? so it keeps all my settings n stuff???

also... as i've installed std ubuntu with unity DE and installed XCFE separately... would i be better off installing xubuntu or can i uninstall unity without collapsing my machine?

not a massive fan of the ubuntu store... is this the main software for updates and installs? or is there something like yumex or the like that i've forgotten about?

The machine is going to be used as a graphics/digital art workstation and I would also like to remove anything uneccessary... any reccomendations of bloatware that I can get rid of?


Thanks in advance for any help!!! you guys always seemed much frendlier than the fedora lot... :D

---

### Post by Shugs81 on 2015-04-25
also another quick one.... why does firefox keep asking me to install stuff everytime I go to a website? what does it do and does it make a difference?

---

### Post by kerry_s on 2015-04-25
1) all you should need is /home
2) +1 xubuntu
3) ubuntu store is there, but you can install & use synaptic, which is what i do. yes, it has software updates
4) i just leave everything as it is, if your not using it it's not running. now if you mean bloat as in space, you can remove what ever you want, the standard applies read everything 3 times before clicking apply & hopefully you don't break nothing.

5) you can turn that off in firefox preferences. in xubuntu you don't have to worry, those are not installed.

---

### Post by Shugs81 on 2015-04-25
Awesome! Good job I'm already downloading xubuntu just in case! Will have to go back into fedora to make sure I've got everything...

Only thing I have to sort now is the hdmi issues... but that may be hardware fail anyway.... and that's for another thread!!

Thanks again.... *virtual fist bump*

---

### Post by kerry_s on 2015-04-25
> **Shugs81 said:**
> Awesome! Good job I'm already downloading xubuntu just in case! Will have to go back into fedora to make sure I've got everything...

Only thing I have to sort now is the hdmi issues... but that may be hardware fail anyway.... and that's for another thread!!

Thanks again.... *virtual fist bump*


xubuntu has great multi-monitor support, i used hdmi on my laptop & i'm using vga on this hp mini netbook.

---

### Post by flaymond on 2015-04-25
Xubuntu is very nice to use, very customizeable and lighter than Ubuntu. Well, I use Lubuntu, with Unity and XFCE in it. (I kinda like Unity, easy to access apps from the left launcher).

---

### Post by buzzingrobot on 2015-04-26
> **Shugs81 said:**
> Hi peeps


I installed Xcfe... seem to be able to use the terminal too... which i couldn't get past fedora commands before just seems a load easier... 

That's confusing, but the "terminal" in Fedora, all Ubuntu flavors, and pretty much all of Linux uses the same shell: Bash. Apart from possible very minor default configuration defaults, they're all identical.

> i've installed std ubuntu with unity DE and installed XCFE separately... would i be better off installing xubuntu or can i uninstall unity without collapsing my machine?

Best to cleanly install Xubuntu if that's what you want to use. Desktop environments are large and complex collections of software packages and removing them is often more trouble than it's worth. (Although, Unity does not execute when you use XFCE, or vice versa, so removing the Unity packages frees up a bit of disk space but shouldn't impact performance.)

> not a massive fan of the ubuntu store... is this the main software for updates and installs? or is there something like yumex or the like that i've forgotten about?

All official Ubuntu software packages are maintained in the Ubuntu repositories (servers).  The store, the Software Center, and other tools all access the same servers. They're all front ends to the same place, and the difference is only in their presentation to the user.  (Although you may find a few for-pay packages via Software Center.)Synaptic is comparable to Yumex and offers a faster and more fine-grained approach than the Software Center.

> 
...would also like to remove anything uneccessary... any reccomendations of bloatware that I can get rid of?

"Bloatware" is usually in the eye of the beholder.  If you want to clear some disk space, remove any packages you don't want to use.  But, be careful to avoid removing required packages:  If you don't know what it does, leave it. *Do not* remove files manually with the file manager or in a terminal outside your own home folder (and be careful there since that folder holds the user-specific config files).

I would avoid trying to disable services and startup apps unless you know what you're doing.  They're there for a reason.  The safest way to free memory, if memory is in short supply, is to use applications that consume less memory. I.e. at the moment here, Firefox with two tabs open is at 388 megs, and Dropbox -- currently inactive -- is at 68 megs.

---

### Post by Shugs81 on 2015-04-26
When I was talking about using the terminals it was more the rpm vs deb... for some reason I really struggled with sudo vs su and yum etc from command line...

I installed a fresh inhalation of xubuntu... nvidia drivers took 3 clicks to install... added Cairo dock as it looks pretty...

Really pleased with it so far... runs smooth and fast... even got manga studio to install first time!! 

And as to the bloat ware.. not really the right term... it's more a case of I'd install something which would have loads of dependencies and if I removed it it would either mess something up by taking one of their dependencies blah blah and end up with bits and pieces all over the place.. to be honest it's something that seems to have got better over the years but I still twitch thinking about trying to sort it all out...

I've always had windows as a fall back but I decided to put all my games on a different machine so that I could keep this one for work... then of course discover steam can stream games now... either way... mostly windows free now! Woop woop!

---

### Post by flaymond on 2015-04-27
[QUOTE=Shugs81]And as to the bloat ware.. not really the right term... it's more a case of I'd install something which would have loads of dependencies and if I removed it it would either mess something up by taking one of their dependencies blah blah and end up with bits and pieces all over the place.. to be honest it's something that seems to have got better over the years but I still twitch thinking about trying to sort it all out...[/QUOTE]

Sounds like you don't like unecessary softwares like GIMP and Pidgin, probably.

Well, you can remove the softwares from the computer, the depends will stay if another software depends on it. Like GCC and sudo.

If you don't like to remove default softwares in Ubuntu one-by-one, you can try Minimal installation. Here - [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Note: Make sure you got a basic shell usage and knowledge, since you might end up with just Text-based interface and need to install window manager and desktop enviroment from start, manually.

* Also, make sure you got the right filesytem for bootable device.

---

### Post by Shugs81 on 2015-04-27
see... when i first started messing with linux (fedora core 3!!) it just pulled all the dependancies off indescriminately... but that was a while ago... lol

gimp isn't unneccesary either... though i need to get the right plug ins... Manga studio doesnt work yet...something wierd is going on when i try to use it with the wacom... but thats another thread!!

---

### Post by wildmanne39 on 2015-04-27
If you truly want a minimal system it is best to do a minimal install, you will pull your hair out trying to remove things while trying not to break ubuntu, especially unity.

---

### Post by Bashing-om on 2015-04-27
@Shugs81; My 2 pounds worth;

> **Wild Man said:**
> If you truly want a minimal system it is best to do a minimal install, you will pull your hair out trying to remove things while trying not to break ubuntu, especially unity.


I am an advocate of the "minimal install" .
If you know what you want, and have some knowledge of the command line and some small amount of knowledge about ubunu's package management system -> it is pretty easy to do.

It is a core install .. all you have is the minimum to boot the kernel, and limited networking; from there you add what you want and only what you want.
I find it to be very fast and very flexible .

[INDENT][INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by yetimon_64 on 2015-04-27
> **Wild Man said:**
> If you truly want a minimal system it is best to do a minimal install, you will pull your hair out trying to remove things while trying not to break ubuntu, especially unity.

Yes, I agree, the minimal installer is a great start off point for custom Ubuntu installs. I have done a few over the years usually with the xubuntu desktop package, some were multi DE builds mostly gnome/xfce and no unity etc.

One helpful script/technique for minimal installs I've used in the past with Ubuntu minimal is at (perfectminimal script) : [[COLOR=#0000ff]--this link--.[/COLOR]]("http://andyduffell.com/techblog/?p=689")

---

### Post by Mark_McDonald on 2015-04-28
> **Shugs81 said:**
> When I was talking about using the terminals it was more the rpm vs deb... for some reason I really struggled with sudo vs su and yum etc from command line...

I installed a fresh inhalation of xubuntu... nvidia drivers took 3 clicks to install... added Cairo dock as it looks pretty...

Really pleased with it so far... runs smooth and fast... even got manga studio to install first time!! 

And as to the bloat ware.. not really the right term... it's more a case of I'd install something which would have loads of dependencies and if I removed it it would either mess something up by taking one of their dependencies blah blah and end up with bits and pieces all over the place.. to be honest it's something that seems to have got better over the years but I still twitch thinking about trying to sort it all out...

I've always had windows as a fall back but I decided to put all my games on a different machine so that I could keep this one for work... then of course discover steam can stream games now... either way... mostly windows free now! Woop woop!

Well I am a complete newbie for sure. But I tried Ubutnu and Xubuntu, I like X better. Why, well I didnt like the left side bar thingy primarily. Hated to hover over that and go down to access other icons. Additionally Ubuntu crashed a lot of times, the reaso why....explained here....I was reminded I should install drivers onto my Dell Inspiron 1525 Laptop. Honestly everything is working fine on my machine. But every now and then, and its waaay less then it was with Ubuntu, with X, it will straight up and crash on me. No mouse movement, nothing. Let sit, come back to it.....nothing. I will install drivers, see what I need to install. But yeah, X didnt crash as much as Ubuntu.

---

