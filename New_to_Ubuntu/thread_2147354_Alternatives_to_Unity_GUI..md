---
title: "Alternatives to Unity GUI."
date: 2013-05-21
forum: New to Ubuntu
---

### Post by BuntuSmuntu on 2013-05-21
OK, so I'm pretty green.This is my first time trying Linux.  

First Impressions: The Unity GUI, while somewhat intuitive, is about exciting as watching paint dry. I wanted to change things and make it look like I want it to look, but there seems to be few settings or skinable features. There doesn't seem to be a way to create shortcuts on the desktop like Windows. Unity seems to want you to use Search every time you want to find an installed program.  And there are no gadgets or geewiz stuff to add to the desktop.  Granted, I understand Ubuntu and other Linux OS want to be lean and mean so they can run on the smallest to the largest computers, phones to server farms, but I have a pretty decent desktop machine with a great graphics card, plenty of ram and hard drive space, and I want to be able to skin the OS to look and do what I want.  I thought Linux would be more privy to the concept of skins and individualization.  But it seems to me a more rigid OS than even Windows.  

However, I know that Ubuntu and other Linux OS support shells and other GUI like KDE, Gnome, and the like. So my question is this: What is the most configurable, skinable, hopefully modular w/plugins, desktop shell out there? Something made for an advanced desktop machine and not a tablet or phone, something with a little more ummmph!

Thanks for any help!

---

### Post by lykwydchykyn on 2013-05-21
You want KDE.  Others are customizable, but not like KDE.

---

### Post by oldfred on 2013-05-21
Some examples.
 Amazing April Screenshots
[http://ubuntuforums.org/showthread.php?t=2131337](http://ubuntuforums.org/showthread.php?t=2131337)
Marvellous May Screenshot Thread
[http://ubuntuforums.org/showthread.php?t=2140890](http://ubuntuforums.org/showthread.php?t=2140890)

I just prefer gnome panel or fallback, but I do not customize it.

---

### Post by Impavidus on 2013-05-21
I think Unity/Gnome 3 is one of the less lean desktop environments for Ubuntu, but it has been designed with small screens and mobile devices in mind.

I use xfce (Xubuntu). Better configurable, less eyecandy, which I don't mind.

---

### Post by mike555 on 2013-05-21
+1 for Xubuntu with the XFCE desktop

---

### Post by craig10x on 2013-05-21
By the way, the whole idea behind the unity dock is to pin all your favorites and most used apps to the dock not the desktop...then you have easy 1 click access and rarely need to go into the search....perhaps you were unaware of that? You seem to think you have to bring everything up in the "dash" search...it's not highly customizable but you can auto hide, shrink the size of the icons and enable workspaces...

It's a more "mac-like" interface...so i gather you probably don't like macs....as suggested, kde would be for you...it's the closest to windows...or xubuntu as also mentioned...

I find unity very nice to work with (and reminds me of when i had a mac as this has the dock, global menu and search similiar to what mac calls "spotlight")
 
But then i am not a "customization maven" as some are here...so for me it's no biggie but perhaps for you it is...so try those two suggestions...

---

### Post by rallyemax on 2013-05-22
IMHO Ubuntu is great if you more or less like the way it comes. I suppose it's not quite "linuxy" in the sense that if you want to make more than trivial customizations or changes, it can often start failing in strange ways. And its forums are of very little help once you modify the canonical system beyond a certain threshold. In both of these ways, it's very much like MacOS, actually (hard to achieve the smoothness of the "standard" install after customization, hard to get any useful feedback on its forums).

If you want to change things around, or maybe you need/want to update some component of Ubuntu to a version more recent than 3 years removed from upstream, but still want stability, why don't you try Debian? Debian is the foundation underneath Ubuntu. Debian implements upstream updates roughly every six months (other than security updates, which are continuous), Ubuntu then packages them after further delay into its own versions -- and once you start compiling software on your machine, you'll realize that Ubuntu's outdated packages are a very real and annoying concern (dependency hell). You can stay relatively stable and yet get even closer to the bleeding edge with Debian's "unstable" flavor (also called "sid"), which is actually one of the more stable distros I've ever run. Debian unstable keeps much more up-to-date (everything from the kernel version to all packages installed from its huge binary repository) than the stable Debian releases, but the way the development cycle works, you periodically get frozen from new updates even while running the unstable flavor.

And if you really want to have full control of your system without having the exercise of that control breaking things, but you are willing to pay the price of learning Linux on a more fundamental level, give Arch a try. You'll be on the bleeding edge of every Linux project, from the kernel to your GUI's calculator program. Sometimes updates will bonk your system until you fix it, though in my experience such bonks are usually partial and your system will still boot and run, though some functionality will be missing unless you downgrade (last resort because it's quite unexciting) or figure out how to make things happy.

Finally, if you want to compile everything yourself, there is Gentoo.

Interestingly, the level of support (in official Wikis and forums) is better in Debian than in Ubuntu, and better in Arch than either Debian or Ubuntu. Gentoo can be hit or miss -- I don't even run Gentoo, but I've encountered solutions in Gentoo's forums on many occasions. The Arch Wiki and forums absolutely rock, they're at the point where if you know more than a trivial amount about computers and have the patience and intellectual horsepower to approach problems analytically rather than just trying random stuff you've seen on the 'net, the level of support exceeds not only other Linux distros, but also MacOS and Microsoft documentation and official forums.

Don't abandon Ubuntu just yet. But carve out a partition on your system (I really recommend full installs for testing out various Linux distros over any LiveUSB rubbish...all you need is a 10GB partition on your system HD, and you can try new distros at will, and that space will let you temporarily live in a new distro for longer than you anticipated if you happen to like it), and try out the other options.

---

### Post by claracc on 2013-05-22
You can install gnome-fallback in order to have a "classic" desktop.

You can also customize it.

Tips an tricks in this thread: [http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

### Post by HermanAB on 2013-05-22
KDE of course.  I like my revolving desktop cube and wobbly windows...

---

### Post by mastablasta on 2013-05-22
KDE is really customizable out of the box. XFCE comes to a very close second as it is easy to customize it.

---

### Post by monkeybrain2012 on 2013-05-22
Maybe you should be more specific about what kind of customization you want. Some are not possible in Unity (like moving the dock), but others can be done (there are many options in ccsm) I think there is only so much time you want to spend on customizing your desktop :) I used to spend more time doing that in gnome 2 since it was butt ugly out of the box. Unity pretty much has everything I need. In KDE I did a bit but mostly to activate functions that I can do with Compiz and Unity like rotating desktop,window and desktop switchers, installing homerun which kind of looks like the dash and enabling some keyboard shortcuts. I am sure there are other options I miss (kde is full of options, to the point of confusing :) ) but I am doing fine without knowing them, so why bother? Any de would allow you to put applets, change wall paper, themes and icons.

---

### Post by fantab on 2013-05-22
> **BuntuSmuntu said:**
> OK, so I'm pretty green.This is my first time trying Linux.  

First Impressions: The Unity GUI, while somewhat intuitive, is about exciting as watching paint dry. I wanted to change things and make it look like I want it to look, but there seems to be few settings or skinable features. There doesn't seem to be a way to create shortcuts on the desktop like Windows. Unity seems to want you to use Search every time you want to find an installed program.  And there are no gadgets or geewiz stuff to add to the desktop.  Granted, I understand Ubuntu and other Linux OS want to be lean and mean so they can run on the smallest to the largest computers, phones to server farms, but I have a pretty decent desktop machine with a great graphics card, plenty of ram and hard drive space, and I want to be able to skin the OS to look and do what I want.  I thought Linux would be more privy to the concept of skins and individualization.  But it seems to me a more rigid OS than even Windows.  

However, I know that Ubuntu and other Linux OS support shells and other GUI like KDE, Gnome, and the like. So my question is this: What is the most configurable, skinable, hopefully modular w/plugins, desktop shell out there? Something made for an advanced desktop machine and not a tablet or phone, something with a little more ummmph!

What do you want to customize? There will always be certain limitations with every desktop interface out there. Unity has its share of limitations but it can be customized. There are tweak-tools avalable for newbs to help them customize their desktops. To customize Unity you have 'Unsettings", "Myunity", Ubuntu-Tweak. Then there is 'compiz-config-settings manager' and 'dconf-editor' for more experienced.

So if you will be explicit about what you want to customize we can help. By the way, you can have icons on desktop in Unity, but, as mentioned, with Untiy-launcher, its kind of overkill. There are Unity themes and Gtk themes to add different themes than those shipped wtih Ubuntu...

---

### Post by zombifier25 on 2013-05-22
You mentioned desktop gadgets. Those are DE-independent and you can add whatever gadgets to whatever desktops. KDE has its own, built-in plasma-widgets. For Unity and others, there's Screenlets (which are a collection of widgets that you can put on the desktop. Pretty straightforward) or Conky (which requires you to write your own configs. There are a lot of conky configs on the Internet for you to try)

With that being said, Unity is not the DE you are looking for if you want to customize your desktop to the extreme. Others, like KDE, Xfce, etc. are more flexible. Refer to the linked screenshot thread for some examples from our very own forum members.

---

