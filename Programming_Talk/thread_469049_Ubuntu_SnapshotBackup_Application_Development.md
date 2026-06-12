---
title: "Ubuntu Snapshot/Backup Application Development"
date: 2007-06-09
forum: Programming Talk
---

### Post by FryerFox on 2007-06-09
I'm working on a snapshot system that uses [rsnapshot]("http://www.rsnapshot.org/") as the underlying snapshot mechanism (a snapshot is a copy of a directory at a certain point in time that doesn't use space for the files that have not changed - like Apple's TimeMachine)

Currently having a little trouble getting menu items to appear and some other GNOME/Debian-convention stuff, but if someone is interested in trying this out, install the attached .deb, and add entries to the applications menu:

title="TimeVault Configuration" 
command=" gksudo '/usr/bin/timevault/timevault --admin' "
icon="/usr/share/pixmaps/timevault.png"

title="TimeVault User Preferences" 
command=" /usr/bin/timevault/timevault --user "
icon="/usr/share/pixmaps/timevault.png"

Install at your own risk - this is version pre-alpha-0.1. There are many aspects that are not fleshed out yet (better snapshot management like root being able to delete intermediate snapshots, writing help files, creating icons, etc.), but these should be getting introduced relatively soon. I was just looking for some community feedback on the project.

It shouldn't really mess anything up seriously unless you are already using rsnapshot. To force an uninstall (uninstalling the .deb from synaptic should work fine, but just in case):

> 
rm -rf /usr/bin/timevault

rm -f /usr/share/pixmaps/timevault.png
rm -f /usr/share/menu/timevault.menu
rm -f /etc/init.d/timevault_init
rm -f /etc/cron.d/timevault


[B]WARNING: If you are already using rsnapshot, then backup the config file (/etc/rsnapshot.conf) first before installing!
[/B]

[B]ANOTHER WARNING: This program may destroy your data and eat your babies, etc. I use it myself without problems, but ideally, only install it in a VM or a test machine.
[/B]

---

### Post by FryerFox on 2007-06-09
P.S. The menu entries are under Administration (for root admin) and Preferences (for single-user preferences). Previous versions are navigate by right-clicking on a file or directory in Nautilus and selecting Scripts->Previous Version.

---

### Post by altonbr on 2007-06-11
I'm worried to try it at the moment, but the concept looks fantastic!

[LIST]
[*] I would say that eventually, it would be best if it said "Backup" right on the right-click menu and not under 'Scripts'
[*] The 'frequency' choices you have are a bit confusing as a regular user wouldn't need to know that you are backing up every day, then keeping one daily-build from every week and then one of the week builds every month and so on. It should just say "monthly", "yearly", etc., with a 'help' button (possibly) to further explain how the program works. That will be a part of your documentation though.
[*] Lastly - for my quick comments - you should try to write a script for the application menu files so that there is no work for the user.
[/LIST]

Of course, I'm trying to speak of what is more 'user-friendly', but as a programmer, I understand that you'll probably want to program to work first, before simplifying it and making it 'pretty'.

Keep up the good work!

---

### Post by FryerFox on 2007-06-11
Actually, I got to work on it more this weekend, and so found out how to add the menu entries correctly.

Also, I am adding the Previous Versions option to the properties dialog in Nautilus for files that are snapshotted (i.e. right-click on a file or directory and go to properties, go to the 'Previous Versions' tab and select one from the calendar).

I will seriously consider an easier way for defining backup frequency (or possibly just assume a default frequency and allow 'expert' users to change it).

Thanks for the suggestions - I was stunned by how little feedback I had received. I guess I figured that backups and snapshots were just not that interesting to most people.

---

### Post by altonbr on 2007-06-11
Well you're also in 'Programming Talk' and not a lot of the regular users would visit this part of the forum... I am surprise that no programmers have made comments though.

I know people do care and are interested in this achievement, so I'd suggest making a separate sub-project on Launchpad for it, or at least a personal website with some documentation and a .deb that is constantly updated.

Don't worry, they will come!

---

### Post by pmasiar on 2007-06-11
> **FryerFox said:**
> I was stunned by how little feedback I had received. I guess I figured that backups and snapshots were just not that interesting to most people.

Not that many people are interested in trying alpha-level software. Hardest part is to get first 3 users and first 3 outside developers/contributors :-) 

Until then, your project is not proven - just one of 10K projects.

Make it easy to install, with .deb, after enabling your private repository. Your program should make all the needed backups, etc - make it easy to try it.

---

### Post by FryerFox on 2007-06-11
> **pmasiar said:**
> Not that many people are interested in trying alpha-level software. Hardest part is to get first 3 users and first 3 outside developers/contributors :-) 

Until then, your project is not proven - just one of 10K projects.

You have a point. I was just looking for some early feedback, like the kind I got from altonbr. Also, I believe that I made the warning a little too strong (it won't really eat your babies - I was exaggerating), since I took a great deal of care to ensure that data would not be damaged. 

> **pmasiar said:**
> Make it easy to install, with .deb, after enabling your private repository. Your program should make all the needed backups, etc - make it easy to try it.

I'm in the process of doing that. Hopefully, I'll have something more polished by this weekend and post it to Launchpad as altonbr suggested, or failing that (i.e. if I can't figure out how to get bzr source control to work, or don't have time), I can post a .deb to the forums instead.

For now, I will remove the attached .deb, but leave the screenshots up.

---

### Post by altonbr on 2007-06-12
Well, I'm going to make a Gusty VM in the next few days and will be able to test it then... Just make sure you give me the link to the .deb when your next version is out, OK? And is Gusty OK or would you like me to test Feisty and older versions as well?

Good luck with getting people involved via launchpad too. Launchpad has made some major improvements recently, and it should be pretty easy to get up and running!

Just a note, solo projects often stay solo project unless there is a large market for your product. I personally think a front end for rsnapshot has a large market, but take pyfragtools as an example: [http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)

It is a HD defragmentor made by a 19 year old - John Dong. He has made several revisions and submitted the code on Launchpad ([https://code.launchpad.net/pyfragtools](https://code.launchpad.net/pyfragtools)) but as far as I know, he's the only one who has worked on it.

The rewarding part of his work is that it is supported by MOTU and can be found in the Ubuntu repositories under the package name 'defrag' [I THINK].

---

### Post by FryerFox on 2007-06-13
Thanks, I appreciate the help.

While I haven't started using bazaar on Launchpad yet, I have hosted the project documentation and .deb installer on it:

[https://launchpad.net/timevault/+download]("https://launchpad.net/timevault/+download")

It should work on both Feisty and Gusty out of the box with the following requirements:[LIST]
[*]You have to choose a location for the backup root (System->Admin->Manage Snapshot).
[*]And you need to restart nautilus (nautilus -q) or log out and then back in.
[/LIST]

---

