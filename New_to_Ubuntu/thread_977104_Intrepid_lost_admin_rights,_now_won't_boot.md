---
title: "Intrepid: lost admin rights, now won't boot"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Summerland on 2008-11-09
Hello all,

I downloaded Intrepid last week and have been dual-booting it with Windows XP.  Had no troubles, everything worked, was very happy with my first Linux experience!

But then . . . yesterday I thought I would set up a user account for my wife.  So I went to System > Administration > Users and Groups, and added a new user.  I logged out, she logged in, surfed on Firefox a bit, then logged out again.  

When I logged in and tried to use Synaptic, it wouldn't accept my password.  I opened a terminal and tried manually, and it still wouldn't accept my password--said I had to see an administrator.  When I went back to System > Administration > Users, I was unable to access any details about my account.  So I logged out and shut down.

The next time I tried to boot, the splash screen froze halfway, then I got a screen of error codes that included the following cryptic messages:

chgrp:invalid group:'adm'
chgrp:invalid group:'root:utmp'
chgrp:invalid group:'root:polkituser'

chown:invalid group:'syslog:adm'

And then it froze!  Tried several times and the same thing happens.  Any ideas on how to regain my account status and successfully boot up again?

---

### Post by darrelljon on 2008-11-10
Use a live cd.

---

### Post by Summerland on 2008-11-11
And how do I use the live cd to restore my admin rights and repair what seems to be broken?

---

### Post by sdowney717 on 2008-11-11
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

read this about fixing sudo
Also, it is a good idea to have an extra super user account for when you get stuck. So, when you get it fixed, create one for backup use.

---

### Post by psusi on 2008-11-11
Looks like your /etc/group file got corrupted somehow.  I wonder if your disk may be going bad?  You can check from the livecd:

sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
sudo smartctl -t long /dev/sda

That will run for a good while in the background, and you can check the results with:

sudo smartctl -l selftest /dev/sda

---

### Post by cerz on 2008-11-12
I have the exact same issue.  I tried booting in recovery mode, dropping to root, and running "adduser *username_here* admin".  It returned "The group 'admin' does not exist."  Bad news.

I first noticed the issue this morning.  The two things I've done recently are a) run some updates yesterday morning b) install subversion according to a how to which I've unfortunately lost since it was bookmarked on the machine that's now unbootable.  If it was the second, I'm guessing it was because the how-to had me add an svn user with 'adduser'.  However, as soon as I tried to add myself to the 'svn' user's group using "useradd -G svn *username_here*", I got "The group svn doesn't exist".  When I ran Users and Groups from the system menu to try to do the same thing, I didn't find that group, or any groups listed, though all my users (including the svn user) did appear.

Thanks for any help!

---

### Post by cerz on 2008-11-12
After doing some more research, I've found that you should NEVER use useradd -G ... because it overwrites your groups.  You have to use useradd -a -G ... which appends.  Checking my /etc/group file from recovery mode shows me that basically all my groups are gone, except for the ones I've inadvertently restored while mucking around for a solution.  Right now I'm thinking I'll try to copy the correct file from a live cd, which might fix it enough to at least boot.

---

### Post by Summerland on 2008-11-13
Thanks to those who commented!

Yes, it looks like my /etc/group file is trashed.  I booted into recovery mode and opened up the file, and it only had these two lines in it:

root:x:0
nogroup:x:65534

I'm assuming this is not normal?  Since I'm a complete noobie, would someone mind giving step-by-step instructions on how to properly restore the file from the live cd to the hard drive from inside recovery mode, then make any necessary edits?

---

### Post by psusi on 2008-11-13
Just copy the file.  If you have your hard drive mounted on /mnt, then just do sudo cp /etc/group /mnt/etc/group.

---

### Post by inspired on 2009-01-25
After discoverying this issue was getting more severe, I have started a new thread so as not to bother the people subscribed to this one, which was from back in November.
New thread for me is [http://ubuntuforums.org/showthread.php?p=6614344](http://ubuntuforums.org/showthread.php?p=6614344)

Any help would be greatly appreciated.
Thanks..
Jonathan


> Hi folks,
I am happy to have found this issue is not unique to my system.

Somehow I lost sudo this morning. Something I installed last night must have stuffed something up, because this morning I had no admin rights. Sudo was broken.

Following instructions in the forums I booted into recovery mode and took a look at the sudo file using visudo. Everything seemed to be the way it was meant to be so I changed nothing and exited ( :q<enter> )

I then tried issuing an adduser command to add me to the admin group. But it gave an error saying the admin group does not exist. That seemed odd, and I rebooted just to see where things were at.

Now when I start up the system it seems completely hosed. Many lines relating to missing groups come up. It then hangs. I am not able to start it up.

So now I need to replace the group file, from what I can ascertain. I am wondering, however, if the default group file from a live cd has everything in it that is needed. Specifically, does any software installations alter the group file in order to set up groups for it to function (such as vbox and so forth)?

With thanks,

Jonathan

UPDATE:
So yes, as it turns out the group file has only the two entries cited above.
I am copying over the entries from the Live disc, but I can see this is incomplete. I have, for instance, determined that virtualbox creates a group.
Can anyone indicate how common it is for apps to create groups for themselves? I have a lot of applications installed on this machine, and I am concerned that some won't work due to the group file being hosed. Do I have to simply reinstall each of those apps as and when I discover them not working?

---

### Post by inspired on 2009-01-25
> **Summerland said:**
> Thanks to those who commented!

Yes, it looks like my /etc/group file is trashed.  I booted into recovery mode and opened up the file, and it only had these two lines in it:

root:x:0
nogroup:x:65534

I'm assuming this is not normal?  Since I'm a complete noobie, would someone mind giving step-by-step instructions on how to properly restore the file from the live cd to the hard drive from inside recovery mode, then make any necessary edits?

I'd be interested to know how or why using visudo cleaned out my group file so that it also had just the two entries mentioned here. Very strange.
It's possible something else did this, but then again I'd like to know what.
I booted. Admin/sudo rights were hosed. But no indication the group file was cleaned out because I did not have any group errors when booting.
Rebooted into recovery.
Ran visudo. Exited without making changes.
Issued an "adduser jonathan admin" command. Got message saying admin group did not exist.
Rebooted.
System hung due to the group file not being there.
Odd.

Jonathan

---

### Post by AndreLeComte on 2009-02-19
[LIST]
[*]For some reason, I have the same issue on my desktop computer.
[*]My notebook computer was also running Ubuntu with the same username and password as my desktop system.
[*]I attached a copy of the etc/group file from my notebook to an email and sent it to my email address.
[*]I started my desktop system using the Ubunutu CD-R.
[*]I downloaded the etc/group file from my web-based email and saved it in the etc folder on my desktop computer.
[*]Now I can log into Ubuntu on my desktop computer, although some features such as visual effects and Internet access are not functioning.
[*]At the end of this message I have posted entries from the auth.log section of GNOME's System Log Viewer.
[*]How can I reverse these changes or restore my desktop system to normal working order?
[/LIST]```

&#65279;Feb 16 13:26:26 Andre polkit-grant-helper[24375]: granted authorization for org.freedesktop.systemtoolsbackends.set to pid 24350 [uid=1000] [auth=andre]
Feb 16 13:27:23 Andre groupdel[24394]: remove group `adm' 

Feb 16 13:27:23 Andre groupdel[24400]: remove group `admin' 

Feb 16 13:27:23 Andre groupdel[24409]: remove group `audio' 

Feb 16 13:27:24 Andre groupdel[24423]: remove group `cdrom' 

Feb 16 13:27:24 Andre groupdel[24429]: remove group `crontab' 

Feb 16 13:27:24 Andre groupdel[24440]: remove group `dialout' 

Feb 16 13:27:25 Andre groupdel[24446]: remove group `dip' 

Feb 16 13:27:25 Andre groupdel[24452]: remove group `disk' 

Feb 16 13:27:25 Andre groupdel[24458]: remove group `fax' 

Feb 16 13:27:25 Andre groupdel[24465]: remove group `floppy' 

Feb 16 13:27:25 Andre groupdel[24471]: remove group `fuse' 

Feb 16 13:27:26 Andre groupdel[24490]: remove group `kmem' 

Feb 16 13:27:26 Andre groupdel[24502]: remove group `lpadmin' 

Feb 16 13:27:27 Andre groupdel[24514]: remove group `mlocate' 

Feb 16 13:27:27 Andre groupdel[24520]: remove group `netdev' 

Feb 16 13:27:27 Andre groupdel[24531]: remove group `nvram' 

Feb 16 13:27:27 Andre groupdel[24537]: remove group `operator' 

Feb 16 13:27:27 Andre groupdel[24543]: remove group `plugdev' 

Feb 16 13:27:28 Andre groupdel[24555]: remove group `pulse-access' 

Feb 16 13:27:28 Andre groupdel[24561]: remove group `pulse-rt' 

Feb 16 13:27:28 Andre groupdel[24571]: remove group `sambashare' 

Feb 16 13:27:28 Andre groupdel[24579]: remove group `sasl' 

Feb 16 13:27:28 Andre groupdel[24585]: remove group `scanner' 

Feb 16 13:27:29 Andre groupdel[24592]: remove group `shadow' 

Feb 16 13:27:29 Andre groupdel[24598]: remove group `src' 

Feb 16 13:27:29 Andre groupdel[24604]: remove group `ssh' 

Feb 16 13:27:29 Andre groupdel[24610]: remove group `ssl-cert' 

Feb 16 13:27:29 Andre groupdel[24616]: remove group `staff' 

Feb 16 13:27:29 Andre groupdel[24623]: remove group `sudo' 

Feb 16 13:27:30 Andre groupdel[24633]: remove group `tape' 

Feb 16 13:27:30 Andre groupdel[24639]: remove group `tty' 

Feb 16 13:27:30 Andre groupdel[24645]: remove group `usbusers' 

Feb 16 13:27:30 Andre groupdel[24651]: remove group `users' 

Feb 16 13:27:30 Andre groupdel[24657]: remove group `utmp' 

Feb 16 13:27:30 Andre groupdel[24665]: remove group `vboxusers' 

Feb 16 13:27:30 Andre groupdel[24671]: remove group `video' 

Feb 16 13:27:30 Andre groupdel[24677]: remove group `voice' 

Feb 16 13:27:31 Andre groupdel[24683]: remove group `winbindd_priv' 

Feb 16 13:27:31 Andre usermod[24690]: change user `andre' GID from `1000' to `0'

Feb 16 13:27:31 Andre usermod[24690]: change user `andre' password

Feb 16 13:27:31 Andre usermod[24696]: change user `avahi' GID from `120' to `65534'

Feb 16 13:27:31 Andre usermod[24696]: change user `avahi' password

Feb 16 13:27:31 Andre usermod[24702]: change user `avahi-autoipd' GID from `113' to `65534'

Feb 16 13:27:31 Andre usermod[24702]: change user `avahi-autoipd' password

Feb 16 13:27:31 Andre usermod[24708]: change user `backup' GID from `34' to `65534'

Feb 16 13:27:31 Andre usermod[24708]: change user `backup' password

Feb 16 13:27:31 Andre usermod[24714]: change user `bin' GID from `2' to `65534'

Feb 16 13:27:31 Andre usermod[24714]: change user `bin' password

Feb 16 13:27:31 Andre usermod[24720]: change user `daemon' GID from `1' to `65534'

Feb 16 13:27:31 Andre usermod[24720]: change user `daemon' password

Feb 16 13:27:31 Andre usermod[24726]: change user `dhcp' GID from `102' to `65534'

Feb 16 13:27:31 Andre usermod[24726]: change user `dhcp' password

Feb 16 13:27:31 Andre usermod[24732]: change user `games' GID from `60' to `65534'

Feb 16 13:27:31 Andre usermod[24732]: change user `games' password

Feb 16 13:27:31 Andre usermod[24738]: change user `gdm' GID from `114' to `65534'

Feb 16 13:27:31 Andre usermod[24738]: change user `gdm' password

Feb 16 13:27:31 Andre usermod[24744]: change user `gnats' GID from `41' to `65534'

Feb 16 13:27:31 Andre usermod[24744]: change user `gnats' password

Feb 16 13:27:31 Andre usermod[24750]: change user `haldaemon' GID from `123' to `65534'

Feb 16 13:27:31 Andre usermod[24750]: change user `haldaemon' password

Feb 16 13:27:31 Andre usermod[24757]: change user `hplip' GID from `7' to `65534'

Feb 16 13:27:31 Andre usermod[24757]: change user `hplip' password

Feb 16 13:27:31 Andre usermod[24763]: change user `irc' GID from `39' to `65534'

Feb 16 13:27:31 Andre usermod[24763]: change user `irc' password

Feb 16 13:27:31 Andre usermod[24769]: change user `klog' GID from `104' to `65534'

Feb 16 13:27:31 Andre usermod[24769]: change user `klog' password

Feb 16 13:27:31 Andre usermod[24775]: change user `libuuid' GID from `101' to `65534'

Feb 16 13:27:31 Andre usermod[24775]: change user `libuuid' password

Feb 16 13:27:31 Andre usermod[24781]: change user `list' GID from `38' to `65534'

Feb 16 13:27:31 Andre usermod[24781]: change user `list' password

Feb 16 13:27:31 Andre usermod[24787]: change user `lp' GID from `7' to `65534'

Feb 16 13:27:31 Andre usermod[24787]: change user `lp' password

Feb 16 13:27:31 Andre usermod[24793]: change user `mail' GID from `8' to `65534'

Feb 16 13:27:31 Andre usermod[24793]: change user `mail' password

Feb 16 13:27:31 Andre usermod[24799]: change user `man' GID from `12' to `65534'

Feb 16 13:27:31 Andre usermod[24799]: change user `man' password

Feb 16 13:27:31 Andre usermod[24805]: change user `messagebus' GID from `119' to `65534'

Feb 16 13:27:31 Andre usermod[24805]: change user `messagebus' password

Feb 16 13:27:31 Andre usermod[24811]: change user `news' GID from `9' to `65534'

Feb 16 13:27:31 Andre usermod[24811]: change user `news' password

Feb 16 13:27:31 Andre usermod[24817]: change user `polkituser' GID from `122' to `65534'

Feb 16 13:27:31 Andre usermod[24817]: change user `polkituser' password

Feb 16 13:27:31 Andre usermod[24823]: change user `proxy' GID from `13' to `65534'

Feb 16 13:27:31 Andre usermod[24823]: change user `proxy' password

Feb 16 13:27:31 Andre usermod[24829]: change user `pulse' GID from `116' to `65534'

Feb 16 13:27:31 Andre usermod[24829]: change user `pulse' password

Feb 16 13:27:31 Andre usermod[24836]: change user `root' GID from `0' to `65534'

Feb 16 13:27:31 Andre usermod[24836]: change user `root' password

Feb 16 13:27:31 Andre usermod[24843]: change user `saned' GID from `127' to `65534'

Feb 16 13:27:31 Andre usermod[24843]: change user `saned' password

Feb 16 13:27:31 Andre usermod[24849]: change user `sys' GID from `3' to `65534'

Feb 16 13:27:31 Andre usermod[24849]: change user `sys' password

Feb 16 13:27:31 Andre usermod[24855]: change user `syslog' GID from `103' to `65534'

Feb 16 13:27:31 Andre usermod[24855]: change user `syslog' password

Feb 16 13:27:31 Andre usermod[24861]: change user `uucp' GID from `10' to `65534'

Feb 16 13:27:31 Andre usermod[24861]: change user `uucp' password

Feb 16 13:27:31 Andre usermod[24867]: change user `www-data' GID from `33' to `65534'

Feb 16 13:27:31 Andre usermod[24867]: change user `www-data' password

Feb 16 13:27:32 Andre groupdel[24876]: remove group `avahi' 

Feb 16 13:27:32 Andre groupdel[24882]: remove group `avahi-autoipd' 

Feb 16 13:27:32 Andre groupdel[24889]: remove group `backup' 

Feb 16 13:27:32 Andre groupdel[24895]: remove group `bin' 

Feb 16 13:27:32 Andre groupdel[24901]: remove group `daemon' 

Feb 16 13:27:32 Andre groupdel[24907]: remove group `dhcp' 

Feb 16 13:27:32 Andre groupdel[24913]: remove group `games' 

Feb 16 13:27:32 Andre groupdel[24921]: remove group `gdm' 

Feb 16 13:27:33 Andre groupdel[24927]: remove group `gnats' 

Feb 16 13:27:33 Andre groupdel[24933]: remove group `haldaemon' 

Feb 16 13:27:33 Andre groupdel[24939]: remove group `irc' 

Feb 16 13:27:33 Andre groupdel[24945]: remove group `klog' 

Feb 16 13:27:33 Andre groupdel[24951]: remove group `libuuid' 

Feb 16 13:27:33 Andre groupdel[24957]: remove group `list' 

Feb 16 13:27:33 Andre groupdel[24963]: remove group `lp' 

Feb 16 13:27:33 Andre groupdel[24970]: remove group `mail' 

Feb 16 13:27:34 Andre groupdel[24976]: remove group `man' 

Feb 16 13:27:34 Andre groupdel[24982]: remove group `messagebus' 

Feb 16 13:27:34 Andre groupdel[24989]: remove group `news' 

Feb 16 13:27:34 Andre groupdel[24998]: remove group `polkituser' 

Feb 16 13:27:34 Andre groupdel[25004]: remove group `proxy' 

Feb 16 13:27:34 Andre groupdel[25010]: remove group `pulse' 

Feb 16 13:27:35 Andre groupdel[25019]: remove group `saned' 

Feb 16 13:27:35 Andre groupdel[25025]: remove group `sys' 

Feb 16 13:27:35 Andre groupdel[25031]: remove group `syslog' 

Feb 16 13:27:35 Andre groupdel[25037]: remove group `uucp' 

Feb 16 13:27:35 Andre groupdel[25043]: remove group `www-data' 

Feb 16 13:29:40 Andre sudo: cannot execute /usr/sbin/sendmail: No such file or directory

Feb 16 13:29:40 Andre sudo:    andre : user NOT in sudoers ; TTY=pts/0 ; PWD=/home/andre ; USER=root ; COMMAND=/etc/init.d/udev restart
```

---

### Post by inspired on 2009-02-20
Andre,
I question whether posting twice is necessary. These two threads where initially unrelated. I had two issues, the later one is the one you have. I have replied to that here [http://ubuntuforums.org/showthread.php?t=1050113&goto=newpost](http://ubuntuforums.org/showthread.php?t=1050113&goto=newpost)

If you take the time to read through this thread (the one you're looking at now), you'll find into on how to fix sudo permissions. But most of the info you need is on that other post.

Regards,

Jonathan

---

