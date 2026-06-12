---
title: "fsck failed, need help"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Anonono on 2008-10-31
When I installed KDE into ubuntu hardy, it came up with a 'fsck'. It took too long, so I skipped it, to get to my new KDE desktop. Then, later, I went through it all, and everything was fine.
Then it happened again, but it failed around 43%. It said to do a manual fsck of the drive dev/sda3, so I ran the command 'fsck /dev/sda3' (Or something like that, it was just common sense), said yes to all the prompts, and then everything was fine.
Now it's happeneing again, but now it is failing at 26 percent. This is the full error I got:

```
Checking drive /dev/sda3: 26% (stage 1/5, 221/587)
/dev/sda3: Inodes that were part of a corrupted orphan link found.

/dev/sda3: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
          (i.e., without -a or -p options)
fsck died with exit status 4
Checking drive /dev/sda3: 26% (stage 1/5, 221/587)
* An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in mainenence mode, with the
root filesystem mounted in read-only mode.
*The root filesystem is currently mounted in read-only mode.
A maintenence shell will now be started.
After performing system maintenence, press CONTROL-D
to terminate them maintenence shell and restart the system.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
```

But if I skip the initial check, then everything runs fine. Would it be okay to somehow disable the fsck? Or is there a batter fix to stop it from happening again? I want to upgrade to Intrepid, and I just want to make sure everything is fine first.

---

### Post by aeiah on 2008-10-31
i think its giving you a fair warning that something really isnt right with your drive. if i were you id back everything up, format the partition, and install 8.10 that way. if the problem persists, you may have a physical error on the disk and it might be time to go shopping :p

---

### Post by Keen101 on 2008-10-31
you should only be getting fsck errors if you have done too many "unsafe" shutdowns, and corrupted some files.

or... your hard drive is going bad.


I've experienced the first one, because i kept having a program freeze the system, and had to do a lot of hard shutdowns. It corrupted my files.


how old is you hard drive?

---

### Post by Anonono on 2008-10-31
> **Keen101 said:**
> you should only be getting fsck errors if you have done too many "unsafe" shutdowns, and corrupted some files.

or... your hard drive is going bad.


I've experienced the first one, because i kept having a program freeze the system, and had to do a lot of hard shutdowns. It corrupted my files.


how old is you hard drive?
Yeah, I have done a few hard shutdowns (Before I learnt Control+Alt+Backspace). My hard drive almost 2 years old. Is there a better fix?

---

### Post by tgalati4 on 2008-10-31
Back up your data.  Run badblocks. Install smartmontools and set up your drive for monitoring.

---

### Post by Anonono on 2008-10-31
> **tgalati4 said:**
> Back up your data.  Run badblocks. Install smartmontools and set up your drive for monitoring.
Um... What?

---

### Post by cariboo on 2008-11-01
I actually just went through the same thing with the  raid array on my server. The problem was caused by a bad ram module, that caused the array to go into a race condition. I ran fsck at the prompt, and answered yes about 4000 times and now have a nice shiny clean raid array again. I lost about 20Gb of 350Gb of files. I had just backed up all the files on the weekend, it was just a matter of restoring the missing files and my array is as good as new again.

Jim

---

### Post by Anonono on 2008-11-01
Anyone else?

---

### Post by Anonono on 2008-11-01
Bump.

---

### Post by Herman on 2008-11-01
:) Hello Anonono,
Here is a link that explains what you should do to run a check for bad blocks in your hard disk, [Running a check for bad blocks on your hard disk]("http://users.bigpond.net.au/hermanzone/p10.htm#bad_blocks_check").
Under that article, there's some info on smartmontools too.

If you don't have badblocks, but just regular, ordinary 'garden variety' file system aches and pains, this link should be the most helpful, [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") - from a Live CD - command line.

If you do have some badblocks, then I agree with the other posters, hard disks come with a reserved area of spare blocks that can be switched for any bad sectors as the disc ages. 
Even new hard disks have a few bad sectors, and we also lose a few here and there as the disc ages. 'Bad sectors' are just spots on the hard disk where the magnetic properties are getting weaker, and when they fall below a certian level, the block is called a 'bad block', as it might not be trustworthy enough to retain data with any certianty.
Normally, these are switched out silently by the hard disk's own software, (firmware), and only after the supply of spare blocks becomes exhausted does the problem become apparent to the operating system and thus the user. 
I'm not sure if this is actually the trouble you're having or not, but if it is, then you can keep your operating system going for a while longer by fixing it with file system checking commands, particularly the last one in the last link.

Make sure you keep good backups, like you always do already anyway, and see what happens in the next few days. Keep an eye on your hard disk, and if it does seem to be getting flakey, it would be best to replace it A.S.A.P.
(If the badblocks command finds some bad blocks).
It's simply not worth it to bother using a hard disk that's suspected of being on it's way out. 
However, maybe you can find a problem and correct it, I have an old hard disk that was giving a lot of errors for a previous owner (not bad blocks though, other errors), and it has been working perfectly for me for quite some time now. I think maybe it was getting hot and I have it in a cooler computer case maybe. 
Generally speaking though, it's probably best to replace the hard drive if there are bad blocks appearing.

Anyhow, see how you go...
Regards, Herman :)

---

### Post by Anonono on 2008-11-01
> **Herman said:**
> :) Hello Anonono,
Here is a link that explains what you should do to run a check for bad blocks in your hard disk, [Running a check for bad blocks on your hard disk]("http://users.bigpond.net.au/hermanzone/p10.htm#bad_blocks_check").
Under that article, there's some info on smartmontools too.

If you don't have badblocks, but just regular, ordinary 'garden variety' file system aches and pains, this link should be the most helpful, [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") - from a Live CD - command line.

If you do have some badblocks, then I agree with the other posters, hard disks come with a reserved area of spare blocks that can be switched for any bad sectors as the disc ages. 
Even new hard disks have a few bad sectors, and we also lose a few here and there as the disc ages. 'Bad sectors' are just spots on the hard disk where the magnetic properties are getting weaker, and when they fall below a certian level, the block is called a 'bad block', as it might not be trustworthy enough to retain data with any certianty.
Normally, these are switched out silently by the hard disk's own software, (firmware), and only after the supply of spare blocks becomes exhausted does the problem become apparent to the operating system and thus the user. 
I'm not sure if this is actually the trouble you're having or not, but if it is, then you can keep your operating system going for a while longer by fixing it with file system checking commands, particularly the last one in the last link.

Make sure you keep good backups, like you always do already anyway, and see what happens in the next few days. Keep an eye on your hard disk, and if it does seem to be getting flakey, it would be best to replace it A.S.A.P.
(If the badblocks command finds some bad blocks).
It's simply not worth it to bother using a hard disk that's suspected of being on it's way out. 
However, maybe you can find a problem and correct it, I have an old hard disk that was giving a lot of errors for a previous owner (not bad blocks though, other errors), and it has been working perfectly for me for quite some time now. I think maybe it was getting hot and I have it in a cooler computer case maybe. 
Generally speaking though, it's probably best to replace the hard drive if there are bad blocks appearing.

Anyhow, see how you go...
Regards, Herman :)
I ran the check, and 0 bad blocks were found, so I'll do the first thing you said.

---

