---
title: "When 11.10 comes out"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by xsabrewulf on 2011-09-18
I have 11.04 installed because I did not want to wait for 11.10.


I have a lot of stuff installed and work related information and I have it set up nice.

when 11.10 comes out, is it possible to UPGRADE keeping everything in tact with no issues? or because its a major release should I reinstall the whole OS?

---

### Post by Lisiano on 2011-09-18
You will get prompted if you want to update to 11.10. No need to re-install. I must say that most people on this forum would probably say that you should do a clean install, but if updating works, just keep on using it. You can always re-install if you have major issues.
Also to answer the question in the thread tittle. October 13th, 2011

---

### Post by dniMretsaM on 2011-09-18
Yes, you CAN upgrade. But upgrades tend to cause problems. So personally, I would recommend backup all your data, (back up the .debs of the programs for easier re-installation if you wish) and do a fresh install. Much safer.

> **Lisiano said:**
> Also to answer the question in the thread tittle. October 13th, 2011

I thought it was the 24th.

---

### Post by Lisiano on 2011-09-18
^---- Told ya about about people saying to re-install.

> I thought it was the 24th.I stand corrected. Note to self. Do not trust random forums. Trust only UbuntuForums and the Ubuntu Wiki
[https://wiki.ubuntu.com/OneiricOcelot](https://wiki.ubuntu.com/OneiricOcelot)

---

### Post by IWantFroyo on 2011-09-18
You can upgrade or do a fresh install. It doesn't matter which one you do, you'll still have to back up.

I prefer a fresh install, because upgrading takes longer, and I have everything already backed up anyways.

---

### Post by Blasphemist on 2011-09-18
My first 3 upgrades I just did as updates. By then I figured I'd messed up enough stuff potentially to start over with a clean install from usb. After all, it's not hard to reinstall software and really everything I wanted was in Documents, Music, Pictures, etc. And not only do you get prompted in the normal update process to do the upgrade if desired, you can also do an upgrade from cd/usb that tries and usually succeeds in doing it fine without loss. Or you can copy/back up what you want and just copy it back in.

Now, I already have a partition with oneiric going. Eventually it will be a released version partition whether I reinstall it to make it clean as it is a sandbox now or just keep updating it. I already use natty, oneiric, fedora, bodhi (I'm on that now), openSUSE, Kubuntu, etc. depending on my interest at the moment. I use a shared partition that has all the docs, pics, music, etc. so the distro is just the front of the truck and interchangeable. I install a new OS at least every week on average as my tastes change and I test something I don't end up liking. I learn from all of it.

---

### Post by dniMretsaM on 2011-09-18
> **Lisiano said:**
> ^---- Told ya about about people saying to re-install.

Getting predictable. Must change tactics.

> **Lisiano said:**
> I stand corrected. Note to self. Do not trust random forums. Trust only UbuntuForums and the Ubuntu Wiki
[https://wiki.ubuntu.com/OneiricOcelot](https://wiki.ubuntu.com/OneiricOcelot)

Ok, I just remembered reading that at the start of the development cycle. It could have changed, but I just wanted to make sure.

---

### Post by IWantFroyo on 2011-09-18
Really there's only one reason to update instead of reinstall, and that's if you've edited system conf files you want to keep (or are too lazy to backup), or if you want to keep the old version of things like GRUB, and a few conf files.

Also, beware. Sometimes the upgrade wizard will throw some more advanced questions at you, that it would be a good idea to use Google for.

As I said, since you have to back up either way, the average user should do a clean reinstall.

Upgrading can be problematic, so I personally trust reinstalls more, anyways.

---

### Post by Lisiano on 2011-09-18
> **IWantFroyo said:**
> Really there's only one reason to update instead of reinstall, and that's if you've edited system conf files you want to keep (**or are too lazy to backup**), or if you want to keep the old version of things like GRUB, and a few conf files.

Also, beware. Sometimes the upgrade wizard will throw some more advanced questions at you, that it would be a good idea to use Google for.

As I said, since you have to back up either way, the average user should do a clean reinstall.

Upgrading can be problematic, so I personally trust reinstalls more, anyways. Sadly the average user doesn't divide / and /home so the average user should try to update. If the average user actually divided / and /home then the average user might be able to decide if he/she wants a re-install or to update.

But yes, backups are recommended either way unless you are a Power-user and know how to recover your files even if you can't boot your OS, your motherboard is fried and you know how to hook up your internal HDD to another computer.
> **dniMretsaM said:**
> Getting predictable. Must change tactics.
Yes sir. Also I suspect you recommend using sudo service instead of sudo /etc/init.d/. And I got a feeling you use SSH.

---

### Post by IWantFroyo on 2011-09-18
> **Lisiano said:**
> Sadly the average user doesn't divide / and /home so the average user should try to update. If the average user actually divided / and /home then the average user might be able to decide if he/she wants a re-install or to update.

But yes, backups are recommended either way unless you are a Power-user and know how to recover your files even if you can't boot your OS, your motherboard is fried and you know how to hook up your internal HDD to another computer.

Yes sir. Also I suspect you recommend using sudo service instead of sudo /etc/init.d/. And I got a feeling you use SSH.

You don't have to reuse the /home partition. You can just put everything back where it was. You just have to copy the folders in your home directory and back them up, then on your new account, you can go inside the folders on your backup drive, and copy and paste them into your new home directory.

I also have a strange feeling that you like to use apt-get instead of aptitude. ;)

---

### Post by Lisiano on 2011-09-18
> **IWantFroyo said:**
> You don't have to reuse the /home partition. You can just put everything back where it was. You just have to copy the folders in your home directory and back them up, then on your new account, you can go inside the folders on your backup drive, and copy and paste them into your new home directory.Remember that the average user is lazy. + Copying the data back and forth will take valuable time in your life you could spend learning about Free software.
> I also have a strange feeling that you like to use apt-get instead of aptitude. ;)Stalker.

---

### Post by vasa1 on 2011-09-19
> **Lisiano said:**
> Remember that the average user is lazy. ...

Some of us (average or below average) users think we are not lazy but just scared stiff reading the disagreement among above average users :D

---

### Post by Lisiano on 2011-09-19
It's not a disagreement. More of a discussion. We just stating our opinions and commenting on others. All the opinions here are good candidates so the average user just has to randomly pick one and stick with it or just read all the opinions and pick one that he/she likes the most

---

### Post by Elfy on 2011-09-19
Some people reinstall, some people upgrade. I upgraded once, it broke. 

If you do upgrade I would be inclined to make sure all ppa's are disabled and that you revert from any proprietary graphics driver back to the default.

You should have backups anyway.

---

### Post by uncontrolable™ on 2011-09-19
I swear by clean installs. Creating a /home partitions and having backups of data is a must. At least with a clean install, you will know whether your system will work well with the new version in a much shorter amount of time.

---

### Post by dniMretsaM on 2011-09-19
> **Lisiano said:**
> Yes sir. Also I suspect you recommend using sudo service instead of sudo /etc/init.d/. And I got a feeling you use SSH.

I honestly have no idea what that means and I have never had any reason to use SSH (except for the occasional use with my iPod). Lol.

---

### Post by 3rdalbum on 2011-09-19
> **Lisiano said:**
> Sadly the average user doesn't divide / and /home so the average user should try to update. If the average user actually divided / and /home then the average user might be able to decide if he/she wants a re-install or to update.

Hasn't been true for a while. If you use the manual partitioning step and do not opt to format your root partition, Ubuntu will tell you that it will delete system files on that partition. **It will retain your /home, even if it's on the same partition.**

I think it's done that since 9.10. Maybe longer.

---

### Post by P05TMAN on 2011-09-19
> **IWantFroyo said:**
> You can upgrade or do a fresh install. It doesn't matter which one you do, you'll still have to back up.

I prefer a fresh install, because upgrading takes longer, and I have everything already backed up anyways.

I have, personally, always had more issues with a fresh install, either because of a bad download, or just installation issues that come about. I just upgrade through the update manager or command line.

---

### Post by coffeecat on 2011-09-19
> **Lisiano said:**
> 
I stand corrected. Note to self. Do not trust random forums. Trust only UbuntuForums and the Ubuntu Wiki
[https://wiki.ubuntu.com/OneiricOcelot](https://wiki.ubuntu.com/OneiricOcelot)

Even then there may be an error - or inconsistency. If you go to that link, it says:

> "Oneiric Ocelot" is the code name for Ubuntu 11.10, scheduled for release on 24 October 2011. See the Oneiric release schedule.

But if you click on the [Oneiric release schedule](https://wiki.ubuntu.com/OneiricReleaseSchedule) link, it says Week 24, October 13th for Final Release. I think there's been a misread, reading week 24 as October 24th. October 13th is a Thursday; October 24th is a Monday. All earlier releases have been on a Thursday, if I remember correctly.

---

### Post by Monsuco on 2011-09-19
> **3rdalbum said:**
> Hasn't been true for a while. If you use the manual partitioning step and do not opt to format your root partition, Ubuntu will tell you that it will delete system files on that partition. **It will retain your /home, even if it's on the same partition.**

I'd still suggest backing up your /home somewhere. There are plenty of things that can go wrong. I've never regretted having a backup.

Ubuntu systems that have been upgraded do tend to be a tad less stable in my experience than ones that have a fresh install. I've generally screwed with so much that it's in my best interest just to start fresh every 6 months anyway. 11.04 never worked for me so I skipped it and I really an anxiously awaiting 11.10 and the chance to start fresh. I must give Ubuntu credit though, in my experience in place upgrades of Ubuntu are generally more stable than in place upgrades of Windows.

---

### Post by MG&amp;TL on 2011-09-19
Windows upgrades are hell :( . I would personally reinstall, but upgrading works for me.

I just looked up what aptitude was. :D

---

### Post by madjr on 2011-09-19
make a new partition and test it on there. Do not upgrade.

11.10 is dramatically different on the inside

---

### Post by dniMretsaM on 2011-09-19
> **coffeecat said:**
> But if you click on the [Oneiric release schedule]("https://wiki.ubuntu.com/OneiricReleaseSchedule") link, it says Week 24, October 13th for Final Release. I think there's been a misread, reading week 24 as October 24th. October 13th is a Thursday; October 24th is a Monday. All earlier releases have been on a Thursday, if I remember correctly.

Ok, thanks for clearing that up. And yeah, that makes more sense. At any rate, it means new stuff sooner. Can't wait!

---

### Post by Mathias1 on 2011-10-08
What is the best way to backup my apps and settings and then restore them?

I'm planning to use GNome 3 on 11.10..

---

