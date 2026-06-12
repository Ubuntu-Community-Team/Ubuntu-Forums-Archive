---
title: "Recommendations re backup folders please"
date: 2011-11-23
forum: New to Ubuntu
---

### Post by nickdc on 2011-11-23
I need to do a fresh install on my old Phillips freevents laptop (currently running dual boot XP + Ubuntu 11.04). After the install I'd like to get back to more or less where I was before, though I haven't got a lot of additionally installed applications and I don't mind reinstaalling apps as and when needed, but I don't want to lose basic settings or accumulated data. I've been reading up on backing up prior to the install and have pretty well decided to use rsync to back up via ethernet to a desktop machine (also dual boot XP + 11.04). I understand how to do this, but all the documentation I've looked at so far is rather vague about what to back up and where to put it. I'd appreciate specific guidance from experienced users on the following:

1. Do I need to back up anything other than my home folder? (If so, what?)
2. Is there anything in my home folder I should exclude from the backup? (eg because it might cause conflicts when restored to the clean installation.)
2. Where on the remote machine should I store the backup? (eg should I create a "laptop backup" folder in my home folder on the desktop, or create a separate folder in the root, or even, as some have suggested, a new partition? If anything other than the first option, please point me in the direction of some clear, step by step instructions.)
3. On a friend's suggestion, I'm currently running Xfce rather than Gnome. I'm minded to try Lubuntu when I re-install. Would this make any difference to any of the answers above?

I'll be very grateful for any advice.

---

### Post by sudodus on 2011-11-23
Hi nickdc,

I'm glad that you prepare so well before your fresh install :)

This thread describes moving from one distro to another
[COLOR=RoyalBlue][http://ubuntuforums.org/showthread.php?t=1881926](http://ubuntuforums.org/showthread.php?t=1881926)[/COLOR]
Oldfreds post is very good.

1. Backup personal data wherever you store them. You should know if they are somewhere else than in your home folder.

2. There are settings (typically in 'hidden files' starting with .) in your home directory, but you need not exclude it.

2b. Put it where it is best for you. But don't put it inside what you plan to backup (backup /home to /something-else). If you have an external hard drive, that might be the best. But make sure to put it on a partition with a linux file-system, otherwise the permissions for files and folders will be garbled. An alternative is to make an image or a compressed archive file, for example a tarball.

3. No it is not a big issue. You can even run a system with several desktops installed and select which one to use at the login screen.

Good luck

---

### Post by mastablasta on 2011-11-23
> **nickdc said:**
>  I've been reading up on backing up prior to the install and have pretty well decided to use rsync to back up via ethernet to a desktop machine (also dual boot XP + 11.04). I understand how to do this, but all the documentation I've looked at so far is rather vague about what to back up and where to put it. .
 
 
why not keep it simple and use mintbackuptool (there is PPA for it). 
 
you will get 4 buttons, 2 for backup, 2 for restore.
 
2 for backup= one to bacup your settings, other one to backup your home
2 for restore= one to restore your settings, one to restore you home
 
easy peasy....
 
Or if you wish to do a whole image of drive kind of backup then use ubutnu based Redo Backup. It's a live CD that will present you with 2 buttons. one for backup and the other one for restore. all that is left is to point to it where to put the images (or where to take them form ) and that's it.

---

### Post by Sef on 2011-11-23
I like to back up with [Clonezilla]("http://clonezilla.org"), so in case of a problem, I can reinstall the os.

---

### Post by Jonathan.Dufte on 2011-11-23
if all your crucial/personal data is located in your home-folder it is sufficient to just copy that.

---

### Post by Jacobonbuntu on 2011-11-23
> **Sef said:**
> I like to back up with [Clonezilla]("http://clonezilla.org"), so in case of a problem, I can reinstall the os.
Ah, thanks I knew there was a program like this, but couldn't find it back :)

---

### Post by nickdc on 2011-11-23
Thanks for the help and suggestions. (Doesn't bode well that I can't even type 1 to 4 without messing up!!)

I'm persevering with rsync (Grsync, actually, as I'm not that confident with the terminal yet) and now have a couple of further questions:

1. Backing up to a pen drive, which has Windows related data on it, I don't want to have to reformat it. Will I be ok if I just tick the box for Windows compatibility in Grsync's options?

NB I've just tried this and all the main data seems to have transferred ok to the backup file, though Grsync reported errors. Unfortunately for some reason (bug?) the scroll bars don't work so I can't examine the full list of errors, but all the ones visible in the window are evolution files, and I no longer use evolution so i'm not too worried. But I obviously don't want to rely on this as my sole backup, so ...

2. I'm having problems executing my first choice, of backing up via ethernet to a local desktop machine. I've mounted the desktop from the laptop and can browse its folders. But I can't see how to input it as a destination in Grsync. The documentation on Grsync says: "Backup over a network is possible, preferably the user should mount the  network share to be backed up to prior to launching the program. The  share would then be listed in the Browse GUI and could easily be added." But I've tried this and the share isn't listed in the Browse GUI!  :confused:

---

### Post by sudodus on 2011-11-23
1. Are you backing up to an archive or do you copy file by file to the pen drive? Consider my point 2b about ***file permissions*** in my previous reply!

2. You must have a server daemon running on the other computer in order to mount it. What kind of connection do you intend to use: samba, sftp (ssh) or ...? This is not the easiest way, but if you want to and have time to learn, it will be interesting.

An external hard drive would be much easier. You can buy or borrow one for the time necessary to re-install your system.

---

### Post by nickdc on 2011-11-23
Why is nothing simple?! But thanks, I greatly appreciate your help.

1. Not archiving; doing it file by file. Take your point re file permissions - see below.
2. As I said in my second post, I can mount it, and can browse to it. Yesterday I tried simply copying and pasting the Home folder on the laptop to a backup folder I'd created within the home folder on the desktop, but it didn't work; I got errors and even after skipping those files the whole process went haywire, ending up saying there was one file to copy in 0 seconds and the disk was still whirring and it went on and on, saying 9.6 gb copied of 9.6 gb, then both figures just went on increasing (there's actually 9.1 gb of data in the folder) and I finally cut it at about 12.5 gb. This happened twice. Another day gone by! That's why I did some more research and decided to use rsync this morning.

As you'll see from the above, I have time and I want to learn. I'm using ssh to connect to the remote dektop, but as I said, I can't see how to enter the (already mounted) destination folder in the Grsync GUI.

I've given up on the pen drive but I do have a WD passport usb drive with me (not in a position to buy or borrow at the moment) but come up against same issues re file permissions etc. Can't just reformat it as I have important stuff on it, taken from Windows machines. Have read a bit about partitioning but looks a bit dodgy - is there a way, using Ubuntu, to simply create an extra Linux compatible partition on it to take the laptop backup, without messing with the stuff already on it? The alternative would be to backup the stuff on the usb drive to the desktop, then reformat it (usb drive) to linux and copy the stuff back when I've done the laptop backup, but I'm reluctant to do that because a) it's telling me it will take 6hrs to copy the stuff from the usb drive to the desktop and b) I don't want to risk the file permissions issue the other way round ie the Windows files getting messed by being transferred to a linux partition.

What's my best way forward? ... I thought I'd left all this behind when I moved over to Linux!!!

---

### Post by sudodus on 2011-11-23
> **mastablasta said:**
> why not keep it simple and use mintbackuptool (there is PPA for it). 
 
you will get 4 buttons, 2 for backup, 2 for restore.
 
2 for backup= one to bacup your settings, other one to backup your home
2 for restore= one to restore your settings, one to restore you home
 
easy peasy....
 
Or if you wish to do a whole image of drive kind of backup then use ubutnu based Redo Backup. It's a live CD that will present you with 2 buttons. one for backup and the other one for restore. all that is left is to point to it where to put the images (or where to take them form ) and that's it.

Now that I know you have a USB hard drive with plenty of room I suggest that you make a backup with ***mintbackuptool ***and/or an image of the disk or partition with ***Clonezilla*** according to previous posts in this thread.

That should be much more reliable than to build your own backup system from basic tools.

---

### Post by Ms. Daisy on 2011-11-23
> **sudodus said:**
> Now that I know you have a USB hard drive with plenty of room I suggest that you make a backup with ***mintbackuptool ***and/or an image of the disk or partition with ***Clonezilla*** according to previous posts in this thread.

That should be much more reliable than to build your own backup system from basic tools.I'm chiming in because I've got similar issues as the OP. I also failed to successfully backup using Grsync onto a USB stick.   It looks as though neither clonezilla nor mintbackuptool are available in the Ubuntu Software Center, correct? Are there no similar, new-user-type backup Ubuntu programs available in the software center? Is Grsync as non-geek as it gets?

---

### Post by Jacobonbuntu on 2011-11-23
> **Ms. Daisy said:**
> I'm chiming in because I've got similar issues as the OP. I also failed to successfully backup using Grsync onto a USB stick.   It looks as though neither clonezilla nor mintbackuptool are available in the Ubuntu Software Center, correct? Are there no similar, new-user-type backup Ubuntu programs available in the software center? Is Grsync as non-geek as it gets?

I do believe this thread is getting unnecessarily complicated....
If your stick is in FAT format, you can choose "Windows compatibility"

....there are indeed two tools that make (cron-) scheduled backups with rsync really a lot easier for non geeks (like me :smile:)

- Grsync
- Gnome schedule


[LIST]
[*]create your backups with the graphical interface of Grsync, run  it once for a test-drive if it works, copy the output (command) of the  backup (at the top of the output list)
[*]open gnome-schedule (GUI) and paste the output, set a schedule in the (easy) interface and voila!
[*]take care that you put directory names with spaces between ""
[/LIST]
if you want you can also make a quicklist of your backupscripts in the Unity launcher, no separate script-files needed :smile:

---

### Post by nickdc on 2011-11-23
Thank you for chiming in Ms Daisy; it's always good to know you're not the only one.

Thanks for your comments, Jacobonbuntu. With respect, perhaps the thread wouldn't have got so complicated if respondees had read my questions with more care and responded to them more exactly. Re your first bullet point: I **want** to use Grsync; I've **tried** using it and not succeeded, as posted above. I'm still waiting for some kind person to explain how I input a destination on a remote desktop which has been mounted, as asked above. Alternatively, how to use it to back up to a WD passport drive which was used on a Windows machine and still contains important data from that machine.

---

### Post by Jacobonbuntu on 2011-11-23
> **nickdc said:**
> Thank you for chiming in Ms Daisy; it's always good to know you're not the only one.

Thanks for your comments, Jacobonbuntu. With respect, perhaps the thread wouldn't have got so complicated if respondees had read my questions with more care and responded to them more exactly. Re your first bullet point: I **want** to use Grsync; I've **tried** using it and not succeeded, as posted above. I'm still waiting for some kind person to explain how I input a destination on a remote desktop which has been mounted, as asked above. Alternatively, how to use it to back up to a WD passport drive which was used on a Windows machine and still contains important data from that machine.

I see, excuse me, indeed I didn't reed the whole thread, nor your first post too well :oops:. forgive me for asking, but if the remote desktop (share?) is mounted, can you not choose its directory in grsync? if not, how is it mounted?

edit; once more I see I didn't reed the whole thread too well.....
my question is (can't get the picture right) is the WD drive connected to the remote machine or the actual computer you want to make backups from? There is no need to format I believe, Ubuntu works well with ntfs too

---

### Post by Jacobonbuntu on 2011-11-23
forget my reply (-s) earlier.
you are very right I did not read your original post well, but reading well does not make it very clear :). As undefined the question is (why use rsync for a one time copy?), as messy the (combination of) answers so far. 

I now understand it is not a question how to set up a backup system, but just a one time backup to move your documents. In that case the Clonezilla suggestion will be the most usefull suggestion so far. However, it is not a good idea to transfer *all* settings files to your new installation. The question is: where do you keep your documents, do you have notes to keep (gnote or something), your email (do you use Thunderbird?) etc.
a lot of these documents are in invisible directories (starting with a .)
if you are still interested, let us know :)

---

### Post by nickdc on 2011-11-23
Hi, thanks for persevering with me!

The WD drive is attached to the laptop I'm trying to back up. I've actually just completed copying the laptop's Home folder to the WD drive using Grsync. I'm pretty sure everything important has copied across ok, but it did report errors, with code 23. Files to do with yobu (???) were in red.

Re the remote attempt, there's very little guidance in the Grsync docs, simply:
"Backup over a  network is possible, preferably the user should mount the network share  to be backed up to prior to launching the program. The share would then  be listed in the Browse GUI and could easily be added."
So, before launching Grsync, I mounted the remote machine using "Connect to server..." on the Places menu (I think that's where it was - I'm back on Xfce at the moment, and that doesn't have the "connect to server" option). An icon for the remote computer appeared on my desktop and I was able to browse the folders in its Home directory and find the folder I had previously created: "Laptop backup". I then started up Grsync from the System menu and browsed to the Laptop Home folder for the "Source" field. I then clicked on the "Browse" button beside the "Destination" field, and the file system browser opened up, but it showed no sign of the remote computer. I could find nothing clickable that would switch me to anywhere beyond the local machine. I tried entering a path at the top (though not very sure how to do that properly) but nothing happened when I clicked "enter". That's when I came back for a follow-up post.

PS I can't experiment anymore tonight with the remote, as my daughter's now sleeping in that room!
This is the 3rd day I've spent on this - just *preparing* for a re-install!

---

### Post by nickdc on 2011-11-23
Jacobonbuntu, thanks again, our two posts must have crossed. 

I decided to use rsync for two main reasons: 1. because I've come across many references to it since I've been learning about Ubuntu and have formed the impression it's very powerful, versatile and reliable, so it made sense to get familiar with it; 2) many of the other suggestions I read about (and recommended by posters to this thread) didn't inspire confidence or threw up further difficulties when I tried them (eg mintbackup tool not installing). I must admit I haven't tried Clonezilla, but as you say, it's a bit overkill for what I want right now. You hit the nail on the head when you say "However, it is not a good idea to transfer *all* settings files to your new installation." That's exactly what I suspected when I made my original post: I asked advice about what to exclude, because I haven't a clue which hidden files might be really useful to pull back over to the new installation and which ones could cause problems. To answer your final questions, I have just one folder in my Home folder: "Nick". No-one else uses this laptop. Everything is in that folder - it's the only one I can open or write to. I have an old copy of Evolution on there; I haven't used it for ages but don't want to wipe it just in case; for email I use Zimbra desktop. I also have RedNotebook. Other than that it's the usual multimedia stuff and documents, letters, spreadsheets etc.

Sorry, I'm a slow typist. By now you may have responded to my previous post!

Calling it a day now. Will probably try the fresh install tomorrow anyway, and hope for the best from what's on the WD drive!

---

### Post by mastablasta on 2011-11-24
why i would not recomend clonezilla to newbies is their interface is horrible. just horrible. i am sure the whole thing is powerfull as it can clone simultaniously on many mashcines. however the interface uses modules to load. means if you select the wrong setting in the wizzard you need to start over from beginning. and let's not mention all the warning about how "the end of the world" might happen if you click forward with wrong settings. it just puts me off. lets say oyu dont' know anythign about computers - those warnings mean as much as "blah, blah, bla.... WARNING all data might be lost".
 
that is why i suggest:
using this Redo Backup: [http://redobackup.org/](http://redobackup.org/) -- it basically uses same tools as clonezilla with much more user friendly interface
edit i just see Redo also does network based backup.
 
Or if you feel it should be a little more complicated interface you can use this Kleo Bare Metal Backup: [http://www.carroll.net/index.php/downloads-kleo](http://www.carroll.net/index.php/downloads-kleo)
 
Comes with a nice manual, is used in businesses and is also Ubuntu based.
 
Both of these two solve the file permisison problems. ofcourse Clonezilla also works, but not user friendly. and no one can convince me otherwise, as even their team sort of admits that.
 
if you do from computer and for linux backups Linux mintbackup tool is as simple as it gets. they use it for upgrades which are in LinuxMint done with a fresh install. will also take care of hidden files. works on Ubuntu as well.

---

### Post by Jacobonbuntu on 2011-11-24
> **nickdc said:**
> 
Calling it a day now. Will probably try the fresh install tomorrow anyway, and hope for the best from what's on the WD drive!

Hi Nick,

I did call it a day as well last night :)
I have to run now, I will get back to it later.
I believe we should not mix the network-backup problem with the re-install questions, but a few things: Xubuntu misses the network icon by default because of a mistake in the installer (some back end stuff, will get back to it later), you have to install it manually. 
The remote computer you are trying to backup to is dual boot as you mentioned before; does it run XP or Ubuntu?

---

### Post by nickdc on 2011-11-24
Hi Jacobonbuntu,

Thanks for your support, I really appreciate it. I agree about separating the two issues. I was wondering last night about posting a separate thread specifically on remote backup using Grsync. Might still do that. Yes, the desktop computer is dual-boot and 99% of the time I'm running Ubuntu. Rarely fire up XP these days. It's an old, slow machine, which is why I thought it would be fine as a repository for a temporary backup.

One other point I should have made more clearly (getting tired last night) re Clonezilla et al: the whole reason I'm doing a fresh install is that I'm getting two main problems on this laptop, which may or may not be related. One is that every update produces an error message, which seems to be to do with depmod (whatever that is) not running. Everything still works, but ... The other, more irritating problem, is that a few months ago the laptop suddenly began hanging when loading a program or file, certain things in particular, where before it had handled everything effortlessly. Researching both these issues led me to the conclusion I'd best do a clean install of the latest version, rather than keep udating/upgrading the existing install. Hence my original post: the last thing I want to do after a fresh install is to restore any bugs or glitches in the present one, so any clone or image of the whole partition is the opposite of what I need. But I don't want to have to start again from scratch, hence my original post: which files in my Home folder are likely to be safe to copy back and will get me back where I was, and which ones might possibly bring back the problems? Maybe there's no simple answer once you know more about it, but it seems such an obvious issue that I was surprised how little advice there is. Most of the stuff I've read is along the lines of: "Oh just copy what you like. It doesn't really matter much with Linux." I came across one post when I was researching depmod, which did give more specific advice, mentioning particular folders and files that might be worth conserving, but stupidly I didn't bookmark it at the time and I've not been able to find it again. I thought my OP would bring somethinmg similar in no time, and was surprised how it has actually developed!

---

### Post by sudodus on 2011-11-24
This thread describes moving from one distro to another
[COLOR=RoyalBlue][http://ubuntuforums.org/showthread.php?t=1881926](http://ubuntuforums.org/showthread.php?t=1881926)[/COLOR]
Oldfreds post is very good.
--
But it might be a good idea to make a fresh install and after that install whatever software you need. You can install software when you need it. Don't be surprised to find that after  six months you'll have quite a different set of software.

So maybe the best for you is to save
- personal files (documents, photos, videos)
- email files (if stored in the computer)
- internet links (save a book-mark file)
and wipe the rest. Then no old dependencies or problems can migrate to your new environment.

Good luck!

---

### Post by nickdc on 2011-11-24
Thank you, sudodus, clear and to the point. I think that's what I'll do. I did look at that thread when you first posted it, especially Oldfred's bit, and booked it for future reference. Right now, I want to keep it as straightforward as possible.

---

### Post by mastablasta on 2011-11-24
then use Mintbackuptool. it will save your personal data files and settings and also which programmes you used, but will leave out the possibly faulty system in the backbackup. 
 
the way you then restore it is that you can first only restore your files and see if you actually need settings to be restored or perhaps you can realtively quickly set them up again (new versions of porgrammes might have different config files). but the major point here is that if you had a bad upgrade it will not be backed up here in this case :-)
 
i used it to "upgrade" to 10.10 Kubuntu. i realised that it was faster to set it up again (email accounts and all) and use only the data files from the backup. Becuase new Linux version as mentioned has new programmes that might have different settings or not. 
 
but not all are so different and new. for example i still restored Wine settings from Mintbackup file so i didn't have to set up Dibalo2 again.
 
oh and i backed it all up via SAMBA network to a WinXP mashine.
 
Mintbackup tool was created exactly for the pupose you need it for. to easilly move from old to a new fresh install.
 
edit: here is the tutorial: [http://community.linuxmint.com/tutorial/view/2](http://community.linuxmint.com/tutorial/view/2)
here is the PPA: [https://launchpad.net/~webupd8team/+archive/mintbackup](https://launchpad.net/~webupd8team/+archive/mintbackup) 
 
though i can't see one for latest version i guess they would still be compatible.
 
You could also try DejaDup. It does something similar.

---

### Post by Jacobonbuntu on 2011-11-24
> **nickdc said:**
> Hi Jacobonbuntu,

Thanks for your support, I really appreciate it. I agree about separating the two issues. I was wondering last night about posting a separate thread specifically on remote backup using Grsync. Might still do that. Yes, the desktop computer is dual-boot and 99% of the time I'm running Ubuntu. Rarely fire up XP these days. It's an old, slow machine, which is why I thought it would be fine as a repository for a temporary backup.

One other point I should have made more clearly (getting tired last night) re Clonezilla et al: the whole reason I'm doing a fresh install is that I'm getting two main problems on this laptop, which may or may not be related. One is that every update produces an error message, which seems to be to do with depmod (whatever that is) not running. Everything still works, but ... The other, more irritating problem, is that a few months ago the laptop suddenly began hanging when loading a program or file, certain things in particular, where before it had handled everything effortlessly. Researching both these issues led me to the conclusion I'd best do a clean install of the latest version, rather than keep udating/upgrading the existing install. Hence my original post: the last thing I want to do after a fresh install is to restore any bugs or glitches in the present one, so any clone or image of the whole partition is the opposite of what I need. But I don't want to have to start again from scratch, hence my original post: which files in my Home folder are likely to be safe to copy back and will get me back where I was, and which ones might possibly bring back the problems? Maybe there's no simple answer once you know more about it, but it seems such an obvious issue that I was surprised how little advice there is. Most of the stuff I've read is along the lines of: "Oh just copy what you like. It doesn't really matter much with Linux." I came across one post when I was researching depmod, which did give more specific advice, mentioning particular folders and files that might be worth conserving, but stupidly I didn't bookmark it at the time and I've not been able to find it again. I thought my OP would bring somethinmg similar in no time, and was surprised how it has actually developed!

Hi Nick,
I think like sudodus said, most documents of productivity, including mail, notes etc are the ones to keep. Settings files can be problematic. That is the reason why upgrading often gives problems. Most of your files will be in your personal folder. Many of them, especially the "supporting" applications , like email, notes etc., will be in folders with the same name as the application, but preceded with a dot. Thunderbird for example keeps its files in .Thunderbird; invisible by default, but press ctrl+h to make it visible. Paste the directory in your new personal folder and all mail and (mail-)settings will be as it was.

In a fresh install of Xubuntu, the gvfs backends are missing, that's why you don't have a network icon :).
Furthermore I do believe you will need a good backup system once you have settled down in your new "home" :)

---

### Post by nickdc on 2011-11-25
Hi all - I've finally got there, back up and running with a fresh install, most stuff back as before and so far only one minor casualty of a broken background image. So thanks for all the help. Guess I was making a mountain out of a molehill - but then that's often how you learn more stuff. 

PS Had a very smooth install of Lubuntu, but immediately didn't like it - hadn't realised it used a completely different suite of software, and no Ubuntu Software Centre a click away. So I downloaded Ubuntu 11.10 and here I am. Pity, because Lubuntu would probably run better than full Ubuntu on this little laptop. Still, the gremlins seem to have disappeared for now, so thanks again for all the help. I shall now start full backup strategy planning!:D

---

### Post by nothingspecial on 2011-11-25
You can install any software available for Ubuntu in Lubuntu eg Firefox or libre office.

Lubuntu uses the synaptic package manager but work is being done on a lubuntu software centre which is installable but still a work in progress.

---

### Post by nickdc on 2011-11-25
Thanks, yes, I realised that and had a go at getting Firefox with the SPM, but in no time I was faffing around not really knowing what to do. With Ubuntu now, I'm back in familiar territory, which suits me for the time being.

---

### Post by Jacobonbuntu on 2011-11-25
Hi Nick,

finally (maybe you know this already), here:
[https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html)
is a pretty perfect and straightforward instruction (4 easy steps :)) how to set up a samba share on the remote computer to make automatic backups. To do so, you should make the share automount, but that is another story...

---

### Post by nickdc on 2011-11-29
Thanks, Jocobonbuntu. That's a useful link. Cheers!

---

