---
title: "I can't win."
date: 2009-06-10
forum: Pennsylvania Team - US
---

### Post by ShadowdogKGB on 2009-06-10
Here I am again. I gave version 7.04 a shot back then. I couldn't get sound to work. Gave up in frustration. 

Fast forward. Tried 9.04. Everything seemed a little smoother. 

However, Pogo.com games would not work. I had the wrong version of Java is what it told me. 

Here's the rub. I spent 2 painstaking hours trying to fix it.

I give up. Again. Life is too short for this.

You see, I have 15 brand new computers I could put Ubuntu on. And the majority of the people who will buy them will play Pogo games.

But to my dismay, something as popular as Pogo is apparently too much to ask for Ubuntu.

My bewilderment is indescribable. My true emotions, restrained.

Does anybody have a reasonable explanation why Pogo and Java have to be such a nightmare? Why put the average person through this contortion?

---

### Post by dcraven on 2009-06-10
Yes. Probably the issue is that whatever Pogo.com is requires Sun's JVM, but in fact you have a less encumbered JVM installed. 

Your best bet is to install the Sun JVM package and you'll likely be set.

Good luck,
~djc

---

### Post by jrdemasi on 2009-06-10
Not to be presumptuous - but did you bother to ask for help on the forums anywhere before giving up?  It's probably a simple solution that could be solved in no time at all, in fact, there may be a thread already relating to your issue.  There are tons of Ubuntu resources out on the web, you just have to look for them.  Now, if you are willing to try to resolve it, I will personally do what I can to assist you.

---

### Post by lamalex on 2009-06-10
Whoa sweet, ive never played pogo games before. Works awesome on my Ubuntu 9.04 64-bit system!


edit: nm, these games actually kinda suck. Still work though.

---

### Post by ShadowdogKGB on 2009-06-11
> **jrdemasi said:**
> Not to be presumptuous - but did you bother to ask for help on the forums anywhere before giving up?  It's probably a simple solution that could be solved in no time at all, in fact, there may be a thread already relating to your issue.  There are tons of Ubuntu resources out on the web, you just have to look for them.  Now, if you are willing to try to resolve it, I will personally do what I can to assist you.

I would have if it were an obscure problem. 

Look, I'm trying to help you guys out. It shouldn't be this hard.

Do you not see the quandary here? Here is this website, Pogo.com, that millions of people use to pass the time away playing little widget games. It's been around forever. Yet I can't do a fresh install of Ubuntu, download the updates, and simply go there without any fanfare and drama?



I am simply confounded as to why, with all the glory that has been heaped upon Ubuntu and Linux, does it have to be so problematic to simply go to a hugely popular site like everybody else.


I did a fresh install of Ubuntu, downloaded all the updates for it, went to Pogo.com and BAM. Stopped dead in my tracks. 

It shouldn't be this way. I don't want to know the details of why it doesn't work and how to make it work. 

99.9% of humans care not a wit either. They just want to click on it and go.

---

### Post by dcraven on 2009-06-11
If I remember correctly, there is an more Free version of Java installed by default that may or may not conform 100% to the more familiar Sun implementation. The Sun version is in the repos.

Perhaps the Sun version takes up more space than the install disc will allow. 

This isn't done for user inconvenience, but rather for licensing or space reasons maybe. I could be wrong, but I doubt Pogo.com is a huge priority for the dev team. Both JVM versions are available in the repository so you can choose which ever version is your preference.

Thanks for your help,
~djc

---

### Post by elizabeth on 2009-06-11
> **dcraven said:**
> If I remember correctly, there is an more Free version of Java installed by default that may or may not conform 100% to the more familiar Sun implementation. The Sun version is in the repos.

That's right.

> licensing ... reasons maybe.

Plus there is a bit of philosophy.

More details here: [https://wiki.ubuntu.com/CommonCustomizations](https://wiki.ubuntu.com/CommonCustomizations)

And here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

And here: [https://help.ubuntu.com/community/FreeFormats](https://help.ubuntu.com/community/FreeFormats)

Specifically:

[I]Proprietary software

Ubuntu is committed to producing a free software system. More information about this philosophy can be found on the [URL="http://www.ubuntu.com/community/ubuntustory/philosophy"]Philosophy page of the Ubuntu website
[/URL]
Software packages such as Macromedia Flash and Sun Java, while able to be redistributed, are not free software, and so will not be included in a default Ubuntu installation. We make these programs available on the network for users who wish to use them, and Ubuntu derivatives may choose to include them by default in their distributions.[/I]

If you're looking for a good Ubuntu derivative that includes non-free, questionably legal software out of the box you might want to check out [Linux Mint]("http://www.linuxmint.com/"). And I don't say "questionably legal" here to be provocative, there are a lot of very serious, very real licensing concerns detailed in the links above that could cause serious, business destroying legal problems for a distributor in certain countries.

---

### Post by bfledderjohn on 2009-06-11
A quick google search found the following information...

> 
Donald,
  In your Linux research have you run across a fix for the inability to play java games on pogo.com?
It fails on Ubuntu 8.04 and Suse 11 that I have tried. I found a few so called fixes that did not work?

As funny as it might sound this is a REAL BIG DEAL to me. There are some exceptional (member) games that I play to fill in a few moments before I have to do something or go somewhere. No leaving windows quite yet.
James

Never mind ! I installed the Sun jre from the package manager and all is well!!


I have the same problem with WEBCT which my college uses for online classes.  Lyz is correct, I think, in telling you that the Sun Java is not installed by default with Ubuntu due to proprietary licensing... Although, I think that now Sun has open sourced Java.   Realistically, in 90% of applications it makes no difference.

The very simple fix is simply going to synaptic (System>Administration>Synaptic Package Manager) and installing Sun JRE.

I am able to run the pogo games since I have the Sun JRE installed.

---

### Post by jedijf on 2009-06-13
Previous posts have all referenced the legal stuff.

Very simply, when I help people with installs, after the initial install I recommend the following:

ubuntu-restricted-extras

sudo /usr/share/doc/libdvdread4/install-css.sh

Reference: [https://help.ubuntu.com/community/RestrictedFormats/]("https://help.ubuntu.com/community/RestrictedFormats/#DVD")


That should get everything that a normal user needs working.

---

