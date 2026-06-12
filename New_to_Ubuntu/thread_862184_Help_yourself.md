---
title: "Help yourself"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by pauper on 2008-07-17
*_Objective:_*
Here is a summary of guidelines, regarding a way to deal with software
issues, I adhere to and someone might find useful. 

*_Event:_*
Something went wrong with software (can't start X session :twisted:, lost sound,
forget sudo password, system locks up, etc.)--take a deep breath, close your
eyes, take a break; go for a walk, meet a woman, meet a man--relax.

Need to finish some important spreadsheets for tomorrow? Use Live CD for the
time being (look up right away "[color=#348781]**(*)Be prepared**[/color]" paragraph). Don't rely on 
"reboot-reinstall" approach without hesitation, you never know--the answer
could be a few commands away.
[sarcasm]I hear someone: But it could take days to pinpoint the fault, and
who knows how long for "someone" to fix it![/sarcasm]
Well, I leave it up to you.

Physical damage to hardware? Refer to merchant policies of vendor you bought
from.

But don't feel low--"[i]dum loquimur, fugerit invida aetas: carpe diem quam
minimum credula postero[/i]" (While we speak, time is envious and is running away
from us. Seize the day, trusting little in the future).

When you feel calm--it's time to act.

*_Steps:_*
[color=#348781][size=+1](*)Gather information.[/size][/color]
Before opening a new thread/filling a bug report run a thorough search:
through forums, mail lists, FAQs, bug reports for similar issues.

When you START a THREAD, provide as much information relative to the subject
as possible, and steps you've already taken, if any. When it's necessary,
attach "lspci", "dmesg", "syslog", output and such--don't make people to ask
for it in the follow-up post.
Here is a good place to get a better understanding of what things to include
and when:

[https://wiki.ubuntu.com/X/Reporting#head-8c2902c284112c960b29386ea3d2f97fd3c57109](https://wiki.ubuntu.com/X/Reporting#head-8c2902c284112c960b29386ea3d2f97fd3c57109)

*List of relevant FAQs with some troubleshooting:*

[color=#E42217]**General:**[/color]
[http://www.tldp.org/FAQ/Linux-FAQ/index.html](http://www.tldp.org/FAQ/Linux-FAQ/index.html)
[http://aplawrence.com/Unixart/troubleshooting.html](http://aplawrence.com/Unixart/troubleshooting.html)
[http://www.linuxtroubleshooting.com/wiki/index.php?title=Main_Page](http://www.linuxtroubleshooting.com/wiki/index.php?title=Main_Page)
[http://www.debian.org/doc/manuals/debian-faq/index.en.html](http://www.debian.org/doc/manuals/debian-faq/index.en.html)

[color=#E42217]**GRUB:**[/color]
[http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible](http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible)
[http://forums.gentoo.org/viewtopic-t-122656.html](http://forums.gentoo.org/viewtopic-t-122656.html)

[color=#E42217]**X Windows:**[/color]
[https://wiki.ubuntu.com/X/Troubleshooting](https://wiki.ubuntu.com/X/Troubleshooting)

[color=#E42217]**GNOME:**[/color]
[http://www.yolinux.com/TUTORIALS/GNOME.html#PITFALLS](http://www.yolinux.com/TUTORIALS/GNOME.html#PITFALLS)

[color=#E42217]**Wireless:**[/color]
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html#debug](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html#debug)

[color=#E42217]**Common gutsy bugs:**[/color]
[http://bapoumba.wordpress.com/2007/10/29/common-bugs-in-gutsy-with-workarounds/](http://bapoumba.wordpress.com/2007/10/29/common-bugs-in-gutsy-with-workarounds/)


[color=#348781][size=+1](*)Maintain etiquette.[/size][/color]
[http://www.psychocats.net/ubuntucat/getting-the-best-help-on-linux-forums/](http://www.psychocats.net/ubuntucat/getting-the-best-help-on-linux-forums/)

Credit for link to ugm6hr from "[New to Ubuntu? Start here...](http://ubuntuforums.org/showthread.php?t=801404)" thread.

[color=#348781][size=+1](*)Be prepared.[/size][/color]
Make a habit of keeping a Live CD. Over some time of going through different
releases you should have a firm grasp of what works where for YOUR system.
Pick that release, burn to CD as ISO image, try if it works and stash it
somewhere.
You WILL need it one day: to finish off some important projects when it's the
only option to otherwise reinstalling, for troubleshooting, to recover
valuable files, to reinstall, etc. Those who bought computer pre-installed
with Ubuntu, should download the same release from mirror-site of:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

[size=3][font=freesans]How to fetch the file in question from hardrive to Live CD environment.[/font][/size]

Reboot computer. Press F12 key when you see BIOS vendor image
(Note: it could be a different Fn key, depending on the manufacturer, mine is
"Phoenix Tech."). Insert Live CD, choose CD/DVD drive. Press Enter. Now, when
prompted, choose "Try Ubuntu without any change..."(Hardy), "Start or install
Ubuntu" (Feisty and Gutsy) option.

Go to Places>Computer, double click on XXX GB Media--this action will mount
your OLD filesystem to /media/disk. Then navigate through it to the file you
looking for; copy that file to /home/ubuntu/Desktop. Right-click on 
XXX GB Media icon on your desktop, select unmount. When the job is done,
save a copy to your web mailbox or USB pendrive.

*An alternative way in terminal:*

Look up the name of your OLD filesystem, usually hda1, or sda1; unless
you keep /home on different partition. Again it probably has the largest
amount of blocks:
```
sudo fdisk -l
```

When in doubt, the following commands might come handy:
```
blkid /dev/sda1
sudo vol_id /dev/sda1
```

Create a mount-point for your OLD filesystem:
```
sudo mkdir /media/disk
```

Mount it:
```
sudo mount -t ext3 /dev/sda1 /media/disk
```

Optional, unless you not sure of the location of the file in question, list all files
in "john_doe" directory:
```
ls -al /media/disk/home/john_doe

```
Copy file:
```
cp /media/disk/home/john_doe/some_spreadsheets /home/ubuntu/Desktop
```

Unmount OLD filesystem:
```
sudo umount /dev/sda1

```
Perform all the necessary actions with that file. Save a copy to your web
mailbox or USB pendrive.

[color=#348781][size=+1](*)DO READ man PAGES![/size][/color]
Believe me you are better off learning something piece by piece in a process
than asking same questions over and over again.
 
"[i]Give a man a fish and you feed him for a day; teach a man to fish and you
feed him for a lifetime.[/i]"

Here "man" stands for a human being, not manual =D>.

[color=#E42217]**Online man pages:**[/color]
[http://linux.die.net/man/](http://linux.die.net/man/)

*Beyond that...*

[color=#E42217]**Kernel Documentation:**[/color]
[http://www.mjmwired.net/kernel/Documentation/](http://www.mjmwired.net/kernel/Documentation/)

[color=#E42217]**Manuals, HOWTOs, WIKIs...**[/color]
[http://www.gnu.org/manual/](http://www.gnu.org/manual/)
[http://www.tldp.org/](http://www.tldp.org/)
[http://www.linfo.org/main_index.html](http://www.linfo.org/main_index.html)

[color=#E42217]**Debian Policy Manual:**[/color]
[http://www.debian.org/doc/debian-policy/](http://www.debian.org/doc/debian-policy/)

[color=#E42217]**Freedesktop standards:**[/color]
[http://standards.freedesktop.org/](http://standards.freedesktop.org/)

[color=#E42217]**GNOME Documentation Library:**[/color]
[http://library.gnome.org/](http://library.gnome.org/)

[color=#E42217]**Mozilla Knowledge Base:**[/color]
[http://kb.mozillazine.org/Knowledge_Base](http://kb.mozillazine.org/Knowledge_Base)

[color=#E42217]**Cheer up!**[/color]
[http://www.mozilla.org/book/](http://www.mozilla.org/book/)
[http://partmaps.org/era/unix/award.html](http://partmaps.org/era/unix/award.html)
[http://en.tiraecol.net/modules/comic](http://en.tiraecol.net/modules/comic)
[http://www.dina.kvl.dk/~abraham/religion](http://www.dina.kvl.dk/~abraham/religion)

[color=green]Do not neglect /usr/share/doc entries![/color]

[color=#348781][size=+1](*)Keep a record.[/size][/color]
Make a habit of writing to some file about encountered issues and applicable
resolutions, plus anything else you learn or configure. Spend some time on it
right now then to rummage through forums again later.

---

### Post by benfindlay on 2008-07-17
Excellent advise, perhaps one for the stickies?

Ben

---

