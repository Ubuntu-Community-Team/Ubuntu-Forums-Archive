---
title: "Forking Debian"
date: 2013-06-01
forum: Programming Talk
---

### Post by ICouldBeAnyone on 2013-06-01
Hello all!

Not sure if this is the correct place to be posting this (or even the right forum) but I am looking at building a custom linux distro.

I intend on modifying most of the GUI code, and some of the backend code, as well as adding my own software. I don't need help with coding (though I may ask a *few* questions on this forum) but I have no idea where to start, if anyone can help I would be greatfull!

Not the best (or most advanced) example of what I can do with code, but it's my only published app, if you would like to see it [you can find it here]("apt:pct-listen")

Thanks in advance for any help!!! :)

---

### Post by Nytram on 2013-06-02
For learning to build your own distro you may find [http://www.linuxfromscratch.org/]("http://www.linuxfromscratch.org/") to be useful.

---

### Post by Bachstelze on 2013-06-02
Sound slike you don't want to modify the distro, but only certain packages in it...

---

### Post by nvteighen on 2013-06-02
> **Bachstelze said:**
> Sound slike you don't want to modify the distro, but only certain packages in it...

What is forking a distro but modifying its packages? ;) Even modifying the behavior of config files and scripts implies modifying packages in any distro that is built on top of a packaging system.

Anyway, I think that before even thinking on touching Debian you should understand it so that you know exactly what you want to modify. Also, having a look on what other derivatives have done will surely inspire you. Dunno, Linux Mint Debian Edition is really popular these days. Part of this decision is also which Debian release you want to fork from, stable ("wheezy", Debian 7.0), "testing" (codename "jessie") or "unstable" (codename "sid")... Ubuntu is a fork from unstable, e.g.

---

### Post by ICouldBeAnyone on 2013-06-02
I was thinking about it last night, and I think I want to fork Ubuntu instead - I understand it better (I have never used Debian).

> **nvteighen said:**
> What is forking a distro but modifying its packages? :wink:  Even modifying the behavior of config files and scripts implies  modifying packages in any distro that is built on top of a packaging  system.

I understand *what* it is, but I don't know where to start! I know what I want to do, I just need some help...

I have no Idea how I would modify the system then put it on a DVD (there will be more to it than just that though (I'm guessing)). I just want some help with that side of it!

Thanks again!

---

### Post by deadflowr on 2013-06-02
> [COLOR=#000000]Ubuntu is a fork from unstable[/COLOR]

That has never been the case.
Ubuntu is always derived from the testing branch.
With the occasional overlap with stable, such as this current development cycle.

[https://launchpad.net/ubuntu/saucy](https://launchpad.net/ubuntu/saucy)

For the OP, forking and modifying are going to be a lot harder to accomplish than you'd really want to do.
Distributions like Debian and/or Ubuntu and even Mint have hundreds to thousands of active developers working on projects full time. In some cases, like those working on Debian, they might work on the project over several years.

However, I don't want to be a total debbie downer on the issue, so there is nothing wrong with building your own highly personalized Ubuntu spin, for your own use only (as well as for friends/family)
If you can follow this, 
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

it might be helpfu for what you want.

---

### Post by Bachstelze on 2013-06-03
> **nvteighen said:**
> What is forking a distro but modifying its packages? ;) Even modifying the behavior of config files and scripts implies modifying packages in any distro that is built on top of a packaging system.

I think "forking" is something a little more involved than just modifying a handful of packages, otherwise installing anything from a third-party repository would be forking...

---

### Post by ICouldBeAnyone on 2013-06-03
> **deadflowr said:**
> That has never been the case.
Ubuntu is always derived from the testing branch.
With the occasional overlap with stable, such as this current development cycle.

[https://launchpad.net/ubuntu/saucy](https://launchpad.net/ubuntu/saucy)

For the OP, forking and modifying are going to be a lot harder to accomplish than you'd really want to do.
Distributions like Debian and/or Ubuntu and even Mint have hundreds to thousands of active developers working on projects full time. In some cases, like those working on Debian, they might work on the project over several years.

However, I don't want to be a total debbie downer on the issue, so there is nothing wrong with building your own highly personalized Ubuntu spin, for your own use only (as well as for friends/family)
If you can follow this, 
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

it might be helpfu for what you want.

This could be interesting, I might be able to get this to do what I want.

**Can I only use this for myself? Am I not able to give others a download via my website?**

If I could, I may try this!

---

### Post by r-senior on 2013-06-03
> **ICouldBeAnyone said:**
> **Can I only use this for myself? Am I not able to give others a download via my website?**
Free software is about freedom. As a general principle, you are free to distribute free software as long as you don't take away someone else's freedom by imposing restrictions or failing to supply source code for anything you modify.

However, you should read this:

[http://www.canonical.com/intellectual-property-policy](http://www.canonical.com/intellectual-property-policy)

---

### Post by deadflowr on 2013-06-03
> **ICouldBeAnyone said:**
> This could be interesting, I might be able to get this to do what I want.

**Can I only use this for myself? Am I not able to give others a download via my website?**

If I could, I may try this!

Possibly.
Depends though.
Looky here on Canonicals Trademark and copyright policy, for which Ubuntu is among
[http://www.canonical.com/intellectual-property-policy](http://www.canonical.com/intellectual-property-policy)

Aye, r-senior beat me!

---

### Post by ICouldBeAnyone on 2013-06-03
> **r-senior said:**
> Free software is about freedom. As a general principle, you are free to distribute free software as long as you don't take away someone else's freedom by imposing restrictions or failing to supply source code for anything you modify.

However, you should read this:

[http://www.canonical.com/intellectual-property-policy](http://www.canonical.com/intellectual-property-policy)

When I read that I laughed a bit... :)

Okay, I am now beginning to think this could be possibly starting to get *just* a little bit completely complicated. ](*,)

But it is okay. I think I have a plan B, I am going to make my idea standalone software that can be installed - and not part of a different fork of Ubuntu. It is going to be much easier.

Thanks for all your help everyone! You have helped me come to a conclusion. Thank you to everyone who helped! :D

---

### Post by ICouldBeAnyone on 2013-06-03
Actually, thinking about it now. The idea I had for the branch of Debian was not a very good one... Glad I didn't go ahead.
It is not a good idea for a standalone program ether

---

