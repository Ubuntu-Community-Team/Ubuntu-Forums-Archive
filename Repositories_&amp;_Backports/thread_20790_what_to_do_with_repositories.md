---
title: "what to do with repositories"
date: 2005-03-18
forum: Repositories &amp; Backports
---

### Post by Datchew on 2005-03-18
following the ubuntuguide.org steps to add other repositories, i now cannot even pull updates and stuff from these

 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

anyone else having trouble?  are the sites down and out? 

secondly... are these extra repositories ones that i should only enable when i want to install something special from them or are they supposed to stay open in synaptic all the time so that when i check for weekly updates, i pull updates from them also. 

right now i have them open in synaptic (they're checked to be used in the repos list)
and whenever i try to check for updates... it bombs out because it cannot contact them.  

help please.

---

### Post by bored2k on 2005-03-18
[QUOTE=Datchew]following the ubuntuguide.org steps to add other repositories, i now cannot even pull updates and stuff from these

 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

anyone else having trouble?  are the sites down and out? 

secondly... are these extra repositories ones that i should only enable when i want to install something special from them or are they supposed to stay open in synaptic all the time so that when i check for weekly updates, i pull updates from them also. 

right now i have them open in synaptic (they're checked to be used in the repos list)
and whenever i try to check for updates... it bombs out because it cannot contact them.  

help please.[/QUOTE]
 Repositories are supposed to stay all the time. Otherwise, how will that program receive update ?


And yes I am using unstable from Marillat and its working .

---

### Post by Datchew on 2005-03-18
here's what i get:

[IMG][IMG]http://img.photobucket.com/albums/v147/talk2frog/synaptic-probs.png[/IMG][/IMG]

---

### Post by bored2k on 2005-03-18
[QUOTE=Datchew]here's what i get:

[IMG][IMG]http://img.photobucket.com/albums/v147/talk2frog/synaptic-probs.png[/IMG][/IMG][/QUOTE]
 Dude wth cant you see the URL's ? Those are not Marillat's failing.
Those are the weird backport repositories you have there.

I can not see Marillat anywhere there .
Or maybe I'm blind _ _  _

Btw your Godzilla avatar is the bomb .

---

### Post by Datchew on 2005-03-18
thanks on the godzilla thing. 

As to the repositories... i know. i have several different ones in there giving me several different errors. 

In truth, i don't have any clue what the hell i'm doing, so please bear with me and spoon feed me a little if you have the patience. 

Here is what i have in my "sources.list" file which (i think?) controls what repositories my computer has access to:

************************************************************************************
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 


 ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main 

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe 

*****************************************************************************

basically, i copied and pasted these in as instructed at the official ubuntuguide.org link here:

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)
doesn't look like a whole lot does it?
Hmmm... i said the same thing... however, here is a picture of my synaptic package manager's list of repositories:

[IMG]http://img.photobucket.com/albums/v147/talk2frog/synapt-repos.png[/IMG]


and here is just an example of one of the 4 or so errors i get EVERY FREAKING TIME I open synaptic package MANGLER. 

[IMG]http://img.photobucket.com/albums/v147/talk2frog/synaptic-error.png[/IMG]


and finally, whenever i try to "reload" and then mark updates using the "smart update" method, it fails all over the place because it cannot contact some of the reposotories and then some of them just bomb out in the download. 

I have a full T3 connection here at work so it AINT my connection. 

If anyone wouldnt' mind simply putting a nice text of exactly what i should have in my "sources.list" I'd be more than happy to just remove everything from synaptic repositories list, and copy/paste the text into my sources.list file. 

At my wits end here.

---

### Post by bored2k on 2005-03-18
[QUOTE=Datchew]thanks on the godzilla thing. 

As to the repositories... i know. i have several different ones in there giving me several different errors. 

In truth, i don't have any clue what the hell i'm doing, so please bear with me and spoon feed me a little if you have the patience. 

Here is what i have in my "sources.list" file which (i think?) controls what repositories my computer has access to:

************************************************************************************
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 


 ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main 

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe 

*****************************************************************************

basically, i copied and pasted these in as instructed at the official ubuntuguide.org link here:

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)
doesn't look like a whole lot does it?
Hmmm... i said the same thing... however, here is a picture of my synaptic package manager's list of repositories:

[IMG]http://img.photobucket.com/albums/v147/talk2frog/synapt-repos.png[/IMG]


and here is just an example of one of the 4 or so errors i get EVERY FREAKING TIME I open synaptic package MANGLER. 

[IMG]http://img.photobucket.com/albums/v147/talk2frog/synaptic-error.png[/IMG]


and finally, whenever i try to "reload" and then mark updates using the "smart update" method, it fails all over the place because it cannot contact some of the reposotories and then some of them just bomb out in the download. 

I have a full T3 connection here at work so it AINT my connection. 

If anyone wouldnt' mind simply putting a nice text of exactly what i should have in my "sources.list" I'd be more than happy to just remove everything from synaptic repositories list, and copy/paste the text into my sources.list file. 

At my wits end here.[/QUOTE]
 I switched to Hoary, but here are my old Warty sources I saved in my email as Backup:

> deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-extras main universe multiverse restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

If you get error on backports, add a # to the beggining of their line to block them from use .

---

### Post by invchrist on 2005-03-18
What does "sudo apt-get install *proglibname*" give, where you replace proglibname with the name of the program or library you want to install?

---

### Post by WW on 2005-03-18
To get things working without marillat, you can comment out all the marillat repositories and do an update.  This won't affect anything that you have already installed from marillat.  You just won't see any updates from marillat.  If everything is working, this might not be an issue.  I installed a few things from marillat a few months ago, got the things that I wanted working, and then commented out the marillat repository.  By the way, I only used the "testing" marillat repository.

Edit: I am running warty.

---

### Post by Datchew on 2005-03-18
thanks Bored2k. 

wiped all repositories manually from synaptic package "mangler" 
deleted EVERYTHING form sources.list

replaced with the stuff you gave me. 

commented out the marillat stuff. 

no more errors. 
updates running fine. 

I appreciate the help.

---

### Post by bored2k on 2005-03-18
[QUOTE=Datchew]thanks Bored2k. 

wiped all repositories manually from synaptic package "mangler" 
deleted EVERYTHING form sources.list

replaced with the stuff you gave me. 

commented out the marillat stuff. 

no more errors. 
updates running fine. 

I appreciate the help.[/QUOTE]
 Rock on 
[img]http://images-eu.amazon.com/images/P/B0001KO8E8.02.LZZZZZZZ.jpg[/img]

---

### Post by Datchew on 2005-03-18
he he he

you truly have a way with words


     ...and uh, photos that are worth a thousand words. 
 :smile:

---

### Post by bored2k on 2005-03-18
[QUOTE=Datchew]he he he

you truly have a way with words


     ...and uh, photos that are worth a thousand words. 
 :smile:[/QUOTE]
  .[img]http://img76.exs.cx/img76/1916/images5kq.jpg[/img]

---

