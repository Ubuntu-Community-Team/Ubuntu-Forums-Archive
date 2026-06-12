---
title: "Ran into a major problem with Ubuntu last night"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by ImThatNerd on 2008-10-26
I ran into a problem when I upgraded to the 8.10 beta last night. The problem can be read (and helped to solve?) [here]("http://ubuntuforums.org/showthread.php?t=959032"). So I am thinking that I won't be able to fix my 8.10 so I was wondering is it possible to keep my current partion and all my files and install 8.04/7.10 and not have to reformat? I have the 8.04 live CD. I just have a ton of files I cant backup at this time and would hate to lose them in a reformat.

---

### Post by dhughes on 2008-10-26
If you put /home is on its own partition I don't see why not.

---

### Post by Xiong Chiamiov on 2008-10-26
> **dhughes said:**
> If you put /home is on its own partition I don't see why not.
If you haven't, then it *might* be possible to change your sources.list to fetch from the Hardy repos again, rather than the Intrepid ones, and downgrade all of your packages.  I'm not sure if apt has that capability.

---

### Post by Sirhanz on 2008-10-26
I read your original problem post, if its not too late, I suggest running ```
sudo apt-get purge
```
Then ```
sudo apt-get update -f
```

---

### Post by handydan918 on 2008-10-26
> **Xiong Chiamiov said:**
> If you haven't, then it *might* be possible to change your sources.list to fetch from the Hardy repos again, rather than the Intrepid ones, and downgrade all of your packages.  I'm not sure if apt has that capability.

Indeed, if you haven't, you can still use the live cd to back up /home...

---

### Post by ImThatNerd on 2008-10-26
> **dhughes said:**
> If you put /home is on its own partition I don't see why not.

How can I tell?

> **Xiong Chiamiov said:**
> If you haven't, then it *might* be possible to change your sources.list to fetch from the Hardy repos again, rather than the Intrepid ones, and downgrade all of your packages.  I'm not sure if apt has that capability.

I can't fetch any sources or packages when I try to do apt-get update in the command prompt in recovery.

> **Sirhanz said:**
> I read your original problem post, if its not too late, I suggest running ```
sudo apt-get purge
```
Then ```
sudo apt-get update -f
```

I tried that and I got some errors about not being able to fetch sources/packages.

> **handydan918 said:**
> Indeed, if you haven't, you can still use the live cd to back up /home...

I have the live cd, how would I go along to backing up /home?

---

### Post by ImThatNerd on 2008-10-26
Any advice? I need to write a big paper for homework tonight.

---

### Post by Xiong Chiamiov on 2008-10-26
If you can't access the internet through Recovery Mode, boot up normally and, once you get the black screen, press Ctrl+alt+F1 to get to a text login (or possibly ctrl+alt+f2).  You can login and try the apt commands again.

---

### Post by Slug71 on 2008-10-26
When you installed 8.04 did you make a separate /home partition? If so when you reinstall 8.10 just don't format the /home.

---

### Post by mike555 on 2008-10-26
put in the live cd , restart so your running from the cd, browse to your files you want to backup and put them on a thumbdrive or external harddrive, or maybe even burn them to cd/dvd ...... once your sure you have them saved ,just install Ubuntu again .......

---

### Post by ImThatNerd on 2008-10-26
> **Slug71 said:**
> When you installed 8.04 did you make a separate /home partition? If so when you reinstall 8.10 just don't format the /home.

I installed it through update manager so I didn't have that option I don't think.

---

### Post by handydan918 on 2008-10-27
It shouldn't matter too much. Just plan on doing the backup. If you can copy your whole /home directory to some other medium ( flash drive, cd/dvd, etc.) that means you can just do a fresh install. Just be sure to verify the backup is useful before reformatting your system.

---

### Post by ImThatNerd on 2008-10-27
I can't backup to a CD or Flashdrive since what I need to save is way to big in size. So I can't just make a backup of home that saves on the hard drive and use that? I really don't want to reformat.

---

### Post by NullHead on 2008-10-27
I would download a copy of gparted and shrink your main partition a enough to make a new ext3 partition and move your files over to the other partition. Then just format the partition with ubuntu on it. 

Make sure to be **very** clean on which partition your erasing though. My suggestion could easily be done wrong and you could use ALL of your data with out even knowing it. 

It could be tricky for you if you're inexperienced with using gparted and live cds/command lines.

---

### Post by starcannon on 2008-10-27
> **NullHead said:**
> I would download a copy of gparted and shrink your main partition a enough to make a new ext3 partition and move your files over to the other partition. Then just format the partition with ubuntu on it. 

Make sure to be **very** clean on which partition your erasing though. My suggestion could easily be done wrong and you could use ALL of your data with out even knowing it. 

It could be tricky for you if you're inexperienced with using gparted and live cds/command lines.
+1 to this idea.

For the paper that needs written tonight, I would suggest writing it using Open Office from the LiveCD, saving the paper to a thumbdrive, and tackling the tech issue this weekend when you have more time, your just gonna be stuck with LiveCD and a thumbdrive for a few days. It's either that, or get an extension on the paper from your professor.

As an aside, it would be good on this new install to create a separate /home partition(indeed the one you create using gparted could work for this). And its generally a less than optimal idea to experiment on your mission critical machine, especially when you have no easy way to back up the mission critical data... russian roulette comes to mind.

GL hope it works out for you.

---

### Post by kansasnoob on 2008-10-27
Well, first of all regarding your 8.10 issues I'd seriously consider this:

[http://ubuntuforums.org/showthread.php?t=950851](http://ubuntuforums.org/showthread.php?t=950851)

Now, I haven't tried it! But I've followed Bobnutfield's advice several times and found him to be reliable.

I have googled to find out what the -phigh part of that command does but haven't found an answer.

As far as installing a new Linux OS and copying files back and forth - YES YOU CAN! Look at this:

[ATTACH]89918[/ATTACH]

You can see I have two Linux OS's - sda1 is 8.04 and sda5 is 8.10. I have a shared swap, but that's only because I was doning some testing (this tiny 30GB drive is just a test drive) - although I normally do that all the time on my normal drive because I usually do run Windows and two Ubuntu based distros on my regular drive.

And I can easily move files from one install to the other. Look:

[ATTACH]89918[/ATTACH]

I can mount the "other" OS to access ALL files there and copy them to my running OS.

My tray(s) are layed out different than the normal Gnome desktop because I can't see the top panel, but you see I have the "window switcher" next to my trash.

So I simply open my HOME in window #1 and then open the other "partition/OS" in window #2. Then I can just copy and paste literally anything from one to the other.

I do not recommend copy and pasting entire directories (like Mozilla) in one fell swoop! Whatever you do, just be patient!

Make sure everything you wanted to copy is where you want it to be before you delete the old partition. And be sure it works! You can backup any file or directory before "replacing or merging" the files.

Clear as mud:confused:

---

### Post by kansasnoob on 2008-10-27
> **kansasnoob said:**
> Well, first of all regarding your 8.10 issues I'd seriously consider this:

[http://ubuntuforums.org/showthread.php?t=950851](http://ubuntuforums.org/showthread.php?t=950851)

Now, I haven't tried it! But I've followed Bobnutfield's advice several times and found him to be reliable.

I have googled to find out what the -phigh part of that command does but haven't found an answer.

As far as installing a new Linux OS and copying files back and forth - YES YOU CAN! Look at this:

[ATTACH]89918[/ATTACH]

You can see I have two Linux OS's - sda1 is 8.04 and sda5 is 8.10. I have a shared swap, but that's only because I was doning some testing (this tiny 30GB drive is just a test drive) - although I normally do that all the time on my normal drive because I usually do run Windows and two Ubuntu based distros on my regular drive.

And I can easily move files from one install to the other. Look:

[ATTACH]89918[/ATTACH]

I can mount the "other" OS to access ALL files there and copy them to my running OS.

My tray(s) are layed out different than the normal Gnome desktop because I can't see the top panel, but you see I have the "window switcher" next to my trash.

So I simply open my HOME in window #1 and then open the other "partition/OS" in window #2. Then I can just copy and paste literally anything from one to the other.

I do not recommend copy and pasting entire directories (like Mozilla) in one fell swoop! Whatever you do, just be patient!

Make sure everything you wanted to copy is where you want it to be before you delete the old partition. And be sure it works! You can backup any file or directory before "replacing or merging" the files.

Clear as mud:confused:

Oops! I messed up the second screenshot!

[ATTACH]89920[/ATTACH]

---

