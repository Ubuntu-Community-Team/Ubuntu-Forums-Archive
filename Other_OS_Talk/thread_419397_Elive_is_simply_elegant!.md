---
title: "Elive is simply elegant!"
date: 2007-04-23
forum: Other OS Talk
---

### Post by RAV TUX on 2007-04-23
I have been using Elive 0.6.7 for a couple of days now and I am in love with e17...

I can live without Beryl, GNOME, KDE, XFCE and even Fluxbox,...enlightenment blows them all away!

I hope to utilize e17 in future builds of Oz, also.

I highly suggest that if you want to see the true future of Linux, you try and install Elive...

---

### Post by RAV TUX on 2007-04-23
very unlike me not to include a screenshot, now all though you can't tell it from this picture the wallpaper is animated the stars sparkle.....also the elive logo reflects on the water as if it is being reflected in the waves, normally the elive logo is very faint but upon mouse over it becomes brighter and reflectively dances on the water,...then the statement 
"where Debian meets Enlightenment" comes up, all very classy and subtle

---

### Post by RAV TUX on 2007-04-23
If you know Debian, you know Elive since Elive is built on a Morphix base, which is built on a Knoppix base, which is built on a Debian base....

If you like apt-get then you will be comfortable with Elive

While not really an accurate comparison I like e17 better then Beryl.

also note: I have along side IceWeasel both the Opera and Konqueror browsers....

---

### Post by Rui Pais on 2007-04-23
You don't even need to change distro.

If you want e17, using Ubuntu, [just compile form latest source]("http://ubuntuforums.org/showthread.php?t=97199") or [go the easy way with deb packages]("http://ubuntuforums.org/showthread.php?t=319336").

e17 is really beautiful, fast, light and can be very productive in terms of use :)

---

### Post by floke on 2007-04-23
Anyone know if the debs work with Feisty?

---

### Post by igknighted on 2007-04-23
> **Steve.K said:**
> Anyone know if the debs work with Feisty?

I would recommend using the newest sources from a developing project like e17 to get the new features anyways.  I would never use old debs, chances are libraries have changed and it would really mess stuff up.

---

### Post by Rui Pais on 2007-04-23
> **Steve.K said:**
> Anyone know if the debs work with Feisty?

the debs on the 2nd link of my post are usually very updated, besides e17 is very independent, don't relly on much of ubuntu base system, so it more or less independent of which version you have. 

But i recommend too install from source. It install under /opt/ not mixing libs and apps with your system and making easy to remove or backup. The only thing with feisty is ensure you don't have automake 1.10 but 1.9 (the default anyway) cause some apps won't compile with the newest automake (and some app won't compile with older version of gcc, but thats not your case).

---

### Post by kazuya on 2007-04-23
i love elive as well. their newest 0.7 release is phenominal. I have it installed in along with Sabayon on my other machine. It just looks way beautiful and functional and fast..
I used to like Beryl as well, But I e17 and e16 are just simply unmatched. Give it a try guys..

The engage thing is one of the things I love about it as well as the theme manager..
I am trying to learn more about the customizability of it.

---

### Post by floke on 2007-04-23
Ok ,so after messing about with Enlightenment all day (bang goes work!) - I couldn't get the code to compile so had to use the debs by the way; and I can't download the LiveCD of Elive since it takes me to a Spanish paypal site after asking me for a donation (see here: [http://ubuntuforums.org/showthread.php?t=419706)](http://ubuntuforums.org/showthread.php?t=419706))!! - so - I'm going to grab a copy of it in the latest LinuxWorld on my way home and try it out.

My question, then, is this: How do I dual-boot Elive with Ubuntu? Will it's grub recognise my Feisty partition? I tried Sabayon a couple of weeks ago and it's grub completely refused to recognise anything other than itself (I ended up reinstalling ubuntu over it), so don't want any hassles (or surprises :) ). Since Elive is Debian-based I'm reckoning it should pick up ubuntu.

In short: How easy is it to dual-boot with this thing?

Cheers

---

### Post by mips on 2007-04-23
> **Steve.K said:**
> Will it's grub recognise my Feisty partition? I tried Sabayon a couple of weeks ago and it's grub completely refused to recognise anything other than itself (I ended up reinstalling ubuntu over it), so don't want any hassles (or surprises :) ). Since Elive is Debian-based I'm reckoning it should pick up ubuntu.

In short: How easy is it to dual-boot with this thing?

Cheers

You will only know once you installed it. The worst that could happen is that you would have to edit your /boot/grub/menu.lst file in the elive partition.

---

### Post by plb on 2007-04-23
enlightenment has always been great. e16 was one of the coolest things when it first came out.

---

### Post by john_spiral on 2007-04-23
> **Steve.K said:**
> My question, then, is this: How do I dual-boot Elive with Ubuntu? Will it's grub recognise my Feisty partition? I tried Sabayon a couple of weeks ago and it's grub completely refused to recognise anything other than itself (I ended up reinstalling ubuntu over it), so don't want any hassles (or surprises :) ). Since Elive is Debian-based I'm reckoning it should pick up ubuntu.

In short: How easy is it to dual-boot with this thing?

Cheers

Got it running the other night, boot off Elive CD, choose the install icon bottom right, during the install it will bring up gparted (used to resize partition). Don't install grub. 

Create an entry in your existing menu.lst to look like the following - will look slightly different for later versions:

title		Elive
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.18-elive root=/dev/hdb4 ro quiet
initrd		/boot/initrd.img-2.6.18-elive
boot

voila!

---

### Post by floke on 2007-04-23
Cheers John

Have actually downloaded e17 now, after trying the EliveCD 0.6.5 version, which didn't work too well with my touchpad and no wireless, so I guess I'll wait until the development moves on a bit. But Enlightenment is great :)

---

### Post by Rui Pais on 2007-04-24
> **Steve.K said:**
> Cheers John

Have actually downloaded e17 now, after trying the EliveCD 0.6.5 version, which didn't work too well with my touchpad and no wireless, so I guess I'll wait until the development moves on a bit. But Enlightenment is great :)

elive is just a debian with a stabilized version of e17 and personal theme. 

elive it's nice if you don't have a linux installed. If you already have ubuntu why install another debian linux, specially if you don't fill comfortable with grub install/config?

If you installed e17 on ubuntu and **its working** then only thing different from elive is the theme that you can get from the cd (mount it and do a search for edj files, copy it to your .e/e/themes/ folder)

---

### Post by raul_ on 2007-04-24
Would someone be kind enough to attach the theme files? :mrgreen:

---

### Post by floke on 2007-04-24
> **Rui Pais said:**
> elive is just a debian with a stabilized version of e17 and personal theme. 

elive it's nice if you don't have a linux installed. If you already have ubuntu why install another debian linux, specially if you don't fill comfortable with grub install/config?

If you installed e17 on ubuntu and **its working** then only thing different from elive is the theme that you can get from the cd (mount it and do a search for edj files, copy it to your .e/e/themes/ folder)

Lol! I thought exactly this last night as I was trying to get to sleep! Am about to try it now.

 Elive also has the engage dock, an integrated file manager (you need to install Thunar of something else, eg PCManWM) with an e71 session; and you won't get the user-panel configuration wotsit (although to be honest I didn't think it looked that good - certainly a bit out of place compared to the artistic merits of the rest of the package).

But I'm sure it'll be very good when it;s 'finished', and it deserves to do very well.

---

### Post by floke on 2007-04-24
> **raul_ said:**
> Would someone be kind enough to attach the theme files? :mrgreen:

Am about to go get them, so will stick them up shortly....

---

### Post by floke on 2007-04-24
Pah! My work PC only has a CDrom player and can't pick up the DVD.
Will have to wait until I get home tonight to do this.
I'll post them up then if no-one does it before.

---

### Post by Sunflower1970 on 2007-04-24
Took me a while to get used to how get around in E17, and configure things, but now that I know, I really do like it. Fast. Elegant. 

I installed E17 over Ubuntu, though...although when I was originally looking around at distros, Elive was one of the many I had d/l'ed to try out a while back :)

---

### Post by mech7 on 2007-04-24
Installing it now the screenshot looks cool :D hope someone can upload the theme :D

---

### Post by raul_ on 2007-04-24
The most "wow"ing thing in E17 has to be the bling in the bars and the animated backgrounds

---

### Post by igknighted on 2007-04-24
I tried it out on the liveCD and wasn't terribly impressed.  There were certainly some very nice effects, but difficulty configuring it, the slowness of the gui, and the awkward nature of the menu structure were too much.  Once they stop trying to bling the menu's and just make them work I will try it again.

---

### Post by floke on 2007-04-24
Ok, bad news.
First, I couldn't access themes from the DVD by mounting it in Feisty and searching through the directories, since the filestructure isn't laid out like this (at least not in this LinuxFormat version);
Second - I booted into the DVD and copied the theme files over to my usb disk, but e17 doesn't recognise them as theme files either if you try to import them or copy them directly into the .e/e/themes folder;
Third - you can't upload them here in any case since they are an invalid file format (.edj)

Hmmpfh.

---

### Post by igknighted on 2007-04-24
> **Steve.K said:**
> Ok, bad news.
First, I couldn't access themes from the DVD by mounting it in Feisty and searching through the directories, since the filestructure isn't laid out like this (at least not in this LinuxFormat version);
Second - I booted into the DVD and copied the theme files over to my usb disk, but e17 doesn't recognise them as theme files either if you try to import them or copy them directly into the .e/e/themes folder;
Third - you can't upload them here in any case since they are an invalid file format (.edj)

Hmmpfh.

tar/gzip them first, then you can upload here

---

### Post by Rui Pais on 2007-04-24
> **Steve.K said:**
> Ok, bad news.
First, I couldn't access themes from the DVD by mounting it in Feisty and searching through the directories, since the filestructure isn't laid out like this (at least not in this LinuxFormat version);
Second - I booted into the DVD and copied the theme files over to my usb disk, but e17 doesn't recognise them as theme files either if you try to import them or copy them directly into the .e/e/themes folder;
Third - you can't upload them here in any case since they are an invalid file format (.edj)

Hmmpfh.

thats because the themes from elive must came from an older version od e17.
There has been a lot of changes in the API that broke the themes in the lasts times...

---

### Post by floke on 2007-04-24
Ok,
Figured out how to do it - but the files are too big to post here.
They are around 1.5mb each!

---

### Post by floke on 2007-04-24
The night bling theme is in the repos though - but you have to select it since it isn't installed from the e17 repos by default.

---

### Post by raul_ on 2007-04-25
Could you post the links to them? Or the packages name if that's the case :) I confess that i prefer the Day theme

---

### Post by raul_ on 2007-04-25
Since we're at it, does anyone know how to install the Engage module? I heard that the project was dead, but it's the only thing i need in E17: a task switcher and a notification area

---

### Post by floke on 2007-04-25
I am using the repositories:

[http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy

The theme is called 'night bling'. The Japan 2007 theme works fine as well, and I think there are a couple of others. Would have posted them here, but the night-bling theme is 2.4mb alone!

Hope this helps

* EDIT * From what I read, Engage is being remade to fit in with the latest code, but the origjnal developer has now left it so it might take a while

---

### Post by FuturePilot on 2007-05-20
The E17 desktop is elegant. In fact it's very beautiful. Whoever started the project had a great idea to center it around some nice eye candy. But I feel that it still needs some work. Either that or I'm not used to these minimal DEs. I kind of miss an archive manager and Gdebi.

---

### Post by Rui Pais on 2007-05-21
> **FuturePilot said:**
> The E17 desktop is elegant. In fact it's very beautiful. Whoever started the project had a great idea to center it around some nice eye candy. But I feel that it still needs some work. Either that or I'm not used to these minimal DEs. I kind of miss an archive manager and Gdebi.

well, i'm not sure that e17 even try to be a really "Desktop Environment" offering a full set of apps for desktop end user... 
the case of gdebi is even worst because it's very distro dependent. If developers of e17 use distros based on rpm or pkg (just as examples, i think they mainly use crux, arch and gentoo) they wont care fore such a thing as a gtk (non e) frontend for an apt. 

But you can always use dpkg on command line, or apt-get gdebi (with some dependencies of gnome...)

You can check too for xfce apps that are smaller and with less dependencies than gnomes equivalents and use in conjugation of e17 (and avoid the constant reinvention of the wheel). Besides file-roller you can use xarchiver or xarchive (this last for more compression formats).

In a general there are always command line independent of the DE apps, or "3rd parties" that offers the functionality of the big DEs equivalents.

---

### Post by RAV TUX on 2007-05-21
> **FuturePilot said:**
> The E17 desktop is elegant. In fact it's very beautiful. Whoever started the project had a great idea to center it around some nice eye candy. But I feel that it still needs some work. Either that or I'm not used to these minimal DEs. I kind of miss an archive manager and Gdebi.are you using the elive OS or just the e17 desktop?

---

### Post by FuturePilot on 2007-05-21
> **RAV TUX said:**
> are you using the elive OS or just the e17 desktop?
I tried the Elive OS and then I also installed e17 on Ubuntu.

---

### Post by RAV TUX on 2007-05-21
> **FuturePilot said:**
> I tried the Elive OS and then I also installed e17 on Ubuntu.
Which do you like better?

I love the elive OS, if I ever went back to a Debian based OS as my primary distro, it would be elive.

---

### Post by FuturePilot on 2007-05-22
I like Elive better. The e17 for Ubuntu is set up way different. I really like that one dark theme. It's really shiny:)

---

### Post by RAV TUX on 2007-05-23
> **FuturePilot said:**
> I like Elive better. The e17 for Ubuntu is set up way different. I really like that one dark theme. It's really shiny:)

I love elive and rank it as one of the top Linux distros of all time, right next to Wolvix.

---

### Post by Freddy on 2007-05-27
Thanks RAV TUX for this post on this great distro, I'm completely in love. I tend to use my terminal and more terminal driven programs now and I really like it.

This will be what I'm going to use for quite some time, atleast until KDE 4 goes gold, I have high hopes for that desktop but now I'm tired of all desktop managers (I used Vista for a week :-)).

---

### Post by markon24 on 2007-05-27
elive is way faster than ubuntu  I should say debian etch is...Nice distro i'm imprest.

---

### Post by RAV TUX on 2007-05-27
> **markon24 said:**
> elive is way faster than ubuntu  I should say debian etch is...Nice distro I'm imprest.

This is a very true and factual statement, I dual booted elive with knoppix installed for quite a while. I have yet to find many Linux distributions as fast as elive. 

> **Freddy said:**
> Thanks RAV TUX for this post on this great distro, I'm completely in love. I tend to use my terminal and more terminal driven programs now and I really like it.

This will be what I'm going to use for quite some time, atleast until KDE 4 goes gold, I have high hopes for that desktop but now I'm tired of all desktop managers (I used Vista for a week :-)).

Good Welcome Freddy even though I develop my own flavor of Linux I feel it is important to keep my finger on the pulse of Linux development. I take great pride in factually reporting my experience so that others like yourself can benefit from.

KDE 4 I trust will be awesome, I am a great fan of KDE, honestly both Gnome and KDE are great.

I like KDE mostly for it's KDE applications, fortunately these can be used actively in e17 as well as Gnome. 

The elive developers have done an awesome job and give to us a unique and awesome environment, E is Linux enlightenment.

---

### Post by Freddy on 2007-05-28
Someone might be able to help me with a little Elive problem of mine cause unfortunately the Elive forums are kind of dead :-(. 

1) I really dislike XMMS so I called up apt-get and got it to fetch me the superior Audacious, all this worked fine and I can call the program up with a little help from the terminal but how do I add it to iBar and the rightclick menu under the sub menu Audio.

2) How do I remove that battery and temp applet, I have seen some folks using a applet with a clock in the southeast corner, how can I use that one instead?

Ohh and I'm using E17. Thanks

---

### Post by Rui Pais on 2007-05-28
> **Freddy said:**
> Someone might be able to help me with a little Elive problem of mine cause unfortunately the Elive forums are kind of dead :-(. 

1) I really dislike XMMS so I called up apt-get and got it to fetch me the superior Audacious, all this worked fine and I can call the program up with a little help from the terminal but how do I add it to iBar and the rightclick menu under the sub menu Audio.

2) How do I remove that battery and temp applet, I have seen some folks using a applet with a clock in the southeast corner, how can I use that one instead?

Ohh and I'm using E17. Thanks

Your questions are purely e17 ones (i doubt there is elive specific issues, since elive it's just debian with a minimal setup and e17 as a DE...)

So:

2) Right click on the modules and choose 'Remove this gadget'

1) It depends on the version elive uses... Different icons support appeared on last times, from eap to pure .desktop, with some variation on the middle... 
But in any version you should have an 'Add Application' menu entry when right click on ibar just choose that, feel the need name/executable and choose an icon.
If that fails launch the app you want and see if it have an icon. If so, on Main menu go:
Configuration->Configuration Panel:
Applications ->IBar Applications. 

Edit: If apps is not list there you may need to go to Menu->Applications Menus and click 'Update/regenerate menu" 

hth

---

### Post by Freddy on 2007-05-28
> **Rui Pais said:**
> Your questions are purely e17 ones (i doubt there is elive specific issues, since elive it's just debian with a minimal setup and e17 as a DE...)

So:

2) Right click on the modules and choose 'Remove this gadget'

1) It depends on the version elive uses... Different icons support appeared on last times, from eap to pure .desktop, with some variation on the middle... 
But in any version you should have an 'Add Application' menu entry when right click on ibar just choose that, feel the need name/executable and choose an icon.
If that fails launch the app you want and see if it have an icon. If so, on Main menu go:
Configuration->Configuration Panel:
Applications ->IBar Applications. 

Edit: If apps is not list there you may need to go to Menu->Applications Menus and click 'Update/regenerate menu" 

hth

1) Sorry no 'Add application ' menu entry when right clicking on on iBar. This might be the option in a vanilla E17 but not in Elive it seems, Elive uses it's own configuring interface, here I can configurate iBar, but I can't seem to figure it out. I cant "add" commands and icons to either the "rightclick" menu or my iBar, the only thing I can do is add the icons located at the left side of the window but not any commands for them. I found something called "Eap configurator" where I could add the path to the executable but nothing shows up anywhere.

I don't get any:
Configuration->Configuration Panel:
Applications ->IBar Applications. 
In the main menu :-(.

2) If I right click on the modules I don't get 'Remove this gadget', I had to:
left click -> configuration -> configuration panel -> module settings
There I found the option to enable or disable modules.

So I guess there is some differences between a vanilla E17 with the Elive one, or maybe I'm just doing something really really wrong :-(.

Thanks for your help, I really, really like this distro and Enlightment is just wonderful in all it's simplicity.

---

### Post by Rui Pais on 2007-05-28
> **Freddy said:**
> 1) Sorry no 'Add application ' menu entry when right clicking on on iBar. This might be the option in a vanilla E17 but not in Elive it seems, Elive uses it's own configuring interface, here I can configurate iBar, but I can't seem to figure it out. I cant "add" commands and icons to either the "rightclick" menu or my iBar, the only thing I can do is add the icons located at the left side of the window but not any commands for them. I found something called "Eap configurator" where I could add the path to the executable but nothing shows up anywhere.

I don't get any:
Configuration->Configuration Panel:
Applications ->IBar Applications. 
In the main menu :-(.

2) If I right click on the modules I don't get 'Remove this gadget', I had to:
left click -> configuration -> configuration panel -> module settings
There I found the option to enable or disable modules.

So I guess there is some differences between a vanilla E17 with the Elive one, or maybe I'm just doing something really really wrong :-(.

Thanks for your help, I really, really like this distro and Enlightment is just wonderful in all it's simplicity.

Well, there are not a 'vanilla' e17 in the common sense of the term. There are a cvs e17, updated continuously. 
Thats much worst. It changes a lot and in most cases 2 version with of 2-3 month of difference will be incompatible and themes/icons sets and even configs fails... 
elive (i don't try it for a long) just stays on a "stable" (usually a day before some big api change) and don't update frequently. Thats good for stability but bad for compatibility :(

if you got the old eap editor maybe the version of e17 is from the time from eap icons (better times, imho, .desktop are more harder) check if you get some menu option on the icon on the window of the running application that allow you to edit icon (usually 'Edit Icon') you can save an eap that way.
Try run from the console eap_edit (type eap and use tab to autocomplete to make sure of the name, i don't remember it exactly...)

Another common trick is to copy an existing eap and edit with one of the tools (the one from eap+tab completion).
There is too an "inside" tool:
```
enlightenment_remote -start-eap-edit some_eap_file.eap 
```

About change ibar.
Check if you got a file ~/.e/e/applications/bar/.order if so you can manually add the eap to the list (they will be at .e/e/applications/all/) Most eap config was made on .order files.

Can you post the elive version you are using and what e17 version (must be an Main menu Enlightenment->About) It's the 999.037 or older?

---

### Post by Freddy on 2007-05-28
> **Rui Pais said:**
> Well, there are not a 'vanilla' e17 in the common sense of the term. There are a cvs e17, updated continuously. 
Thats much worst. It changes a lot and in most cases 2 version with of 2-3 month of difference will be incompatible and themes/icons sets and even configs fails... 
elive (i don't try it for a long) just stays on a "stable" (usually a day before some big api change) and don't update frequently. Thats good for stability but bad for compatibility :(

if you got the old eap editor maybe the version of e17 is from the time from eap icons (better times, imho, .desktop are more harder) check if you get some menu option on the icon on the window of the running application that allow you to edit icon (usually 'Edit Icon') you can save an eap that way.
Try run from the console eap_edit (type eap and use tab to autocomplete to make sure of the name, i don't remember it exactly...)

Another common trick is to copy an existing eap and edit with one of the tools (the one from eap+tab completion).
There is too an "inside" tool:
```
enlightenment_remote -start-eap-edit some_eap_file.eap 
```

About change ibar.
Check if you got a file ~/.e/e/applications/bar/.order if so you can manually add the eap to the list (they will be at .e/e/applications/all/) Most eap config was made on .order files.

Can you post the elive version you are using and what e17 version (must be an Main menu Enlightenment->About) It's the 999.037 or older?
Puh I have to give this up for tonight :-(.
Yeah you are of course right, it's the .eap file inside ~/.e/e/applications/all that is missing. Elive Panel is somewhat buggy and havn't saved them for me. It has never been a problem for me to open up the Eap Editor but I need to configurate it properly though, so thanks for making me study other pre-configured .eap files, I had missed to specify path ; ).

Thanks for helping me, I would have quit this WM is it wasn't for you.

---

### Post by Rui Pais on 2007-05-28
> **Freddy said:**
> Puh I have to give this up for tonight :-(.
Yeah you are of course right, it's the .eap file inside ~/.e/e/applications/all that is missing. Elive Panel is somewhat buggy and havn't saved them for me. It has never been a problem for me to open up the Eap Editor but I need to configurate it properly though, so thanks for making me study other pre-configured .eap files, I had missed to specify path ; ).

Thanks for helping me, I would have quit this WM is it wasn't for you.

Glad i could help :) 
and happy if i contributed some how for another user of e17 (sorry if i couldn't be more clear, i have old versions of e17 with eaps around but had not time to reboot to it and check my suggestions...) 

have a lot of fun :)

---

