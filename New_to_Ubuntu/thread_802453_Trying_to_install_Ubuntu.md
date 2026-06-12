---
title: "Trying to install Ubuntu"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by zfolwick on 2008-05-21
HELP!  I am a beginner who's trying to install Ubuntu.  I am trying to install it as the sole OS, but it WON'T install!  I've tried Ubuntu first, then Mandriva

I load the LiveCD (i586), and am getting all sorts of problems.  When it wants to partition the HD, it only seems to recognize 447.7 MB.  What gives?

Full message:

"Guided - resize SCSI1 (0,0,0), partition #5 (sda) and use freed space"

New partition size: (then the slider bar showed 50% at 447.7 MB)

grrr!

*Edit

when I *tried* partitioning before, it says (and continues to say) " No root file system is defined."

what do I do?

---

### Post by justin whitaker on 2008-05-21
> **zfolwick said:**
> HELP!  I am a beginner who's trying to install Ubuntu.  I am trying to install it as the sole OS, but it WON'T install!  I've tried Ubuntu first, then Mandriva

I load the LiveCD (i586), and am getting all sorts of problems.  When it wants to partition the HD, it only seems to recognize 447.7 MB.  What gives?

Full message:

"Guided - resize SCSI1 (0,0,0), partition #5 (sda) and use freed space"

New partition size: (then the slider bar showed 50% at 447.7 MB)

grrr!

What happens when you select guided-use entire disk?

---

### Post by shifty_powers on 2008-05-21
ok, first of all why the i586? (64-bit iirc). usre someone will disagre with me, but as a beginner, unless you have some presing need for it, go for 32-bit.

secondly, might it not be easier to use wubi until you are more confident adn then go for a full dual boot?

[http://wubi-installer.org/](http://wubi-installer.org/)

> 
Wubi is Simple

No need to burn a CD. Just run the installer, enter a password for the new account, and click "Install", go grab a coffee, and when you are back, Ubuntu will be ready for you.
Wubi is Safe

You keep Windows as it is, Wubi only adds an extra option to boot into Ubuntu. Wubi does not require you to modify the partitions of your PC, or to use a different bootloader, and does not install special drivers. It works just like any other application. Wubi is spyware and malware free, and being open source, anyone can verify that.
Wubi is Discrete

Wubi keeps most of the files in one folder, and if you do not like it, you can simply uninstall it as any other application.
Wubi is Free

Wubi and Ubuntu cost absolutely nothing (free as in beer), but yet provide a state of the art, fully functional, operating system that does not require any activation and does not impose any restriction on its use (free as in freedom).


---

### Post by sam_delta on 2008-05-21
you may onlyl have 447.7 megbyte as "freeded space" which means space that has no format.

if you want to keep windows ,you need to make windows partition smaller, to free up more space
to free up more space, click alt+f2 in the live cd and type "gksudo gparted", and shrink the windows partition into a smaller partition, leaving more "Freeded space"

if you want to have nothing but ubuntu in your pc, just select the option that says "use the entire disk" and it will delete any other partitions  and install ubuntu ontop of everything

sam

---

### Post by zfolwick on 2008-05-21
sadly, I know enough to make me dangerous.

I want to ditch windows, so I grabbed linux.  I just grabbed what said "install for pc"

anyways, like napolean, I've apparently burned my windows bridge, not only that, but my laptop isn't currently hooked up to the web- so I've having to use my desktop windows system to get info to make my laptop run!

ugh.

---

### Post by zfolwick on 2008-05-21
Sam:

There's no going back for me now!  Windows is history on this machine!

Also, for whatever reason, when I select "Use entire disk" it says there's no root file system.

??

---

### Post by zfolwick on 2008-05-21
mmmmk.  So's I get get ya'll to where *I'm* at with the screen:

the "Prepare partitions" page in the install window.  Step 4 of 7.

I have three 'devices':

/dev/sda
  /dev/sda1                       76717 MB
  /dev/sda5 swap                   3306 MB

there's a message at the bottom:

"you need to specify a partition fro the root file system (mount point "/") with a minimum size of 2 GV, and a swap parttion of at least 256 MB.  You may also set up other partitions if you wish.

---

### Post by justin whitaker on 2008-05-21
> **zfolwick said:**
> mmmmk.  So's I get get ya'll to where *I'm* at with the screen:

the "Prepare partitions" page in the install window.  Step 4 of 7.

I have three 'devices':

/dev/sda
  /dev/sda1                       76717 MB
  /dev/sda5 swap                   3306 MB

there's a message at the bottom:

"you need to specify a partition fro the root file system (mount point "/") with a minimum size of 2 GV, and a swap parttion of at least 256 MB.  You may also set up other partitions if you wish.

Right, you set up /dev/sda1 as primary, but a mount point is not set for it. 

Now, I have never used the live cd installer, but in the alternate version, you could tab down, hit enter, and be taken to a screen that allows you do set the format and mount point for that partition. 

That's what you need to do. Set that partition as the /root partition, and save the changes.

---

### Post by mick8985 on 2008-05-21
No don't set as /root just /

---

### Post by zfolwick on 2008-05-21
ok:  just to update:

tried the guided install - use entire disk option.  Error message "Failed to create a file system:  the ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed."

Will now restart and try "manual install".

**EDIT**:

I selected /dev/sda1 type as jfs and mount point as /.  I also have the option to select /home.  What would all of that do?

The big question being. . . what *should* I be using?  Tried ext3 and ext2.

---

### Post by shifty_powers on 2008-05-21
are you getting rid of windows? if so, and you have no data you mind using, then use the manual option and then delete all partitions and then:

/ mount point, about 5-10gig
/home mount point, everything else after / and swap
and one partition using swap as it's file structure and about 1-2 gig

---

### Post by zfolwick on 2008-05-21
> **shifty_powers said:**
> are you getting rid of windows? if so, and you have no data you mind using, then use the manual option and then delete all partitions and then:

/ mount point, about 5-10gig
/home mount point, everything else after / and swap
and one partition using swap as it's file structure and about 1-2 gig

so.. . what I get is this:

/dev/sda1    ext3  /    10026 MB unknown
/dev/sda2    swap       69997 MB unknown

this what you're talking about?

---

### Post by Nubnut on 2008-05-21
That's it, the /root partition appears as just /
select that and see if the installed lets you through to the next screen

---

### Post by zfolwick on 2008-05-21
by the way, I've discovered [this site]("http://www.easy-ubuntu-linux.com/ubuntu-installation-606-11.html") and am trying to use it.  Slightly different version of the OS, but I hope it works.

---

### Post by Zentradi-359 on 2008-05-21
Hi Zfolwick.

I had much of the same issue. I ended up booting into the live cd then doing the "gksudo gparted" and deleted all the partitions and made sure it wrote the changes to the HD. (Comit change or something (still a newbie too)) The rebooted and ran the install from the lice cd.

Hope it helps.


Zentradi

---

### Post by zfolwick on 2008-05-21
** UPDATE **

OK!  So after following the instructions [here]("http://www.easy-ubuntu-linux.com/ubuntu-installation-606-6.html"), I've discovered that. . . ext3 won't work and my computer froze before I could implement the changes to ext2.

I've considered ditching the whole Gutsy thing.  Is there another version that people are using that they would be willing to walk me through?

---

### Post by shifty_powers on 2008-05-21
why are you using gutsy anyways?

you should be using hardy, 8.04.

and as for ext2, first i heard about it. you should be absolutely fine with ext3.

and you should end up with three partitions.

/dev/sda1 ext3 / 10026 MB
/dev/sda2 ext3 /home 59000 mb
/dev/sda2 swap 10026 MB

roughly

---

### Post by shifty_powers on 2008-05-21
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

will give you a btter guide.

jyust browse the whole psychocats site. fantastic for newcomers ;)

---

### Post by zfolwick on 2008-05-21
SUCCESS!!!

I am SOOO Happy.


Good day, Linux!

---

### Post by shifty_powers on 2008-05-21
glad to help ;)

---

