---
title: "itunes"
date: 2009-05-10
forum: North Carolina Team - US
---

### Post by gmoney671 on 2009-05-10
Has anyone found a way to run iTunes on Ubuntu 9.04 without errors? This is the only thing holding me back from fully converting to Linux. I have an iPhone and I need iTunes to work Pls. help!!!

---

### Post by undadecor on 2009-05-10
I don't know about that, but take a look at these if you haven't done so already:
[LIST]
[*][https://help.ubuntu.com/community/PortableDevices/iPhone]("https://help.ubuntu.com/community/PortableDevices/iPhone")
[*][http://ubuntuforums.org/showthread.php?t=588246]("http://ubuntuforums.org/showthread.php?t=588246")
[/LIST]

---

### Post by europa on 2009-05-14
When I was using iTunes with Linux, I used VirtualBox.  Install winxp on there along with iTunes. works just as well.

If you just want to update music, Songbird is great.

[http://getsongbird.com](http://getsongbird.com)

---

### Post by ReddogOne on 2009-05-18
> **europa said:**
> When I was using iTunes with Linux...

What I do as well. Works a treat. Not totally getting away from the evil MS but keeping it locked in a cage in a corner where it can't do no harm ;)

---

### Post by DLG102282 on 2009-05-18
> **ReddogOne said:**
> What I do as well. Works a treat. Not totally getting away from the evil MS but keeping it locked in a cage in a corner where it can't do no harm ;)
Have you tried running it in WINE?

---

### Post by blade1950 on 2009-05-18
I've found that the best solution is to drop ALL software that is MS based including the "Workarounds, ie, Wine, VB, etc) I have had very good success finding alternates that are native to Ubuntu. Try this one. It works quite well.
 
[http://banshee-project.org/](http://banshee-project.org/)
 
T

---

### Post by Paul41 on 2009-05-18
iTunes doesn't work in WINE ([http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)) but as suggested you could use VirtualBox.

---

### Post by ReddogOne on 2009-05-19
> **DLG102282 said:**
> Have you tried running it in WINE?

Yeah! Pants! Sure people can get it working with a bit of work but life is too short. 

Like the concept of WINE and wish it did work but I haven't the time to hack or contribute to the project so the one stop VirtualBox solution is the way for me.

---

### Post by shashikejayatunge on 2009-11-15
i  too  have  the  same  problem,,  i have  an ipod  touch,  and  tried  all  gtkpod,banshee,songbird,  but  those  dont  detect  my  ipod,, why  is  this hapening???

---

### Post by internalkernel on 2009-11-18
> **shashikejayatunge said:**
> i  too  have  the  same  problem,,  i have  an ipod  touch,  and  tried  all  gtkpod,banshee,songbird,  but  those  dont  detect  my  ipod,, why  is  this hapening???

What version of Ubuntu are you using? There was a known issue with 9.10 switching to device-kits to facilitate mounting and identification of ipods. So, Banshee, songbird and a few others had their ipod support broken. 

There are a few workarounds for this, I am still using Banshee with my ipod. It syncs everything including playcounts & ratings. Only a couple of notes to mind, it syncs one-way - from your playlist to the ipod. It's not bi-directional like iTunes. But, in my quest for an itunes replacement (that didn't require installing an entire OS) I've found Banshee to be the closest thing.

---

### Post by keenboy on 2009-11-30
The lack of iTunes for Ubuntu or any other Linux distro is worrying. It is a well documented fact that users who are used to using iTunes will dislike using anything else which makes the migration to linux very painful when it really shouldn't be.

I have been using Linux for a few years now and have migrated friends and family to Linux because their MS machines suffered from usual problems which stopped them from doing the basic things they wanted to do.

Now I get asked the question of "Can I use iTunes?". This is where the migration falls apart because the answer is of course, no.

iPods and iPhones are getting more and more popular every day and it's fair to say most people have one. My calculations tell me that if potential new ubuntu fans find out they cannot use iTunes to configure their apple devices the Ubuntu popularity will recede as the apple popularity grows.

I'm sorry this isn't an answer to the original question.

This has been an issue for ages and reiterating my point above it isn't the first time this question has been asked and until something gets done it definitely won't be the last time.

My questions to whoever it concerns (Mark Shuttleworth at Canonical) are:

i) Why can't iTunes be ported to Ubuntu?

ii) Realistically will it ever be ported to Ubuntu?

I think it's important to have these questions answered.

Thanks,

---

### Post by Paul41 on 2009-11-30
> **keenboy said:**
> The lack of iTunes for Ubuntu or any other Linux distro is worrying. It is a well documented fact that users who are used to using iTunes will dislike using anything else which makes the migration to linux very painful when it really shouldn't be.

I have been using Linux for a few years now and have migrated friends and family to Linux because their MS machines suffered from usual problems which stopped them from doing the basic things they wanted to do.

Now I get asked the question of "Can I use iTunes?". This is where the migration falls apart because the answer is of course, no.

iPods and iPhones are getting more and more popular every day and it's fair to say most people have one. My calculations tell me that if potential new ubuntu fans find out they cannot use iTunes to configure their apple devices the Ubuntu popularity will recede as the apple popularity grows.

I'm sorry this isn't an answer to the original question.

This has been an issue for ages and reiterating my point above it isn't the first time this question has been asked and until something gets done it definitely won't be the last time.

My questions to whoever it concerns (Mark Shuttleworth at Canonical) are:

i) Why can't iTunes be ported to Ubuntu?

ii) Realistically will it ever be ported to Ubuntu?

I think it's important to have these questions answered.

Thanks,

iTunes can't be ported to Ubuntu because it is a proprietary Apple application. The only way to get it to work natively in Linux would be for Apple to release a Linux version. Realistically, I don't see that ever happening.

---

### Post by internalkernel on 2009-11-30
> **keenboy said:**
> Now I get asked the question of "Can I use iTunes?". This is where the migration falls apart because the answer is of course, no.

iPods and iPhones are getting more and more popular every day and it's fair to say most people have one. My calculations tell me that if potential new ubuntu fans find out they cannot use iTunes to configure their apple devices the Ubuntu popularity will recede as the apple popularity grows.

My questions to whoever it concerns (Mark Shuttleworth at Canonical) are:

i) Why can't iTunes be ported to Ubuntu?

ii) Realistically will it ever be ported to Ubuntu?

I'm going to agree with Paul41 here... 

Apple will never release iTunes for Linux, not before Hell freezes over at least... Seriously, look at the battle that Palm Pre and Apple had been going through earlier this year. Everytime Palm had their system working, Apple _intentionally_ broke support in the next release of iTunes. 

What do you think the real problem is here? Is it that Apple hasn't released a version of iTunes for Linux or does it have to do with the fact that every time another application builds support for iPods, iTouchs - that Apple breaks that support? 

Let's get right down to brass tacks... OSX is unix based, it's a port of BSD for God sakes - that should make porting iTunes to another Linux variant pretty easy. Probably easier than porting it to Windows... Apple has taken everything from the Open Source community and has given nothing back; not even a port of iTunes... I wouldn't hold your breath for it to happen. 

AND, yes you are totally correct. Helping people who own these devices migrate to linux is usually met with head aches. They don't care about the politics of open source, or the fact that Apple is worse than Microsoft... they just want that 200$ device to work the way it's supposed to. 

My advice... use Windows from a Virtual Machine. Yes, it sucks... but usually Linux support is only 6 months behind the popular main stream support so it'll catch up - it's usually a temporary situation. And get involved with the projects that are making a difference, help them where ever you can - you don't have to be a programmer to help... this is an open source community.

---

### Post by heepie on 2010-01-15
I couple of days ago trying to install ie4linux i discoverd **playonlinux** application... Lets you install all kinds of windows applications: from ie, itunes, office 2007 and a tone of games

sudo apt-get playonlinux

or just go to the respiratories

---

### Post by gijsterbeek on 2010-02-04
> **DLG102282 said:**
> Have you tried running it in WINE?

Works quite ok with current stable Wine version. I had to install an old iTunes 7.3.2 installer (available at [http://www.oldapps.com/itunes.php](http://www.oldapps.com/itunes.php) ) to be able to play my own music. Connecting to the iTunes store didn't work, though.

---

### Post by tareksobh on 2010-03-16
Okay... This might sound really stupid, but if Wine can run Windows applications on Ubuntu, is there a Linux application that can run Mac applications on Ubuntu? At least, if such an application exists, we could try installing the Mac version of iTunes on Ubuntu!!

---

### Post by Paul41 on 2010-03-16
> **tareksobh said:**
> Okay... This might sound really stupid, but if Wine can run Windows applications on Ubuntu, is there a Linux application that can run Mac applications on Ubuntu? At least, if such an application exists, we could try installing the Mac version of iTunes on Ubuntu!!

As far as I know there is nothing that will allow you to run Mac applications.

---

### Post by tyre_ on 2010-03-20
> **blade1950 said:**
> I've found that the best solution is to drop ALL software that is MS based including the "Workarounds, ie, Wine, VB, etc) I have had very good success finding alternates that are native to Ubuntu. Try this one. It works quite well.
 
[http://banshee-project.org/](http://banshee-project.org/)
 
T

Awesome!  Just what I was looking for :D

---

### Post by vpraveen84 on 2010-03-21
> **heepie said:**
> I couple of days ago trying to install ie4linux i discoverd **playonlinux** application... Lets you install all kinds of windows applications: from ie, itunes, office 2007 and a tone of games

sudo apt-get playonlinux

or just go to the respiratories

itunes 7 doesn't seem to work well through this. Tried it on ubuntu 9.10.

---

### Post by cph05a on 2010-04-18
iTunes 7.6 and 8.2 both run in Crossover 9.0. iTunes 8.2 seems to run a lot faster than 7.6. 

When installing itunes, put it in a winxp bottle. When asked, uncheck the box for automatic updates and say no to auto run. I get an error message saying the installation failed, but in fact it runs quite well.

I'd recommend using ether songbird or amarok, but if you must have itunes it can be done.

---

### Post by wharfrat507 on 2010-05-21
With the latest long term release 10.04 there seems to be native support for the Iphone and Ipod. Please see link below.
[http://www.osnews.com/story/22942/Ubuntu_10_04_To_Support_iPhone_iPod_Touch_](http://www.osnews.com/story/22942/Ubuntu_10_04_To_Support_iPhone_iPod_Touch_)

---

### Post by elidoperezmd on 2010-05-26
but how about the apps, can i sync apps thru amarok?

---

### Post by internalkernel on 2010-05-27
> **elidoperezmd said:**
> but how about the apps, can i sync apps thru amarok?

That seems to be the biggest issue, syncing is something of a work in progress for most of these apps. But never the less, it is progress that Ubuntu can recognize and at least "push" files to these devices. I'm sure syncing is only a matter of time... 

The only apps that I'm aware of that can sync, are gtk-pod and Banshee. I've had horrible luck running Banshee as of their last release (1.6), lots of freezes and it always seems to be maxing one of my CPUs out. But your mileage may vary.

As a result I've resorted to gtk-pod, although this is not without it's downside - I had a difficult time figuring out just how to sync my ipod. It's not exactly intuitive... 

On the plus side it does allow you to set up smart playlists that the ipod recognizes, a feature Banshee did not have. 

good luck...

---

