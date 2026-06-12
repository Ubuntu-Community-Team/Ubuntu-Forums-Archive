---
title: "Black screen, Ati Mobility Radeon HD 5470"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by peter95 on 2011-11-03
*note: sorry for my english

Hello everyone reading my thread. For the first of all I need to say that I am new here, and new to ubuntu. So I found out about ubuntu as an alternative to Windows and Mac about two months ago when the 11.04 version was, so I tryed to install it on my notebook because the webpage said that ubuntu works with everything. So ubuntu was installed and I was like WOW. BUT, than the problems started, just after the first update and reboot screen was black and it didn't do anything, I haven't heared any HDD sound, not even the indicator for the HDD activity was indicating :( . So I gave up and returned windows back. And again, not so long ago, new ubuntu version was tuned and I couldn't help myself because it looks so damn great, so sleek and I like alternatives to almost everything. This time i got to the menu: try ubuntu, install ubuntu and so. I clicked try ubuntu, and after I selected it the screen went black, I heared some disc spinning, and than nothing happened. After that I said to myself: maybe this ubuntu isn't that great and compatible and easy to install. I found some websites saying: ubuntu sucks, ubuntu fails, and digged out some info that after the 8.04 version ubuntu got more and more worse.

So now my question to you is: what should I do? Is ubuntu comunity bunch of crazy people working with the OS that doesn't works? Could the Laptop setup be the problem?

I didn't found any threads talking about similar problems, others have problems with sound, wireless internet and so. I wish I had only those.

About the hardware, I have a notebook old about a year, but that doesn't matter because ubuntu works with everything, right? 
It is HP G72-a10em
Intel core i3 @ 2,27
3 gb memory
Ati Mobility Radeon HD 5470 (I think this could also be the problem)
320 gb HDD

Thank you very much for support, and again sorry for my english.
Sencerly yours :D , Peter from Zagreb, Croatia!

---

### Post by Majorix on 2011-11-03
> **peter95 said:**
> Ati Mobility Radeon HD 5470 (I think this could also be the problem)

That should be the problem. Sometimes some updates break ATI drivers. You might just stick with an older driver that works (you said it worked on 11.04 until the updates, right?)

---

### Post by bluexrider on 2011-11-03
Personally use LinuxMint Katya on my Desktop and LinuxMint Julia on my Laptop. Both are derivatives of Ubuntu. I don't have any issues with either one. I removed MS Windows some time ago and have never looked back. 

[http://www.linuxmint.com/release.php?id=15](http://www.linuxmint.com/release.php?id=15)

Might want to take a look


Good Luck 

You can find me in the LinuxMint Community too

---

### Post by wolfen69 on 2011-11-03
> **peter95 said:**
> Is ubuntu comunity bunch of crazy people working with the OS that doesn't works?
 
I've been called crazy before, but I can assure you that ubuntu works just fine for most people. And yes, there are a few computers that will not work easily with ubuntu, that's the nature of open source.
> Could the Laptop setup be the problem?
I suspect this is a video card issue. Did you install any video drivers? Have you even seen the desktop yet?

---

### Post by wolfen69 on 2011-11-03
> **bluexrider said:**
> Personally use LinuxMint Katya on my Desktop and LinuxMint Julia on my Laptop. Both are derivatives of Ubuntu. I don't have any issues with either one. I removed MS Windows some time ago and have never looked back. 

[http://www.linuxmint.com/release.php?id=15](http://www.linuxmint.com/release.php?id=15)

Might want to take a look


Good Luck 

You can find me in the LinuxMint Community too

It's great that you find Linux Mint a great alternative, but please suggest other distros only as a last resort. We are here to help people with ubuntu, not linux mint. Thank you.

---

### Post by mörgæs on 2011-11-03
Linux does not work with everything. Some hardware vendors do next to nothing to support Linux while others show a genuine interest.

How does a live boot of Xubuntu 11.10 work?

---

### Post by peter95 on 2011-11-03
Thank you all for support, I see all of you think that graphic card is the problem, so how canI install the driver without geting to the ubuntu desktop? And do you think that nVidia has better cards to offer in case of ubuntu more than ati does?

---

### Post by tehcavil on 2011-11-03
> **peter95 said:**
> Thank you all for support, I see all of you think that graphic card is the problem, so how canI install the driver without geting to the ubuntu desktop? And do you think that nVidia has better cards to offer in case of ubuntu more than ati does?

Well, ATI has a reputation of making terrible drivers for linux (and even windows for that matter) so Yes, Nvidia > ATI every time.

However your is a mobility card integrated into your mobile computer so that doesnt really help. Load up an live CD, access your old filesystem to get any files you need off of it (save them on a usb drive). Then, use the gparted disk utility to wipe the drive of linux and start over.

Reinstall linux.

if you choose to use 11.04 instead of 11.10, DO NOT upgrade to 11.10, just do a clean install of 11.10 instead. If you use 11.10, DO NOT use the updated (post-release) proprietary ATI/AMD driver, it will break your system, (same happened to me).

---

### Post by TechZilla on 2011-11-03
You really need to be more specific about both your problem, and the circumstances leading to it.

What if you boot Ubuntu live from the new release?  Does it boot correctly?  Does X load as expected?  We need to narrow the scope.


... BTW, my troll radar went off, while reading this post.

---

### Post by Miljet on 2011-11-03
This thread seems to have a rather extensive troubleshooting guide for graphics problems -- including ATI chips.

[http://ubuntuforums.org/showthread.php?t=1743535&highlight=black](http://ubuntuforums.org/showthread.php?t=1743535&highlight=black)

---

### Post by Toz on 2011-11-03
> **peter95 said:**
> so how canI install the driver without geting to the ubuntu desktop?

jockey-text
```
$ jockey-text --help
Usage: jockey-text [options]

Options:
  -h, --help            show this help message and exit
  -c, --check           Check for newly used or usable drivers and notify the
                        user.
  -u, --update-db       Query driver databases for newly available or updated
                        drivers.
  -l, --list            List available drivers and their status.
  -a, --auto-install    Enable drivers that can be automatically installed.
  --hardware-ids        List hardware identifiers from this system.
  -e DRIVER, --enable=DRIVER
                        Enable a driver
  -d DRIVER, --disable=DRIVER
                        Disable a driver
  --confirm             Ask for confirmation for --enable/--disable
  -C, --check-composite
                        Check if there is a graphics driver available that
                        supports composite and offer to enable it
  -m free|nonfree|any, --mode=free|nonfree|any
                        Only manage free/non-free drivers. By default, all
                        available drivers with any licence are presented.
  --dbus-server         Run as session D-BUS server.
  --no-dbus             Do not use D-BUS for communicating with the backend.
                        Needs root privileges.
  -k KERNEL, --kernel=KERNEL
                        Use a different target kernel version than the
                        currently running one. This is only relevant with
                        --no-dbus.
```

If I remember correctly, it goes something like this:
1. List available drivers:
```
sudo jockey-text --list
```
2. Install:
```
sudo jockey-text -a xorg:fglrx
```

---

