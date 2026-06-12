---
title: "Why does Ubuntu have space problems?"
date: 2011-11-15
forum: Recurring Discussions
---

### Post by Glenn nl on 2011-11-15
The kernel is about 120 mb I read, how come 580 MB is not enough space? Is it because of Unity-2D´s QT? Is it because of Mono?

---

### Post by Harry33 on 2011-11-15
> **Glenn nl said:**
> The kernel is about 120 mb I read, how come 580 MB is not enough space? Is it because of Unity-2D´s QT? Is it because of Mono?

There are a number of software that has grown in size recent years.
Sure Unity-2D takes some room.
But about Mono: Precise is moving back to Rhythmbox, thus rejecting Banshee. Perhaps mono will go too.
There are only Tomboy and Gbrainy left of those using Mono.

---

### Post by directhex on 2011-11-15
> **Glenn nl said:**
> The kernel is about 120 mb I read, how come 580 MB is not enough space? Is it because of Unity-2D´s QT? Is it because of Mono?

There are a lot of preconceptions about how Ubuntu's disk space works.

The CD contains a 700 MiB **compressed** disk image, made with SquashFS. Extracted, this disk image is about 2.2 GiB. So when people say "this app uses X meg", they mean "X out of 2.2 gig" not "X out of 700 meg". The actual effect on the overall SquashFS image is very hard to calculate without regenerating it from scratch, which is slow, so nobody does it.

So a kernel image takes up between 115 and 150 meg out of 2.2 gig. Banshee+Tomboy+gbrainy+Mono take up about 40 meg out of 2.2 gig. LibreOffice Writer takes up (I forget the exact numbers) around 150 meg out of 2.2 gig. It adds up - but the number you're working to is "about 2.2 gig" not "700 meg"

---

### Post by BillyBoa on 2011-11-15
> **Glenn nl said:**
> The kernel is about 120 mb I read, how come 580 MB is not enough space? Is it because of Unity-2D´s QT? Is it because of Mono?

I guess you are using a separate /boot partition. I don't know the size you assigned to it, but if you are using 11.04, you have a bunch of old kernels accumulated.

use *uname* to find which kernel you are using:

```
uname -r
```

Then you go to Synaptic, search for *linux-image* and delete the kernels you don't use.

---

### Post by jerrylamos on 2011-11-15
> **BillyBoa said:**
> I guess you are using a separate /boot partition. I don't know the size you assigned to it, but if you are using 11.04, you have a bunch of old kernels accumulated.

use *uname* to find which kernel you are using:

```
uname -r
```

Then you go to Synaptic, search for *linux-image* and delete the kernels you don't use.

Obsolete kernels & headers use up a bunch of space.  I do a "ls boot" after updates to see how much dead stuff is left, then if the various apt-get clear options (clean, autoclean, autoremove) don't clean it up I crank up synaptic and do a really remove.

Now update/upgrade do leave the old kernel around - that's fine, the new one might not even boot....

Jerry

---

### Post by BillyBoa on 2011-11-15
> **jerrylamos said:**
> 
Now update/upgrade do leave the old kernel around - that's fine, the new one might not even boot....

Jerry

That's true. If you delete the old kernels you are locking the doors to the past, in case of an emergency.

---

### Post by philinux on 2011-11-15
Moved to Recurring Discussions.

---

### Post by coffeecat on 2011-11-15
@Glenn nl, before this thread goes too far off into the wrong direction, would you please confirm whether you mean space on the live CD or space on an installation? 120 + 580 = 700, so I guess you are talking about the live CD and directhex has given you a good reply, but others seem to think you mean space on an installed system.

Which is it? :)

---

### Post by Glenn nl on 2011-11-15
> **coffeecat said:**
> @Glenn nl, before this thread goes too far off into the wrong direction, would you please confirm whether you mean space on the live CD or space on an installation? 120 + 580 = 700, so I guess you are talking about the live CD and directhex has given you a good reply, but others seem to think you mean space on an installed system.

Which is it? :)

The Live-CD.
Ubuntu will use 750 MB for a Live-CD for Precise, but how come this is not enough anymore?

---

### Post by coffeecat on 2011-11-15
> **Glenn nl said:**
> Ubuntu will use 750 MB for a Live-CD for Precise, 

May, not will, if you believe omgubuntu:

[http://www.omgubuntu.co.uk/2011/11/ubuntu-12-04-disc-size-to-be-750mb/](http://www.omgubuntu.co.uk/2011/11/ubuntu-12-04-disc-size-to-be-750mb/)

> Update: It&#8217;s not actually confirmed that the size of 12.04 will be 750mb. Rather, if it has to go over 700mb, then that&#8217;s okay &#8211; however the developers will still try to keep it under the CD-R limit.

There's already been an discussion about this here:

[http://ubuntuforums.org/showthread.php?t=1876376](http://ubuntuforums.org/showthread.php?t=1876376)

---

