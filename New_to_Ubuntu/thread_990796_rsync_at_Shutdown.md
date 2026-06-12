---
title: "rsync at Shutdown"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by Quarkrad on 2008-11-23
I have set up rsync so that my personal files (docs, spreadsheets, photos) are copied from one folder/partition to another folder/partition on a 2nd hd in my pc.  (Hope I've explained OK - simple backup/mirroring from 1st hd to 2nd hd.  Not at hd level but a specific folder).

If I run rsync manually all is fine - great, duplicates what I had on winXP.  My problem is when I had winXP the backup would launch itself on PC shutdown (I used a tool called SmartSync Pro).  This was just the trick for family members who wanted the PC to do everything for them.

Can anybody help how to do this - run rsync at shutdown?   I have googled and there are lots of scenaros using ssh to backup remotely but this is too complicated - I would like to do this locally.

---

### Post by Dedoimedo on 2008-11-23
Hello,
You could write a script and then add it to the shutdown scripts, with a very low number, so it gets done before anything else goes down ...
Dedoimedo

---

### Post by mbsullivan on 2008-11-23
Hi Quarkrad,

I assume that you have the command that you want to use all figured out, so I'm not going to lookup the rsync syntax again. Put the command in a script (let's call it script.sh for now).

In order to make script.sh run @ shutdown every time, run the following from the command prompt:

(1) move the script to the /etc/init.d folder

```
sudo move ./script.sh /etc/init.d/
```

(2) start the script at the appropriate *run levels* (for "shutdown" and "reboot"):

```
sudo update-rc.d script.sh start 03 0 6 .
```

Ok... so this looks pretty hairy. Here's a brief (and probably incorrect) explanation. Ubuntu still uses the system to startup/shutdown scripts inherited from Unix System V (SysV). Basically, the operation of the computer is separated into different [run levels]("http://www.debian-administration.org/articles/212"). 

At each run level (0-6), the system starts any script starting with the letter "S" in /etc/rcN.d/, and halts any scripts starting with the letter "K". The order in which the scripts are started and stopped are determined by their priority level, denoted by a number following the letter.

The officially supported way to insert or remove scripts from any run level is using the "update-rc.d" command, which has a fairly obtuse syntax. It takes scripts from /etc/init.d and puts appropriate symlinks into the /etc/rcN.d/ folders.

Dissecting our command, we're putting symlinks to start /etc/init.d/script.sh in run levels "0" (System Halt), and "6" (System Reboot). The script is given a priority level of 03, which (I think) should run it right after displaying the shutdown splash screen.

Mike

---

### Post by Quarkrad on 2008-11-23
Mike, Dedoimedo - thank you very much for replies.  Apologies - I should have explained that I have only migrated to Ubuntu/Linux for a few weeks so, although I was fairly happy with DOS some years back, getting my head around new coding,syntax and scripts is a bit of a mountain range at the moment.  I have spent too many years with windows and now almost dependent on GUI.
I have played a bit with the terminal and used commands mostly copied from other people when I have googled to find out how to do something.  I am afraid I do not have a command to run rsync.
All I have done is to use the GAdmin-rsync GUI that I access from Applications/System Tools to set up rsync.   I 'run' rsync by clicking on the 'Run Selected Backup' option that is top left of the GAdmin window.
I appreciated, if I get to my automated activity, I will have to set it up via the terminal but it is easier for me at the moment to use the GUI to prove the transfer works.  Any help on where I can go to learn how to write/setup the command would be appreciated.  From what Mike has provided, it looks like I am almost there.   This is a killer for me/family so much appreciation - I now think this could actually work.  Struggling with this to get the family fully on board with Ubuntu (note: Ubuntu 8.10).

Rds

---

### Post by mbsullivan on 2008-11-23
> I have only migrated to Ubuntu/Linux for a few weeks

Welcome!

> getting my head around new coding,syntax and scripts is a bit of a mountain range at the moment

I can appreciate that... for better or worse scripting is the most powerful way to "automatically" do anything in Linux (including backing things up). The good news is that, unlike Windows, once you get the hang of it you can automatically schedule just about anything :)

> I am afraid I do not have a command to run rsync.
All I have done is to use the GAdmin-rsync GUI that I access from Applications/System Tools to set up rsync.

Okay... I looked at GAdmin-rsync (I'm not familiar with the tool), and there's good news: it seems that the GUI can create an appropriate script for you :)

So... here's what I think you should try. Open GAdmin-rsync and set everything up as you want it. 

(1) Click on "save backup". This will create a script that has all of your settings at /etc/gadmin-rsync/scripts/gadmin-rsync-[name of your backup].sh

(2) Copy this script to /etc/init.d ... in order to do this, open a terminal window (Applications->Accessories->Terminal) and type the following (substituting in the name of your backup):

```
sudo -s
cd /etc/gadmin-rsync/scripts/
cp gadmin-rsync-[name of your backup].sh /etc/init.d/backup.sh
```

This will copy the script to the right folder, and rename it to "backup.sh".

One hint for typing commands at the command line: when you're typing out a long pathname, you can hit "Tab", and the system will fill in any matching folder/filenames for you. It can save a lot of time.

(3) Follow the previous instructions for executing this script at shutdown. Specifically, run the following command from the command line:

```
sudo update-rc.d backup.sh start 03 0 6 .
```

This should automatically backup your machine upon shutdown or reboot. One word of warning, though... This could take a while, and makes your shutdown hang on the splash screen until it finishes!

Let me know if you have any questions.
Mike

---

### Post by Quarkrad on 2008-11-23
Mike - wow, many thanks.  Followed your instructions (I was googling and playing with/attempting to use simple rsync commands via the terminal) and all went will.  Was not sure where to enter the last command 

sudo update-rc.d -n backup.sh start 03 0 6

so I close down the terminal and reopened - then entered the command.  This is what came back:


liz@liz-winfast:~$ sudo update-rc.d -n backup.sh start 03 0 6
Use of uninitialized value $level in string ne at /usr/sbin/update-rc.d line 243.
Use of uninitialized value $level in pattern match (m//) at /usr/sbin/update-rc.d line 244.
update-rc.d: error: expected runlevel [0-9S] (did you forget "." ?)
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
liz@liz-winfast:~$ 

many thanks Graham

---

### Post by mbsullivan on 2008-11-23
Hi Graham,

You were correct... enter the command in a terminal window.

The reason that it complained is that you didn't put a "." at the end of the command.

Update-rc.d has the strangest (1) name and (2) syntax of any regularly used program I can think of... I know, it's not friendly at all!

One more thing -- I messed up with the command, the -n switch shouldn't be in there. With the -n, the system won't actually make the changes, it'll just tell you what it would do if you had run the command "for real". I used it that way on my system, but you should remove that part to actually make the command execute:

```
sudo update-rc.d backup.sh start 03 0 6 .
```

You're almost there (hopefully)!
Mike

PS: I removed the offending -n from the previous messages in order to help anybody else who wanders into the thread.

---

### Post by Quarkrad on 2008-11-23
Mike - I do not know what to say ......... perfection.  I never thought this would work but here I am and it works like a dream.  I have looked over my shoulder for some years re Linux but never really looked into it.  My disappointment with Vista (camcorder works with XP but Vista ignores) and the never ending checking for virus/mail/spyware + a little Microsoft arrogance has prompted me to switch to Linux.  Ubuntu is very good for the family who want something that works and it provides me with whole mountain range of learning to satisfy the 'mecano man' in me.   It will be a long journey but I must say I'm very impressed.  Once again, many thanks.

Graham

---

### Post by mbsullivan on 2008-11-23
> Mike - I do not know what to say ......... perfection. I never thought this would work but here I am and it works like a dream

Wonderful! I'm glad to hear it. The handling of startup/shutdown events is one of the antiquated parts of Ubuntu right now, but perhaps things may change, eventually. We're slowly moving to a new process (called "Upstart"), but development has not been quick.

> it provides me with whole mountain range of learning to satisfy the 'mecano man' in me.

I think that the transparency of Linux, in general, can make it fairly pleasurable to work with. There is a steep learning curve, certainly... but in the end you'll not only get your computer working a certain way, but you can slowly learn how the whole system works.

One more thing that I thought I should mention... **if you ever want to update your backup script**:

(1) Setup your profile in GAdmin-rsync how you want it, as before

(2) Just copy the generated script over the previous /etc/init.d/backup.sh

The scripts at the various runlevels are symbolic links (analagous to "shortcuts" in Windows), such that replacing /etc/init.d/backup.sh with a new version will update everything.

I'm glad it worked out for you!
Mike

---

