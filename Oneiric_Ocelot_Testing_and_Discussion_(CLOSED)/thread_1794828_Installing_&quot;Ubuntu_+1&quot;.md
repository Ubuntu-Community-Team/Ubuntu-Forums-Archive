---
title: "Installing &quot;Ubuntu +1&quot;"
date: 2011-07-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by EgoGratis on 2011-07-01
How do you install "Ubuntu +1" for testing? Last version + upgrade? Normal installation + "Ubuntu +1" just newer works.

Thanks!

Edit: I must correct myself!

Last **[SIZE=4]STABLE[/SIZE]** version + upgrade to "Ubuntu +1" usually works. Normal installation **[SIZE=4]OF[/SIZE]** "Ubuntu +1" just newer works.

---

### Post by lucazade on 2011-07-01
> **EgoGratis said:**
> How do you install "Ubuntu +1" for testing? Last version + upgrade? Normal installation + "Ubuntu +1" just newer works.

Thanks!

last version  + upgrade
or directly from daily build:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by cariboo on 2011-07-01
You can install Oneiric Ocelot, any of the regualr ways, using update-manager:

```
update-manager -d
```

just make sure you're running a totally up-to-date and properly working Natty (11.04)

You can get a Live CD iso here:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by EgoGratis on 2011-07-01
Yes if i use the latest stable version and upgrade it to development version it usually works but:

> or directly from daily build:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Does this actually work for you? 

It never works for me.

---

### Post by cariboo on 2011-07-01
What do you mean it never works? 

I just did a clean install on one of my systems yesterday, every thing went without a hitch. I'll probably be doing a clean install on this system later on today, using today's daily live, updated via zrsync.

I either use a CDR\W burned using brasero, or a USB thumb drive created with the Startup Disk Creator utility.

---

### Post by lucazade on 2011-07-01
> Does this actually work for you? 

It never works for me.

I'd say not always, but often during first alphas.

In the latest daily build images there was a broken login manager (lightdm) that leave you in a shell without actually loading the desktop.
Starting the login manager manually it solves this temporary issue.
(sudo service lightdm restart).

another way is to use alternate build image that 
uses a "dos-style" installation instead of loading the desktop.
you can find alternate images here:
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

---

### Post by cariboo on 2011-07-01
I call the alternate install iso text-based, as many users have never seen a dos screen. :)

---

### Post by EgoGratis on 2011-07-01
> **cariboo907 said:**
> What do you mean it never works? 

I just did a clean install on one of my systems yesterday, every thing went without a hitch. I'll probably be doing a clean install on this system later on today, using today's daily live, updated via zrsync.

It just never works. I download the image and use UNetbootin to put it on the USB key. It does not mater if its desktop or alternate CD image there is just no way i will install it successfully. It was like that in past versions too and it is the same now! But the final version i can usually install with no problems. But for development version i never managed to install it unless i installed latest stable version + update. Should i use something else instead of UNetbootin? Is the problem in the fact i don't burn the CD image and use USB key instead? This happened in previous versions too, but now i decided to ask here about it! What do you think.

---

### Post by seeker5528 on 2011-07-01
> **EgoGratis said:**
> How do you install "Ubuntu +1" for testing? Last version + upgrade? Normal installation + "Ubuntu +1" just newer works.

*I* make sure my current installation is up to date, edit '/etc/apt/sources.list', then review any *.list files in '/etc/apt/souces.list.d/' for any PPA or other unofficial source I might be using and typically rename them or disable them.

Then I would most commonly open Synaptic, make sure 'Settings --> Preferences --> General --> System upgrade:' is set to 'Default Upgrade', then click the 'Mark All Upgrades' button. After installing those updates, I usually try to stick to smaller groups of packages, always making sure to look at any packages that would be removed, canceling if I don't like what would be removed or canceling if I can't select all of some group of related packages that seem like they should be all upgraded at once.

Also switch back and forth between upgrading packages and removing obsolete ones, since it is some times necessary to select an obsolete package for removal, to give the resolver a kick in the *** if the resolver is having issues finding a solution when selecting packages to upgrade.

Of course the usage of update manager to go from the current release to the +1 release needs testing as well.

For a new install I would probably try the latest daily ISO first, then if that didn't work get the most recent Alpha or Beta ISO.

Later, Seeker

---

### Post by EgoGratis on 2011-07-01
> **EgoGratis said:**
> How do you install "Ubuntu +1" for testing? Last version + upgrade? Normal installation + "Ubuntu +1" just newer works.

Thanks!

I must correct myself!

Last **[SIZE=4]STABLE[/SIZE]** version + upgrade to "Ubuntu +1" usually works. Normal installation **[SIZE=4]OF[/SIZE]** "Ubuntu +1" just newer works.

If i have installation of NN upgrading to OO this will probably work! If i want to install OO somewhere to test it i will not succeed! This is what i meant. And it was like that in the past too (previous versions of Ubuntu). Is it because i use UNetbootin and do not burn LiveCD from the ISO image or is "daily CD" image usually just too "broken" and you just have to have a bit of luck to download it at a right time?

---

### Post by jbicha on 2011-07-01
Just as a by-the-way, I had to disconnect the Internet to get the July 1 daily build to install. With internet, ubiquity tried updating language-pack-gnome-en package but the latest version of that package has a bug and installation would completely stop then. I expect that the language pack bug will be fixed shortly.

---

### Post by EgoGratis on 2011-07-01
So bottom line you just have to have a bit of luck to get the "daily CD" image that will work. Does my understanding of "the issue" make sense?

---

### Post by cpatrick08 on 2011-07-01
> **EgoGratis said:**
> So bottom line you just have to have a bit of luck to get the "daily CD" image that will work. Does my understanding of "the issue" make sense?

pres alt+f2 type in update-manager -c -d and i will pop up a update manager windows and it will allow you to update to a development verson of ubuntu

---

### Post by EgoGratis on 2011-07-01
Didn't you read what the topic is about?

---

### Post by seeker5528 on 2011-07-01
> **EgoGratis said:**
> So bottom line you just have to have a bit of luck to get the "daily CD" image that will work. Does my understanding of "the issue" make sense?

Not every daily build works, sometimes maybe several days in a row, so there is a luck of the draw factor, but from what you have posted of your own experience it sounds like there may be issues related to you particular hardware that increase the odds that it won't work until later in the dev cycle where versions of stuff change less and focus shifts more and more to refining things for the final release.

Later, Seeker

---

### Post by sparker256 on 2011-07-01
> **EgoGratis said:**
> Didn't you read what the topic is about?
Yes If you have a previous version of Ubuntu then get a daily live from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) and use Startup Disk Creator to make a live USB. In my testing three or four cycles if you can get the live to boot and run on the hardware that you want to install on you have a very good chance of it installing correctly. That being said there may be a bad daily live but if it is bad the chance is it will not boot either.

One other thing is this is a alpha and things break so make sure that your install in on a spare partition spare computer so that if things go wrong you can get back here for help. 

Lastly I always install on separate /root and /home to allow much faster reinstall if that is needed. I do keep versions of daily lives but update until my system is so broke that it is the only option.

Bill

---

### Post by cariboo on 2011-07-01
I'm posting this from a fresh clean install that finished less than 5 minutes ago, I had no problems with the install process,

---

### Post by EgoGratis on 2011-07-02
> Not every daily build works, sometimes maybe several days in a row, so  there is a luck of the draw factor, but from what you have posted of  your own experience it sounds like there may be issues related to you  particular hardware that increase the odds that it won't work until  later in the dev cycle where versions of stuff change less and focus  shifts more and more to refining things for the final release.Yes i am thinking in this direction too but the "funny" thing is if i do latest stable + "Ubuntu +1" i usually can use "Ubuntu +1" just fine. And another thing. On the end of development cycle daily CD  just starts to work... It could be hardware or i just happen to pick daily CD that does not work or i am doing something that i should not with daily CD. Maybe i should burn daily CD to the CD and not use UNetbootin!?

> **cariboo907 said:**
> I'm posting this from a fresh clean install that finished less than 5 minutes ago, I had no problems with the install process,

You used latest daily CD (graphical or alternative)? I downloaded one about a week back and two of them (graphical and alternative) yesterday and had no luck. Did u burn it to CD or put in on the USB and what method did u use? Thanks.

---

### Post by cariboo on 2011-07-02
> **EgoGratis said:**
> Yes i am thinking in this direction too but the "funny" thing is if i do latest stable + "Ubuntu +1" i usually can use "Ubuntu +1" just fine. And another thing. On the end of development cycle daily CD  just starts to work... It could be hardware or i just happen to pick daily CD that does not work or i am doing something that i should not with daily CD. Maybe i should burn daily CD to the CD and not use UNetbootin!?



You used latest daily CD (graphical or alternative)? I downloaded one about a week back and two of them (graphical and alternative) yesterday and had no luck. Did u burn it to CD or put in on the USB and what method did u use? Thanks.

One thing, don't use unetbootin, use the USB Disk Creator utility.

I have done it both ways, this time I used a CDR/W for the daily live iso, the last install I did on my netbook was via a USB thumb drive. I've had zero problems with either using method. I generally use the Desktop iso.

---

### Post by EgoGratis on 2011-07-02
> One thing, don't use unetbootin, use the USB Disk Creator utility.I started using UNetbootin when Ubuntu 10.04  was released and "official tool" just did not work for me. UNetbootin worked for me without any problem for 10.04, 10.10 and 11.04. Final versions. I did some test. I used the same ISO (alternative) daily CD:

UNetbootin (latest version) didn't work. I could start the installation but it was corrupted and didn't went trough. Tool for USB installation creation in Ubuntu 11.04 is not able to create USB installation disk successfully for me. Tried it multiple times! Then i went and burned the image to DVD-RW. Everything worked flawlessly. Burning, installation... Fantastic!

So i am glad in the end that i did ask this question here! After a lot of troubles in the past i decided i will not use Ubuntu tool or UNetbootin for daily CD. This is perfectly clear to me now! I always thought daily CD is just not there yet but it was the other way around. Tools for creating USB installation are not there jet! The only thing i am wondering about and might try in the future when it comes to daily CD development images (beside burning it to the optical disc) is "hybrid ISO". What does that mean and how do i use it? Thanks!

---

### Post by linuxman94 on 2011-07-02
For hybrid ISOs, you don't need to use an extra tool to get the ISO to boot from a USB disk.  All you have to do is go in the terminal and enter this command (check the paths first!) and the USB drive will be bootable.

```
sudo dd if=/path/to/isofile of=/dev/sdb (<-- make sure the of path is correct or you may screw your system!)
```

---

### Post by julianb on 2011-07-03
i recommend just putting the ISO on a usb stick and booting from there. [http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/)

---

### Post by EgoGratis on 2011-07-03
> **linuxman94 said:**
> For hybrid ISOs, you don't need to use an extra tool to get the ISO to boot from a USB disk.  All you have to do is go in the terminal and enter this command (check the paths first!) and the USB drive will be bootable.

```
sudo dd if=/path/to/isofile of=/dev/sdb (<-- make sure the of path is correct or you may screw your system!)
```


Superb! I will try this in the future!

> i recommend just putting the ISO on a usb stick and booting from there.

This look like MultiSystem:

[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

But the "manually way"? I appreciate your answer BUT for daily CD images i will burn the ISO image to optical disc or will try the hybrid ISO (dd) in the future. Without much work and any additional "tools"! :)

---

### Post by EgoGratis on 2011-07-17
OK i "bricked" Oneiric Ocelot test install while testing different things on it and decided it was time to test this method and see how it works:

> sudo dd if=/path/to/isofile of=/dev/sdb (<-- make sure the of path is correct or you may screw your system!)

Everything went  without any problems from beginning to the end!

Thanks for the help!

---

