---
title: "Should I be worried about using an old hard drive?"
date: 2017-10-26
forum: New to Ubuntu
---

### Post by matthorton2 on 2017-10-26
Hi,

I want to move over to Ubuntu from Mac OS X as I feel Ubuntu has got to the point where it can do everything I need. I have used Linux a long time ago (2004) but I've got no idea how worried I should be about using an old 320gb SATA hard drive with the current Ubuntu? Should I worry about files getting corrupted if my hard drive starts to fail? Obviously, I will have good backups too. 

I have checked the hard drive with the live cd and disks app, smart test shows everything to be ok. 
I have also ran badblocks -wvs from the live cd and that also shows no errors. 

I have a second old Seagate Barracuda 320gb IDE hard disk. Should I put that into the pc too and set up some kind of mirroring? The motherboard offers raid and I understand that software raid and LVM offer mirroring too. Do I bother doing any of these to avoid hassle later on or is it not necessary with the current file system?

Many thanks, 
Matt


------
3GHZ x4 AMD, 8GB RAM, GTX 970

---

### Post by Georgia boy on 2017-10-26
Why not? Not being smart retort but if all seems to work I'd give a shot. There's people that buy used drives off of Ebay and they last them.If you are going to backup as you say then I'd go for it. I'm still running my old MS Windows XP media Center Edition 2005 Hp Paavilion a1440n on all original equipment.All I did was add a couple mem cards to bring it up to 4gb mem from the 2 it came with. Still running good. 

Should see the hell I cause when telling the spammers that call what kind of keyboard I'm using. Pees them off when I tell them I'm running Linux on the pc and using keyboard. Keep saying I lied to them.  :D

But knowing that there's people that go out on places like Ebay and get used stuff or from pc's that's being tossed and still using the stuff I'd say give it a shot. 

But see what others will say also. That's just my view on the subject.

---

### Post by Andrew_Lucas on 2017-10-26
I would second what's already been posted. If you're not worried about failure, because you have backups, why not just suck it and see?

---

### Post by Bucky Ball on 2017-10-26
Install Ubuntu, tweak it to how you like it then immediately clone the install before going any further so if the drive dies, you can install a new on and clone the backup to the new one and back to square one. 

If it's working, don't waste it. It still has some useful life. If you don't want to take the chance, give it to someone  who will or think of the environment and recycle it, if you can do so in your part of the world. 

Working computer parts should never become landfill (and no computer parts should in the 21st century, but that's the world we live in and another story ...). :)

---

### Post by matthorton2 on 2017-10-26
> **Andrew_Lucas said:**
> I would second what's already been posted. If you're not worried about failure, because you have backups, why not just suck it and see?

What I'm worried about is a file becoming corrupt, me not noticing, and then one day finding that something doesn't work. It would mean having to find the problem file and then digging through backups to find a working version of it. If I can take steps now, to avoid hassle like this, I will. 

Is this something that happens with the current filesystem or am I worrying needlessly? Would setting up a mirrored drive prevent against this or would it be a waste of time?

...I think I read somewhere that bad blocks are automatically 'remapped' so that they are not used and no data is lost. Is this correct?

---

### Post by RobGoss on 2017-10-26
I would have to say loosing data can happen at any point on any machine, having a backup is always a smart thing to do

I have a few older machine that have SATA hard drives in them and I don't worry at all about anything failing. Ubuntu works great out of the box, well at least for me when ever I do an installation so no worries there

Give it a go and see how it runs

---

### Post by Autodave on 2017-10-26
13 machines running. Oldest is a single core, 2 gig RAM, EIDE HD with a build date of 1996. Still going strong.

---

### Post by RobGoss on 2017-10-26
+1 Audodave

---

### Post by ajgreeny on 2017-10-26
I still use a couple of very old IDE disks in a caddy as a backup destination.

They both came out of old machines long since gone to the great computer-heaven, but these old disks still perform fine for the purpose for which I use them.

---

### Post by Tadaen_Sylvermane on 2017-10-27
Just because something is old doesn't mean it won't last, while new does not mean going to last either. Things fail and it's quite random. I'd use it till it dies. As you said, you have good backups. No sense throwing away a drive that very well could keep running for a few years yet.

---

### Post by SeijiSensei on 2017-10-27
If you do have two equal sized drives, then I would use both to create a RAID1 array with mdadm.  I'd partition the drives to have a small /boot partition (say 1 GB), a larger main partition for / (say 30-40 GB), and allocate the rest to /home. I'd not worry about RAID for the first two, but use it to create the /home filesystem which is where you'll be storing most of your personal stuff.

One other test you can run is to install the **smartmontools** package to view each drive's S.M.A.R.T data.

---

### Post by matthorton2 on 2017-10-29
thanks for all the advice, made me feel a lot more comfortable using the old drive. i'll just make sure i have backups. i also ran smartmontools and everything is ok.

SeijiSensei, would you still recommend raid1 with mdadm for the sake of convenience even if i have a good system of backups?[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=698195")

---

### Post by SeijiSensei on 2017-10-29
RAID is not a backup solution. It's intended to provide redundancy in the case of a drive failure. If putting it together seems more work than it is worth, that's fine. In this case where the drives' lifetimes are problematic, RAID might provide some insurance.  Backups are good, but even better if they are not needed.

---

### Post by ra7411 on 2017-10-29
You can get "powered-on" cumulative time from Ubuntu  Disks,  cntrl+s.

From the top link, below:
[COLOR=#666666][FONT=&amp]The chart below shows the percentage of drives at Backblaze that are still alive at different ages:[/FONT][/COLOR]

[LIST]
[*]For the first 1.5 years, drives fail at 5.1% per year.
[*]For the next 1.5 years, drives fail LESS, at about 1.4% per year.
[*]After 3 years though, failures rates skyrocket to 11.8% per year.
[/LIST]


Below are a couple links that might help.
I assume this info is reliable and would be interested in comments on it,  either way.

[https://www.backblaze.com/blog/how-long-do-disk-drives-last/](https://www.backblaze.com/blog/how-long-do-disk-drives-last/)

[https://www.backblaze.com/blog/hard-drive-reliability-stats-q1-2016/](https://www.backblaze.com/blog/hard-drive-reliability-stats-q1-2016/)

---

### Post by kurt18947 on 2017-10-29
I'll second the "disks" app found on live installs. A few click will get you to the SMART data for your disk. I'm always surprised by how little run time is shown, a disk that may have been installed in a fairly active machine for a couple years may show only a few months runtime. SMART also gives quite a number of other measures of disk health. If all those parameters are within limits, I'd use the disk without reservation. Of course backup of personal info goes without saying. It's pretty fast to restore an Ubuntu system if necessary.  I use flash drives and Lucky Backup which is one GUI for rsync, there are other GUI s as well.

---

### Post by Bucky Ball on 2017-10-29
> **kurt18947 said:**
> I'll second the "disks" app found on live installs.

The 'Disks' app (if we are talking about the same thing) is actually gnome-disk-utility and is in the repos. You don't need to be in a live session to use it (if a live session booted from the install media is what is meant by 'live install'). 

You can install 'Disks' (gnome-disk-utility) from your package manager or

```
sudo apt install gnome-disk-utility
```

:)

---

### Post by poorguy on 2017-10-29
This is what ***Gnome Disk Utility*** shows about my hard drive. 
It's been this way since 2014 and hasn't changed never changes.

Disk is OK, ***219 bad sectors*** (33° C / 91° F)

---

