---
title: "need good backup/restore plan"
date: 2020-02-28
forum: New to Ubuntu
---

### Post by coley9225 on 2020-02-28
I'm a noob, just so you know. I know enough, and learn fast enough, to figure things out sometimes. I know enough to experiment and get myself into trouble sometimes. I've played with live usb for a couple years , untill I finally fought my way through a dual boot install. Anyway, I've had lubuntu 18.04 installed for about 4 weeks, and lubuntu 19.10 for about 3, and messed both up to the point of needing to reinstall and start over. I've written 2 bash scripts that work(credit to those who helped, here on the forums), and installed apps. I need a backup and restore program, cli or gui, that is not to complicated, or a method such as dd, so when I screw things up again I can easily restore my system, and pickup where I was, without the hassle of a reinstall and reinstalling all my added apps. Thanks, in advance.

---

### Post by TheFu on 2020-02-28
Have you searched these forums for answers yet?  There are 500 different backup/restore techniques, each with PROS/CONS and all with caveats. 

Again, these forums are full of prior knowledge.

Backups can solve many problems, if performed correctly.  

If we do image-based backups, that restricts many things from being possible. They aren't flexible.  OTOH, they are bonehead simple, but downtime is required so almost nobody actually creates images.  Images are the size of the source, so having versioned imaged backups usually isn't possible.

If we do file-based backups, it is much more flexible, at the cost of slightly more complexity. Being able to restore to a completely different machine, different storage, only selected files, selected directories, and don't get me started about having versioned backups - say 180 days of versioned backups that fit in about 1.3x the storage.  With just a little pre-planning, we can easily capture a list of manually installed packages, which is much more efficient than actually backing up all those files.

Some stuff to think about.

---

### Post by ra7411 on 2020-02-28
I'm what I would call a routine Ubuntu user - a couple desktops that I use for business, personal business and entertainment.

When I install Ub, I separate the o/s (/) from the my user files (/home). My /home user files are about 200 gbs, and after the first lengthy backup, I do quick daily incremental backups. My o/s is about 12 gbs, I back that up about once a month.

I use 2 backup programs: 

1] grsync - an incremental gui program that can be installed from the software center, it's used for backing up user files (/home).
2] qt5-fsarchiver - a gui full backup program for the o/s, it saves everything in that partition. It takes maybe 15 minutes to backup the whole o/s, and about 1/2 that to restore it.
    Fsarchiver is easy to install for terminal use, but getting the qt5- gui set up can be a hassle. Also, most of the gui versions around have poor english wording. "Stored partition" button is actually to store the partition you're backing up. It backs up and restores quickly, and is a good choice to preserve your o/s before updates or any big changes you're going to try. I've used it for a number of restores and it worked. You can backup the o/s "live" - that is, while you're using the computer for work. You can install fsarchiver through Synaptic package mgr, and sometimes synaptic shows qt5-fsarchiver, but how well it actually installs the gui is mixed.

Where to put your backups is an important part of any plan. An additional hard drive in the machine separate from where the main files are is best in case the main HD fails. But what if the machine gets burnt by an electrical glitch or lightning? A backup storage that is kept out of any wire hookup except during use is good, but what if the whole place burns down? You can upload everything to the "cloud", but unless you encrypt everything, there's no security/privacy. Also, many ISPs have much slower upload speeds than download which may make the whole process too slow.  
Basically, you have 3 backup storage "type areas" and you have to allocate files to those depending on time and consequences of losing data.

---

### Post by Tadaen_Sylvermane on 2020-02-29
Unless heavily customized I find just wiping out and reinstalling easier than trying to restore my systems. As long as you have your data safe that is my recommendation. 

I second the separate data however I use a partition just for data with folders symlinked in into my home folder. This way no home files carry over. There are pros and cons to both methods.

---

### Post by GhX6GZMB on 2020-02-29
I think most replies are missing the point, which is that of a new user experimenting with Lubuntu. I was at exactly the same point 8 months ago: messing around and getting lost. The only option was: reinstalling.

Coley, first get rid of the double Ubuntu/Lubuntu installation, it makes no sense.

When that's done, install Timeshift. It's already available in your package, you just need to install it.

Run Timeshift and do a **full** backup including /root and /home. Now you have a basic image. When restoring you can always exclude stuff that you don't want to restore.

Then, play around, produce disasters and modify stuff you shouldn't.

You'll always be able to get back to the previous state.

Have Fun :)

---

### Post by DuckHook on 2020-02-29
I've found that there is an easy-ish, simple-ish, somewhat trouble-free-ish way to backup system files. The mealy-mouthed phrasing in the preceding sentence should be a dead giveaway that it is not really a slam-dunk either.

The way I do it is to set up my system for multiboot. Once booted into any one partition, the other partitions are then unencumbered and free to *dd* onto external media. To back up the current partition, simply boot into an alternate one.

Having outlined this methodology, I must admit to rarely making use of it. Like Tadaen_Sylvermane says, the OS is not my focus. It's always the data. If the data is safe, reinstalling the OS is merely an annoyance. A big annoyance perhaps, but never a disaster.

What I've found to be a much more useful strategy is the following:

I have an old box that I fire up about once every two weeks. Once it is running, I update its OS and *rsync* my */home* directory to it. That way, if my working box fails, I have an entirely separate piece of HW that I can have up and running almost instantly. In my experience, HW failures are even more problematic than OS failures because waiting for/buying physical parts can be more hassle than reinstalling an OS.

Re data: I go one step further: data is on mirrored NASes that are backed up every night. Directories are then symlinked over the network back to locations where apps expect to find them. My wife shares the same data on some files (Music, Photos, Videos, etc). Personal or unique stuff (Desktops, Docs, Downloads, etc) are kept locally but *rsync-ed* to the NASes. Getting the initial *rsync* scripts right was not trivial (eg hunting down and excluding tmps/caches), but you only have to do it once, then a cron job runs it nightly.

---

### Post by DuckHook on 2020-02-29
> **ml9104 said:**
> I think most replies are missing the point, which is that of a new user experimenting with Lubuntu. I was at exactly the same point 8 months ago: messing around and getting lost. The only option was: reinstalling.

Coley, first get rid of the double Ubuntu/Lubuntu installation, it makes no sense.
Disagree. See my previous post.
> When that's done, install Timeshift. It's already available in your package, you just need to install it.

Run Timeshift and do a **full** backup including /root and /home. Now you have a basic image. When restoring you can always exclude stuff that you don't want to restore.

Then, play around, produce disasters and modify stuff you shouldn't.
Again, disagree. See below.
> You'll always be able to get back to the previous state.

I do agree with this, but not in the way you have outlined.

Respectfully, I think your assessment is in error. The OP was not merely asking a technical question. The more fundamental context underlying the question was, "how can I make life easier on myself and recover from screwups?"

The old-timers were answering that more underlying context as much as the question itself. And in that spirit:

@coley9225

I would highly recommend that you ***not*** do your experimenting on your bare-metal installs. Instead, spin up VMs and experiment on them instead. Break them as much as you want because it is child's play to fall back to a good snapshot. Keep your base OS pristine, as close to default as possible, and refrain from installing any PPAs, extensions, customizations or other funny business. You will thank yourself for such self-discipline when your upgrades go as smooth as silk and you rarely have to visit these forums for emergency help.

---

### Post by GhX6GZMB on 2020-02-29
@DuckHoook, did you read the OP at all?
You're a major professional at a level that neither I not the OP can follow. Please!

You can disagree with me, fine, but you're in a completely different world. OP and I are both noobs, and your super-advanced, multi-machine, multi-whatever VM setups are only frightening, not helpful.

Just sayin'

---

### Post by DuckHook on 2020-02-29
> **ml9104 said:**
> @DuckHoook, did you read the OP at all?
You're a major professional at a level that neither I not the OP can follow. Please!

You can disagree with me, fine, but you're in a completely different world. OP and I are both noobs, and your super-advanced, multi-machine, multi-whatever setups are only frightening, not helpful.

Just sayin'
While hardly a professional and not at all a "major" professional, I understand and accept your point. Sometimes, we old hands forget what it's like when first starting out.

That said, I stick with my last recommendation: do your experimenting on a VM. The OP is capable of installing multiboot on his/her system. Installing a VM like VirtualBox or Qemu/KVM is far easier—there are simple step-by-step instructions all over the internet. Example: [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation)
…if the choice is VirtualBox, it's even simpler: [https://itsfoss.com/install-virtualbox-ubuntu/](https://itsfoss.com/install-virtualbox-ubuntu/)

Once installed, the user's life becomes a study in calmness and serenity.

So, in keeping with your stated goal, it is far preferable to do any experimentation on a VM rather than on the base install.

Hope this clarification is helpful.

---

### Post by coley9225 on 2020-02-29
WHOA....Didn't mean to start any major fights here...lol. I appreciate the tips. I do tend to go above and beyond my capabilities, often having a mess before I realize what I've done. As far as the dual lubuntu, I fought for 2 years to get 18.04 to install, and now 20.04 is right around the corner. I installed 19.10 to get a feel for the lxqt desktop, and I'm glad I did. There are differences in some of the things. I will probably keep 18.04 in, just reduce the drive space it uses, just so I have a running os to be able to do system restore, or reinstall of my normal os. Because of my computer, I have to install a new os without bootloader, then go into a usable os and update grub. Anyway, again, I appreciate the tips. There is a lot of info here to let soak in, plus any additional responses. I'm sure I'll run across something I can utilize, possibly a combo of things from the suggestions.

---

### Post by TheFu on 2020-02-29
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) has a 6-line script for simple backups. Simple and useful.
Run it with sudo or from the root crontab.

It will create 90 days of versioned backups of the most important directories, system settings, and user files. It also makes a list of installed packages, which can be fed back into a freshly completely

The backup storage has to be mounted to /Backups in the script.  2 lines of the script will mount and umount it, but an fstab entry for that partition/LV is a prerequisite. The backup storage needs to be native linux, so not NTFS or FAT32 or exFAT. 

Restore process is
[LIST=1]
[*]Fresh OS install
[*]Restore all HOME data
[*]Restore /root/ stuff.
[*]Restore any specific system settings in /etc/, but only those things you specifcally touched. If you ddn't touch anythng, don't restore that file.
[*]Using the list of packages installed (see /root/bac* ) feed that list into APT to install them.
[/LIST]
Done. Profit!

Easy to move to a new computer. 
Easy to swap storage bigger or smaller.  
Easy to install a backup from yesterday, last week, last month, or 87 days ago. 
Easy to restore 1 file or entire directory from any backup set.

60 days of backups is about 1.3x the original size. YMMV, but that's what I see here across 15 systems over the last 10+ yrs.  If we backup 10G of stuff, then 60 days is about 13G.  Seems like a bargain to me.

Anyone can do this.  We never want to assume the people posting here are capable of above average stuff.

---

### Post by coley9225 on 2020-03-05
Well this is where I stand, for now.
ml9104, thanks for the reference to timeshift. This looks like it will help for the time being. I can at least breath a little easier with this installed. while not the ideal option, for a noob it seems to be adequate.
DuckHook, you made major suggestions, and I appreciate them all. Yes I'm a noob, but your ideas make sense. I'll follow up on them as well.
TheFu...I am working on implementinf your script. I have formatted a 200GB partition on a 2TB external drive and made an entry in fstab to mount it at /backups. I have modified script to adjust to my computer. I'm stuggling with the crontab entry, but I'll get that figured out, or start a new thread to address that. I do have a question though. Can this script be run while I'm active on the computer, or do I need to run it at a time when the computer will be idle. I have a laptop, set up in my bedroom, and would prefer to not leave it powered up all night. If the computer needs to be idle, I can set it up to run manually, and not use crontab( although that would be another great learning experience), and do my backup at lunchtime or just before shutting down at night.
And just so everyone undeerstands, if you look at my join date, it was 2018, however, that was me looking for install help. Since then, I've used live usb to get a little feel for linux, and have only had lubuntu installed and working since Feb 2, 2020...so I am very new to all this. I can't express enough my appreciation, on this thread as well as others, for all the help you folks have given me.

---

### Post by TheFu on 2020-03-06
All backup tools prefer for the system to be quiesced as the backups run.  Files being changed aren't great for backups, but on a typical desktop, the files being changed aren't important, so it doesn't really matter.

OTOH, if the system is running a DBMS and changes are actively happening while the backup is being created, that DB will sometime be corrupted and the backup for it for that night, useless.  There are a few different strategies to prevent that.  LVM snapshots, dump the DB(s) to text files, then be certain to backup the DBs.  A concrete example: 
  [https://ubuntuforums.org/showthread.php?t=2401600&p=13802377#post13802377](https://ubuntuforums.org/showthread.php?t=2401600&p=13802377#post13802377)

Timeshift is like Back-In-Time, just a little different about the timing of the backups and the removals.  B-I-T is pretty slick for end users files.  It creates a backup set every 1 or 2 hours, then selectively deletes the sets to use less storage over time. Effectively having just weekly backups for the current month, then only monthly backups for all prior months this year, and only 1 yearly backup for each prior year.  Be cause the "sets" are really 99% hardlinks, deletion is very fast.  I used B-i-T for a few years, for Mom's desktop.  Worked well enough for her needs, though she did notice the slowdown every hour as a "snapshot" was taken.  What B-i-T calls a snapshot isn't technically one, but close enough.  

Both use hardlinking as the way to have many backup versions without needing tons of storage.  There are many backup scripts that work this way that have been around since the late 1980s.  Hardlinks have some flaws because they don't maintain ownership, group changes, permission changes or ACL changes over time.  Those things don't change too often, but when they do, it is important to have the older versions tied to the older backup data.

There is no reason that Timeshift or B-I-T can't be used as the backup method in the script I linked. You just wouldn't need to include all the OS stuff. 

That's where rdiff-backup does NOT fail. Those things are all stored as metadata as changes happen over time.  Also, it doesn't do hardlinking, rather it performs reverse diffs for changed files where the most recent backup is like an rsync mirror and older versions only contain diff.gz for modified files.  This does cause one liability.  Intermediate backup sets cannot be removed, since older backup sets are dependent on all the diff.gz files.  But the much greater efficiency for storage and required transferred data makes up for it.  
Most of the time, we just need to restore a file or directory from last night.  Doing that with any of these 3 tools is just a cp or rsync if that is preferred.  Of course, each of the tools has a --restore option too.  I usually only use that when a file was corrupted and not noticed for over a month.  Without versioned backups, there wouldn't be any hope at all to get most, if not all, that data back.

I have a laptop that runs the backup job nightly, then self-suspends after it completes.  I really need to switch that backup to be "pulled" by the backup server. Using a "push" backup is a liability for malware and crypto-ware.  The suspend would be part of my *post-backup* script for that laptop.

---

### Post by coley9225 on 2020-03-13
I'm going to mark this thread solved. I have the script working well( thanks TheFu), make crontab entry to run at 1 pm daily, and got fstab set properly. I'm writing a couple new scripts to keep me from using my computer during back. It's a 3 script setup. Script 1 will go in crontab,( replacing the existing one), it will launch a new terminal window and launch script 2. Script 2 reminds me it's time for the backup, and offers me a chance to delay running. If I choose no delay, I get 5 minute delay to give time to save my work, then runs backup. If I chose to delay, it sleeps for the time I choose, the starts script over. Script 3 is the backup script itself. when backup completes, returns to script 2, that will complete that script and return to script 1. Script 1 ends with letting me know backup has completed, sleep 3 seconds to give me time to read that, then exits, which closes the terminal. I have 2 pieces yet to figure out before I'm totally satisfied with it. The first is I want to find a way to minimize the terminal window to taskbar and restore automaticly, thereby getting the terminal off screen during delay or while backup runs, and restoring to proceed further. I tend to be forgetful at times, so minimizing manually and I'll forget about it..lol. The other thing I want to do is set a time limit on answering the posed questions, so if it launches and I'm not home, it won't sit there all day waiting for input. Kind of a no input after x seconds=assume no, and go on with script. Thanks again to everyone for tips and help, the 'buntu community rocks>

---

### Post by TheFu on 2020-03-13
Trying to have cron start any GUI anything is a less-than-great idea. It will fail all the time.

---

### Post by coley9225 on 2020-03-13
Not a cron starting GUI set up. Cron will start a bash script that will open a standard terminal window. The script works fine when launched from terminal, so I figured it's worth a try. If it fails, then I go back to the drawing board. I just need a way to run it so I get the reminder part, and also gives the opportunity to postpone for (x) minutes if I want. Like I said, I'm a little forgetful, and will lose track of time doing things that may scramble the backup. I would think that cron would launch the script, and the script is what starts the terminal window. I'll show you the scripts and let you see if you think this route will go for me.
Script to start and end the process:

#!/bin/bash

#start new terminal, run backup script, and exit terminal after 3 second delay
qterminal -e "/home/charles/this.sh &&
    echo "Backup is complete, you can now resume work safely" &&
    sleep 3 &&
    exit" 
Script that offers delay option:

#!/bin/bash

echo "Backup will start in 5 minutes." &&
echo "Would you like to delay the backup?"
    read answer
    answer=${answer^^}
    answer=${answer:0:1}
    
if [[ ${answer} = 'Y' ]] ;
    then #echo "After chosen delay time, backup will run without any further warning."
        echo "How many minutes do you want to delay?"
        read answer
        sleep ${answer}m &&
        /home/charles/this.sh  #starts this script back at top
        
else
    echo "Backup will begin in 5 minutes." &&
    echo "Please save your work and limit computer use until complete." &&
    sleep 5m &&
    /home/charles/mystuff/backup-script.sh
    
fi

And the third script is the backup script you shared. I welcome any input on the script set up and whether you think this will work, as well as suggestions on alternatives or improvements. Plus, this is a good way for me to learn how to do this stuff, by trying things and failing, and learning from those mistakes. Thanks

---

