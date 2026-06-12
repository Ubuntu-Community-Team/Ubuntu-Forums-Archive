---
title: "make launcher on desktop"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by ecs_pf5 on 2008-11-27
On Kubuntu 8.10 I installed firefox from a tar.gz archive

I found part of it installed here:

/home/linux/firefox/firefox

which seems to be a shell script, anyways, if I click on it, FF launches just fine.

but i would like to place a launcher on my Desktop. How can I do this?

---

### Post by Paqman on 2008-11-27
> **ecs_pf5 said:**
> On Kubuntu 8.10 I installed firefox from a tar.gz archive


That's really not a good idea, you won't be receiving any security updates. I would advise removing all trace of this install and using the standard one.

As for launchers, i'm not very familiar with KDE, but can't you just right-click on the desktop to create a launcher?

---

### Post by ecs_pf5 on 2008-11-27
don't seem to be able to, no..

the reason for the firefox install like that was, I wanted to get flash working in Konqueror. so I downloaded the flashplayer-installer from Adobe and extracted and ran it, but it said it couldn't find any of the browsers it normally installs to.

that's why I tried to install FF, but I couldn't find it in adept.. so I did the tar.gz thing

I'm used to apt-get & dealing with the repos in Ubuntu, but Kubuntu has foxed me a bit. I guess I must be short of something in adept

right-click on desktop though & all I get is..

run
add widgets
add panel
desktop settings
lock widgets
lock screen
leave

---

### Post by Paqman on 2008-11-27
> **ecs_pf5 said:**
> 
I couldn't find it in adept.. so I did the tar.gz thing


Have another look. It'll be in there, guaranteed.

---

### Post by ecs_pf5 on 2008-11-27
That's encouraging, I'll go have another root :)

---

### Post by ecs_pf5 on 2008-11-27
Hmm.. the only thing I can find on a search for 'firefox' is something with the title "Firefox Web Browser", but which doesn't look from the description much like the full browser:

"This package ships the firefox branding bits. If you remove this package you your user experience will become that of the abrowser."

(3.0.4+nobinonly-0ubuntu0.8.10.1)

I tried updating the sources to no avail 

But just now I tried

sudo apt-get install firefox

& 'something' seems to be happening..

---

### Post by Skripka on 2008-11-27
> **ecs_pf5 said:**
> Hmm.. the only thing I can find on a search for 'firefox' is something with the title "Firefox Web Browser", but which doesn't look from the description much like the full browser:

"This package ships the firefox branding bits. If you remove this package you your user experience will become that of the abrowser."

(3.0.4+nobinonly-0ubuntu0.8.10.1)

I tried updating the sources to no avail 

But just now I tried

sudo apt-get install firefox

& 'something' seems to be happening..

That is the package you want.

Bear in mind Adept (Package Manager, as well as Add/Remove) right now is _***VERY buggy and broken***_, many KDE4 users are encouraging folks to use Synaptic instead, myself included.

This is the description from Synaptic:

meta package for the popular mozilla web browser
Firefox 3 is the next major release of the standalone Mozilla browser; it is
written in the XUL language and designed to be lightweight and cross-platform.

This is a meta package that will point to the latest firefox package in ubuntu.
Don't remove this if you want to receive automatic major version upgrades for
this package in future.

---

