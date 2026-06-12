---
title: "Whats Next?"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by huwaw69 on 2008-11-01
Alright i have a problem...

I already successfuly and w/o a doubt installed ubuntu 8.10 on my HP Laptop, and guess what i just
can't stop admiring how beatiful this OS/Linux Distro... Im defintely loving this... And Thanks you for those who is responsible for this distro...

#Im impressed w/ my desktop cause it has so many effects.. i mean it wobbles.. it has the 3d effect.. rotating cube... I don't know what you call this but i think this is the Compiz-Fusion if im not mistaken RIGHT?

BUT... There is one thing Bothering me...What should i do next with it.. i mean, what is the first and foremost to learn except for the manual/documentation...

Anyone?

#---Im Just A Noob Who Knows Only Nothing About This...---#
#---And Can I Install Guitar Pro on "-UBUNTU-"---#

---

### Post by Sealbhach on 2008-11-01
Is everything working? No problems at all?:confused:

You must tell us what this great machine of yours is. Really, it would be useful for the developers to know - so put a post in this thread here:

[http://ubuntuforums.org/forumdisplay.php?f=103](http://ubuntuforums.org/forumdisplay.php?f=103) 

and say what hardware you are using.

Also, you could look at

[http://uk.youtube.com/watch?v=RgmtkgXs-1I](http://uk.youtube.com/watch?v=RgmtkgXs-1I)

to get used to the terminal.

Also, just stick around this forum here, see what problems other users encounter and the solutions they find.

Don't know about Guitar Pro. 

.

---

### Post by Patrick793 on 2008-11-01
If it's your first time with Ubuntu, it would be a big help if you learned some commands for the terminal, seeing as the terminal may be the only thing you have to save your computer if it gets borked.

EDIT: About Guitar Pro, you may be able to install it with wine.

Download and install Wine. Just download [this file](http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.7~winehq0~ubuntu~8.10-0ubuntu1_i386.deb), and you will be able to install and run Windows programs in Ubuntu.

---

### Post by CatKiller on 2008-11-01
> **huwaw69 said:**
> BUT... There is one thing Bothering me...What should i do next with it.. i mean, what is the first and foremost to learn except for the manual/documentation...

Just use it for a while to do whatever it is you use a computer for. Just get used to any differences that you find from what you're used to. You may find that there are some things that don't seem straightforward, and then there will be an opportunity to learn.

Otherwise, as Sealbhach says, hang around on the forum and see what other people are doing. You might find that they're trying something that you might be interested in doing.

I hate to break it to you, but using a computer isn't necessarily that exciting by itself :)

Some games are quite good - I heartily recommend Pioneers. You might also try to experiment with the different audio recording/mixing stuff that you can do. If you get your teeth into that, it might keep you quite busy for quite some time.

EDIT: Apparently TuxGuitar is similar to Guitar Pro, but I've not used either.

---

### Post by huwaw69 on 2008-11-01
#---- Thanks Guys ----#
@Sealbhach 
*There seems no problem at all

@Patrick793
*I'll Try Guitar Pro in wine but i hope RsE works fine here

@CatKiller
*hmm maybe ill also try that one tuxguitar...

#--- I appreciate the help guys ---#

oh there is one thing
it alsmost slipped aut of my mind
--Whenever i start ubuntu
loading starts..........................Then uhmmmmmm lets say 1 sec. The MONITOR CRASHES as in Grumbled graphics can't explain...
so far i don't know what seems to be the source of that... but my conclusion is im using too much desktop effects...cMaybe Compiz Fusion

I have an ATI radeon i dont know what model how do i know it here in ubuntu?

---

### Post by Patrick793 on 2008-11-01
You mean when you log in?

I had the same problem on my desktop.

At the login screen, go to settings (or whatever it is at the lower left corner), hit sessions, and then click Failsafe Gnome. When you are logged on, go to System > Administration > Hardware Drivers, and look for one for your video card.

---

### Post by phidia on 2008-11-01
To find your card open a terminal from Applicatiions > Accessories and enter "lspci | grep VGA" (without the quote marks)

See the viedo wiki [here]("https://help.ubuntu.com/community/Video").

---

### Post by billgoldberg on 2008-11-01
> **huwaw69 said:**
> Alright i have a problem...

I already successfuly and w/o a doubt installed ubuntu 8.10 on my HP Laptop, and guess what i just
can't stop admiring how beatiful this OS/Linux Distro... Im defintely loving this... And Thanks you for those who is responsible for this distro...

#Im impressed w/ my desktop cause it has so many effects.. i mean it wobbles.. it has the 3d effect.. rotating cube... I don't know what you call this but i think this is the Compiz-Fusion if im not mistaken RIGHT?

BUT... There is one thing Bothering me...What should i do next with it.. i mean, what is the first and foremost to learn except for the manual/documentation...

Anyone?

#---Im Just A Noob Who Knows Only Nothing About This...---#
#---And Can I Install Guitar Pro on "-UBUNTU-"---#

I've written a little blog post on what to do after installing Ubuntu.

See:

[http://linuxowns.wordpress.com/2008/10/30/5-things-to-do-after-installing-ubuntu-810-intrepid-ibex/](http://linuxowns.wordpress.com/2008/10/30/5-things-to-do-after-installing-ubuntu-810-intrepid-ibex/)

--

Your thanks should go to our [SABDFL]("https://wiki.ubuntu.com/MarkShuttleworth").

---

### Post by meindian523 on 2008-11-01
1]Read the help,it's good for newbies.
2]Follow the links in my sig for newbies and adding your hardware to the recommended hardware list PROVIDED you didn't have to install any proprietary drivers

---

### Post by Separ on 2008-11-01
A solution for Guitar Pro is Tuxguitar. The ubuntu repos don't have the latest version so i recommend you downloading it from sourceforge or the Tuxguitar site. It even opens Powertab (.ptb) files too! It requires Java tho if you want the full thing. I use it all the time and it's great!

---

### Post by huwaw69 on 2008-11-01
My Video Card is ATI Radeon IGP 330m/340m/350m/
Do i nid to post this to recommended Drivers? coz for me this video card really sucks!


@Patrick
 Ill Try That Later on...

@Separ
hmmmm gotta find how to install java now hehehe... anyways thanks!

---

### Post by meindian523 on 2008-11-02
If it works,post it.And post any issues with it in the comments,if possible.

---

### Post by huwaw69 on 2008-11-02
It definetly works! but the tux guitar had a slight problem!
guess what! i solved it myself hahaha...
the problem is it dont have a sound.. so i install the alsa-plugin
but alsa-plugin didn't work so i tried to find in the packages if there is another one..
then i found the java sound plugin so installed it and... TADA it worked perfectly...

But i cant seem to open frostwire
i try to open it on the terminal but it says:
"oopppsss your jre is not the latest version!"
not exactly that word but its the same point..
so i downloaded the latest jre via terminal i followed the instructions on java.com
then updated it... now my jre has the latest version.. but the frostwire says i still don have the updated java... so i checked it in the terminal it says my jre version is 1.6.something but when i try to open my frostwire it says my jre is still 1.5.something... So any ideas? why is it like that?

---

