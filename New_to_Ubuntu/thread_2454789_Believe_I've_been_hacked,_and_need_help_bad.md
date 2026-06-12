---
title: "Believe I've been hacked, and need help bad"
date: 2020-12-05
forum: New to Ubuntu
---

### Post by jeffpas2 on 2020-12-05
I think I've been hacked  :(  .....  I won't go into all the details why I think this is true..... but I have two computers, one ran Linux MInt and the other had Ubuntu (I can get to a salvage # prompt on the Ubuntu, and give version information if necessary).
Both pretty old OS versions.    In fact I had one PC about 8 years, and the laptop running Ubuntu about 10.

Anyway all was fine on the Linux Mint computer when I noticed suddenly my IP address was showing as IPV6 instead of IPV4.   I'd never seen that before.  
So I rebooted.   But suddenly the PC won't boot anymore- instead it goes directly to (initramfs).    
After a couple days of struggling I finally discovered 14 bad blocks in my root filesystem, that have made it unmountable.
Can someone do this to your hard disc remotely?

I would have thought it just a coincidence, even though I've never seen this happen in my life.    But I got on an old 2nd laptop I rarely use, as a backup- and suddenly all my firefox windows closed on their own there.  So I unplugged it from the 'net.     I then noticed strangely, that my sd flash and USB ports would not recognize any external devices to copy off any data.

Anyway a few days later, I finally got up the confidence to try rebooting that (expecting something similar).

It wasn't the same.
Instead, on the Ubuntu laptop- I suddenly now can't log in at all.   I get the login screen - enter my password.   It starts to go in as if accepted, but then goes directly back to the login window again.
What's weird is, right before I rebooted, I specifically double checked my user and root passwords, to make sure they worked.   They worked fine.

When I drop out to an emergency recovery prompt (#), and try to change/update my username password, I get:

passwd: Authentication token manipulation error
passwd: password unchanged

It won't let me update my user password as root at all.
So both computers tanked, at the same time, after 8-10 years?   
It seems quite a coincidence.

Anyway I found this article:

[https://askubuntu.com/questions/57620/g ... ange-my-us]("https://askubuntu.com/questions/57620/getting-an-authentication-token-manipulation-error-when-trying-to-change-my-us")

It suggested following these steps:

# mount -o remount,rw /
# chmod 640 /etc/shadow
# sudo passwd USER

I tried this and changed my user password, and got a message updated 'successfully'. 
But when I reboot again to the login screen, it still doesn't work.   Still, I get the exact same thing.
I enter the password for the user account, and it just comes back to the login screen, goes nowhere.
If I enter any other password, it says 'incorrect password'.

Does anybody know what this is, how that might happen.... and how to fix it?

---

### Post by guiverc on 2020-12-06
You have provided few specifics. You mention two ages (8 & 10), but not if that's the age of the computers themselves, or the age of the OS installed.   *The computer on which I'm typing this is a 2009 dell, so it's ~11 years old, but it's running Lubuntu hirsute which will be the 21.04 release; hardware & software age differs and can be a clue*.

I would boot *live* media first, and not try and touch your system(s).  I tend to check the health of a drive on any unusual behavior first thing; in theory it should be done regularly anyway (to prevent data loss), but I use problems as a *random* trigger to check health too.  Almost every drive has SMART diagnostics ([https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)) which I'd run from the *live* system so if the drive is dying, or has problems, any remaining life is kept for any needed restoration of data.

You describe a login loop, this can occur for many reasons; so I'd suggest a terminal login first (and check you have space), but given other problems I'd avoid booting it until you know disk(s) are healthy.  Most other causes for a login-loop require change(s) in the prior two sessions before the login-loop occurred, but you provided no clues as to what happened in those sessions, so assuming no real change I'd check space in $HOME first (ie. your user directory).

Given the age of the hardware, I'd likely also open the boxes up & do a cap-check (ie. scan the motherboard for issues, clean if necessary, especially check for swollen capacitors, heat signs etc).

I won't provide anything on software, as you've not provided details as to your software stack (what age, release details etc).  I'd explore the hardware first anyway.

---

### Post by jeffpas2 on 2020-12-06
Well I kind of wish I had posted this in the GENERAL forum, as this one doesn't seem to get much activity.
I'm feebly hoping there is some other explanation for this odd string of setbacks....  other than some hateful cyber attack.

Anyway one explanation I found online for at least part of the odd behavior with the Ubuntu laptop was the file system being full.

# df - v

Shows the root filesystem at 99%.   Pretty close to tapped out.
If I run:

# du -a /var | sort -n -r | head -n 10

I can see the top 10 files in size.   Three of these are:

/var/cache/apt
/var/cache/apt-xapian-index
/var/cache/apt-xapian-index/index.1

Can I remove these?

---

### Post by jeffpas2 on 2020-12-06
Oops just saw your reply.
The / file system is at 99%
Two others are showing with the df command:

/boot/efi                        99%
/var/lib/lightdm/.gvfs     99%

What details do you want?
I have a root prompt.
I feel as if I should free up some space now

---

### Post by wildmanne39 on 2020-12-06
*Thread moved to **New to Ubuntu for a more appropriate fit**.*
>  After a couple days of struggling I finally discovered 14 bad blocks in my root filesystem, that have made it unmountable.
Usually means hard drive issues and I do not believe this symptoms are because of being hacked.
>  Shows the root filesystem at 99%. Pretty close to tapped out. 
The root file system being full will create a login loop where you will not be able to get to your desktop, you will need to free up space on your drive and as guiverc suggested you should run smart diagnostics.

There are two answers at the following link that should help you free up space, there are several answers at the link with different ways of freeing up space so I suggest you review the whole page before settling on one method.

[https://askubuntu.com/questions/57994/root-drive-is-running-out-of-disk-space-how-can-i-free-up-space](https://askubuntu.com/questions/57994/root-drive-is-running-out-of-disk-space-how-can-i-free-up-space)

---

### Post by jeffpas2 on 2020-12-06
I booted the Ubuntu laptop to a Linux MInt Live USB and ran the disk utility, and it looks like there are 0 bad sectors.
Disk is "OK".
I can see my files.   Though practically everything here I haven't used in years.
[COLOR=#000000]/var/cache/apt[/COLOR]
[COLOR=#000000]/var/cache/apt-xapian-index[/COLOR]
[COLOR=#000000]/var/cache/apt-xapian-index/index.1

can I just delete these off the root prompt, with RM command?
My understanding is a cache directory is temporary anyway.


[/COLOR]

---

### Post by deadflowr on 2020-12-06
> can I just delete these off the root prompt, with RM command?
My understanding is a cache directory is temporary anyway.



You should use the apt clean command to clear of the cached apt archives.
These are the archives of packages installed, either from installing new software or installing new updates for existing, already installed software.
While you probably can just delete the archived content, it is best to use the tools design to do it for you,
as it will guarantee everything is properly cleaned.

Cached files are not temp files, they stay as long as you have them, indefinitively.
Cached files are for easy to retrieve files, so it takes shorter times to run things.
( The cached apt files are the downloaded installation files, they're cached so if you need to reinstall, it only needs to run the installer part, and not the retrieval bit.
This cuts the downtime of installation since the need to download a large file is not needed, as you already have it.)

---

### Post by jeffpas2 on 2020-12-06
Deleted files when at the emergency # prompt and dropped root filesystem to 96%.
Rebooted and got back to the user login prompt.
It takes the password, but again just goes to the login window again, doesn't let you in.  Any other password it says, "Invalid password".

It appears to be locked in a login loop.
How this started, I wish I could find out.

Its strange that I've never seen this happen before.   I've had the laptop since at least 2009.

---

### Post by jeffpas2 on 2020-12-06
********************FIXED*********************!!!!!!!

[https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop)

---

### Post by wildmanne39 on 2020-12-06
> It appears to be locked in a login loop.
How this started, I wish I could find out.
Like I said on my previous post I believe this is exactly what happens when your root files system runs out of space however it has been a long time since this has happened to me because I make my root partition kinda large, it sounds like from what you have said that Ubuntu is a very old version, I recommend posting the specs of your computer and the version of Ubuntu you are using, it is probably best to wipe the drive and start over if it is as old a version as it appears to be, I recommend for a system as old as what you have stated that you try lubuntu from livecd or liveusb.

I am not saying that freeing up enough space will not get you back in but if it is a very old version of Ubuntu then I would not waste the time it will take to get back in.
[https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)

---

### Post by jeffpas2 on 2020-12-06
These two files needed to be changed from root to username ownership in user's directory..... and now everything working A-OK

.Xauthority
.ICEauthority

chown USERNAME:USERNAME [filename]

For some reason they were owned by root, and that didn't allow the user to log in.    
But is there any way to discover how this problem came about?

---

### Post by guiverc on 2020-12-06
That problem can be created by a user running a GUI program using root (ie. sudo) privileges, thus changing the permissions from the original owner to root, likely because a setting was changed whilst using elevated privileges.

GUI programs should not be run by root or with `sudo`.  If you looked at the file stats (`stat ~/.Xauthority` for example) before you changed ownership again, you've had had the date/time of the last change.. it'll likely now have the timestamp of your 'fix' (thus prior clue gone).  Next I'd look in your `history` (*though default of command log is to not store date/time of each command, but that's something I always change*) for clues as to commands run using `sudo` that should not have been.

---

