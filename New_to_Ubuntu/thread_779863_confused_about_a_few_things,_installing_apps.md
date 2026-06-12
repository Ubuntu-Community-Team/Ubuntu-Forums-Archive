---
title: "confused about a few things, installing apps"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by srossnz on 2008-05-03
i've used the add/remove utility a few times.  For example to install compiz, but after installing such apps it says it's installed and then what?  I see nothing anywhere related to the app.  As a windows switcher these linux desktops really need to get this sort of thing nailed down.  Also, there are several interesting apps that look great but when I find install instructions it looks like 5days and a degree from MIT is required to install it.  Things are getting better but I still feel like the linux desktop community are too smart for their own good, this stuff needs extreme dumbing down if it is going to be a dominant force in the market..  How about a mantra "My grandma could install it", then we'd be getting somewhere.  I'm sticking with ubuntu, so far I'm happy but windows is still far easier with all the 1-click installable apps.

---

### Post by NightwishFan on 2008-05-03
Some apps need to gui way to start them. Anything that does likely will show up in the menu. Also if you have gutsy or hardy compiz is installed by default and you only need the compiz config settings manager.

---

### Post by SunnyRabbiera on 2008-05-03
actually we have better tools then add/remove and honestly linux is not as hard as you think.
its just about thinking differently, not all applications need compiling if you know how to work things.
Applications themselves are usually installed in usr/bin or usr/lib, to find out where things are installed needs a better application installer then add/remove and thus brings us to synaptic package manager.
synaptic is located under system in administration, it will give you a far longer list of applications to work with then add/remove and if you want ti to you can make it list where it puts things...

---

### Post by srossnz on 2008-05-03
cool, where is this settings manager?  I see it nowhere.  Thanks :)

---

### Post by srossnz on 2008-05-03
> **SunnyRabbiera said:**
> actually we have better tools then add/remove and honestly linux is not as hard as you think.
its just about thinking differently, not all applications need compiling if you know how to work things.
Applications themselves are usually installed in usr/bin or usr/lib, to find out where things are installed needs a better application installer then add/remove and thus brings us to synaptic package manager.
synaptic is located under system in administration, it will give you a far longer list of applications to work with then add/remove and if you want ti to you can make it list where it puts things...

Interesting, will have a look, thanks

---

### Post by SunnyRabbiera on 2008-05-03
you will need to install the comiz settings manager actually, its not on by default...
but installing it is easy.

---

### Post by NightwishFan on 2008-05-03
Activate compiz with: System -> Preferences -> Appearance -> Desktop Effects

Then run this command. (you dont have to run a command its just easier this way)
```
sudo apt-get install compizconfig-settings-manager
```

Then play with compiz settings in System -> Preferences -> Advanced Effects (or something.. i dont use compiz anymore)

---

### Post by SunnyRabbiera on 2008-05-03
> **NightwishFan said:**
> Activate compiz with: System -> Preferences -> Appearance -> Desktop Effects

Then run this command. (you dont have to run a command its just easier this way)
```
sudo apt-get install compizconfig-settings-manager
```

Then play with compiz settings in System -> Preferences -> Advanced Effects (or something.. i dont use compiz anymore)

actually its listed as advanced desktop effects.
I still use compiz.

---

### Post by srossnz on 2008-05-03
most helpful, thanks guys!

---

### Post by SunnyRabbiera on 2008-05-03
you see, its all about the right tool for the right job.
Now add/remove is a great tool dont get me wrong but there are far better tools out there such as apt-get and synaptic.
we can help you if you give us a chance, the linux community in general is among the most helpful out there.

---

### Post by kirios on 2008-05-03
System > Preferences > Appearances > Visual Effects to customize desktop effects after installing compiz. 

If you want to customize further, System > Administration > Synaptic Package Manager, then search for and install compiz-config.

> **srossnz said:**
> i've used the add/remove utility a few times.  For example to install compiz, but after installing such apps it says it's installed and then what?  I see nothing anywhere related to the app.  

System > Administration > Synaptic Package Manager > Settings > Repositories. Make sure *main*, *restricted*, *universe* and *multiverse* are selected. Click on Reload. Select the package you want to install and click on Apply. 

Seems reasonably easy to me. :-)

> **srossnz said:**
> Also, there are several interesting apps that look great but when I find install instructions it looks like 5days and a degree from MIT is required to install it.  Things are getting better but I still feel like the linux desktop community are too smart for their own good.... windows is still far easier with all the 1-click installable apps.

---

### Post by Paqman on 2008-05-03
> **srossnz said:**
> windows is still far easier with all the 1-click installable apps.

Ubuntu can install 100 aps in one go. It can also automatically update ALL the software on your machine so you're always up to date. Plus all the software in our repos is 100% guaranteed spyware/adware free.

I'd love to have that kind of system for Windows.

There are one-click ways of installing Ubuntu aps. They're called .debs and they work the same as .exes (except that they have all the extra benefits I mentioned) Have a look at [GetDeb](http://www.getdeb.net/) if you're interested.

---

### Post by srossnz on 2008-05-03
cool, as I sit here and tinker I have a few more interface questions:

-I have what appears to be 1 extra desktop I can switch to, how can I add more?
-is there a way to have different backgrounds on each desktop?  When I change the background on one it changes it on the other
-if i click and drag a window around it's very choppy, i was given an option to enable drivers for my videocard so did that, it's a geforce 8800gtx 768meg
-i see i can have a quick launch at the top is there a way to 'autoarrange' them so they are spaced apart equally?
-i have virtualbox running in seamless mode, which does work but when i minimize any windows app my screen goes nuts, half black on the top etc -maybe something is wrong with my video

I'm sure I'll have more questions and more googling to do.  Thanks!

---

### Post by Thingymebob on 2008-05-03
> **srossnz said:**
>  so far I'm happy but windows is still far easier with all the 1-click installable apps.
Since When?
1-100 clicks Find App (probably loaded with spyware/Adware);
click download app;
click unzip app;
click setup.exe;
1-1000 clicks Next/OK without reading message.

My Granny Does that And I'm round every week sorting out the mess.
and your saying she can't do:

Menu->addremove->search->check->install

or Menu->administrative tools->synaptic package manager->search->check->install

---

### Post by SunnyRabbiera on 2008-05-03
> -I have what appears to be 1 extra desktop I can switch to, how can I add more?

This is a feature in linux called virtual desktops, its like having two desktops for the price of one.
Virtual desktops have been around for forever here.

you can add more if you wish by right clicking the virtual desktop application and selecting "preferences"
you can go up to 16 different virtual desktops! (though you may want to stick with just 2 or go up to 4 if you really want to)

> -is there a way to have different backgrounds on each desktop?  When I change the background on one it changes it on the other

Not on gnome, gnome is your desktop UI and that is not a feature as of yet...
though if you want to you can install KDE another UI that does the same basic job but works a little different.

> -if i click and drag a window around it's very choppy, i was given an option to enable drivers for my videocard so did that, it's a geforce 8800gtx 768meg

This is related to your video card I am afraid, some cards simply wont play nice with effects if you are using them.
some cards work good, some cards are bad, and most others are crap.
Its all trial and error, I am afraid as we dont have as many drivers as windows does but its not our fault. Remember that most cards work for windows only and its often up to us to crack as many as possible to work for us.

> -i see i can have a quick launch at the top is there a way to 'autoarrange' them so they are spaced apart equally?
Its not really a quicklaunch per se, its actually just links to applications placed onto the panel (or taskbar in windows terms)
what you ask is not really all that possible, though we have a quick launch like application called the drawer, you can get it by right clicking the top or bottom panel and select "add to panel"
and you can scroll down to drawer and click "add" and the drawer will be added to your panel

> 
-i have virtualbox running in seamless mode, which does work but when i minimize any windows app my screen goes nuts, half black on the top etc -maybe something is wrong with my video

this may be related to your video card issue, there might not be anything we can do for you here.

---

