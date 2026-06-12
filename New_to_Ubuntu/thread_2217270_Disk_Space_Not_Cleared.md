---
title: "Disk Space Not Cleared"
date: 2014-04-16
forum: New to Ubuntu
---

### Post by zaivala on 2014-04-16
I had some files I could not get access to (were marked as owned by Root -- see another thread). I managed to get the files restored onto another drive partition with full access. I then went back to the original partition sda6 and had to use Nautilus to delete the folders...

Which it did, without moving anything to Trash and without clearing the space. Disk Usage Analyzer reports "Could not scan folder "/" or some of the folders it contains" -- the files "deleted" should have freed up over half the usage of the partition and did not.

I hope that is understandable.

How can I get this space back?

Using Ubuntu 13.10 64-bit on a Dell Optiplex 740 (AMD dual-core, 3 Gb RAM)

---

### Post by jbaerboc on 2014-04-16
Hi Zaivala. When you went through nautilus to delete those files did you run Nautilus as root? I see from your profile you've been around awhile so maybe I'm waaay off here :). Just incase you didn't you can run gksu nautilus from your terminal which will open nautilus in sudo mode [after typing in your password of course]. 

Otherwise if you did delete the folders while in gksu nautilus do you know if you just simply hit delete or did you shift+delete [skips trash and perma-deletes]? I would suspect that maybe sudo has it's own trash folder hidden somewhere if what you did wasn't a perma delete.

---

### Post by zaivala on 2014-04-16
Yes, I ran gksu nautilus. Yeah, I've been around a while, but it's been on and off with a lot of going off and using oher Linuxes, may never get to be an Experienced User. I was told by another user that gksu is an incidence of sudo, and I did have to use my password.

I simply hit delete, did not know shift+delete. It did not go to Trash at all, and the space did not clear up. Any idea where the secret delete is?

I've had three different responses to my Root comments. One is that (unlike sudo) when a drive or folder is listed as root ownership, there ain't a damned thing you can do without finding the secret root login (which Ubuntu completely hides and nobody seems to know); the other is that your login password should work (it didn't, or I wouldn't have had a problem in the first place); and the third was that I *already* had ownership of the folder/drive (so why couldn't I use the files?).  I'd rather have someone like you sincerely offering to help than someone telling me I don't have a problem when I do.

Moss

---

### Post by baphomet2 on 2014-04-16
I would navigate to the drive on the command line to see if there are any hidden files (.Trash, etc).  You can get on there as root if you do "sudo su -" on the command line and then navigate away.

---

### Post by steeldriver on 2014-04-16
root's trash should be at /root/.local/share/Trash

```

sudo ls -l /root/.local/share/Trash/files

```

Interestingly, 13.10 (unlike 12.04) has added an option to gvfs-trash to *empty* the trash from the command line - but no matter what I try (sudo , sudo -H, sudo -i) I can't get it to understand I want to empty root's trash not mine! However it should be safe to do

```

sudo rm -rf /root/.local/share/Trash/

```

(this will delete the whole Trash directory i.e. both files and info - it will be recreated as needed next time you trash something as root).

---

### Post by zaivala on 2014-04-16
> **steeldriver said:**
> 
Interestingly, 13.10 (unlike 12.04) has added an option to gvfs-trash to *empty* the trash from the command line - but no matter what I try (sudo , sudo -H, sudo -i) I can't get it to understand I want to empty root's trash not mine! However it should be safe to do

```

sudo rm -rf /root/.local/share/Trash/

```

(this will delete the whole Trash directory i.e. both files and info - it will be recreated as needed next time you trash something as root).

OK I tried this in Terminal. It sat there for a second or five and then gave me back my prompt... so it did something which took a while.  Let me go check the drive...

Yep, that worked. Wow. Seems to have wiped more than I thought was there to wipe... Thanks a bunch, and hope I haven't wiped something I wanted LOL.

---

