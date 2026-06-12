---
title: "Total beginner here."
date: 2007-07-08
forum: Pennsylvania Team - US
---

### Post by ShadowdogKGB on 2007-07-08
Hi, I just got up and running with Ubuntu 7.04 on an older machine here for the first time. I was very impressed because it recognized all the hardware without a hitch.

Now on to the next hurdle. If I can get this thing to run the popular chat programs, connect to the common wireless routers from Lynksys and Belkin, and connect to the popular printers from Lexmark and HP; and do this all without too much difficulty, I'd have something worthwhile to offer people who can't afford/or don't want to buy  Windows XP. I fix computers here in PA.

---

### Post by lisati on 2007-07-08
There are a couple of chat programs that come pre-installed. I haven't actually tried them yet, but they can be found at on the "Applications"->"Internet" menu. There is also available a version of SKYPE that can be installed. If you go to [www.skype.com](www.skype.com), you'll have to click on the "Download"  button next to the "Home" button to get a copy that works with Ubuntu. I have a copy up and running on my laptop.

---

### Post by lamalex on 2007-07-08
the installed "gaim" does AOL Im, Gadu-Gadu, Google Talk, Groupwise, ICQ, IRC, MSN, QQ, SIMPLE, XAMP, Yahoo, and Zephyr. Are there even any more? I hope that helps ya!

---

### Post by jedijf on 2007-07-08
Welcome!  I think that all of your expectations can very suitably be met with ubuntu, and its various flavors or kubuntu, xubuntu, and edubuntu, just to name the most popular.  

Take time to learn what you have just installed, and then venture to the other flavors.  You are in a great position to influence people and at least give them the option of the ubuntu's and all that they offer.

Hopefully, if you haven't already, you will join the LoCo, and start to get involved with projects in your geographic region.

Great to have you on board.  Check out [www.meetlinux.com](www.meetlinux.com) for a listing of all of this LoCo's resources and planned events.

:)

---

### Post by kejava on 2007-07-08
Sounds like you're looking for a chat client like [gaim]("http://pidgin.im/pidgin/home/").  Don't be thrown off by the link.  I believe gaim is being replaced by pidgin, although it's not in the repositories yet ... that I know of.  Anyway, don't let that throw you off.  Gaim should be installed by default on regular Ubuntu.  If it's not, just open up Synaptic Package Manager, search for "gaim", and install it.

As for working with specific routers, you shouldn't have any issue.  The main problem you could have is getting Linux to work with your wireless network adapter.  Linux is pretty good with supporting most adapters but there are still some odd balls.  Often times you can just plug them in, they're detected, and your given a list of routers to connect to.  Keep in mind, some old adapters don't support WPA-PSK.  Let us know what make/model you have.

Many printers are supported.  I haven't had any issues lately.  Any specific model you're interested in?

-kevin

---

### Post by ShadowdogKGB on 2007-07-08
Ok sounds like a plan. I have a question though. I'm not use to the install procedure. Like for instance, Adobe Flash Player has a plug-in for Firefox. I download it, open it and extract it. But after that I'm completely clueless.

---

### Post by kejava on 2007-07-08
I haven't installed it yet but the [Adobe Flash Player plugin]("https://help.ubuntu.com/community/MultimediaApplications#head-8da6bb74fc999112e0c2ec15e70c1cb4a1187107") is also available from the repositories.  Just open Synaptic Package Manager (SPM) and search for "flashplugin-nonfree".

The download from the Adobe site would require more work but we could walk you through it.  Try the one through SPM first though.

---

### Post by ShadowdogKGB on 2007-07-08
Well, I am very appreciative of the help. However, you'll have to think of me as someone who has just been dropped into a strange foreign city. I am truly lost. I'll get the hang of it I'm sure. 

When I extract the Adobe plug-in, the readme says to navigate to the folder and type in + $ ./flashplayer-installer.

I don't know how to navigate in Terminal. I am stuck in owner@owner-desktop: -$

---

### Post by zero244 on 2007-07-08
I use Kopete for Yahoo and MSN messaging. Kopete is actually a KDE app but runs fine on Gnome.
There is a pretty good chance your printers will work
Scanners are a little iffy a lot of the time.
Good Luck and welcome to the forum and the world of Linux minus MS.

---

### Post by ShadowdogKGB on 2007-07-08
I fix computers here in rural PA. Ninety-nine percent of them are just home computers that are used by mostly women and kids. They do all the usual stuff like chat programs, online games like Pogo.com, print and store photos, and some online shopping like ebay. I'd say 90% of the people who call me are utterly and completely clueless about computers; and that's just with Windows XP. I couldn't imagine the calls I'd be getting if I threw Ubuntu in their lap without first learning it myself and having a rock solid package I can give them.

So, for just starting out, I think I've got something I can work with. Only time will tell. I do have a candidate for my first Ubuntu machine though. I'm gonna give it a shot. I just need a little more time to work it out.

---

### Post by gwengirl5 on 2007-07-08
> **ShadowdogKGB said:**
> Ok sounds like a plan. I have a question though. I'm not use to the install procedure. Like for instance, Adobe Flash Player has a plug-in for Firefox. I download it, open it and extract it. But after that I'm completely clueless.


I was having the exact same problem. I uninstalled Ubuntu and went back to windows because I was banging my head about it. I finally figured out I should probably ask for help and have decided to use my old old gaming PC and try it out there first. 

I'm going to give it one more try. I really hope I can get flash and shockwave installed.

---

### Post by kejava on 2007-07-08
ShadowdogKGB and gwengirl5,

Did you both find that installing the "flashplugin-nonfree" package from Synaptic Package Manager did not work?  It basically automates what we used to have to do from the command line with the Adobe download.  I just tried it and it seemed to work fine.

I'm not sure about shockwave though.  Perhaps someone else can comment on that.

---

### Post by Cuogar on 2007-07-08
> **ShadowdogKGB said:**
> Well, I am very appreciative of the help. However, you'll have to think of me as someone who has just been dropped into a strange foreign city. I am truly lost. I'll get the hang of it I'm sure. 

When I extract the Adobe plug-in, the readme says to navigate to the folder and type in + $ ./flashplayer-installer.

I don't know how to navigate in Terminal. I am stuck in owner@owner-desktop: -$

You can use the **cd** (change Directory) command to move around. As a fellow beginner, I often use cd and then **ls** (List, I think) to get a list of the directories and files in my current location. An example would be to get to the root directory I would type **cd /**, to go into a directory in the current location I can type **cd /usr** or I can go to a specific spot by using the **cd** command and the full path name. a better explanation of how to move around can be found in the documentation found on the Ubuntu website.
Here is the part about the Command Line Interface, Terminal. though admittedly, it hasn't helped past being able to move around.:-(
[https://help.ubuntu.com/7.04/basic-commands/C/](https://help.ubuntu.com/7.04/basic-commands/C/)
Hope this helps and good luck.

---

### Post by ShadowdogKGB on 2007-07-08
Firefox automatically installed it for me when I went to Pogo.com. Whew. 

If I'm going to offer machines with Ubuntu on them they need to be as Windows-like as possible. :(
I'm getting the hang of it though. I've got Quicktime to install, now working on Windows media player. I've installed WINE but I'm not sure yet how it works. I'd like to be able to install and run Microsoft apps because that's familiar territory for most folks I deal with. Limewire installed without a hitch. 

Nothin's perfect but we're getting there!

---

### Post by gwengirl5 on 2007-07-08
> **kejava said:**
> ShadowdogKGB and gwengirl5,

Did you both find that installing the "flashplugin-nonfree" package from Synaptic Package Manager did not work?  It basically automates what we used to have to do from the command line with the Adobe download.  I just tried it and it seemed to work fine.

I'm not sure about shockwave though.  Perhaps someone else can comment on that.

I haven't tried it tonight. I read your suggestion though.I've been trying to fix another computer of mine. It's a rather new gaming PC and I've had my mind on that most of the night.

I'll go back to the Ubuntu machine tomorrow :)

---

### Post by ShadowdogKGB on 2007-07-09
I'm trying to install Cabextract-1.2

I navigated to the folder using terminal and used the /configure command. It starts to run but then gives me "error: c compiler cannot create executable"

How does the extract function work (not Cabextract)? I extract the folder but I'm not sure if I'm doing it right.

---

### Post by kejava on 2007-07-09
ShadowdogKGB,

Are you referring to this [cabextract]("http://www.kyz.uklinux.net/cabextract.php") application?  If so, it's already in the Ubuntu package repositories.  No need to compile it.

Just go to System --> Administration --> Synaptic Package Manager.  Click on the Search button and enter "cabextract".

As a beginner, why aren't you installing your applications from SPM?  Compiling you're own packages from source is a bit of an advanced topic.  It's not that I don't think you're capable of it, but why do things the hard way?  Someone already went through the trouble of compiling/packaging most of the applications you've mentioned.

If there's a reason you don't want to use SPM, let me know and I'll stop suggesting it.

---

### Post by ShadowdogKGB on 2007-07-09
I'm getting the hang of it. I didn't realize the SPM had it in there. I needed Cabextract and WINE to make IE6 work. I got it to work finally. I'm trying to make the machine as Windows-like as possible.

---

### Post by jedijf on 2007-07-09
use firefox as your browser - many windows people are currently using firefox or at least considering it.

---

### Post by ShadowdogKGB on 2007-07-09
I wanted to try the Codeweaver demo but I couldn't get it to install. It's supposed to be able to run MS Office 2003 and other Windows apps. When I open it, it says it can't open it. I tried the install script from their web page but it didn't work either.

---

### Post by jedijf on 2007-07-10
Shadow,

From what I see from your posts, it is as if you want to run Windows on Linux.  

What makes Linux special is the apps that are created for linux, some of which (many) are very similar to their Windows cousin.

It is just my opinion, that to give yourself the true linux experience, you should explore the apps already available in the Ubuntu install and get familiar with those.

If you decide that you need or want to explore more specific apps, about 18,000 more are available through synaptic.

Also, before you go to synaptic, be sure to check the add/remove programs part of the application menu; the software may already be downloaded, just not installed.

For help finding comparable programs in linux for windows apps, ask here or search google.  Asking here will give feedback to the experience of the particular app, and google will show you how many options linux has available.

As Kejava said, initially you may want to stick to apps that you find through synaptic to manage the download and all the dependencies associated with the app.  In time, compiling is definitely an option.

Hope this helps.

---

### Post by ShadowdogKGB on 2007-07-10
I fix computers here in PA. I keep a couple of used machines here for sale. I'd like to be able to sell them with Ubuntu installed on them because a lot of people I see are rather poor. They mostly want to use chat, email and internet. Some may need office apps but not much.

---

### Post by jedijf on 2007-07-10
shadow,

now we're talking 

im - gaim

email - web based via firefox

email - client based - thunderbird

office apps - open office

for lesser machines  xubuntu

gaim - thunderbird or web based email - abiword for word proc and gnumeric for spreadsheets

more info on xubuntu and its apps here :

[http://linux.about.com/od/xubuntu_doc/a/xubudg21t01.htm](http://linux.about.com/od/xubuntu_doc/a/xubudg21t01.htm)

old macs same stuff ppc brings them back to life also

---

### Post by jedijf on 2007-07-10
shadow and all newcomers:

I apologize that I forgot this, sometimes it's hard to remember being new.

A great place to start is right in:

Places --> Home Folder --> Examples

From there I would suggest Book-toc

after reading those chapters from the Ubuntu book, anything that interests you from the examples, or all of them, would be a great beginning.

Welcome, keep up the good work.

---

### Post by ShadowdogKGB on 2007-08-07
Well it's been a while. I've come to one conclusion though. There's no way I'm gonna put this in front of a customer. There's no way the average person, housewife, layman, whoever, is going to tolerate this. Sure, I can handle it. But man, until it gets to be completey automated, with as minimal user input as possible, and interacts with MS Windows seamlessly  it's just not gonna happen as far as I can tell. It's gonna have to be one or the other. It's a long struggle for sure.

I know I'm not helping much by my complaining. I'm sorry. I'm not a programmer. People just want to turn on their computers and have them work without giving them fits, and without having to go through convoluted steps to make programs work.It's just not there yet. Perhaps in 5 to 10 years. But not today.

---

### Post by elizabeth on 2007-08-08
FWIW, one of my favorite things about the time I spent in the housewife role was the time I had to learn Linux.

I now work as a Debian Sysadmin.

---

### Post by jedijf on 2007-08-08
Shadow,
Thanks for the experience and the feedback.

I think, as I may have mentioned in a previous post, that the approach taken was flawed.

Linux, whatever flavor, is NOT and does not CLAIM to be windows.  Trying to fit a round peg into a square hole will never work.  (Well, not never, but it is difficult and frustrating; I still attempt at times)

Taken on its own merit, with no preconceptions, may be a better way to approach a switch.  Not trying to do things the exact (software wise via wine or other) same way.

I think (actually I know, from many installs for prior windows users) that Ubuntu has everything ready to run out of the box for the average user.
     1) Gnome / KDE / Xfce Gui's
     2) Firefox Web Browser
     3) Open Office Suite
     4) F-Spot Photo Software
     5) Gimp - for the more artistically inclined
     6) Rythmbox - Media player
     7) Gaim / Pidgin - Instant Messaging
8)Thunderbird - Email Client

Usually. I find, that the average user doesn't require much more than that; and if they do we can usually find a program that satisfies that itch.

Don't give up, keep playing.

---

### Post by lamalex on 2007-08-08
> **ShadowdogKGB said:**
> Well it's been a while. I've come to one conclusion though. There's no way I'm gonna put this in front of a customer. There's no way the average person, housewife, layman, whoever, is going to tolerate this. Sure, I can handle it. But man, until it gets to be completey automated, with as minimal user input as possible, and interacts with MS Windows seamlessly  it's just not gonna happen as far as I can tell. It's gonna have to be one or the other. It's a long struggle for sure.

I know I'm not helping much by my complaining. I'm sorry. I'm not a programmer. People just want to turn on their computers and have them work without giving them fits, and without having to go through convoluted steps to make programs work.It's just not there yet. Perhaps in 5 to 10 years. But not today.

Seems that you're a 'windows' person. Meaning, you'd rather have your computer tell *you* what to do, instead of you tell your computer what to do. Minimal user input? Then what's the point of the computer?

How about MS work seamlessly with Linux? That's 100% possible, specs for /all/ of our software (not just specs, source code too) are available for ANYONE to read, MS doesn't offer that. Their specs for their 'standards' and formats are poorly written and convoluted, not to mention not available under any sort of reasonable license. Lack of seamless interaction isn't our fault, it's theirs. (and even without their source or quality specs, we've still make it happen), ever use samba, and I mean, really use samba, as a full domain controller, that works perfectly with active directory, usually better than MS AD?

Have to go through convoluted steps to make programs work? Have you ever fixed a windows computer? 
[LIST]
[*]Linux -> a few shell commands and an edit to a config file
[*]Windows -> Search through 8 submenus and then use some archaic tool that was carried over from Win95 that hardly worked then
[/LIST]

---

