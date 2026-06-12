---
title: "k9copy always crashes"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by super newbie on 2008-07-10
Hi all...before i upgraded to 8.04 i was using k9copy without any problems.  Since the upgrade i have not been able to get it to work.  When i launch the program it comes up without any problems but when i try to choose the "open" button in order to select a source from which to copy from, it shuts down immediately.  Any suggestions would be greatly appreciated.  Thanks everyone

---

### Post by ChameleonDave on 2008-07-10
Try reinstalling it and then running it with the following commands in the terminal:

```

sudo apt-get purge k9copy && sudo apt-get install -y k9copy
k9copy

```

If it works, then hooray.  If it crashes again, please post the terminal output here.

---

### Post by super newbie on 2008-07-10
i'm not sure if this is what you were looking for , but here's what happened when i launched it from the terminal


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xd68e

*** libdvdread: CHECK_VALUE failed in ifo_read.c:766 ***
*** for pgc->nr_of_programs <= pgc->nr_of_cells ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:784 ***
*** for pgc->program_map_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:785 ***
*** for pgc->cell_playback_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:786 ***
*** for pgc->cell_position_offset != 0 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

libdvdread: Invalid title IFO (VTS_09_0.IFO).
KCrash: Application 'k9copy' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
mike@mike-desktop:~$ 



hope this helps

thanks again

---

### Post by super newbie on 2008-07-10
FYI - here is what i did to "set-up" my multimedia

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

this was the guide i used when i was running Gutsy.  i don't know if they have anything to do with each other, but i thought i would let you know..

---

### Post by mc4man on 2008-07-10
If you upgraded from gutsy to hardy there could be any number of issues. Is there any problem playing back the dvd using vlc, ect.?
Assuming you ran the purge and re install from above then maybe try going in your home dir. -> .kde/share/config and delete the k9copy file inside. Then retry.
Note: purging does not remove the above file, won't hurt to delete, it's recreated when you start k9 again.

---

### Post by ChameleonDave on 2008-07-10
> **super newbie said:**
> i'm not sure if this is what you were looking for , but here's what happened when i launched it from the terminal


Yes, thanks.

By purging and reinstalling, we can confirmed that the problem is not caused by any of your personal settings.

The error messages that came up complain about two separate pieces of software missing or malfunctioning.  This immediately suggests that we should reinstall that software and then try again.  While we're are at it, let's reinstall some of its other dependencies too.  Do the following in a terminal:

```

sudo apt-get install --reinstall k9copy libdvdread3 drkonqi libdvdnav4 libdvdcss2 mencoder vamps
k9copy

```

---

### Post by super newbie on 2008-07-12
@ chameleon dave - here's what happened when i ran the code you provided

mike@mike-desktop:~$ sudo apt-get install --reinstall k9copy libdvdread3 drkonqi libdvdnav4 libdvdcss2 mencoder vamps
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package drkonqi is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  kdebase-runtime-data
E: Package drkonqi has no installation candidate
mike@mike-desktop:~$

i see that drkonqi is not available so i installed kdebase-runtime-data through synaptic pakage manager. rebooted and still the program crashes immediately after clicking the open button

i will keep searching the forum for someone else who has this problem.  i want to thank you again for your time and patience.  if you can suggest any other ideas, that would be great, if not, i have no problem going back to gutsy.  thanks again

---

### Post by super newbie on 2008-07-12
@ mc4man just to be clear, i did a fresh install of 8.04 not an "upgrade" i don't know if that makes a difference.  also i could not find the file you mentioned (i am very new to linux) if this is a "hidden" file could you please be more specific as to where i could find it. thanks for your help

---

### Post by mc4man on 2008-07-12
Go to home dir. -> view -> show hidden files, then it's in .kde ....
The package kdebase-runtime-data is unnecessary - it's for kde4. drkonqi is also not needed or available.
Edit : thats places -> home > view in taskbar -> show hidden files then look for .kde and follow path from above

> i have no problem going back to gutsy You'll get no argument here about gutsy, I think it's the best atm if A/V stuff is very important to you. I tri-boot w/ xp, gutsy and hardy and intend to hold on to gutsy as long as possible. That being said i think you should stick this out and get it resolved even if you end up back in gutsy. Solving problems is the best way to learn

I'd still like to know if you can playback that title.

---

### Post by super newbie on 2008-07-13
@ mc4man i followed your instructions, no luck, still crashes.  if i get time tomorrow maybe i'll do a fresh install of 8.04 and load k9copy first thing and see what happens.  if i have no luck with that then i might go back to 7.10.  i agree that trying to solve problems is the best way to learn, but i really don't know much about linux, all i can do is what people on the forum suggest.  although reading thru the forum is a good way to see the steps people go thru to solve their particular problems.  i think i might actually be learning something (go figure). any other ideas would be great.  thanks for your help and quick response...and yes i can can play the disc...when i put a disc in the drive it automaticaly starts to play using "totem movie player"

---

### Post by ramjet_1953 on 2008-07-13
Try this:

1. Navigate to [COLOR="Blue"]System>Preferences>Sessions[/COLOR]

2. When the window opens, click on the [COLOR="Blue"]Add Button[/COLOR]

3. In the name and command section type [COLOR="Red"]dcopserver
[/COLOR]
4. Click on [COLOR="Blue"]OK[/COLOR]

5. Re-boot.

Hopefully, it will now run OK.

Regards,
Roger

---

### Post by mc4man on 2008-07-13
> if i get time tomorrow maybe i'll do a fresh install of 8.04
Before doing that just go into home dir. and delete the .kde folder itself, and then try again.

---

### Post by super newbie on 2008-07-17
thanks everyone for your help...i've tried all the things you've all suggested, but nothing seemed to work.  i ended up doing a fresh install of 8.04 and everything seems to be ok for now.  i haven't had a lot of time to do much experimenting yet, but from what i have seen so far, i think it works.  thanks again everyone for all the help.....

---

### Post by oldos2er on 2008-07-17
You can see here [http://sourceforge.net/project/showfiles.php?group_id=157868](http://sourceforge.net/project/showfiles.php?group_id=157868) that there are two versions of k9copy, one for KDE 4.* and one for older versions. I wonder if maybe you weren't using a wrong version before you reinstalled. Sorry I didn't see this thread sooner!

---

### Post by super newbie on 2008-07-19
everytime i've installed this program i've done it through the add/remove option under the applications menu.  i;m 99.9 % sure it was the same version, but you never know, thanks for the suggestion

---

