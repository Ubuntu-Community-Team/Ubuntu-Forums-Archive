---
title: "Ubuntu 13.10"
date: 2013-07-14
forum: New to Ubuntu
---

### Post by DrDos345 on 2013-07-14
First, sorry for the long winded post.

I was running windows Vista and contracted a very serious virus that wiped my whole system. I did not take the proper precautions, nor did I use available MS disks to fix the problem. I ended up using kill disk to wipe the drive. That said, enter Ubuntu.

I started with the down load for 13.4 since my UUI installer did not show 12.4 LST or whatever. It wasn't to bad. Not windows of course. Let me say that I can change hardware, even build a computer to a certain extent, but working with a prompt other than HTML codes I am lost. Let's just say I suck at trying to figure out the directions even for Ubuntu Live CD to try and repair my disk. I did manage to use Testdisk with some results, but it looks like I will have to take it in and suffer $700 to get my stuff.
That said, enter Ubuntu 13.10.

Yes. I down loaded this monster and my life has been a living hell. First my mouse froze, then the comp crashed. Would not let me report anything to the devs and now it is running a series of line with the left side increasing from 400 to now1832. All I can make out is Nouveau, PGRAPH, CH-1, (unknown), sub c 7 class, mthd, and data this line has been running for about five minutes now and it does not look like it will stop.

I had two drives in my comp which is a Gateway GM5260 (nothing special just standard comp) and since all the original problems were on the C drive (which had my first DL of 13.4 on it) I took it out and replaced with my smaller 160gb drive to install Ubuntu 13.10.

I figure I am going to re-install 13.4 if this machine ever gets tired of running these lines of code or whatever. I should say a few things about ubuntu for the devs:

1: It is not quite user friendly enough for the non-geek such as myself. I noticed this especially in the fixes for drives and such. I wasn't put on this earth to learn the command prompt and the instructions posted on the web (which I spent literally hours going over leave much to be desired). Maybe its because I am an English major or something or I am just a dumbshyte.

2: You need to work some more on wine. If Ubuntu could support MS office and a full version of Adobe Standard I would be delighted and tell MS to take dump on the rest. My publisher does not know how to build my books using Linux, in fact it is probably my stupidity on the subject of learning things (again I bring up posts that make no sense to me but might to a dev).

Ten minutes now and the code is still screaming down my screen. Not sure what to do, but would like to continue with Ubuntu. If I want MS  garbage again I will buy a new comp. Can anyone give me some pointers on good posts for learning Ubuntu, working with the OS. I did manage to DL a whole slew of stuff and work with it in 13.4 such as Wine, Libre, and few other apps so I am not completely ignorant, but a little help is always appreciated.  Cheers!

It's up to 3034 now, I hope it is not counting up every cylinder or something.

---

### Post by perspectoff on 2013-07-14
Ubuntuguide uses cut-and-paste suggestions, though it may not suit you and is a bit outdated.. Still, it has lots of links to other sites.

Kubuntu is much closer to what you're used to in Windows (in fact, the Windows 8 UI seems to be merely trying to copy the Ubuntu and Google Android UI's).

Ubuntuguide/Kubuntuguide: [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by DrDos345 on 2013-07-14
I also wanted to say that during the install of 13.10 I did opt to give a key to encrypt my files which has to be put in at start up. Other than that it installed the same way 13.4 did.

---

### Post by snowpine on 2013-07-14
13.10 won't be released until October. Of course it is buggy.

---

### Post by deadflowr on 2013-07-14
Be fully advised that 13.10, aka saucy salamander, is currently in a state of development flux.

Unless you are prepared to deal with on again off again breakage, don't run it, yet.

---

### Post by DrDos345 on 2013-07-14
Thanks deadflowr, but TO LATE. The question is, "How can I stop this incessant code from running so I can re-install 13.4?" Do I just shut down the machine while the code is running? Will 13.4 wipe the drive before I install it? Can I install over 13.10? I ask the last question because when 13.10 began to search for info to send to the devs, it said I had old versions or code or something that caused it to be wacky. Any suggestions?

---

### Post by DrDos345 on 2013-07-14
Oh, sorry snowpine, I really didn't know. When I saw it on my installer (UUI) I just thought it was an upgrade or something and might have something new (what I had not seen previously).

---

### Post by deadflowr on 2013-07-14
> **DrDos345 said:**
> Thanks deadflowr, but TO LATE. The question is, "How can I stop this incessant code from running so I can re-install 13.4?" Do I just shut down the machine while the code is running? Will 13.4 wipe the drive before I install it? Can I install over 13.10? I ask the last question because when 13.10 began to search for info to send to the devs, it said I had old versions or code or something that caused it to be wacky. Any suggestions?

Just throw the live cd for 13.04 in your cd drive(or usb stick if that's how you installed ) and reinstall it over again.
To install over the old version, there should be an option to install over existing.
If not you can use the advanced option, "something else"
Something else will give you the full layout of your partitions.
Find the partition you have 13.10 on and click change/edit(forget which word it is).
make your filesystem type(normally ext4 is a good choice).
and mark what's to be mounted(the / symbol is root, so for a basic setting choose this)
After you set your partitions click enter/ok and follow the rest of the install guides.(ie, name, password, etc,etc.)

Edit: we aren't, as a whole, an acronym savvy group, so what is UUI?

---

### Post by monkeybrain2012 on 2013-07-14
13.10 is alpha and it is only for testers so it is expected to be very buggy. Get 12.04 or 13.04.

---

### Post by DrDos345 on 2013-07-14
UUI is a very nice Universal USB Installer. I wish it would have had 12.4 LTS, but it does not. Thanks for that info I have 13.4 on a stick and I will put it over the other in a little. Cheers!

---

### Post by DrDos345 on 2013-07-14
Thank you deadflowr, I am now up and running in 13.4. The install gave me a a choice of wiping the drive and then installing 13.4 
which is what I did. It also gave me the something else choice, but I wanted to make sure that none of 13.10 that was installed
would somehow get into my new system. I will now spend some time reading FAQ pages. Cheers!

---

### Post by deadflowr on 2013-07-14
> **DrDos345 said:**
> Thank you deadflowr, I am now up and running in 13.4. The install gave me a a choice of wiping the drive and then installing 13.4 
which is what I did. It also gave me the something else choice, but I wanted to make sure that none of 13.10 that was installed
would somehow get into my new system. I will now spend some time reading FAQ pages. Cheers!

Yeah, the something else option is how I've install everytime, regardless of whether the disk I'm installing on is split up for multiple OS' or not, so I tend to not pay any attention to the other choices. Hence why I don't know what they're actually called.(But I know they exist)

There's a lot of documentation for helping get situated learning and using Ubuntu, and linux in general.
Here's a couple places to look at, with helpfulness, hopefully
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
and for offline fun, you can download a copy of 
[http://ubuntu-manual.org/downloads](http://ubuntu-manual.org/downloads)

Enjoy, and note if you have any problems, start a thread and help will most likely be on the way.

---

### Post by Impavidus on 2013-07-14
> **DrDos345 said:**
> 
2: You need to work some more on wine. If Ubuntu could support MS office and a full version of Adobe Standard I would be delighted and tell MS to take dump on the rest.
Microsoft doesn't disclose all details needed for making all programs work on wine. Therefore a lot of guesswork by the wine devs is involved. The day MS discloses all details is the day you and many others will ditch a lot of MS products. Which explains why MS won't tell.

---

