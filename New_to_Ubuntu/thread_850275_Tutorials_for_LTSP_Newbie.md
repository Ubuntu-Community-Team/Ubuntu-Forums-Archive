---
title: "Tutorials for LTSP Newbie?"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by Linux&amp;Gsus on 2008-07-05
I'm working with a non-profit organisation / training center. We have a little internet cafe for the students that still runs with Windows NT. Which is...old. And actually it doesn't work really well. Better say, reliable but really slow. But the computers are really only there for internet, so no other applications besides IE are running. Which probably wouldn't be possible, anyways. Means, not even a PDF reader is available.
As you probably know NT isn't supported anymore, so no security updates. Which isn't exactly helpful, I guess.

What I would like to propose is a Terminal Server setup with Linux (LTSP). For one I think an up-to-date system would be good in terms of security, and Linux is more secure by default, anyways. Not that something really dramatic would have happened in the past but we all know it can happen at any time. Just one click in an email...
Although, my theory is that the system is so old that it's not supported anymore, not even by viruses and trojans. :lolflag:

Also, I think that Linux fits perfectly for that purpose since we are non-profit and there isn't really a budget for it. The students pay a little fee for using the internet cafe but that is mainly to cover the internet cost.
So, upgrading to a newer Windows version isn't really an option. Unless someone comes by with a donation specifically for that purpose.

So, my idea is to set up LTSP with KDE (since it's looking more like Windows) and connecting 6 clients (using the machines that are there already). Actually, best would be to make it as Windows looking as possible. This is not push people towards Linux, most of them haven't even heard of it. Well, and as you can imagine I don't want to sit there all day long and helping them getting along with an unfamiliar "something".
In other words, most of those folks who are using these computers are not computer savvy at all. Those who are most likely bring their own laptops.

OK, this is the situation. Now here are my questions.
[LIST]
[*]I have never done anything with LTSP or Terminal Server in general. I know about the LTSP website. But I was wondering if anyone know about a good, fool proof tutorial. Preferred for K/Ubuntu based. Well, but just anything easy to understand would be helpful.
[*]There are 6 machines that could be used as clients. What software do I use for a client and what are the requirements for that?
[*]What would be the requirements for the Server for using a browser (most likely Firefox I guess), PDF reader, OOo, Kopete/Pidgin/Skype (chat only, our students are from all around the world, I think they would appreciate a chat with friends and family back home...), anything else important? Since we have families coming by as well I guess an occasional game like Mines or a Paint like drawing program would be nice as well.
[*]How would I get the closest Windows (XP?) like look-and-feel? Any themes/tutorials around for that? I know, it's a bit *cough* perverse *cough* to make Linux look like Windows. But I guess you understand that I don't want to be a baby sitter for those folks who just want to check their webmail account.
[*]Is there anything I have overlooked so far?
[/LIST]

Thanks for any help, ideas, suggestions, tutorials,... on that topic.

---

### Post by bodhi.zazen on 2008-07-05
First, unless you are familiar with Linux it will take time for you to transition as well :)

Take a look at edubuntu :

[http://www.edubuntu.org/Download](http://www.edubuntu.org/Download)

The download page has links to informational pages and how-tos such as this:

[https://wiki.edubuntu.org/HardyClassroomServer](https://wiki.edubuntu.org/HardyClassroomServer)

=========

Next, to be honest, you can add KDE, but I am not sure it is worth the hassle. It is fairly straight forward to use the gnome menu, and you can put launchers for Firefox or other apps on the desktop or menu bar. YOu can also write a one page hand out "How to use Firefox" ...

---

### Post by Linux&amp;Gsus on 2008-07-05
Thanks for the links.
Got a few questions here. Isn't Edubuntu geared  towards younger students, as in Primary/High School? Our students are *slightly* older, as in University students.

With KDE vs Gnome vs what ever DE, I don't want to start a war here. But I think people who think that Windows is the computer and IE is the internet and haven't seen nor heard anything else have a rather hard time adjusting to something different. People just hit the bottom left corner to get a menu with their programs. They simply don't look at the top. Actually someone who looked at my computer asked me if that is Vista. I told the person that this is Linux and it must have sounded as if I have said something in a foreign language.
I don't know to what extend Gnome is adjustable since I personally use KDE. Not for the works-like-Windows reason, but that's not topic anyways. I simply don't know Gnome or any other DE.

However, what I do know is that I'm dealing here with people who don't know what a Linux is. Could be anything, they have never heard that word. For them a computer equals Windows and internet equals IE. Of course there are all grades in between knowing nothing and knowing it all. But the knowing it all kinda person has most likely a laptop with them. And I need to be prepared for the knowing nothing people. These are the folks who have the problems with anything other then Windows. I have many many stories about that topic. 

A hand out is a good idea. But honestly it should be short (one page as you said) and it will only be so if the desktop looks somehow familiar. Otherwise I have to explain every single step.
So, I don't care about people like me, I find my way through, no matter the DE. But I simply don't have the time every quarter to baby sit the computers for a month to make sure that everyone know what they are doing.

From that point of view I thought that KDE comes closest to the Windows look and feel. But really everything that make it more looking like Windows is better. At the end I don't care what DE is installed/used.
This isn't a project to promote Linux. It's a (rather cheap) service we provide for our students and I want it for those who look after that as trouble free as possible. That includes the need of guidance for those who don't know much about computers.

So, here's the catch. If I want to propose that upgrade/change then I need to put these things into the calculation. It must be a familiar looking desktop. I'm totally fine if I can adjust Gnome to meet the needs. As long as it's possible.

---

### Post by bodhi.zazen on 2008-07-05
Edubuntu is geared to younger students it is true, but the edubuntu documentation goes through setup ...

You are talking about several steps here :

1. Setting up your LTSP. Edubuntu will do much of this automatically. If you do not like the look and feel of Edubuntu, you can change it later or your can do a manual installation of the various packages after your are more familiar with the whole process.

2. "Look and Feel". Unless you install windows it is going to look and feel like Linux. Your users will come in 2 types: The first will "explore" on their own and click through the menus. The second will not. This second group will need a little hand holding if you change your system (regardless of OS or DE).

Most "normal" people can adapt to either gnome or KDE and I do not think the DE you go with is as important as OS. If you go with windows, most people will be more familiar with it and you will have less questions / hand holding. If you go with Linux most people will adopt fairly quickly, although you will have more hand holding.

Keep in mind, if you go with Linux that almost implies Firefox (as opposed to IE). In my experience, asking users to adjust to Linux is the big step and you should ask yourself if you are willing to support users as they transition, even if using it on a limited basis.

In my experience you can not just install KDE and have less problems because it looks more like windows. The truth is Linux is not windows and if you go with Linux you should be willing to give a little more support then if you go with windows. Over time I think this will lessen as students will help each other.

---

### Post by kansasnoob on 2008-07-05
I know nothing about servers and very little about networking in general but I noticed that you asked about, "People just hit the bottom left corner to get a menu with their programs. They simply don't look at the top."

The Gnome desktop is quite easily modified. This is mine:

[ATTACH]76524[/ATTACH]

[ATTACH]76525[/ATTACH]

[ATTACH]76526[/ATTACH]

So you can see that's pretty much what mine does. I'd have to send hundreds of screenshots to show all the options. What I do is modify the upper panel and then delete the lower panel. Then I move the upper panel to the bottom. It takes about 2 minutes!

---

### Post by Linux&amp;Gsus on 2008-07-06
Thanks for your input, guys.

@kansasnoob
I wasn't aware (out of ignorance about the topic ;) ) that it's possible to change Gnome to look like that. I always used KDE and didn't care about Gnome.
May the Gnomeists forgive an ignorant KDEer. :lolflag:

@bodhi.zazen
I wasn't aware that Edubuntu actually does a great deal towards LTSP. So, that's actually really cool. I've been scanning through some links on the pages you posted and it looks really helpful.

You are right with the 2 (main) types of people. I don't care so much about the first type, as you said they will search AND find their way through the menus.
The other group is my concern. I don't mind holding hands / baby sitting. No matter if it's explaining what ever Linux DE, OSX, or Windows to a life long Mac user, for that matter. However, the problem with that is that I'm hardly available at the actual Internet Cafe. I don't want to go through the why and how and when and where. That would be too much for this thread.
Just that much, we have (depending on the time of the year) 70-150 new students every 3 months with increasing tendency. Aged 17-70 (literally) with all sorts of knowledge and backgrounds. Due to our staff circumstances this Internet Cafe needs to be as easy to work with for the students, as anyhow possible. With as little holding hands as we can make it happen. I would even go that far and have an IE icon on the desktop so that people find the browser.

I know that this is a tall order. But I only say that much: Someone once referred to "the blue cable" as the internet. Which happened to be a blue colored Ethernet cable. Someone else asked me if that gray internet cable (Ethernet cable that is of course) works the same like the blue one or if the blue cable is better.

So, I personally never cared about themes. The only thing I really did is making the KDE panel transparent because I don't like the gray/silver look. But besides that everything is default. Works fine for me.
But for that purpose, if it exists, I would look into using something like a WinXP theme. Or what ever else is out there that looks the closest to what an average Windows user is used to.

Well, I know that Linux is not Windows. Actually the fact the Linux != Windows is one of the big reasons I use Linux. There are many things that I don't like about Windows and the look and feel is the least of the problem.
Also, I know that this means a minimum amount of guidance and maybe a bit more for those who never heard that anything else besides Windows exists. Some just do it, others are fine with half a page to a page of essentials and some need physical guidance where to go and where to click. I know that and I don't mind.
But due to the circumstances I would like to reduce that to possible minimum. And that's probably what I need tips for how to best do that. Well, besides the LTSP of course.

Something I still haven't found is some info for system specs for my original mentioned scenario. There are 6 possible machines at them moment for clients. But if it's easier to calculate, specs for 10 clients is just as fine.
The scenario was as follows:
> What would be the requirements for the Server for using a browser (most likely Firefox I guess), PDF reader, OOo, Kopete/Pidgin/Skype (chat only, our students are from all around the world, I think they would appreciate a chat with friends and family back home...), anything else important? Since we have families coming by as well I guess an occasional game like Mines or a Paint like drawing program would be nice as well.
I want to use Hardy, of course. LTS would be a wise for an Internet Cafe, I guess.

Cheers.

---

### Post by ugm6hr on 2008-07-06
The requirements for the server are documented here:
[http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/server-hw.html](http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/server-hw.html)

> Edubuntu, being a GNU/Linux based operating system, makes efficient use of memory. The usual formula that's used for adding memory to a thin client server is:

256 + (128 * users) MB

So, if your target is to have a server with 20 terminals, you'll need:

256 + (128 * 20) = 256 + 2560 = 2816 MB

Rounding up, you'll need 3 1 Gig simms. Making sure you've got enough memory is the single most important thing you can do to help the performance of an Edubuntu/LTSP thin client server. If you do not have enough memory in your server, you'll find your server will have to use the hard drive as an overflow "virtual" memory. Hard drives are much slower than memory, so you'll find things getting very slow if this happens.

If you intend to make heavy use of graphics work in your curriculum, you may want to add even more, perhaps doubling the previous estimate.

So about 2GB RAM should be reasonable.

And the processor:

> How fast a processor you need is entirely dependant on what programs you plan to use. Interactive games require a bit more than say, a word processor. If you plan to use Java and Flash plugins in your web browser, these can consume a lot of processing power. For a "mixed" model, i.e. some people playing TuxMath, a few people browsing the web, and a few people typing in OpenOffice.org, a 2GHz or better processor should be able to adequately handle 20 people with some minor delays. A 3GHz processor would be better. 

I would agree that Edubuntu is a good pace to start.  Some of the Apps are aimed at young children, [but]("http://edubuntu.org/Screenshots")...

> Edubuntu also provides three different theme setups, 'young', for younger users, 'plain' for a clean desktop setup, and 'default', which is a general purpose theme setup.

As mentioned - just move the panel to the bottom and remove the Places and System menus of Gnome.

I think it is even possible to rename "Applications" to "Start" - but have never tried.  The text config is normally /etc/xdg/menus/applications.menu on a desktop (uncertain with LTSP).

How to install: [https://wiki.edubuntu.org/HardyClassroomServer](https://wiki.edubuntu.org/HardyClassroomServer)

---

### Post by Linux&amp;Gsus on 2008-07-06
That is some good piece of information there, ugm6hr. This is just a cool forum. I love it.

So, I sort of know that the specs would not need to be astronomical. But that is just cool. I mean, we are talking about an just released OS, right. Actually I never understood why people thought that Linux needs a lot resources. Compare Hardy to Vista... Anyways, different topic.

Well, if I understood that right in this link >>[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall")<< then LTSP installation isn't going through Edubuntu anymore but through the "normal" Ubuntu via the alternate CD. Is that right? Does that mean that Edubuntu is no longer needed for LTSP unless I want the apps and desktop from  that distro? Or do I still need it for the actual LTSP setup? Please excuse if that is a dump question. But I have never done anything with LTSP before.

I guess I need to do some more reading and then write down a proposal. Then I'll see what else I need.

Cheers.

---

### Post by ugm6hr on 2008-07-06
> LTSP installation isn't going through Edubuntu anymore but through the "normal" Ubuntu via the alternate CD.
That is what I understand from that statement too, but haven't done this myself.

I am uncertain which components of Edubuntu are on the "Add-on CD", but believe it is basically the edubuntu-desktop components.

If you use Synaptic (or presumably Adept for you), you can search for edubuntu-desktop and see what its dependencies are.  Most are educational apps etc, but it does include "thin-client-manager-backend" which is not installed as part of the ltsp-server package.

So you may need to add a few packages manually to simplify things if you opt to avoid Edubuntu.

---

### Post by Linux&amp;Gsus on 2008-07-06
> **ugm6hr said:**
> ...Most are educational apps etc, but it does include "thin-client-manager-backend" which is not installed as part of the ltsp-server package.

So you may need to add a few packages manually to simplify things if you opt to avoid Edubuntu.

That would make sense. Thanks for the hint.

Which DE it really will be (if the proposal goes through anyways) is probably something I'll need to see on a test install with maybe just a couple clients or so. And then discuss with fellow admins and probably a few test persons.

---

### Post by ugm6hr on 2008-07-06
> **Linux&Gsus said:**
> Which DE it really will be (if the proposal goes through anyways) is probably something I'll need to see on a test install with maybe just a couple clients or so. And then discuss with fellow admins and probably a few test persons.

There is also an edubuntu-desktop-kde package that you might want to experiment with.

But I think that KDE has lost its LTS status (if that's important).

---

### Post by bodhi.zazen on 2008-07-06
> **Linux&Gsus said:**
> Well, if I understood that right in this link >>[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)<< then LTSP installation isn't going through Edubuntu anymore but through the "normal" Ubuntu via the alternate CD. Is that right? Does that mean that Edubuntu is no longer needed for LTSP unless I want the apps and desktop from  that distro? Or do I still need it for the actual LTSP setup? Please excuse if that is a dump question. But I have never done anything with LTSP before.

There are two options, both use the standard Ubuntu install CD + an add on Edubuntu CD.

1. Desktop -> Use the Ubuntu Desktop CD + edubuntu add on.

2. Server -> Use the Ubuntu Server CD (for LTSP) + edubuntu add on.

As I said, you can start with edubuntu which will configure your server + clients "automatically" and allow you to ease into installing LTSP.

You can, of course, set up LTSP without edubuntu. If nothing else the edubuntu documentation is very helpful.

---

### Post by Linux&amp;Gsus on 2008-07-14
Thanks again for all your help, guys. A test environment will be installed and, well, tested. That's what a test environment is for, I guess ;)
Then we'll see how it goes.

Thanks again, you're a great bunch of people.

---

### Post by altonbr on 2008-08-20
Just quickly, not speaking on LTSP but on making GNOME (for me) look like Windows:

**Add applications to desktop**
Look through your Applications menu and right-click all the applications you want your users to use and left-click "Add this launcher to desktop".

**Remove applications menu**
Once that is done, remove the "Applications Places System" menu.

**Remove shortcuts on top panel**
Delete 'Firefox', 'Help' and 'Evolution' shortcuts in the top panel.

**Move applets to bottom panel**
Move your 'date', 'sound' and 'notification area' applets to the bottom left hand corner like it is in Windows.

**Remove the top panel**

**Remove applets in bottom panel**
We will be adding the trash can to the desktop so you can get rid of the 'trash' applet. Also the 'workspace switcher' will not be needed as we will only have one workspace. Make sure there is only one work space (right-click > properties) and then delete the 'workspace switcher'

**Lockdown GNOME**
Hit alt + F2 to run a command (since you can no longer run the terminal if you did everything properly). Type 'gconf-editor' (without the quotes) and hit enter.

Now change these settings:
_desktop > gnome > lockdown_
check disable_command_line (this will disable hitting alt + F2 like you just did)
check disable_lock_screen
check disable_printing (if warranted)
check disable_print_setup
check disable_save_to_disk (if warranted)
check disable_user_switching

_apps > panel > global_
check disable_force_quit
check disable_lock_screen
check disable_log_out
check locked_down (to disable messing with the panel)

Any now your desktop should be (almost) fully locked down and looking similar to Windows!

**_Note_**
The program 'Lockdown Editor' or 'pessulus' also achieves the same effect instead of manually runing 'gconf-editor'

---

### Post by altonbr on 2008-08-20
Here's a screenshot so you know what I'm talking about...

---

