---
title: "Why is the 64-bit version not recommended for daily desktop use?"
date: 2010-06-01
forum: Recurring Discussions
---

### Post by wombatvvv on 2010-06-01
Hello,

Obviously a new user here. I have a brand spanking new 64-bit laptop and I'm wondering why the 64-bit version is not recommended for daily desktop use (that's what it says on the Ubuntu homepage)?

I have installed the 32-bit version, but I'm wondering what are the good reasons not to have installed the 64-bit version?

Thanks.

---

### Post by cmileto on 2010-06-01
Works fine for me.

---

### Post by howefield on 2010-06-01
[https://bugs.launchpad.net/ubuntu-website/+bug/585940](https://bugs.launchpad.net/ubuntu-website/+bug/585940)

---

### Post by samstreet101 on 2010-06-01
Yeh i've been using karmic (9.10) 64-bit without problems and installed 10.04 when it came out, again 64-bit and had no problems what so ever. I would think that the reason they don't recommend it for daily usage on their website (or at least put that disclaimer up) is that ubuntu is aiming for the absolute mainstream and as such must accomodate less technically able users who may or may not know whether they have a 64-bit processor in their machine and hense if they installed the 64 bit version and it turns out they only had a 32-bit machine...it won't work and would no doubt confuse someone who didn't know what they're doing. Whereas the 32-bit version which runs on i-386 instruction sets will work on 99% of all PCs.

---

### Post by Grenage on 2010-06-01
> **wombatvvv said:**
> Hello,

Obviously a new user here. I have a brand spanking new 64-bit laptop and I'm wondering why the 64-bit version is not recommended for daily desktop use (that's what it says on the Ubuntu homepage)?

I have installed the 32-bit version, but I'm wondering what are the good reasons not to have installed the 64-bit version?

Thanks.

No good reasons; I'd install x64.

---

### Post by moody_mark on 2010-06-01
Im using 64-bit on a daily basis for my work, the only problem I see is that my battery seems to run down quicker, and I had troubles getting flash working, but thats it, does anyone know why this is "not recommended"?

I must admit this is the first time ive seen this, is this a new statement?

---

### Post by SoFl W on 2010-06-01
> **samstreet101 said:**
> ... as such must accomodate less technically able users who may or may not know whether they have a 64-bit processor in their machine and hense if they installed the 64 bit version and it turns out they only had a 32-bit machine...it

I tried to install the 64bit version on my 32bit laptop.  It told me it couldn't perform the install because of the incompatibility.

(I was using a usb stick and didn't know what version was on the stick)

---

### Post by howefield on 2010-06-01
> **Grenage said:**
> No good reasons

Well, there are a couple.

Firstly you may not have a machine capable of running 64 bit (not the case for the OP) and secondly, flash is still in beta (albeit, as stable for me as I could want).

64 bit is generally considered business as usual, so much so, that these forums no longer see the need for a separate 64 bit forum. Correctly in my view.

---

### Post by samstreet101 on 2010-06-01
> **SoFl W said:**
> I tried to install the 64bit version on my 32bit laptop. It told me it couldn't perform the install because of the incompatibility.
 
(I was using a usb stick and didn't know what version was on the stick)
 
Yeah I remember having that issue installing it on a friend's machine. Thankfully if i remember correctly I think it prompts you with that error before you get to the point of actually installing it.

---

### Post by SoFl W on 2010-06-01
> **howefield said:**
> [https://bugs.launchpad.net/ubuntu-website/+bug/585940](https://bugs.launchpad.net/ubuntu-website/+bug/585940)

They don't give an answer on that page, just people discussing why they feel it says not to use it.

---

### Post by shuttleworthwannabe on 2010-06-01
Just install it and test it--it flies compared to 32-bit. Also will notice apps opening faster.

---

### Post by howefield on 2010-06-01
> **SoFl W said:**
> They don't give an answer on that page, just people discussing why they feel it says not to use it.

And your point is ?

The link was merely to let the OP know that a bug has been filed on launchpad regarding this.

---

### Post by Paddy Landau on 2010-06-01
I had 32-bit Hardy, and now installed 64-bit Lucid on a machine.

It works a little faster, but that may be because it's Lucid not Hardy.

Only 1Gb RAM, yet I've had no 64-bit related problems whatsoever. Happy to have made the switch.

---

### Post by wombatvvv on 2010-06-01
Thanks very much to everyone who replied.

I guess I'll be installing the 64-bit version over the weekend. Ho hum.

---

### Post by wombatvvv on 2010-06-01
> **moody_mark said:**
> Im using 64-bit on a daily basis for my work, the only problem I see is that my battery seems to run down quicker, and I had troubles getting flash working, but thats it, does anyone know why this is "not recommended"?

I must admit this is the first time ive seen this, is this a new statement?


Unfortunately, Flash is quite important in my work. How bad are the problems with it? How difficult is it to get working?

Thx!

---

### Post by DavePlummer on 2010-06-01
Package flashplugin-nonfree from the repositories installs the 32-bit version of Flash, with all required support for it to work in the 64-bit environment. Alternatively, you can download and install Adobe's alpha version of 64-bit Flash (instructions are located elsewhere in the forums). I have used both, and the both work fine, with a minor exception. Hulu.com doesn't currently work with the 64-bit version. You can download and run Hulu Desktop to work around that problem. Hope this helps.

---

### Post by ELD on 2010-06-01
I added my input on the bug report.

I am hoping flash do some more work on their 64bit version soon. Since IE has 64bit and Firefox is moving to 64bit maybe they will feel the need a little more?

---

### Post by Paddy Landau on 2010-06-01
> **DavePlummer said:**
> Hulu.com doesn't currently work with the 64-bit version.
I haven't had Flash problems, and I simply installed from the repositories. Hulu.com works for me, too.

So, it seems that different hardware has different problems. Maybe I was just lucky?

---

### Post by lancest on 2010-06-01
64 bit on my 4 GB desktop. 

Flash is much improved on Firefox (no more greyout crashes).

Firefox won't go full screen with Flash if using Compiz.

Chromium browser will do full screen Flash with Compiz.

---

### Post by ELD on 2010-06-01
> **Paddy Landau said:**
> I haven't had Flash problems, and I simply installed from the repositories. Hulu.com works for me, too.

So, it seems that different hardware has different problems. Maybe I was just lucky?

That means you will have 32bit flash mate, repositories don't do the 64bit version.

---

### Post by moody_mark on 2010-06-01
> **wombatvvv said:**
> Unfortunately, Flash is quite important in my work. How bad are the problems with it? How difficult is it to get working?

Thx!

This is what I done:

1. Installed the "ubuntu-restricted-extras"
2. Noticed some flash sites the buttons dont work properly (e.g. BBC iplayer)

Followed the HOWTO here

[http://heratech.net/blog/sham/cant-click-playpause-flash-youtube-etc-ubuntu](http://heratech.net/blog/sham/cant-click-playpause-flash-youtube-etc-ubuntu)

```
Sometimes the flash player will work but the controls will be unresponsive, heres how to get around that problem;

edit the file /usr/lib/nspluginwrapper/i386/linux/npviewer

and add the following line before the last line

export GDK_NATIVE_WINDOWS=1

then restart any apps using flash

/usr/lib/nspluginwrapper/i386/linux/npviewer


```

I did try to install the 64-bit flash but it doesnt seem to have taken, according to my browser in still running the npwrapper about:plugins in firefox shows 

```

    File: npwrapper.libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r45
```

---

### Post by wombatvvv on 2010-06-01
One other thing guys ... my laptop is an i7 64-bit machine. The Linux download is "amd 64-bit" ... is that going to be compatible with my i7 processor?

Thanks.

---

### Post by formaldehyde_spoon on 2010-06-01
> **wombatvvv said:**
> One other thing guys ... my laptop is an i7 64-bit machine. The Linux download is &quot;amd 64-bit&quot; ... is that going to be compatible with my i7 processor?

Thanks.

Yes, don't let the 'amd' throw you.

---

### Post by Spike-X on 2010-06-01
> **wombatvvv said:**
> One other thing guys ... my laptop is an i7 64-bit machine. The Linux download is "amd 64-bit" ... is that going to be compatible with my i7 processor?

Thanks.
Yeah, that'll be fine. I'm running an Intel CPU as well, not a drama at all.

---

### Post by ELD on 2010-06-02
> **formaldehyde_spoon said:**
> Yes, don't let the 'amd' throw you.

It is something that bugs me why they have to put amd64, why can't they simply put 64bit?

---

### Post by Paddy Landau on 2010-06-02
> **ELD said:**
> It is something that bugs me why they have to put amd64, why can't they simply put 64bit?
Don't allow yourself to be bugged. It's only historical reasons.

---

### Post by ELD on 2010-06-02
> **Paddy Landau said:**
> Don't allow yourself to be bugged. It's only historical reasons.

I know all about it, it still bugs me though. Confuses new users.

---

### Post by Paddy Landau on 2010-06-02
> **ELD said:**
> I know all about it, it still bugs me though. Confuses new users.
True. I have seen a bug or brainstorm or something raised to have the name changed.

---

### Post by 3rdalbum on 2010-06-02
> **ELD said:**
> It is something that bugs me why they have to put amd64, why can't they simply put 64bit?

"Why do they say i386, my computer's a Pentium not a 386?"

"Why does ia32 stand for 'Intel Architecture 32' when AMD and VIA CPUs use it too?"

The name is AMD64, which is the set of extensions to x86/ia32 that AMD came up with for 64-bit. As opposed to ia64, which is a different architecture altogether.

---

### Post by 3rdalbum on 2010-06-02
> **shuttleworthwannabe said:**
> Just install it and test it--it flies compared to 32-bit. Also will notice apps opening faster.

Not possible. It allows 64-bit numbers to be dealt with quicker, and allows longer memory addresses. Running a 64-bit operating system does NOT cause your disks to put programs into memory quicker.

---

### Post by formaldehyde_spoon on 2010-06-02
> **3rdalbum said:**
> Not possible. It allows 64-bit numbers to be dealt with quicker, and allows longer memory addresses. Running a 64-bit operating system does NOT cause your disks to put programs into memory quicker.

It's true that just simply pulling data off disk into memory won't be any faster, because the bottleneck is the disk, but 64 bit does more than just allow''64 bit numbers to be dealt with quicker'', so if opening an app involves any computation then it's possible that 64 bits could see it loaded faster (it's probably unusual for a difference to occur that is noticeable though).

---

### Post by brivy on 2010-06-02
Just my two cents, but there really isn't a whole lot of performance difference between when doing general everyday sorts of tasks.  I tried 64-bit Lucid and had some of the Flash issues as mentioned in previous posts.  No big deal, installed the 32-bit version and never looked back.  Probably will try again in two more cycles, maybe 11.04.  Hopefully with a better laptop! ;)  Application software still doesn't demand the need for a 64-bit OS.

---

### Post by NightwishFan on 2010-06-02
Install the 64-bit flash plugin. Works flawlessly. There is no reason to not use 64-bit, despite what is 'recommended'. They could have worded that better: "Use this if you are at all unsure."

Then again, 32-bit may be getting legacy, but there is no problem using it now.

---

### Post by carolinason on 2010-10-06
Ubuntu 64bit is only for nightly users. "Those" that are daily users should refrain from such activities.

---

### Post by Paddy Landau on 2010-10-06
> **carolinason said:**
> Ubuntu 64bit is only for nightly users. "Those" that are daily users should refrain from such activities.
Are you sure? I'm not a nightly user. I use the computer only during the day. I've been using 64-bit since Lucid came out, and I am happy with it.

---

### Post by beew on 2010-10-06
It depends on the software you run. Some are still 32 bits only and some may have buggy 64 bit versions.

I think it is good advice. Just because the software you use have good 64 bit versions it doesn't mean it is the norm.

---

### Post by ELD on 2010-10-06
> **carolinason said:**
> Ubuntu 64bit is only for nightly users. "Those" that are daily users should refrain from such activities.

Sorry but...what?

---

### Post by formaldehyde_spoon on 2010-10-06
> **beew said:**
> It depends on the software you run. Some are still 32 bits only 
Very, very, very few 32 bit applications cannot be run on 64 bit. So this is not applicable to 99% of us.

> and some may have buggy 64 bit versions.
 No more likely at all than having buggy 32 bit versions.  This is NOT something you can just pin on 64 bit.
> 
I think it is good advice. Just because the software you use have good 64 bit versions it doesn't mean it is the norm.The ''norm'' is by definition whatever the majority uses.  That's (probably) still 32 bit, but it won't be for long.

---

### Post by ELD on 2010-10-07
> **formaldehyde_spoon said:**
> Very, very, very few 32 bit applications cannot be run on 64 bit. So this is not applicable to 99% of us.

No more likely at all than having buggy 32 bit versions.  This is NOT something you can just pin on 64 bit.
The ''norm'' is by definition whatever the majority uses.  That's (probably) still 32 bit, but it won't be for long.

For once i agree with you on all points.

It is VERY hard to find something that doesn't work on 64bit Ubuntu that does on 32bit.

---

### Post by carolinason on 2010-11-19
> **Paddy Landau said:**
> Are you sure? I'm not a nightly user. I use the computer only during the day. I've been using 64-bit since Lucid came out, and I am happy with it.

Well, it is also dark on the other side of the world when you use it during the day, technically making it okay to use 64 bit. Actually, since it is dark somewhere on the planet at all times, Ubuntu 64 bit is an excellent anytime version to run (obviously on 64 bit capable systems). :lolflag: it says, "way too much ubuntu"

---

### Post by carolinason on 2010-11-19
> **ELD said:**
> Sorry but...what?

I thought a little comedy might be okay. Sorry, if I might be "off thread".

---

