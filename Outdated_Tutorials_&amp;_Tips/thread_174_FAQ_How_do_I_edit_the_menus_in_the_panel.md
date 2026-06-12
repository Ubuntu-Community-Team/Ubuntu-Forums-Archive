---
title: "FAQ: How do I edit the menus in the panel?"
date: 2004-10-11
forum: Outdated Tutorials &amp; Tips
---

### Post by ubuntu-geek on 2004-10-11
There is no easy way to do this in modern versions of GNOME.

If you really want to change things, the menu items are ".desktop" text files in /usr/share/applications/. You can edit them in a text editor (like gedit or nano).

---

### Post by dawynn on 2004-10-23
I've posted this in other threads -- but, if the menus are really that hard to work with in Gnome, why is it considered worthy of Ubuntu?  The Ubuntu philosophy is -- "It should just work."  Since Gnome doesn't, why was it chosen over KDE (which *does* work -- and has a very good menu manager), or any of the other numerous Window Managers?

---

### Post by FLeiXiuS on 2004-10-23
Boo KDE, Gnome is much cleaner and easier to use, I haven't had a problem with it yet.  Perhaps your overlooking the situation. :-k

---

### Post by leeech on 2004-10-24
it is kind of horible... try install crossover and office xp...

you will get one messy menu

tidy them up one by one... then know what? my 2nd user account's menu also messy... 

anywhere to change global menu arrangement... else everytime i create a new user, i have to resort things

---

### Post by flygmaskin on 2004-10-25
[QUOTE=leeech]it is kind of horible... try install crossover and office xp...

you will get one messy menu

tidy them up one by one... then know what? my 2nd user account's menu also messy... 

anywhere to change global menu arrangement... else everytime i create a new user, i have to resort things[/QUOTE]
 Just copy your custom config files to /etc/skel/, they will then be copied to all new users home directories.

---

### Post by dawynn on 2004-10-25
Maybe it would be helpful (since this *is* the FAQ's and HOWTO's area) for someone to write-up how the menus are stored.  flygmaskin indicated that we could copy the custom config files into /etc/skel.  That'd be great, if we knew where our custom config files were located.

Adding and removing entries is pretty simple in gnome.  All it takes is a right-click (OK -- not sure how Mac users would accomplish that).  But how about trying to move a menu entry into a new folder?  Drag-and-drop doesn't work.  I could delete and re-add, but I would lose a lot of the configuration information.  There is no option to cut-and-paste.

So, if anyone has had any success with "sorting" or heavily modifying their gnome menus -- please feel free to inform us about what you did!  Or about any web documentation that you found especially helpful.

Thanks!

---

### Post by jdong on 2004-10-25
Also , try navigating Nautilus to **applications:///** to modify just the current user.

---

### Post by WW on 2004-10-26
For a single user, anyway, it is not difficult.

For a quick change to a submenu in Applications, just right-click in the menu.  You'll see several editing options.

You can also find instructions in the Ubuntu Wiki FAQ:

    [http://wiki.ubuntu.com/FrequentlyAskedQuestions](http://wiki.ubuntu.com/FrequentlyAskedQuestions)

(The wiki seems to be changing fairly frequently, but the relevant question should be in the section labeled "Configuring the Desktop".)

---

### Post by umarmung on 2004-10-27
Ok there is no easy way to change the entries in 'Computer', but I see no problems changing the applications menu.
As jdong already said: 
**nautilus applications:///** and edit the menu for a single user

**sudo nautilus applications-all-users:///** and edit the menu for all users. Where is the problem?  8)

Oh BTW, a new menu editor and rewritten menu code is planned for gnome 2.10 as far as i know.

---

### Post by r_a_trip on 2004-11-26
I already knew about the nautilus applications:/// thing. Google is marvelous.

Yet, Ubuntu has another menu right next to Applications called Computer. How do I go about changing anything in there?

---

### Post by nehalem on 2004-11-27
I must say this is one of those gnome things that baffles me.  There are just a couple of areas where you have to shake your head because Gnome is so far in some ways (like having a universal contact management backend, evolution-data, nothing like this on Windows) and then being so unfar in other ways, like this example.  I mean editing menus should have been one of the first things possible, it's just such basic feature of a modern desktop.

---

### Post by DoubleDangerClub on 2004-11-29
[QUOTE=nehalem]...it's just such basic feature of a modern desktop.[/QUOTE]

Agreed.  I used to think KDE was the way to go because it was flashy, but when I started actually using it, man oh man...Gnome just sat right with me.

---

### Post by monte.lin on 2004-12-17
Debian has great menu management system for almost every window manager, Ubuntu chooses to bypass it. That is O.K. if we are in KDE since it has its own menu manager, but then we are in Gnome. 

After several days fighting with Gnome/Nautius, I now know how good KDE really is. I will definitely apt-get install those KDE things after I finished reading these Howto topics and know how to switch window manager safely in Ubuntu.

I need stable and reliable lib and packages, but I surely don't need these Gnome junks.

---

