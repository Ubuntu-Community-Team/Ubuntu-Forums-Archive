---
title: "What are the dissadvantages of Maverick Meerkat right now?"
date: 2010-05-17
forum: Recurring Discussions
---

### Post by aviramof on 2010-05-17
Should i download and install Maverick Meerkat right now what are the problems i should face? did grub 2 install process is better now? 
is there an fglrx driver now? how about kernel what kernel is there right now? and what about plymouth and all sort of other things like compiz 
should they work better now? and what about file manager is there any hope of a file manager better then the current nautilus version?
 
Because too be honest i wasn't thrilled with Final lucid lynx it still had problems with plymouth and fglrx still had problems with installing 
grub 2 on my computer,ubiquity process took ages to install the dvd version(about 40 minutes or more) fglrx driver did not had support 
with newer kernels other then 2.6.32.
 
And frankly the biggest problem i had wi is how to manage files with the current files managers you have there are so limited compare to 
windows 7 file manager,for instance you can't arrange pictures according to dimenssions and etc and all sort of other options that you can 
see in the attached picture i just felt that it's too limited for me. 
 
And i also didn't liked that there are not enaf gui's support you relly too much on the terminal you should improve the gui's part if you want to attract more people to use linux.

---

### Post by philinux on 2010-05-17
Eh!

The problem is that Maverick is still lucid just now apart from a few upgrades.

See the release schedule sticky.

---

### Post by DougieFresh4U on 2010-05-17
> **aviramof said:**
> Should i download and install Maverick Meerkat 
 

You can not 'download' Maverick yet. Has to be 'dist-upgrade' from Lucid at this stage of the game  :P

---

### Post by lykwydchykyn on 2010-05-17
> **aviramof said:**
> Should i download and install Maverick Meerkat right now what are the problems i should face? 

No.  Especially since you give the impression that you're fairly new at this.  Maverick development has just started, and it's going to go to all heck and back before it's done.
> 
 and what about file manager is there any hope of a file manager better then the current nautilus version?
 
I doubt Nautilus is going to make great gains in the next six months, unless Maverick goes to GNOME 3.  Nautilus isn't the only file manager on Linux, though.  Have you tried Kubuntu?  KDE may be more to your liking.

> 
And frankly the biggest problem i had wi is how to manage files with the current files managers you have there are so limited compare to 
windows 7 file manager,for instance you can't arrange pictures according to dimenssions and etc and all sort of other options that you can 
see in the attached picture i just felt that it's too limited for me. 

I don't know if there is a file manager available that will do this, but there are a number of photo organizers.  As I mentioned, you might like KDE because it has a couple of file managers that are both very powerful.
 
> 
And i also didn't liked that there are not enaf gui's support you relly too much on the terminal you should improve the gui's part if you want to attract more people to use linux.

What did you have to do on the command line?

---

### Post by aviramof on 2010-05-17
I am not so new to linux but i stopped using it because i felt that i can't continue to use it's uncomftarble file managers it just wasn't as comftarble as windows 7 file manager
and at times i was forced to boot back to windows 7 to do spesifie things like sort pictures according to dimenssions and etc.
 
and as for the terminal i did a lot of things there that i didn't had a problem with them but the biggest problem i had was that i was not able to delete files 
from ubuntu partition except from the home folder without using commands like sudo rm -rf and etc because of strange permissions problems despite the 
fact that i am the sole administrator i discoverd that taking owenrwhip here is very hard or impossible via nautilues and that was incredibly annoying.
 
And like i said this is pretty much why i stopped using ubuntu at all just because of the bad file manager and the fact that is not much i can do to improve it and i didn't 
liked other files manager i tried either maybe dolphine would be better when i try it in the future most likely only in july when 10.4.1 version be released.

---

### Post by ranch hand on 2010-05-17
That is very strange.  I have no trouble at all in deleting anything from my installs from nautilus, even in other installations.

I can delete things that I shouldn't even think of deleting.  I have gotten over that but it was no problem to do it.

I suspect that you have nautilus configured in a new and different way.  I would go to synaptic and purge it and reinstall it.  Do not mess with the settings and read the man page.

---

### Post by taavikko on 2010-05-17
> **ranch hand said:**
> 

I suspect that you have nautilus configured in a new and different way.  I would go to synaptic and purge it and reinstall it.  Do not mess with the settings and read the man page.

Removing nautilus (or any other app) still leaves user specific config files to $HOME
And thus reinstalling nautilus once again, what happens...

Nautilus has it's pro's & con's...

People who might be thinking of using devel version of entire system, should be little more experienced in using it than average Joe.

So even though there's no "disadvantages" yet, there will be!

---

### Post by ranch hand on 2010-05-17
> **taavikko said:**
> Removing nautilus (or any other app) still leaves user specific config files to $HOME
And thus reinstalling nautilus once again, what happens...

Nautilus has it's pro's & con's...

People who might be thinking of using devel version of entire system, should be little more experienced in using it than average Joe.

So even though there's no "disadvantages" yet, there will be!
Well, you can decrease my ignorance by telling me if purging gets rid of those .whatever  files.

I take it from what you say that it does not.

---

### Post by Arla on 2010-05-17
In a word, any/all problems.

Maverick is up for testing, so right now, a whole world of problems could be waiting, your system could be hosed anytime you run update, it's part of the fun of testing in the development cycle.

---

### Post by taavikko on 2010-05-17
> **ranch hand said:**
> Well, you can decrease my ignorance by telling me if purging gets rid of those .whatever  files.

I take it from what you say that it does not.

No it doesn't.
It removes the system-wide settings, not the ones users have made.

This is because if user decides to reinstall the application, 
it will have the desired settings.

if wishing to revert to default settings, removing the right .* will suffice.

---

### Post by ranch hand on 2010-05-17
Ah, I am now a little more educated, thanks.

That also sounds a lot easier and quicker.

---

### Post by philinux on 2010-05-17
I don't think the OP got the point of post #2.

---

### Post by lykwydchykyn on 2010-05-17
> **aviramof said:**
> 
and as for the terminal i did a lot of things there that i didn't had a problem with them but the biggest problem i had was that i was not able to delete files 
from ubuntu partition **except from the home folder** without using commands like sudo rm -rf and etc because of strange permissions problems despite the 
fact that i am the sole administrator i discoverd that taking owenrwhip here is very hard or impossible via nautilues and that was incredibly annoying.


Your problem is not the file manager, but a lack of understanding (or just dislike) of basic Linux/Unix security.  Deleting things outside of your home folder takes root privileges.  If you want to do this with Nautilus, you'll have to run it as root.

There may be an easy way to do this in GNOME, or you may have to make a custom shortcut to run "gksudo nautilus".  I don't use GNOME so I don't know off hand.

---

### Post by ronacc on 2010-05-17
gksudo nautilus is the correct way to run nautilus with root privileges .

but actualy the more I hear from this guy the more he sounds like a troll . If he is so dissapointed with ubuntu what is he doing here ?

---

### Post by kansasnoob on 2010-05-17
Perhaps I'm being the "turd in the punch bowl" here, but I recall aviramof during Lucid development complaining to no end! Requests regarding grub2 boot experiences were especially common.

I'd say this: design decisions are not made on the forums -PERIOD-. You can only effect the direction in which Ubuntu goes by getting involved in other ways, as you can see here I'm still learning:

[http://ubuntuforums.org/showthread.php?t=1482615](http://ubuntuforums.org/showthread.php?t=1482615)

I follow the Ayatana list and some of the suggestions repulse me, but that is one of the places where design decisions are made!

If, as you say, "i stopped using it because i felt that i can't continue to use it's uncomftarble file managers it just wasn't as comftarble as windows 7 file manager", I think you should forget about Ubuntu!

**I can NOT imagine us trying to be more like Win 7!**

---

### Post by screaminj3sus on 2010-05-17
> **kansasnoob said:**
> Perhaps I'm being the "turd in the punch bowl" here, but I recall aviramof during Lucid development complaining to no end! Requests regarding grub2 boot experiences were especially common.

I'd say this: design decisions are not made on the forums -PERIOD-. You can only effect the direction in which Ubuntu goes by getting involved in other ways, as you can see here I'm still learning:

[http://ubuntuforums.org/showthread.php?t=1482615](http://ubuntuforums.org/showthread.php?t=1482615)

I follow the Ayatana list and some of the suggestions repulse me, but that is one of the places where design decisions are made!

If, as you say, "i stopped using it because i felt that i can't continue to use it's uncomftarble file managers it just wasn't as comftarble as windows 7 file manager", I think you should forget about Ubuntu!

**I can NOT imagine us trying to be more like Win 7!**

To be fair I think windows explorer is a lot better than nautilus :P

@ OP I would stick with lucid and jump in to maverick at beta 1 where its not so insanely unstable. The early stages are boring and full of breakage :)

---

### Post by donniezazen on 2010-05-17
Just wait a few days Maverick is going to get dirty.

---

### Post by ronacc on 2010-05-17
> **screaminj3sus said:**
> To be fair I think windows explorer is a lot better than nautilus :P


no file manager in windows is as good as the sorriest file manager in linux , There are files in windows that you CANNOT DELETE or MODIFY with any file manager or even open to look at . Therefore no file manager in window even deserves the name since it cannot manage files .

---

### Post by anders_c_ on 2010-05-17
I think win7 is a decent OS overall, but i simply hate the file manager...so i guess we're all different :)

---

### Post by nanog on 2010-05-17
Theoretically, one could install headless win7 in vbox/kvm, mount ubuntu filesystem as root in win7 via dokan sshfs, make windows explorer location a startup item, copy/create windows explorer icon, and add gnome menu with appropriate shell command. Probably not a good idea though.

---

### Post by MacUntu on 2010-05-17
Nautilus stinks - we all know it. Sadly GNOME devs will never abandon it. /rant

Try GNOME Commander or Krusader for file managing and Dolphin if you are more into file browsing.

---

### Post by ronacc on 2010-05-17
krusader is one of the first apps I add to a fresh install along with K3B .

---

### Post by screaminj3sus on 2010-05-17
> **ronacc said:**
> no file manager in windows is as good as the sorriest file manager in linux , There are files in windows that you CANNOT DELETE or MODIFY with any file manager or even open to look at . Therefore no file manager in window even deserves the name since it cannot manage files .

Thats just a ridiculous argument.

---

### Post by ronacc on 2010-05-17
what is ridiculous about the (true) statement that file managers under windows cannot manage some of the files on the system ?

---

### Post by screaminj3sus on 2010-05-17
I was mostly criticizing the incredibly hyperbolic nature of the post that all windows file managers are "worthless" because of that one limitation. Windows users dont spend all day modifying critical system files, in fact that limitation is there for a reason.

I actually think windows explorer handles dealing with files needing admin access much better than linux file managers in some ways. For example:

You want to copy a file to program files, which needs admin access. You copy, hit paste and it prompts for permission and you click yes.

In linux? it wont even let you! you have to go to the terminal and open the file manager as admin, and also if you have one nautilus window as admin you cant copy files from that to the admin one which is just annoying from a usability point of view.

---

### Post by cecilpierce on 2010-05-17
> **ronacc said:**
> krusader is one of the first apps I add to a fresh install along with K3B .

Me to but I think midnight commander is a little simpler to use, when I ran windows I used ZTree, it would do everything you should'nt do !

---

### Post by ronacc on 2010-05-17
yes MC is another one I install on first boot .

---

### Post by qamelian on 2010-05-17
> **MacUntu said:**
> Nautilus stinks - we all know it. Sadly GNOME devs will never abandon it. /rant
I love when people make blanket statements like this. I don't know any such thing. Nautilus does exactly what I need a file manager to do and even a little bit more. I don't think it stinks at all.

---

### Post by MacUntu on 2010-05-17
> **qamelian said:**
> I love when people make blanket statements like this.

Rants tend to be objective and full of well-founded arguments. ;)

---

### Post by Ibidem on 2010-05-17
PcmanFM provides a few of the things I see mentioned here, to some degree:
1.  Open current folder as root (also in xfe)
2.  Copy/paste to & from root file manager
(Also open in terminal, and a few other things I like)

---

### Post by aviramof on 2010-05-18
> **qamelian said:**
> I love when people make blanket statements like this. I don't know any such thing. Nautilus does exactly what I need a file manager to do and even a little bit more. I don't think it stinks at all.
 
If your happy with nautilus that mean that you are not doing enaf with it for instance like i said go to your near pictures folder and try to arrange the pictures by dimmessions and see if you can do it. and how about arrange by company or event or album or artist or owner or file version or video compression or any of the dozens of options windows 7 can sort file accroding to them as you can see in the attach image just look at the size of the list of options that i can sort file according to this variables.
 
And as for PcmanFM i have tried lubuntu and xubuntu for a short time but unfortunally 
there RTL support is not as good as the original ubuntu i also tried kubuntu-desktop for
a brief moment before it crashed my system at that time maybe i would try it again when 10.04.1 be released.

---

### Post by Sophont on 2010-05-18
I get that arranging your pictures with a file manager is very important to you, but that is a fairly special purpose feature - especially for a general purpose file manager.

I'm certainly not against Nautilus being able to do that (assuming it doesn't "cost" too much in form of bugs and bloat).

But I never missed that feature and I bet that most users don't think that sorting by picture dimensions is a very important feature for a file manager.

Nautilus does well as a file manager for what I want from it.
And unlike the Windows Explorer it doesn't stop to take a break all the time.
For the (IMHO) main uses of a file manager Nautilus does copying/moving/deleting/etc - even thumbnailing - well and fast. In my experience much faster than WExplorer that I have to use a lot every day and always wish it would be more like Nautilus.

No idea why some people get worked up about Nautilus. It manages my files very well.

---

### Post by philinux on 2010-05-18
Thread moved to Recurring Discussions.

---

### Post by qamelian on 2010-05-18
> **aviramof said:**
> If your happy with nautilus that mean that you are not doing enaf with it for instance like i said go to your near pictures folder and try to arrange the pictures by dimmessions and see if you can do it. and how about arrange by company or event or album or artist or owner or file version or video compression or any of the dozens of options windows 7 can sort file accroding to them as you can see in the attach image just look at the size of the list of options that i can sort file according to this variables.
 
Sorry, but I don't agree. In my opinion, the things you describe are not the domain of the file manager and should be handled by a separate image management/cataloging application. In fact, it appears that I dislike the file manager in Windows 7 for the same reasons you like it. If Nautilus was modified in the ways you want, I'm afraid I would stop using it and replace it with a file manager without what I consider inappropriate "bells & whistles". To each his own. 

By the way, I use Nautilus more than you seem to think. In fact, all ( and I do mean ALL) of the file management on my Win7 box is done across a network using Nautilus from my laptop.

---

### Post by MCVenom on 2010-05-18
Have you tried Konqueror? It's a file manager! It's a web browser! It has Google shortcuts! :p

Seriously, if Konqueror doesn't do it, that's saying something. We must be talking about a really extraneous feature here! :lolflag:

---

### Post by 10027586 on 2010-05-18
Lucid was released only a few weeks ago, so Maverick won't have much new just yet. Why? Well most of the software comes from upstream, Canonical (Ubuntu) just packages it nicely so it's easy for us to use.

> is there an fglrx driver now?
ATI is always some way behind (ask Arch users about the trouble it gives them when Arch users always have bleeding-edge stuff). Canonical has no control over that. As it is the version used in Lucid is a preview version released early as ATI have only just begun supporting the newest version of Xorg. Don't like it? Try the open drivers, they're actually very good these days. See the "Ati coming of age" thread.

> how about kernel what kernel is there right now?
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/) knock yourself out. That's the latest version straight from Mr Torvalds, and you can have it in Lucid. Grab linuxheaders generic, linuxheaders all and linuximage generic either x86 or x64 depending on whether you went 32-bit or 64-bit. Once done, install them all.

> plymouth and all sort of other things like compiz should they work better now?
What's wrong with them exactly? They work fine here.

> is there any hope of a file manager better then the current nautilus  version?
What do you consider better? It's a file manager, it does a good job. You can resize individual icons on desktop (can't in Win7). You have tabbed file browsing (can't in Win7). You have split-pane viewing (stolen from Dolphin). It's easy to use, could be a little lighter (in which case grab pcmanfm if you want that). It's linux. Don't like one component? Swap it out for a better one.

> CLI/GUI
What exactly are you trying to do which requires the terminal? The terminal isn't needed for most tasks, but does make a wonderful tool for tech support on those occasions when things go wrong. The reason is that it offers precision and it's easy to follow instructions, after all you're just typing, no-one has to explain what a particular icon looks like (which may have moved or changed according to your theme or customisation). The terminal is wonderful, embrace it.

---

### Post by Chame_Wizard on 2010-05-18
Dolphin and Krusader FTW.:guitar:

---

### Post by WinterRain on 2010-05-18
> **aviramof said:**
> 
And i also didn't liked that there are not enaf gui's support you relly too much on the terminal you should improve the gui's part if you want to attract more people to use linux.

I use the terminal because I want to, not because I have to. My GF uses ubuntu full time, and has never had to use the terminal. Heck, she doesn't even know what it is.

---

### Post by aviramof on 2010-05-19
I don't have problems using terminal i just don't like it when there is no other gui option except using the terminal and i consider my self an advance user so i think 
my needs are a lot more complicated then what your GF might be doing with ubuntu.

---

### Post by Elfy on 2010-05-19
@ aviramof - Thread closed - this has turned into just another one fo your rants against linux file managers.

---

