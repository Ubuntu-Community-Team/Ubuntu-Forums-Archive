---
title: "Ubuntu Firefox different than Windows?"
date: 2013-04-07
forum: New to Ubuntu
---

### Post by Greg Mueller on 2013-04-07
My wife and I both have accounts at the local bank which offers on line banking.
She uses Windows 7 Firefox and I use Ubuntu 11.04 Firefox 16.02

When I log in to the bank the first page is the same on both of our computers
However on my computer I have to answer challenge questions and it asks me if I want to register my computer and I always say yes, when I answer the challenge question.

My wife's computer does not ask the challenge question and takes her to a page which asks for the second password, which is the way mine used to behave.

I can only guess that there is some sort of security setting in Ubuntu or Firefox for Ubuntu that keeps my computer from storing whatever registration cookie (etc) that the bank wants to put on there. We checked and both of our computers have the same boxes checked in the settings in preferences.

Any suggestions?

Thanks
Greg

---

### Post by vasa1 on 2013-04-07
Are both browser versions the same? Why is yours version 16? The latest is v.20.

---

### Post by Greg Mueller on 2013-04-07
> **vasa1 said:**
> Are both browser versions the same? Why is yours version 16? The latest is v.20.


Not sure why it's 16. Can't really figure out how to update it

Hers is 19

---

### Post by vasa1 on 2013-04-07
> **Greg Mueller said:**
> Not sure why it's 16. Can't really figure out how to update it

That's because Ubuntu 11.04 is no longer supported. It's EOL was October 28, 2012 ([https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29](https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29)). You won't be receiving security updates for it. It's probably not a good idea to use an unsupported operating system.

You should upgrade!

---

### Post by Greg Mueller on 2013-04-07
I tried the updated Ubuntu and didn't care for the way it looked and the side bar and all that

---

### Post by gerowen on 2013-04-07
> **Greg Mueller said:**
> I tried the updated Ubuntu and didn't care for the way it looked and the side bar and all that

Ubuntu 11.04 isn't supported any more.  You can continue to use it, but you will be stuck with whatever versions of software it was given before it's EOL (End Of Life).  If you want to try upgrade, you can use 12.04 (Long Term Support, guaranteed support for 5 years) or 12.10.  Both of them come with Unity, but if you don't like it you can install other desktop environments from the software center including Gnome, XFCE, KDE (Xubuntu, Kubuntu, etc. are made by Canonical and default to different desktop environments to make setting them up easier), etc., to use instead of Unity.  This will give you the classic look that you want, but with newer versions of software and continued updates.  As far as I'm aware, LTS versions, such as 12.04, get 5 years of support and security updates, and regular versions, such as 12.10, get 9 months.

Edit: If you really want to keep 11.04 and use a newer version of Firefox, just go to [www.getfirefox.com](www.getfirefox.com), download the tarball, extract it, and run the file inside the folder named "firefox".  You can create shortcuts to this executable and everything as well, and it "should", as far as I'm aware, update itself like the Windows version for as long as Mozilla supports Ubuntu 11.04.

---

### Post by vasa1 on 2013-04-07
> **Greg Mueller said:**
> I tried the updated Ubuntu and didn't care for the way it looked and the side bar and all that
Then you can try Xubuntu or Lubuntu or Kubuntu. Doing banking with insecure software isn't recommended.

---

### Post by PhilGil on 2013-04-07
> **Greg Mueller said:**
> I tried the updated Ubuntu and didn't care for the way it looked and the side bar and all that

Ubuntu 12.04 LTS provides a [Gnome Classic]("http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed") session, gets Firefox updates and will be supported for another four years. Or, as vasa1 states, try one of the other desktop environments that's more like Gnome 2.

Not sure about your cookie problem. I'd try with a newer version of Firefox and then re-post if you're still having problems.

---

### Post by Greg Mueller on 2013-04-07
> **gerowen said:**
> Ubuntu 11.04 isn't supported any more.  You can continue to use it, but you will be stuck with whatever versions of software it was given before it's EOL (End Of Life).  If you want to try upgrade, you can use 12.04 (Long Term Support, guaranteed support for 5 years) or 12.10.  Both of them come with Unity, but if you don't like it you can install other desktop environments from the software center including Gnome, XFCE, KDE, etc., to use instead of Unity.  This will give you the classic look that you want, but with newer versions of software and continued updates.  As far as I'm aware, LTS versions, such as 12.04, get 5 years of support and security updates, and regular versions, such as 12.10, get 9 months.

Edit: If you really want to keep 11.04 and use a newer version of Firefox, just go to [www.getfirefox.com](www.getfirefox.com), download the tarball, extract it, and run the file inside the folder named "firefox".  You can create shortcuts to this executable and everything as well, and it "should", as far as I'm aware, update itself like the Windows version for as long as Mozilla supports Ubuntu 11.04.


Is there a way to have both systems on the same hard drive so I don't lose 11.04 ?
Just in case I don't like the new one.



Ooops I answered before I saw the edit

---

### Post by Greg Mueller on 2013-04-07
I'm getting in to deep water for me.....
Can I partition the hard drive and have the newest ubuntu on one partition and the old one on the other?

---

### Post by gerowen on 2013-04-07
> **Greg Mueller said:**
> Is there a way to have both systems on the same hard drive so I don't lose 11.04 ?
Just in case I don't like the new one.

If you want to mess around with 12.04/12.10 and see if you like them with different desktop environments, you can install them alongside one another, it should prompt you in the installation process if you want to "Upgrade", "Replace", etc..  If you have an extra hard drive I'd recommend putting the different version on that different hard drive, because if you don't like it, it's much less time consuming and less risky to just wipe the whole drive, make new partitions, and redo your bootloader than it is to resize existing partitions on your system hard drive.  That way you're not messing with the drive that has 11.04 on it, which you know you like.  You could also try running them inside a virtual machine, albeit with reduced performance, using Oracle's Virtualbox ([http://www.virtualbox.org](http://www.virtualbox.org)).  I use Virtualbox to tinker around with different operating systems all the time.

---

### Post by Impavidus on 2013-04-07
Try Ubuntu 12.04 LTS and Xubuntu 12.04 LTS and possibly some others from a live disk. Pick the one you like most, backup your files and install. Keeping an insecure system because you may not like the new version doesn't sound very secure to me. Xubuntu 12.04, which I use myself, can be configured to look similar too the old interface.

It's interesting to see how many different ways banks have to secure your account. I only need a single username+96 bit password to get in, and one-time confirmation codes send by text message to actually transfer money.

---

### Post by edeneen on 2013-04-07
> **Greg Mueller said:**
> I'm getting in to deep water for me.....
Can I partition the hard drive and have the newest ubuntu on one partition and the old one on the other?

why don't you update and just make the desktop environment one you prefer ?

---

### Post by SeijiSensei on 2013-04-07
In answer to your original question, it's likely that your Firefox is configured to block cookies while hers is not.  Here's a simple test.  Choose Edit > Preferences > Privacy, and click the link to examine your cookies.  If there is an entry for your bank, remove it, then try again.

---

### Post by Greg Mueller on 2013-04-07
I downloaded 12.04 and will give it a whirl

Thanks for the efforts guys

---

### Post by kuifje09 on 2013-04-07
Be aware of the fact a life cd/dvd does not always show exactly what you get when you install it later, or after the first update.
I found 12.04LTS was fine from the dvd but after the first update I could trash my videocard.

---

### Post by uzumakifahim on 2013-04-07
> **Greg Mueller said:**
> I'm getting in to deep water for me.....
Can I partition the hard drive and have the newest ubuntu on one partition and the old one on the other?

That's possible, if you want. I think as you want a gnome classic like environment, so, I suggest you to check the screenshots of Xubuntu, lubuntu and kubuntu and select which one is good for you. In that case, no need for new partion and other hassels.

---

