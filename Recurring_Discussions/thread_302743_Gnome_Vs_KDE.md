---
title: "Gnome Vs KDE"
date: 2006-11-19
forum: Recurring Discussions
---

### Post by stoer on 2006-11-19
Hi all,
(just read through this all - sorry for the longwinded start, my question is at the end ;) )

I've been using Ubuntu since the summer, dual booting on my laptop (xp-pro).
40 gb for win-xp, 30 gb for Ubuntu and a fat32 shared partition 10 gb.

I've been 'playing' with computers since the Sinclair zx spectrum, BBC Acorn - so for quite some time.  I've done the usual win 95,98,xp route and was generally unhappy with the amount of time i spent 'repairing' and reinstalling my system (to be honest, most problems were caused through my own curiosity and the urge to 'tweak' and 'tinker'.)

I experimented with the ubuntu live cd, just to see if there were any issues eg. wireless, graphics etc. and because there weren't, i bit the bullet and installed.  I have encountered very little in the way of problems and am totally impressed by what i have encountered through day to day usage.  I'll just add a little emphasis to that, I AM TOTALLY IMPRESSED!!!
There have, of course, been countless problems.  It's a much steeper learning curve here in Linux land and issues such as the correct installation of graphics cards (ATI mobility 9700), 'Mounting drives', installing 'Multimedia-compatability' are NOT intuative.
But, with a great deal of reading, forum trawling and with the help of many, many helpfull and friendly people here in the Ubuntu community i now have a working, stable and very useable system. Thank you.

I still have windows running alongside, why? Kids that love thier games, that's why.  For myself, i'm still looking for a way of replacing 'Newsleecher' a Usenet binary reader with probably the best,quickest and easiest search engine that there is.
My current computer use can be summed up very easily.
Gaming, internet, Light office work (letter writing and spread sheets), Photo collection (digital camera and video, i hope eventually to do some digital video stuff), and 'Downloading' (Usenet - film and music) cd and dvd burning.
The computer is shared with my wife and my son (4 yrs) and soon also my 1 year old daughter.

So, here's the nub, at last!   ***(QUESTION)***
I started out using Ubuntu with Gnome, no special reason, just happened that way.  I see alot of interesting programs however that are to find in the KDE environment. Some of these work well under Gnome and some don't.  
eg K3b and K9copy, home finance etc - K3b works without a hitch but K9copy has the occaisional temper tantrum.  Through all my trawling i've seen a number of interesting KDE applications and now i'm beggining to wonder if the grass isn't greener...
I'd like to give KDE a try.  I'd like to install it alongside Gnome, i know that this is easy to do, but...
I need to install it in such a way that if it dissapoints or doesn't offer me a better alternative to Gnome that i can Uninstall it EASILY and without damaging my present setup and i don't know how to do this.
Will installing KDE cost me alot of space? and will i need to go through the whole driver install route again? (ATI card).
Any KDE users out there that want to convince me that this is worth the effort???
Again thanking you all for making this not only a great OS but also a great experience.
Cheers!

---

### Post by Perfect Storm on 2006-11-19
The easeist way:

```
sudo aptitude install kubuntu-desktop
```

then logout and at the login screen choose session and pick KDE.

If you're unhappy about KDE, simply:
```
sudo aptitude remove kubuntu-desktop
```

---

### Post by fzf3 on 2006-11-19
I tried that.

KDE seemed to install OK but when I logout or restart and click on options & choose sessions at the login screen, there is no option to choose KDE.

---

### Post by stoer on 2006-11-19
> **Artificial Intelligence said:**
> The easeist way:

```
sudo aptitude install kubuntu-desktop
```

then logout and at the login screen choose session and pick KDE.

If you're unhappy about KDE, simply:
```
sudo aptitude remove kubuntu-desktop
```

Thanks for your reply.
That easy.... then i'll give it a whirl.
Does installing the KDE desktop alongside Gnome involve installing the whole gammet of drivers, mounts, mods and multimedia all over again or does the installation take this from what already exists in the system (installed for Gnome), i guess it does -  just wishfull thinking on my part ;)

Cheers.

anybody else with any tips/tricks for quickly setting up KDE?
Any must haves? Custom mods?

---

### Post by Perfect Storm on 2006-11-19
Nothing else needs to be setup. KDE is just envoriment like gnome, XFCE on top of the base and the kernel.

---

### Post by qpieus on 2006-11-19
No, you shouldn't have to mess around with drivers, mounts, mods and multimedia again, that will still work. I did the same thing you are considering - started with ubuntu then switchd to kubuntu. Enjoy.

---

### Post by stoer on 2006-11-19
> **qpieus said:**
> No, you shouldn't have to mess around with drivers, mounts, mods and multimedia again, that will still work. I did the same thing you are considering - started with ubuntu then switchd to kubuntu. Enjoy.

This gets better and better, almost as good as having the keys to the brewery.

Cheers.

---

### Post by poohbear1616 on 2006-11-19
When i installed kde I used kde-desktop instead of kubuntu-desktop. I ended up with the gnome and kde aps listed side by side. Does using the kubuntu package have the same effect as just saying kde in the command?

---

### Post by LLRNR on 2006-11-19
First time when I installed *kubuntu-desktop* on top of default Ubuntu 6.06 I also got both Gnome and KDE apps listed in the K Menu, which didn't bother me at all... on the contrary even! The second time I installed kubuntu-desktop on top of Gnome I did it right after a fresh install and I got in my K Menu an entry for the Debian menu, where I have most of the Gnome apps separately. I don't know if this answers your question because I never tried *kde-desktop* lol, but I don't think it's a bad thing to have all the apps at your disposal. Although, of course, Gnome apps work better in Gnome and KDE apps work better in KDE... :)

---

### Post by podunk on 2006-11-19
kubuntu-desktop is just a teaser. If you really want the KDE experience install KDE! kde-core, kde-admin, kde-dev - just enter kde in the package manager and install it all! :-D

KDE is amazing. Your tea is steeped to perfection, your boiled egg always comes out right, and your toast is perfectly browned. 

Be very sure to give Konqueror a good go, it's truly the most amazing piece of software I've found in over 20 years of playing with computers. Kontact is what Outlook wanted to grow up to be before it's Momma dropped it on it's head.

3.5.5 is faster and has more eyecandy that 3.5.3, you need to add the kde repositories from the Kubuntu.com site.

Has anyone tried loading kde 4 into Dapper yet?

---

### Post by poohbear1616 on 2006-11-19
I just istalled the kde-desktop a couple of days ago, so I'm still playing around with it. When I installed I chose kde as the default, but my screen look is the same. Same wallpaper, same settings for screensaver, etc... Only thing different I noticed is the added aps. It added a barrel load of aps lol. Including a maze of aps in debian. I might play around with it and take  out kde and try the kubuntu package to see if its the same. Just a note: I noticed the little description bubbles that pop up when you mouse over the ap titles for kde don't display.

---

### Post by mexlinux on 2006-11-19
You will be amazed with the kde possibilities

---

### Post by rlozano on 2006-11-19
> **stoer said:**
> 
So, here's the nub, at last!   ***(QUESTION)***
I started out using Ubuntu with Gnome, no special reason, just happened that way.  I see alot of interesting programs however that are to find in the KDE environment. Some of these work well under Gnome and some don't.  
eg K3b and K9copy, home finance etc - K3b works without a hitch but K9copy has the occaisional temper tantrum.  Through all my trawling i've seen a number of interesting KDE applications and now i'm beggining to wonder if the grass isn't greener...
I'd like to give KDE a try.  I'd like to install it alongside Gnome, i know that this is easy to do, but...
I need to install it in such a way that if it dissapoints or doesn't offer me a better alternative to Gnome that i can Uninstall it EASILY and without damaging my present setup and i don't know how to do this.
Will installing KDE cost me alot of space? and will i need to go through the whole driver install route again? (ATI card).
Any KDE users out there that want to convince me that this is worth the effort???
Again thanking you all for making this not only a great OS but also a great experience.
Cheers!

it really depends on what and how you present your personality in your computer. if you want a combination of simplicty+a little eye candy, you go with gnome. if you want eye candy, just like (if you are used to windows) KDE is the one for you.

as far as application is concern, Gnome and KDE have their respective set and equivalent. so far i have no issue using applications from both sides as i have them both in my PC.

as to your question on how to go back to either plain Gnome or KDE, here's a good note from aysiu.

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

hope this helps.

---

### Post by stoer on 2006-11-19
Ok people,
thanks for all the replies.
I'm reading through alot of the links right now. Some very good sites and blogs. I liked the Gnome eyecandy especially.

To avoid confusion:

If i install the KDE desktop alongside my installed version of Gnome, i'm actually 'not' installing KDE?
Just the desktop, a "limited" insight into KDE itself but an incomplete insight. Is that right??

If i want to experience the full metal jacket version of 'KDE' i need to install "KDE - Complete with core et al", is that possible on top of Gnome? or does that mean i need to install it seperately? on another partition for example.?

Sorry if this seems a dumb question, but i think i'm confusing myself now ;)

Cheers.

---

### Post by aysiu on 2006-11-19
If you install KDE, you're actually installing KDE.

The two don't really get installed on top of each other, but--as you said--alongside each other. That way, when you log in, you have the choice to log in and use the KDE desktop environment or the Gnome desktop environment.

---

### Post by stoer on 2006-11-19
I'm replying from within Konqueror, must say it leaves an impression.
Just need a month or two to absorb whats going on :)

Guess i'm going to have to learn a whole lot of new stuff now, right?

Again thanks for your comments,tips and feedback, 
If there's anyone out there who's taken this route and has any advice regarding do's and dont's and anyone who'd just like to add any essential app's for me to look at, i'd really appreciate it.

current used apps - Gnome
cd/dvd - burning K3 and k9copy
Binary downloads (usenet) - Hellanzb
mediaplayer - movieplayer
photo's - picasa (google)
Video - Kino
Office - open office
internet - firefox
mail - evolution
chat - gaim
Music - i've too many to mention, still trying to find the right one.

Just say,for arguments sake.  That over a month or two i really do prefer KDE to Gnome is it feasible that i can then erase Gnome leaving a functional KDE behind?  (guess it is if it's installed alongside...)
Or is that what was meant in psychocats install notes where it says you'll be asked to chose between KDM or GDM...which can be changed later "by modifying the /etc/X11/default-display-manager file"??

Ha!!
I really, really love it here. So much to do, so much to see and so much to learn.

Really appreciate all your help.
Cheers!

---

### Post by seijuro on 2006-11-19
> **podunk said:**
> Kontact is what Outlook wanted to grow up to be before it's Momma dropped it on it's head.

LMAO that is so true too! As someone else mentioned I also boke in to Ubuntu with standard Ubuntu and Gnome then switched to Kubuntu. I've been using various distros of Linux for about 5-6 years with all the different window managers and desktop environments and I keep coming back to KDE it just has a slick polished feel along with high configurability and tons of apps such that all of these things put together can not be found anywhere else.

> **stoer said:**
> Just say,for arguments sake.  That over a month or two i really do prefer KDE to Gnome is it feasible that i can then erase Gnome leaving a functional KDE behind?  (guess it is if it's installed alongside...)

It's been my personal experience over the years across many other distros that gnome is quite ugly to uninstall however with the detailed additions to make Ubuntu easier to use and manage someone may know of a simpler way. Personally if I was going to remove Gnome I would just back up my data and throw on a fresh install Kubuntu.

---

### Post by Ateo on 2007-05-19
> **Artificial Intelligence said:**
> If you're unhappy about KDE, simply:
```
sudo aptitude remove kubuntu-desktop
```

Incorrect my friend. This will *only* uninstall the meta package called kubuntu-desktop and nothing else.

---

### Post by jordanmthomas on 2007-05-19
...unless you installed kubuntu-desktop with aptitude instead of apt-get.

---

### Post by Psicolonia on 2007-05-19
long time kde user, switch to gnome now... they are very much alike. gnome is simpler and powerfull. KDE has more power and more confusion. I'm a software developer and I think there are cool apps for KDE. and I run them: ON GNOME! I do admit it has advantages... but... also disadvantages! see the review of post #13. It's wiser than calling out for the fans.

Best thing KDE has is guidance for laptops. And I use it, flawlessly on gnome! ;)

---

### Post by thunderkyss on 2007-05-20
hey guys. I just installed the KDE desktop ontop of my Ubuntu install. 

Everything looks exactly the same, and I really want to try the Kubuntu GUI.

Right now, it's still got the gnome panels & menus.

I want to use the KDE Kubuntu GUI is there a way I can get this install to look & act like Kubuntu without installing Kubuntu??

---

### Post by Bachstelze on 2007-05-20
In the Sessions menu of your login screen, you should have a KDE option.

---

### Post by thunderkyss on 2007-05-20
> **HymnToLife said:**
> In the Sessions menu of your login screen, you should have a KDE option.


Ah........... now I see it. So that's the "Sessions menu" 


Thanks, it's working (& looking great)

---

### Post by mexlinux on 2007-09-29
I'm writing a blog about this topic, I'm showing only advantages of both desktops, and I'm trying to make it completely unbiased.
You can see it here:
[kde vs gnome]("http://www.bbnuke.com/kdevsgnome")

---

### Post by dptxp on 2007-09-29
> **mexlinux said:**
> I'm writing a blog about this topic, I'm showing only advantages of both desktops, and I'm trying to make it completely unbiased.
You can see it here:
[kde vs gnome]("http://www.bbnuke.com/kdevsgnome")


We all try to compare Gnome with KDE. For me, Gnome is simpler to navigate.
And as per reports, Gnome is much more stable.

---

### Post by Perfect Storm on 2007-09-29
Thread moved.

---

