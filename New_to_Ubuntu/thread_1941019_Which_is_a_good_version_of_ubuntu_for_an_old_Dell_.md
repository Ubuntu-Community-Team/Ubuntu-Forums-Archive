---
title: "Which is a good version of ubuntu for an old Dell Vostro 1000?"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by flexy1984 on 2012-03-14
Hi all,

I have an old Dell Vostro 1000 that Im using and was able to install Ubuntu 11.10 on it.

However, theres some issue with the ati display driver xpress 1150 and it uses some default driver with 1280*800 resolution. It works well for most part but seems to be sluggish a lotta times. After a bit of research, I was able to figure that ati doesnt have support for the display card anymore.But, i also read that some of the older versions of ubuntu would work with the card.

I was wondering if someone could guide me to an older version or maybe a different distribution of linux which would be able to leverage the display card.

Thank you in advance for any help.

---

### Post by BBQdave on 2012-03-14
> **flexy1984 said:**
> I was wondering if someone could guide me to an older version or maybe a different distribution of linux which would be able to leverage the display card.

I run [Debian 6]("http://www.debian.org/") on a dell inspiron 1100 (2.0GHz celeron with 1gb of ram). It is responsive, incredibly stable (best distro I have ever used) and supported for a good while yet. This notebook is my main work station, with Debian 6 the only distro installed.

I am using Debian 6 with Gnome 2 (default desktop) and I use backports for a few applications that I need to have current (recently released applications).

Ubuntu is based on **Debian** for good reason  :D

---

### Post by HeroOfCanton on 2012-03-14
I use Xubuntu and love it. Personally switched more as a matter of taste, but it should run better if you're having trouble with the load of Unity.

---

### Post by ewz on 2012-03-14
Hello 
1280x800 seems to be the right res for that screen size
You could try a lighter desktop like Xubuntu I had  similar issue with an older ATI card, it would run the Unity desktop ok but would get bogged down after awhile. I installed the Xubuntu Desktop and now it flying :-) 

if you don't want to reinstall you system you can open up a terminal and type "sudo apt-get install xubuntu-desktop" once installed, reboot and select xubuntu at the login screen

hope this helps :D

---

### Post by flexy1984 on 2012-03-14
Thank you so much for the quick replies guys....
I was trying to use the OS for some android development  and maybe thats the reason it acts sluggish..But i will definitely  give xubuntu a shot....if its lighter, it should give better performance I guess...
Like you said Im not very keen on reinstalling a different os....might go that route if thats the only option though,...

---

### Post by HeroOfCanton on 2012-03-14
> **flexy1984 said:**
> Thank you so much for the quick replies guys....
I was trying to use the OS for some android development  and maybe thats the reason it acts sluggish..But i will definitely  give xubuntu a shot....if its lighter, it should give better performance I guess...
Like you said Im not very keen on reinstalling a different os....might go that route if thats the only option though,...

Eclipse is the main use for my Xubuntu machine too. Not only is it faster, but IMO it's laid out a lot better for development purposes. Give it a shot and see what you think. Lubuntu is another option. I'd try them both out first then do a reinstall with the version you end up liking best. Will be a lot of "waste" when you install all 3 DEs. (Install Lubuntu same as previous post but with "lubuntu-desktop")

---

### Post by flexy1984 on 2012-03-14
> **HeroOfCanton said:**
> Eclipse is the main use for my Xubuntu machine too. Not only is it faster, but IMO it's laid out a lot better for development purposes. Give it a shot and see what you think. Lubuntu is another option. I'd try them both out first then do a reinstall with the version you end up liking best. Will be a lot of "waste" when you install all 3 DEs. (Install Lubuntu same as previous post but with "lubuntu-desktop")

Thank you ...I think Im doing something wrong here or maybe just misunderstood what was to be done. So, I did the sudo apt-get.....xubuntu and it went on installing a couple of things.
When I restarted the laptop, it showed me the xubuntu splash screen, and then booted up with the same. But then it took me to the ubuntu login prompt and I see the same ubuntu 11.10 desktop...Is this how it is supposed to be? I was assuming that Id see a dual bootloader and Id have to choose xubuntu or something....Pardon my ignorance.

---

### Post by HeroOfCanton on 2012-03-14
> **flexy1984 said:**
> Thank you ...I think Im doing something wrong here or maybe just misunderstood what was to be done. So, I did the sudo apt-get.....xubuntu and it went on installing a couple of things.
When I restarted the laptop, it showed me the xubuntu splash screen, and then booted up with the same. But then it took me to the ubuntu login prompt and I see the same ubuntu 11.10 desktop...Is this how it is supposed to be? I was assuming that Id see a dual bootloader and Id have to choose xubuntu or something....Pardon my ignorance.

Click the little gear icon on the login screen and choose an XFCE session.

---

### Post by flexy1984 on 2012-03-14
> **HeroOfCanton said:**
> Click the little gear icon on the login screen and choose an XFCE session.

lol...thanks...I knew it had to be something stupidly simple that I was missing..

---

### Post by flexy1984 on 2012-03-14
> **HeroOfCanton said:**
> Eclipse is the main use for my Xubuntu machine too. Not only is it faster, but IMO it's laid out a lot better for development purposes. Give it a shot and see what you think. Lubuntu is another option. I'd try them both out first then do a reinstall with the version you end up liking best. Will be a lot of "waste" when you install all 3 DEs. (Install Lubuntu same as previous post but with "lubuntu-desktop")

You mentioned trying it out first and then doing a reinstall with the version I like the best...Did you mean doing a clean install of xubuntu by taking off ubuntu?

---

### Post by HeroOfCanton on 2012-03-14
> **flexy1984 said:**
> You mentioned trying it out first and then doing a reinstall with the version I like the best...Did you mean doing a clean install of xubuntu by taking off ubuntu?

Yes. If you like XFCE download [Xubuntu ]("http://xubuntu.org/getxubuntu/")and do a full clean install. If you find yourself missing anything from the standard distro you can just apt-get it.

---

