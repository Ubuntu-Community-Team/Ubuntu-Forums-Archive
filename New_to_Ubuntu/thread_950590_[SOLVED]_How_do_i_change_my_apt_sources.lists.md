---
title: "[SOLVED] How do i change my apt sources.lists"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by J03y on 2008-10-17
How do i change my apt sources.lists to point to [http://old-releases.ubuntu.com/?](http://old-releases.ubuntu.com/?) Please, i need exact steps. :(

---

### Post by LowSky on 2008-10-17
I just skimmed the site you posted and don't see any reason why you would need that in your apt sources? Not to mention the site was slower than molases in the Artic

---

### Post by NewJack on 2008-10-17
Got to agree with LowSky, why would you want to point your sources.list there?

---

### Post by J03y on 2008-10-17
> **NewJack said:**
> Got to agree with LowSky, why would you want to point your sources.list there?

Read this and then you'll know why:

[https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades)

Still I'm not really sure if this is what i have to do to upgrade from 6.10 to 7.04 =P

---

### Post by drs305 on 2008-10-17
I normally provide answers without editorial comment unless I think someone is going to 'hurt' their machine, so this post will just tell you how to do what you are asking.

I have not used this address and am not on my ubuntu machine, but in general this is how you should do it. For this example, I will use the 'edgy' repository. Should you want another distro, go to the link and investigate what is available (hoary, breezy, etc).

Open a terminal:

Backup and open sources.list for editing:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.17102008
gksudo gedit /etc/apt/sources.list
```

The address of the old repositories is:
[http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/)

If it conforms to the standard, the sources.list address would omit the 'dists' directory, so the line to add to sources list would be:
```

deb http://old-releases.ubuntu.com/ubuntu **edgy** main multiverse restricted universe

```

Change **edgy** to the applicable distro.
Save the file, then run the following to update your system:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by LowSky on 2008-10-17
Your still using 6.10? there is no security supports for that and 7.04 is now not supported as of yesterday I believe...
the newest version, 8.10 comes out in 2 weeks!
If you need long term support Upgrade to 8.04 using a Live CD that way you have no glitches and things run just fine, just back up your files to another partition or CD-R or what ever

---

### Post by J03y on 2008-10-17
> **LowSky said:**
> Your still using 6.10? there is no security supports for that and 7.04 is now not supported as of yesterday I believe...
the newest version, 8.10 comes out in 2 weeks!
If you need long term support Upgrade to 8.04 using a Live CD that way you have no glitches and things run just fine, just back up your files to another partition or CD-R or what ever Yea, I tried to burn ubuntu 8.04 into a CD but messed up my CD-RW Drive. So i think my only choice is to buy the CD.:(

---

### Post by Duck2006 on 2008-10-17
> **J03y said:**
> Yea, I tried to burn ubuntu 8.04 into a CD but messed up my CD-RW Drive. So i think my only choice is to buy the CD.:(

Or go to the ubuntu web site and chose ship-it and they will send you one for free.

---

### Post by J03y on 2008-10-17
> **Duck2006 said:**
> Or go to the ubuntu web site and chose ship-it and they will send you one for free.But I have to wait for ten weeks.

---

### Post by Duck2006 on 2008-10-17
> **J03y said:**
> Well, I don't think they,ll send it completely free, will they? o.O

Yes

---

### Post by J03y on 2008-10-17
I have to wait for ten weeks :mad:

---

### Post by Duck2006 on 2008-10-17
> **J03y said:**
> I have to wait for ten weeks :mad:

That's the only down side to it. So if you want it sooner you have to buy one or download one and burn it to a CD.

---

### Post by NewJack on 2008-10-17
Where do you live?  If you are in the States, I'll burn a copy and mail it out to you, for free of course.

---

### Post by lwhitney on 2008-10-17
drs305, what then? i did what you said and it gave me a done with :

E: some indexes failed to download, ignored or old ones used..

how do you run the upgrade? assuming one ca

---

### Post by panhandle on 2008-10-17
It doesn't actually take 10 weeks for delivery. I ordered one because I was curious and it arrived in about 14 days.

---

### Post by drs305 on 2008-10-17
> **lwhitney said:**
> drs305, what then? i did what you said and it gave me a done with :

E: some indexes failed to download, ignored or old ones used..

how do you run the upgrade? assuming one ca

I am on a business trip and don't have access to ubuntu at the moment. I will be home in about 8 hours and can look at it then.

You may need to make sure your new reference is the only repository that is being looked at. Since the message says 'some indexes...' failed, if it is trying to access the original, defunct repos you will get that message. Before abandoning this attempt, I would make sure your attempt to upgrade only includes this new repository - that is disable all other repositories.

I can't remember what edgy has - if you have synaptic or software sources you can go into the repository list and disable all references other than the 'old-releases' one. If you have to do it manually, open up sources.list as you did before and place a comment symbol (#) in front of every line *except* the line containing 'old-sources'. This will prevent the update from looking at edgy repositories that no longer exist.

If that doesn't work, the example I gave put the website address in the format of a normal sources.list deb entry. It is possible you have to use the full address (include the '/dists/' in the address) or it may be that this repository simply won't work in the manner I suggested.

---

### Post by J03y on 2008-10-17
how do i disable the repos again?

---

### Post by J03y on 2008-10-17
> **drs305 said:**
> I am on a business trip and don't have access to ubuntu at the moment. I will be home in about 8 hours and can look at it then.

You may need to make sure your new reference is the only repository that is being looked at. Since the message says 'some indexes...' failed, if it is trying to access the original, defunct repos you will get that message. Before abandoning this attempt, I would make sure your attempt to upgrade only includes this new repository - that is disable all other repositories.

I can't remember what edgy has - if you have synaptic or software sources you can go into the repository list and disable all references other than the 'old-releases' one. If you have to do it manually, open up sources.list as you did before and place a comment symbol (#) in front of every line *except* the line containing 'old-sources'. This will prevent the update from looking at edgy repositories that no longer exist.

If that doesn't work, the example I gave put the website address in the format of a normal sources.list deb entry. It is possible you have to use the full address (include the '/dists/' in the address) or it may be that this repository simply won't work in the manner I suggested.I opened the repos list with synaptic but I'm not sure what to disable. Some expecific details on what to disable exactly will be most appreciated.:)

---

### Post by lwhitney on 2008-10-17
jo3y and drs305...i believe we can get this to work. i have to go to a wedding, so i don't know how long i will be (open bar). drs305 is right! although its not quite as simple. you are going to have to start the update just looking at that one old-release repos, it will run a little then it will say something like changing edgy to feisty, here you will pause and go  into (terminal) the apt/souces.list and manually change these (the automatic didn't work for me). you also have to take the 'us' off of the archive repos ( i am going to try both...with 'us' and without 'us'). thats as far as i have gotten..i have to go this second but will come back to this asap.

i will email when i can

ps i had a terminal open and the update manager open at the same time.

---

### Post by J03y on 2008-10-17
> **lwhitney said:**
> jo3y and drs305...i believe we can get this to work. i have to go to a wedding, so i don't know how long i will be (open bar). drs305 is right! although its not quite as simple. you are going to have to start the update just looking at that one old-release repos, it will run a little then it will say something like changing edgy to feisty, here you will pause and go  into (terminal) the apt/souces.list and manually change these (the automatic didn't work for me). you also have to take the 'us' off of the archive repos ( i am going to try both...with 'us' and without 'us'). thats as far as i have gotten..i have to go this second but will come back to this asap.

i will email when i can

ps i had a terminal open and the update manager open at the same time.Thank you a lot, honestly. But right now i just want to disable all references other than the 'old-releases' one, but I'm not sure how to do it.

---

### Post by drs305 on 2008-10-17
> **J03y said:**
> I opened the repos list with synaptic but I'm not sure what to disable. Some expecific details on what to disable exactly will be most appreciated.:)

Again, I'm going from memory. If your synaptic is similar to the current version, you would untick everything in Ubuntu Software, as  these are links to the now-disabled official edgy repositories. In the Third-Party tab (again, if it is like the current version), you would untick every entry except the one to the 'old-versions' link. Essentially everything officially connected to 'edgy' is no longer supported and probably not available online. So the only reference you want enabled is the one to 'old-versions'.

Since edgy's synaptic may not look like the current version, if this doesn't work you can open sources.list and the only line without a comment should be the 'old-versions' reference. 

Even with all this, you may still get the message - I don't know how ubuntu's update system will interact with the 'old-packages' repository. You might check their site to see if there are any instructions or information about using it to update older systems.

---

### Post by J03y on 2008-10-17
> **drs305 said:**
> Again, I'm going from memory. If your synaptic is similar to the current version, you would untick everything in Ubuntu Software, as  these are links to the now-disabled official edgy repositories. In the Third-Party tab (again, if it is like the current version), you would untick every entry except the one to the 'old-versions' link. Essentially everything officially connected to 'edgy' is no longer supported and probably not available online. So the only reference you want enabled is the one to 'old-versions'.

Since edgy's synaptic may not look like the current version, if this doesn't work you can open sources.list and the only line without a comment should be the 'old-versions' reference. 

Even with all this, you may still get the message - I don't know how ubuntu's update system will interact with the 'old-packages' repository. You might check their site to see if there are any instructions or information about using it to update older systems.Yea, I went to their website, and there it said the same thing that you said, but they were saying it with less details. But, i think i did something with the backups and i think ill have to re-install the live CD again.

---

### Post by J03y on 2008-10-17
Never mind i got it working, thank you.:)

---

