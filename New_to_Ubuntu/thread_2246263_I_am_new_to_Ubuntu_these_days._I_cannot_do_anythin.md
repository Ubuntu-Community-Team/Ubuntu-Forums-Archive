---
title: "I am new to Ubuntu *these* days. I cannot do anything with it."
date: 2014-09-29
forum: New to Ubuntu
---

### Post by morthawt on 2014-09-29
This interface is truly terrible. I cannot find any tools at all except for a handful which are pinned on this toolbar on the left. I used to be pretty decent with Ubuntu, not an expert though because I am a Windows techie not linux, but I knew enough to get the job done. Now with the new version I have had to give up and use Lubuntu.

Is there a setting or command that we can just get a **normal **ubuntu interface instead of this linux version of Windows 8's failed interface? I was googling on this and finding strange guides where you need to do all kinds of steps but then some people say Ubuntu removed the ability to remove the new interface or something? I find this very disturbing if that is true. I hate it when an operating system developer just goes and changes everything when people are used to how a system works. What do I need to do?

---

### Post by robin_de_bruin on 2014-09-29
i would recommend [http://lubuntu.net/](http://lubuntu.net/)

---

### Post by morthawt on 2014-09-29
As I said in my post, I had to resort to using Lubuntu. But I would like to use Ubuntu since when ever anyone has asked me what linux they should try out I recommend Ubuntu. But now with this change in the interface, unless there is an easy setting or something, I cannot any longer send people to Ubuntu because it has been crippled to the point of being useless.

---

### Post by robin_de_bruin on 2014-09-29
if you are using lubuntu then you are just using ubuntu with LXDE as a user interface 
hence the name lubuntu LXDE + ubuntu

---

### Post by Lars Noodén on 2014-09-29
You could try using XFCE4, which is another desktop environment.  You can find it in the repositories.  Once it is installed, log out, click on the ubuntu circle near your login name and choose XFCE.  Or if you want to wipe everything, you can install [Xubuntu](http://xubuntu.org/)

As far as the dock goes, many also like cairo-dock.

---

### Post by Morbius1 on 2014-09-29
How about Xubuntu: "Ubuntu with half the fat" [SUP]TM[/SUP]

More evolved than LXDE but still designed for the desktop.

---

### Post by Rob Sayer on 2014-09-29
I don't like the Unity DE either but it is *not* a copy of Windows 8.  It's older.

And if you don't like Unity, you have other alternatives than LXDE.

---

### Post by vasa1 on 2014-09-29
> **morthawt said:**
> ...
Is there a setting or command that we can just get a **normal **ubuntu interface ... What do I need to do?
The command would be ```
sudo apt-get install suitable_desktop_environment
```Most of these are in the standard repository. And things like MATE can be currently installed via a ppa. Lots of choice :)

---

### Post by morthawt on 2014-09-29
So is there no easy way for an end user to ditch the new interface? Anything I have seen requires typing commands and modifying files. I am hesitant to go through all that work and the average computer users I know would never even install it to begin with if I had tried Ubuntu sooner to let them know not to use it. So far the easiest suggestions have been to use a different flavour of Ubuntu. Why have Ubuntu not provided an ability to alter the interface to one that is a normal interface to get away with that useless one? There are no menus or anything that show you what you have accessible except for a handful of icons. It is dreadful and I quite frankly am at a loss why they did this. I have seen complaints about this dating back several versions. It has been a long time since I used ubuntu as a desktop OS because usually I deal with the server version on my VPS.

---

### Post by Lars Noodén on 2014-09-29
You can run Synaptic and find the package LXDE or XFCE4.   Or you can find it in the software center.  Either one will install with a click or two.  Give one a try, you'll find it easy.  I'd recommend Synaptic.  

People will often present solutions to run in the terminal because 1) the shell is unambigous, 2) being text-based it can be described easily in a text-based forum, 3) it's what is most powerful and flexible, and experienced users gravitate to  it.   However, graphical interfaces to the package manager have been provided and they are the Software Center and Synaptic, which are two ways to do the same thing. 

Once you have the new desktop environment, you'll have to log out, select the new DE, and log back in again to make the switch.  That's all done graphically.

---

### Post by morthawt on 2014-09-29
So you just install the new interface and then you get the option to choose it before you login?

---

### Post by ajgreeny on 2014-09-29
> **morthawt said:**
> So you just install the new interface and then you get the option to choose it before you login?

Yes.

Xubuntu is my favourite, but you can try Mate, Cinnamon, KDE, LXDE (lubuntu-desktop), and so on, and so on.

That's the beauty of Linux; so much choice, unlike Windows which usually gives you a choice of - well, actually no choice at all, or not without installing some other utility, which is what you seem to be complaining about having to do in Ubuntu.

---

### Post by ian-weisser on 2014-09-29
> **morthawt said:**
> So is there no easy way for an end user to ditch the new interface?

If you don't like Unity, then go into Software Center and install a desktop environment you do like.
One click to open Software Center.
A second click to install an entire integrated desktop environment.
LXDE, XFCE, KDE, Mate Gnome, Unity. And others via PPA. Your choice. Two clicks and a search box.

I think two clicks and a search box is pretty darned easy.



> **morthawt said:**
> Anything I have seen requires typing commands and modifying files. I am hesitant to go through all that work

Vasa1's post was exactly one easy command, and zero modifiying files.
And it works, too.
Try it. One command.


> **morthawt said:**
> Why have Ubuntu not provided an ability to alter the interface to one that is a normal interface to get away with that useless one? 

We did.

Okay, we get it. You don't like Unity. You will never like Unity. You would rather be pecked to death by ducks than forced to use Unity. You like to be rude about it.
Nobody is forcing you to use Unity. We don't care if you use Unity or not.
Install ANY of the SIX supported desktop environments.
Two clicks and a search box. Or one command.

---

### Post by MartyBuntu on 2014-09-29
I don't understand. You're already using the LXDE desktop as you stated in your first post (using Lubuntu).

You don't like Unity, so you chose LXDE...is there a question there somewhere?

---

### Post by craig10x on 2014-09-29
Unity is just a dock...you know, like the apple computers have...and mac fans love the dock...it's just that it is on the left instead of on the bottom but works in the same way...

To add apps to it you just open them from the dash search on top and that they appear in the unity dock and you right click to lock them in....You put your favorites and most used apps on it for quick "1 click" access and for apps you don't use frequently, you just find them in dash search and click them to open...And you can also remove any you don't want on the unity dock...After using it for about 2 weeks you might get to like it like most of us do here...but sounds to me like you have a closed mind about giving it a fair chance, so your best bet is to install xubuntu, kubuntu or lubuntu, then...

You can think of Unity as a short cuts taskbar...because that is basically what a dock is...and it ain't nothing like windows 8, as you compared it to..FAR FAR more intuitive...

---

### Post by morthawt on 2014-09-29
> **craig10x said:**
> Unity is just a dock...you know, like the apple computers have...and mac fans love the dock...it's just that it is on the left instead of on the bottom but works in the same way...
To add apps to it you just open them from the dash search on top and that they appear in the unity dock and you right click to lock them in....You put your favorites and most used apps on it for quick "1 click" access and for apps you don't use frequently, you just find them in dash search and click them to open...After using it for about 2 weeks you might get to like it like most of us do here...but sounds to me like you have a closed mind about giving it a fair chance, to your best bet is to install xubuntu, kubuntu or lubuntu, then...

You can think of Unity as a short cuts taskbar...because that is basically what a dock is...and it ain't nothing like windows 8, as you compared it to..FAR FAR more intuitive...
Well if it is just a dock, where is the normal button you click to being up the usual menu with access to all the programs like it was previous to this unity? I do not care if the dock is there as long as the normal functionality is there.

---

### Post by craig10x on 2014-09-29
You mean a fan-out menu?...what's so wonderful about that?..then you have to pivot through a whole list to find the app you want to open...Why do you need to see a whole list...you know what you run...

On my Unity Dock i have: dash search, firefox, libre office, ubuntu software center, system settings, chrome, pidgin, sabnzbd (for download nzb files), psensor (temp monitor), system monitor, rhythmbox, vlc media player, calculator, screenshot, brasero disc burner, avidemux and workspaces....That's everything i normally might want to get at...for terminal, i bring it up in dash search...if i want the updater or package manager, ditto...

And that's about it....so, why would i want to look at a fan out menu of apps?  what a waste of time!  Also, i reduced the size of the unity bar to 38 pixels and auto hide (which is in the system settings)...

---

### Post by morthawt on 2014-09-29
> **craig10x said:**
> Why do you need to see a whole list...you know what you run...
Oh I know do I? Do new users of Ubuntu know what they run? With the old interface I could start fresh having never used linux before and know how to get to messaging programs I have never even heard of, games, other utilities I have never heard of. What do I get now? Office package and maybe a couple of other things. Where is everything else? I do not see any menus showing a nice list that is easy to see everything you have.

---

### Post by Vladlenin5000 on 2014-09-29
Everything else is where everything else plus what you already mentioned always was. You have an Apps lens showing you ALL installed apps and allows filtering also. Everything you have in the idiotic, non-productive anachronistic fan-out menu is there in a nice, modern SINGLE view. Plus, you can search any app just by typing 2-3 letters -> Much faster than drilling down the old menu. 
EVERYBODY, from Apple to Microsoft (late & flawed as usual but now in the right track), understood a long time ago the focus should be in the user's experience, ie, user's data and apps and how to access both seamlessly. Ubuntu with Unity achieved this first and better than anyone else.

Your issue - and many other people's -  seems to be that you're crystallized in the 90's. No wonder the Lubuntu's aesthetics appeals to you. Now, how about dusting those old Nirvana CDs (or the tapes you most likely still have) and rock on? :guitar:

---

### Post by craig10x on 2014-09-29
And if you are that stuck in the 90's and must have the old fan out menu, it's very simple to add on....just install Classic Menu Indicator from the ubuntu software center...then there will be an icon on the right side of the top panel and when you click it, the fan menu with all apps will drop down:
[http://www.howtogeek.com/189929/how-to-install-and-launch-the-classic-gnome-menu-in-ubuntu-14.04/](http://www.howtogeek.com/189929/how-to-install-and-launch-the-classic-gnome-menu-in-ubuntu-14.04/)

Totally unnecessary, but if it makes you happy...there you go...problems solved :D

By the way, regarding your comment, do new users know what they run? well, perhaps not all but for example, let's say a new user wants to know if an app is installed already that will take a screenshot?
If he types that word in the search he will see ...oh, yes, there it is!   Or wants to burn a disc...type disc burner and he will see brasero...etc. etc...

But if you prefer to drudge through the old style fan menu, there is your solution...

---

### Post by QIII on 2014-09-29
Several suggestions were made for more traditional style DEs instead of Unity.

Since this seems to have devolved into a chance to prod the OP...

Closed.

---

