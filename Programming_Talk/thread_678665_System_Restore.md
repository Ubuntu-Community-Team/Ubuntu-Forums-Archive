---
title: "System Restore"
date: 2008-01-26
forum: Programming Talk
---

### Post by LaRoza on 2008-01-26
sysres has obtained its original goal. It now has all the features and a .deb installer, plus an icon and menu entry.

For the code, see [https://launchpad.net/sysres](https://launchpad.net/sysres)

For the .deb, you can get 1.0 here: [https://launchpad.net/sysres/trunk/1.0](https://launchpad.net/sysres/trunk/1.0)

The future holds uncertainity, and we hope to enhance it without any feature creep.

---

### Post by popch on 2008-01-26
While working on a slightly similar project I came to the conclusion that a very robust and simple way to do that consists of taking a snapshot of everything in certain places and just offering to restore each item as it was just after installing. This would encompass places like /etc, home, and so on.

This is based on the observation that it is easier to detect 'places' (directories) which hold things worth restoring than to enumerate which things you would actually need.

---

### Post by LaRoza on 2008-01-26
> **popch said:**
> While working on a slightly similar project I came to the conclusion that a very robust and simple way to do that consists of taking a snapshot of everything in certain places and just offering to restore each item as it was just after installing. This would encompass places like /etc, home, and so on.

This is based on the observation that it is easier to detect 'places' (directories) which hold things worth restoring than to enumerate which things you would actually need.

My goal is to have a simple windows with options to backup local settings, grub settings, video settings and perhaps others. It is simple to make, but I am looking for specific files or settings to backup. 

I want it to work on working systems, and be able to have more than one restore point to roll back to. This is rather simple, of course.

I'll stick to the settings I listed until I get it working. (Just started it, and it is 0546, and I haven't slept yet, so it is still an infant idea). I have it creating restore points for GNOME at the moment. Just need to be able to restore from them. (A reverse of the creating the restore point)

---

### Post by popch on 2008-01-26
Looking at individual things worth saving and restoring, those come to mind:

LAN and most especially WLAN settings
Desktop effect settings
Access settings for the SAMBA client
User account data
Bookmarks
Cookies
Mail account settings
ISP related settings for accessing the internet

Once you start thinking along those lines you can hardly stop any more, I fear. Where do you draw the line between 'settings' and 'data'?

---

### Post by LaRoza on 2008-01-26
> **popch said:**
> Looking at individual things worth saving and restoring, those come to mind:

LAN and most especially WLAN settings
Desktop effect settings
Access settings for the SAMBA client
User account data
Bookmarks
Cookies
Mail account settings
ISP related settings for accessing the internet

Once you start thinking along those lines you can hardly stop any more, I fear. Where do you draw the line between 'settings' and 'data'?

I am making a system restore program, not a backup program.

I am sticking with settings for the system, not applications (except GNOME). Tarring up the home directory is not my goal (simpler, but not my goal).

I think I am going to stick with what I listed and perhaps the network settings. Thanks for the suggestions.

---

### Post by popch on 2008-01-26
> **LaRoza said:**
> I am making a system restore program, not a backup program..

I do not quite understand the objectives, then. Just out of curiosity: Where do the settings come from which you intend to restore? The original out-of-the-box settings?

---

### Post by LaRoza on 2008-01-26
> **popch said:**
> I do not quite understand the objectives, then. Just out of curiosity: Where do the settings come from which you intend to restore? The original out-of-the-box settings?

Windows System Restore is the basis for this.

The settings are whatever the user decides save.

One could to the original settings, but this could be used to snapshot the system when it is working.

Basically, when one adds new hardware (such as a video card) and then reconfigures xorg (sudo dpkg-reconfigure -phigh xserver-xorg) they should make a backup, or when editing fstab, etc. This does everything in one step.

It is meant to abstract the configuration. It is for those used to Windows (if I get it working) 

The motivations for this:

* Boredom. I haven't slept at all this night (the sun will be rising in an hour or two) and have nothing to do
* Practice. Need to program *something*
* Mildly useful. I see system restore posts on occasion like [http://ubuntuforums.org/showthread.php?t=418309](http://ubuntuforums.org/showthread.php?t=418309)
* Why not? I have nothing else to do. (Except writing my book, which I am in no hurry to finish)

---

### Post by popch on 2008-01-26
Ah, now I understand.

Good luck, then, and have fun.

Douglas Adams used to take baths for hours when he was in no particular hurry to finish his books. Writing computer programs in that kind of situation is definitely a new one for me. Good luck, there too.

---

### Post by LaRoza on 2008-01-26
> **popch said:**
> Ah, now I understand.

Good luck, then, and have fun.

Douglas Adams used to take baths for hours when he was in no particular hurry to finish his books. Writing computer programs in that kind of situation is definitely a new one for me. Good luck, there too.

Douglas Adams, one of my favourite writers :)

I have no publishing company (fortunately or unfortunately) with deadlines for me.

I always code to relax. The book's subject is a bit depressing, to write at least, so I don't want to immerse myself in it.

---

### Post by stevescripts on 2008-01-26
LaRoza 

Sounds like (yet another) worthwhile effort. Keep up the good work!

Steve

---

### Post by LaRoza on 2008-01-26
> **stevescripts said:**
> LaRoza 

Sounds like (yet another) worthwhile effort. Keep up the good work!

Steve

I hope to make it useful.

I am making it have two modes, one for root, and one for user. Adding GUI after, trying to get a good design. This time, I am going to think it through a bit, and not use the development method I normally use.

(Still haven't gone to bed....)

---

### Post by pro003 on 2008-01-26
Well good like with that!

I was seeking all day long for a linux/ubuntu sowtware which could be used to restore my system on ubuntu gutsy and there wasn't anything like that on internet, of course excluding backup programs but that's only backup, as you've mentioned before. 

Although, there was a guide for making a system backup and restore using a command shell, you might want to take a look at it...


[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)


Cheers

---

### Post by LaRoza on 2008-01-26
That command is overkill.

The restore files that my program makes are small, less than 5 kb at the moment.

I am attempting to mimic the Windows System Restore.

If you have had to or wanted to Restore you system, what settings caused the issue? (So I can make sure my app addresses that issue)

---

### Post by bschleusner on 2008-01-26
apt-get sources would be nice...

---

### Post by LaRoza on 2008-01-26
> **bschleusner said:**
> apt-get sources would be nice...

Ok :)

Added it now.

---

### Post by LaRoza on 2008-01-26
The development so far:

Most of the basics are down, except, the ability to actually restore. I am saving that for a VM, because it will have to overwrite files I'd rather keep and don't want to test it with. The creation of restore points is easy and functional, and the ability to create two different types of restore points, and choice to restore from them and view and select restore points is working.

The next thing is the GUI.

I want it to work easily on Ubuntu, so I am going towards Tkinter (don't flame), and might just use EasyGUI for now, if it has one feature I want.

It generates a list of restore points that are found, and I want to make them selectable. A bullet list would be ideal. Is there an simple way to make a widget that allows a user to select from a list? Hopefully, a pre built solution. I don't like making GUI's, because they are boring, and I actually like command line input and output.

---

### Post by rabbit73 on 2008-01-26
I just turned up this post after a search on  "system restore ". I was looking for just such an app since I finished reinstalling everything about an hour ago. I totally hosed my system attempting to install cairo dock and couldn't reconfigure xserver. I just manually copied the fstab and xorg files to my home folder (different partition) with .safe extensions. A utility with a one keystroke solution and multiple restore points would have helped immensely. Good luck with it!

---

### Post by LaRoza on 2008-01-26
> **rabbit73 said:**
> I just turned up this post after a search on  "system restore ". I was looking for just such an app since I finished reinstalling everything about an hour ago. I totally hosed my system attempting to install cairo dock and couldn't reconfigure xserver. I just manually copied the fstab and xorg files to my home folder (different partition) with .safe extensions. A utility with a one keystroke solution and multiple restore points would have helped immensely. Good luck with it!

It is almost operational, not bad for one day (night) and accidently deleting my source file...

I see all that you listed is already part of it, I am going to add support for KDE and Xubuntu as well, easy to do. I just need to find out the all the configuration directories to use.

---

### Post by LaRoza on 2008-01-30
Updates:

* It is pretty functional, except for actually restoring.
* I am adding a GUI to most of it, unfortunately, my design requires it to be modified, so it is half GUI and half CLI

It will need people to test it soon, any takers? The biggest flaw will be the UI, I am no expert in such designs and rather dislike coding GUI's, so it is a clunky design. If anyone would want to make it pretty after looking at, go ahead. The one requirement is that it uses Tkinter.

---

### Post by xlinuks on 2008-01-30
I like creating GUIs, but I can only create them in Java.. as far as I understand you use Python.
I find your idea very interesting (and useful), and I guess you're right that we need a restore program rather than a backup one (which would require way too much space to be efficient)
I would like it to restore (in a user friendly way) at least these:
1) /etc/fstab
2) /etc/X11/xorg.conf
3) the Gnome settings from my HOME directory (file associations, etc)

---

### Post by LaRoza on 2008-01-30
> **xlinuks said:**
> I like creating GUIs, but I can only create them in Java.. as far as I understand you use Python.
I find your idea very interesting (and useful), and I guess you're right that we need a restore program rather than a backup one (which would require way too much space to be efficient)
I would like it to restore (in a user friendly way) at least these:
1) /etc/fstab
2) /etc/X11/xorg.conf
3) the Gnome settings from my HOME directory (file associations, etc)

I use many languages, for this, I am using Python and Tkinter.

Those are already part of it :) Glad I know I knew what to include.

---

### Post by seventhc on 2008-01-30
> **LaRoza said:**
> Updates:

It will need people to test it soon, any takers?
I can give it a test. :)

---

### Post by LaRoza on 2008-01-30
> **seventhc said:**
> I can give it a test. :)

Thanks.

It will require hosing your system with no backups for it to be a true test though.

Just kidding, no one has to do anything during the testing they don't want to. The creation of restore points is entirely safe, unless you have a file named the same as the system restore files do which is unlikely, because they have a funny name, a custom section and the date in their title.

---

### Post by seventhc on 2008-01-30
I can hose this system, nothing on it, so at most if the restore fails I'll just reinstall it.
anything that is important is already saved externally, so no worries.

edit..
would this be something like...create a resore point, maybe install some stuff, then try to restore it to before the install??

---

### Post by LaRoza on 2008-01-30
> **seventhc said:**
> I can hose this system, nothing on it, so at most if the restore fails I'll just reinstall it.
anything that is important is already saved externally, so no worries.

edit..
would this be something like...create a resore point, maybe install some stuff, then try to restore it to before the install??

Perhaps it could, it won't do a few system rollback, only settings.

If one manages to bork their xorg.conf, menu.lst, or their gnome settings, this could restore it.

It basically mimics the Windows System Restore (which just backups the registry) and saves system settings.

---

### Post by seventhc on 2008-01-30
>  If one manages to bork their xorg.conf, menu.lst, or their gnome settings

Ok, I think I can manage that. ;)

---

### Post by popch on 2008-01-30
Wouldn't it be useful for testing purposes if the application had a separate option 'bork system' with sub-options offering to bork specific parts?

---

### Post by LaRoza on 2008-01-30
> **popch said:**
> Wouldn't it be useful for testing purposes if the application had a separate option 'bork system' with sub-options offering to bork specific parts?

I wouldn't want to write any destructive code (those Windows scripts didn't count).

Right now, I haven't written the code to restore, just everything up to that with just a message saying it isn't done.

I also ran into GUI problems, and I have to fix that. Of course, if anyone wants to test the CLI code I will give that to. The code for the core of it is separate from the use of it.

---

### Post by popch on 2008-01-30
> **LaRoza said:**
> I wouldn't want to write any destructive code 

I understand your consideration but think it would be less dangerous to run some carefully designed and selectively destructive script than to rely on the people testing the restore to reliably damage the proper parts of their system.

It would not be a perfectly complete test accounting for all imaginable situations. Still it would reliably test the basic functionality.

Besides, intentionally borking the system with carefully designed code can do it in a way which is recoverable, while manually doing so might leave your system in an unpredictable state.

---

### Post by LaRoza on 2008-01-30
> **popch said:**
> I understand your consideration but think it would be less dangerous to run some carefully designed and selectively destructive script than to rely on the people testing the restore to reliably damage the proper parts of their system.

It would not be a perfectly complete test accounting for all imaginable situations. Still it would reliably test the basic functionality.

Besides, intentionally borking the system with carefully designed code can do it in a way which is recoverable, while manually doing so might leave your system in an unpredictable state.

Perhaps just renaming the files in question, or changing your theme would be more suitable for testing. Then, for serious work, I'd use a VM.

This is meant to restore still working, if damaged systems. 

Perhaps a rename script would be in order, which can undo everything easily. (It would effectively backup the files too)

---

### Post by seventhc on 2008-01-30
Well, instead of writing destructive code, maybe put a file in there with some suggestions of what to bork or how you want it borked etc. This way you aren't writing malicious code, but still getting to test it in the environment that would be more geared towards the end result.

---

### Post by LaRoza on 2008-01-30
> **seventhc said:**
> Well, instead of writing destructive code, maybe put a file in there with some suggestions of what to bork or how you want it borked etc. This way you aren't writing malicious code, but still getting to test it in the environment that would be more geared towards the end result.

The function of the script is simple and easy to verify. The UI is what concerns me.

The biggest unknown to me is how to restore, as I never had to do what it is going to do. It is a simple procedure, but one I'd rather test. It wouldn't be good if /etc/fstab was restored, but everything else in /etc was deleted in the process.

---

### Post by xlinuks on 2008-01-30
Well, for instance if we take /etc/fstab:
I guess for now it would be good if we just overwrite the file with the backed-up one.
But later, I think, there should be some code that would actually check what volumes the user has on his computer and based on this info create on the fly a new fstab file to replace the old one. The reason I'm saying this is cause I lost a partition using GParted (it unmounted it but I couldn't find a way to mount it back, a bug in GParted I guess), so after reboot Gutsy threw me to a root console to "repair the filesystem". That's why IMO a simple restore of the backed up file wouldn't be a complete feature. The (your) app should scan (correctly) for volumes (such as /dev/sda3, /dev/sda4 ), at least starting at some future release..
It should not include (into the /etc/fstab) the volumes that are removable drives - which IMO is pretty hard to implement if one doesn't have experience in such domains (thus I mean programmers like me)
Just my 0.02$

---

### Post by LaRoza on 2008-01-30
> **xlinuks said:**
> Well, for instance if we take /etc/fstab:
I guess for now it would be good if we just overwrite the file with the backed-up one.
But later, I think, there should be some code that would actually check what volumes the user has on his computer and based on this info create on the fly a new fstab file to replace the old one. The reason I'm saying this is cause I lost a partition using GParted (it unmounted it but I couldn't find a way to mount it back, a bug in GParted I guess), so after reboot Gutsy threw me to a root console to "repair the filesystem". That's why IMO a simple restore of the backed up file wouldn't be a complete feature. The (your) app should scan (correctly) for volumes (such as /dev/sda3, /dev/sda4 ), at least starting at some future release..
It should not include (into the /etc/fstab) the volumes that are removable drives - which IMO is pretty hard to implement if one doesn't have experience in such domains (thus I mean programmers like me)
Just my 0.02$

I think you have to understand the program design for this.

It restores to a previous state, it doesn't fix anything.

It is solely meant to undo system changes, not fix or diagnose them.

---

### Post by Cappy on 2008-01-30
The biggest problem with it is that if someone messes up the system config they probably aren't going to be able to use this program if it is a self run shell script, hard-to-find application, or not automatically backing things up already.

My opinion is that either
A) Upon encountering a problem with one of the backed up files this script replaces the broken file. This is done in the background. The user is informed that the settings were replaced because they were corrupt. 
B) Upon encountering a problem the user can boot up an ubuntu CD. The program can be run off the Live CD and you can choose to restore the state of the newest modified files on the hard drive (or any media obviously). This would require the script making it onto the Ubuntu CD or the Ubuntu repos.

These are both assuming worst case where a normal user cannot boot into X .. possibly due to broken X or driver settings. Possibly a kernel upgrade problem. These are probably the kind of situations people would benefit from a backup system the most.

Making the "restore" function work easily when things are broken is going to be a big challenge.

---

### Post by LaRoza on 2008-01-30
> **Cappy said:**
> The biggest problem with it is that if someone messes up the system config they probably aren't going to be able to use this program anyway.

My opinion is that either
A) Upon encountering a problem with one of the backed up files this script replaces the broken file. This is done in the background. The user is informed that the settings were replaced because they were corrupt.
B) Upon encountering a problem the user can boot up an ubuntu CD. The program can be run off the Live CD and you can choose to restore the state of the newest modified files on the hard drive (or any media obviously). This would require the script making it onto the Ubuntu CD or the Ubuntu repos.

Making the "restore" function work easily when things are broken is going to be the biggest challenge.

Actually, this agonized me. The problem:

* I can only assume the system has a home directory
* I must store the restore points somewhere
* If something hoses the home, the restore points will be gone to.

It is perfectly functional from any media, including Live CD's, so far. If nothing else, it creates a backup of the settings which any user can manually put back.

Now that you bring it up, it is a good thing to consider when impementing the restore feature (which isn't done yet), because I have to take into account this script might be running from a different user/system/cd.

Because I am restricting it to standard Python modules (now my decision to use Tkinter makes sense), and it is not complex and runs fine from anywhere on my system.

Of course, if someone had made restore points, they don't need to use my program to restore from them. If they are savvy enough to run a program off a live cd to fix a system, they probably understand that it is simple to untar the restore points.

My main focus is on new users:

* I just tried to install <weird package> and now everything looks funny
* I tried editing my fstab (what is it anyway?) and now I can't see my Windows partition
* I tried a new video card, and I don't like it, and when I removed it, everything looks big

and other configuration issues that are easily solved by making backups and knowing what you are doing.

---

### Post by cprofitt on 2008-01-30
> **LaRoza said:**
> I am making a system restore program, not a backup program.

I am sticking with settings for the system, not applications (except GNOME). Tarring up the home directory is not my goal (simpler, but not my goal).

I think I am going to stick with what I listed and perhaps the network settings. Thanks for the suggestions.

Remember that you can take an inventory of installed packages with Synaptic that can be imported in Synaptic to re-install them as well... not sure if that is something you would want, but it would be appreciated by many I think.

---

### Post by LaRoza on 2008-01-30
> **PrivateVoid said:**
> Remember that you can take an inventory of installed packages with Synaptic that can be imported in Synaptic to re-install them as well... not sure if that is something you would want, but it would be appreciated by many I think.

Could you explain that? I know one can get all the packages installed with a command (forget it though) is there a a file to parse?

Once I get this to work (GUI issues and restore not finished now), I will be very open to adding to it and probably have a little page for it somewhere.

---

### Post by mssever on 2008-01-31
I have to mention that I haven't read the entire thread. I hope I'm not being redundant.

I have a couple thoughts about this program. First, I think that it's a great idea. Back when I used Windows, System Restore was a lifesaver. (Personally, I find Windows easier to hose accidentally than Linux, but maybe that's just me.)

I would like the ability to manually specify files to be included in the restore. Some use cases:[LIST=1]
[*]On my server, I have Apache's configuration heavily customized, so losing that customization would be more painful than losing fstab. Of course, this is approaching the goals of a backup program.
[*]Suppose I want to experiment with some major reconfiguration of my machine that is too extensive to rely on my ability to remember everything I changed. The ability to simply add that stuff to my restore data set would give me the freedom to explore without worrying about losing important configuration if I mess up.[/LIST]Another thing: Have you considered making a text-based version, as well? I imagine that one common use case would be someone who hosed X. They'd likely end up booting into single-user mode, and wouldn't be able to access a GUI program. But they'd benefit from curses. Presumably, if you try to create a Tkinter window when you're not running X, you'll get an exception. You could then catch that exception and launch the curses interface. (I guess you're dead set on Tkinter. I'm pretty much dead set against it because it's terribly ugly and its menus are broken. I'd much prefer GTK. But, it's your program, not mine.)

Finally, will this program automatically create restore points every so often like the Windows program does?

---

### Post by seventhc on 2008-01-31
IMO Tkinter will work on everyones machine, once you use anything different, then it might no longer work out of the box. Of course I may be completely wrong as I am new to python and programming in general.
I do however think it's a good idea for it to default to a text based version if tkinter can't start due to problems with x.
As far as looks are concerned I don't think that will concern anyone using it as most likely they will be thinking about a hosed system and wanting it back.

---

### Post by LaRoza on 2008-01-31
> **mssever said:**
> 
I have a couple thoughts about this program. First, I think that it's a great idea. Back when I used Windows, System Restore was a lifesaver. (Personally, I find Windows easier to hose accidentally than Linux, but maybe that's just me.)

I would like the ability to manually specify files to be included in the restore. Some use cases:[LIST=1]
[*]On my server, I have Apache's configuration heavily customized, so losing that customization would be more painful than losing fstab. Of course, this is approaching the goals of a backup program.
[*]Suppose I want to experiment with some major reconfiguration of my machine that is too extensive to rely on my ability to remember everything I changed. The ability to simply add that stuff to my restore data set would give me the freedom to explore without worrying about losing important configuration if I mess up.[/LIST]Another thing: Have you considered making a text-based version, as well? I imagine that one common use case would be someone who hosed X. They'd likely end up booting into single-user mode, and wouldn't be able to access a GUI program. But they'd benefit from curses. Presumably, if you try to create a Tkinter window when you're not running X, you'll get an exception. You could then catch that exception and launch the curses interface. (I guess you're dead set on Tkinter. I'm pretty much dead set against it because it's terribly ugly and its menus are broken. I'd much prefer GTK. But, it's your program, not mine.)

Finally, will this program automatically create restore points every so often like the Windows program does?

Windows uses a central registry which is a big binary file that is easy to mess with. Any body interested in creating a piece of malware should exploit the registry.

It would be easy to add a custom file or directory, I will add that soon.

I am ahead of you :) I wrote it entirely as CLI at first to get the logic down, then, in my way, I had to do a slight redesign for the GUI. I made the GUI (warning: I am not a UI expert and dislike GUI coding), and last night added the ability to use it in CLI for that very reason (no X) and the fact I still like the CLI better. It makes no sense to me to have a GUI for this, but you know how some people are.

I prefer wxWidgets, however, Tkinter comes with standard Python and I am not going to have any requirements beyond what is standard.

The way to use it in the CLI is to have a command line option. Didn't code that part yet...

You could set it to do that, however, I see no reason to. If anyone want regular backups, they can automate it themselves. Linux isn't Windows and doesn't need to have backups of its registry every minute.

Right now, my home directory is filled with restore points (funny named files) because half the time I test it, I create  a new one. I don't want to flood another users home directory. 

The restore points are going to be stored in a directory (probably hidden) soon. I haven't coded that part yet.

---

### Post by LaRoza on 2008-01-31
> **seventhc said:**
> IMO Tkinter will work on everyones machine, once you use anything different, then it might no longer work out of the box. Of course I may be completely wrong as I am new to python and programming in general.
I do however think it's a good idea for it to default to a text based version if tkinter can't start due to problems with x.
As far as looks are concerned I don't think that will concern anyone using it as most likely they will be thinking about a hosed system and wanting it back.

That is why I chose it.

It has a CLI version, that can be started on the command line.

It looks "ok", and is using the EasyGUI module. It isn't good looking, but I am, and that is what is important.

---

### Post by psychok7 on 2008-02-01
any ideia when ur super program will be ready?? i think its one of the most important features ubuntu should have, even by default. please let us know when youll get it done, the name, and the site were we can get it. oh one question. will this be the first attempt anyone has ever made for system restore on ubuntu?

---

### Post by pmasiar on 2008-02-01
> **popch said:**
> Besides, intentionally borking the system with carefully designed code can do it in a way which is recoverable, while manually doing so might leave your system in an unpredictable state.

I am not sure why you are afraid of manual borking. You know which files were backed up, right? You can even see where they are copied, right? And I hope that directory structure and filenames are same as in original system, just root directory has funny name, right?

So start up your trusted mc, find the files, and bork some file. Reboot to see system borked. Then try restore backup: if system is not unborked, unbork the file you borked manually using mc again.

Why you need to automate the "creative" part: which file to bork, and how?

---

### Post by pmasiar on 2008-02-01
> **LaRoza said:**
> It looks "ok", and is using the EasyGUI module. It isn't good looking, but I am, and that is what is important.

 :-)

Most important thing in development is to have your priorities right, and you obviously do.

---

### Post by popch on 2008-02-01
> **pmasiar said:**
> I am not sure why you are afraid of manual borking. You know which files were backed up, right? You can even see where they are copied, right? And I hope that directory structure and filenames are same as in original system, just root directory has funny name, right?

So start up your trusted mc, find the files, and bork some file. Reboot to see system borked. Then try restore backup: if system is not unborked, unbork the file you borked manually using mc again.

Why you need to automate the "creative" part: which file to bork, and how?

I suggested this because LaRoza was (still is?) looking for people who can test his program. 

Under that condition, I feel that it would be safer for the would-be testers if the program included a sort of testing suite which included the 'borking' as well. I also feel that not all would-be testers would be savvy enough to take sensible measures before testing. I can kind of imagine the dialog between LaRoza and someone who thought that the restorer could work miracles and then found out that it could not.

---

### Post by sayakb on 2008-02-01
LaRoza

Sorry, couldn't read all the posts in this thread.. Just posting what I screw up mostly..
1. I often install some or the other "wrong package" which gifts me a "broken cache" situation.. All installed packages will be restored with your program.
2. Graphics.. as you already mentioned.. I screw the X server or my desktop composite mgr..
3. GRUB.. as you said.
4. And all system settings but not files.

It would be a charm if accidentally, some system files are lost and they could be revived by your program.

If my points are redundant and they were already discussed before, please ignore.

---

### Post by pmasiar on 2008-02-01
> **LaRoza said:**
> 
My main focus is on new users:
* I just tried to install <weird package> and now everything looks funny
* I tried editing my fstab (what is it anyway?) and now I can't see my Windows partition
* I tried a new video card, and I don't like it, and when I removed it, everything looks big


Because I know you are smart hacker without formal education, let me point out for you that you just reinvented [http://en.wikipedia.org/wiki/Use_case](http://en.wikipedia.org/wiki/Use_case) - a way to gather specification and describe parameters of solution. Msserver mentioned other interesting usecases, like borked X and no GUI, noTkinter.

What you want to do is to get a wiki and flesh out usecases with enough details (and use human names for them) so you can better imagine expectation and skill level of each user, so you will develop not a script, but application. Formal CompSci education sometimes does make solving problem simpler :-)

So even if you have to reinvent the wheel, it might be hexagon or octagon, and not the usual square :-)

---

### Post by LaRoza on 2008-02-01
> **popch said:**
> I suggested this because LaRoza was (still is?) looking for people who can test his program. 



I understand. I am sort of hoping for testers that know what they are doing (and therefore don't need the program) so they can tell if it is technically useful.

> **LinuxIsInnovation said:**
> 
Sorry, couldn't read all the posts in this thread.. Just posting what I screw up mostly..
1. I often install some or the other "wrong package" which gifts me a "broken cache" situation.. All installed packages will be restored with your program.


I believe the package manager can fix that, so I am not going to reinvent the wheel, unless it is a file that can be backed up, I am not going to put it in the program (yet anyway)

---

### Post by LaRoza on 2008-02-01
> **pmasiar said:**
> Because I know you are smart hacker without formal education, let me point out for you that you just reinvented [http://en.wikipedia.org/wiki/Use_case](http://en.wikipedia.org/wiki/Use_case) - a way to gather specification and describe parameters of solution. Msserver mentioned other interesting usecases, like borked X and no GUI, noTkinter.

What you want to do is to get a wiki and flesh out usecases with enough details (and use human names for them) so you can better imagine expectation and skill level of each user, so you will develop not a script, but application. Formal CompSci education sometimes does make solving problem simpler :-)

So even if you have to reinvent the wheel, it might be hexagon or octagon, and not the usual square :-)

I have no formal education in **Computer Science or Programming**, I do have a degree (recently graduated) in Criminal Justice.

That said, yes, your advice is very good. If I weren't some person sitting in my room, and looking for a job and ordering weird things from amazon, [this is the latest]("http://www.amazon.com/Toy-Vault-Cthulhu-small-plush/dp/B0006FUAD6/ref=pd_ys_qtk_k2a?pf_rd_p=233144501&pf_rd_s=center-1&pf_rd_t=1501&pf_rd_i=home&pf_rd_m=ATVPDKIKX0DER&pf_rd_r=1EHPZP9XPW360RC35542"), and was a real programmer, I might make this a real project. If I can finish it to my satisfaction, I will probably make it available with a site/wiki of its own.

I am not going to get anyone's help on it, until I have a working application.

---

### Post by LaRoza on 2008-02-01
> **psychok7 said:**
> any ideia when ur super program will be ready?? i think its one of the most important features ubuntu should have, even by default. please let us know when youll get it done, the name, and the site were we can get it. oh one question. will this be the first attempt anyone has ever made for system restore on ubuntu?

It is sort of ready now. Of course, it doesn't restore yet, that is the last thing that needs to be done.

I don't know if it is the first, it certainly isn't hard to do.

I will let it be known when it is ready for testing.

---

### Post by sayakb on 2008-02-01
> **LaRoza said:**
> I understand. I am sort of hoping for testers that know what they are doing (and therefore don't need the program) so they can tell if it is technically useful.



I believe the package manager can fix that, so I am not going to reinvent the wheel, unless it is a file that can be backed up, I am not going to put it in the program (yet anyway)

Thats not I exactly mean.. The Windows system restore keeps a track of installed/removed programs.. when we attempt to repair a broken package, it often removes certain important packages, including ubuntu-desktop, panels etc..When we restore linux to any previous state, all the packages installed at that point would be restored back and any newly installed/removed packages will not be valid. Its your wish ofcourse what you want to include, its your own code :D

---

### Post by LaRoza on 2008-02-01
> **LinuxIsInnovation said:**
> Thats not I exactly mean.. The Windows system restore keeps a track of installed/removed programs.. when we attempt to repair a broken package, it often removes certain important packages, including ubuntu-desktop, panels etc..When we restore linux to any previous state, all the packages installed at that point would be restored back and any newly installed/removed packages will not be valid. Its your wish ofcourse what you want to include, its your own code :D

If the package manager can't fix it, I doubt I could.

I am a beginner in programming (it will be one year later this month).

Windows also doesn't have a package manager, and uses a single registry. Any time an application is installed, it makes changes to the registry (this is one reason why viruses are so easy to make, and so much fun), in Linux, the configurations are in text files.

I never had problems fixing broken packages. Could you explain the issue better? This also restores the package sources list.

---

### Post by pmasiar on 2008-02-01
> **LaRoza said:**
> I have no formal education in **Computer Science or Programming**, I do have a degree (recently graduated) in Criminal Justice.


Yes, I know, sorry for misunderstanding.

I hope you will not prosecute me, honestly I just mis-spoke.  :-)

I just wanted to show you (and others) that even in CompSci, an area where so many self-learned hackers happily prosper, formal CompSci education might be real positive.

---

### Post by LaRoza on 2008-02-01
> **pmasiar said:**
> 
I just wanted to show you (and others) that even in CompSci, an area where so many self-learned hackers happily prosper, formal CompSci education might be real positive.
Yes, learning the language syntax is easy. I now have books and references for the more important topics. I would have been nice to have a bit of education on project management, and algorithms and data structures, and others.

Looking at my code for this project, I am sure I am breaking a few rules. The number one is my total lack of comments.

---

### Post by sayakb on 2008-02-01
I dun think that it needs further highlighting :(
When we have a broken cache, each time, when trying to fix it, it removed all my necessary packages (because of broken libc6 package) and those removed packages refused to be re-installed..

---

### Post by LaRoza on 2008-02-01
> **LinuxIsInnovation said:**
> I dun think that it needs further highlighting :(
When we have a broken cache, each time, when trying to fix it, it removed all my necessary packages (because of broken libc6 package) and those removed packages refused to be re-installed..

What caused this problem?

---

### Post by mssever on 2008-02-01
> **LinuxIsInnovation said:**
> I dun think that it needs further highlighting :(
When we have a broken cache, each time, when trying to fix it, it removed all my necessary packages (because of broken libc6 package) and those removed packages refused to be re-installed..
Recovering from a broken libc6 situation is the job of the package manager--especially since it isn't a trivial situation. However, it might be nice if System Restore could store a list of currently installed packages at each restore point so the user could, after doing something that borked their installed packages, do something like ```
sudo aptitude install $(system-restore --list-packages --restore-point=foo)
```This is a very real scenario. Shortly after I started using Ubuntu and hadn't really learned my way around APT yet, I did something that caused aptitude to decide to uninstall much of KDE plus a number of other things, which I didn't notice until too late. I don't know what I did wrong, and I haven't had problems with aptitude lately--probably because I know enough now to not make whatever mistake I made earlier.
> **pmasiar said:**
> Msserver mentioned other interesting usecases,
My nick is mssever, not msse**r**ver. :) It's based on the standard username formula at my first job (first initial, middle initial, first five letters of last name), not a Microsoft server.

---

### Post by LaRoza on 2008-02-01
Could someone tell me where the currently installed packages are listed?

---

### Post by mssever on 2008-02-01
> **LaRoza said:**
> Could someone tell me where the currently installed packages are listed?

After looking around a bit, it appears that /var/lib/dpkg/status has that info. It doesn't appear to list whether a package was automatically installed, though--which would be nice info to maintain.

---

### Post by pmasiar on 2008-02-01
> **mssever said:**
> My nick is mssever, not msse**r**ver. :) It's based ... not a Microsoft server.

I apologize to associate you with evil! I was always curios: such a smart guy (or gal as might be the case) with such a nick. It is well known that people raed olny fisrt and lsat leettrs of any wrod, and any premuatatoin isnide are esay to sikp over. :-)

---

### Post by mssever on 2008-02-01
> **pmasiar said:**
> such a smart guy (or gal as might be the case)Guy
> It is well known that people raed olny fisrt and lsat leettrs of any wrod, and any premuatatoin isnide are esay to sikp over. :-)

Yes, I've had to look up how to spell your nick several times, due to omitting letters in my attempted pronunciation of it.

---

### Post by LaRoza on 2008-02-01
> **mssever said:**
> 
Yes, I've had to look up how to spell your nick several times, due to omitting letters in my attempted pronunciation of it.

People seem to mess my name up too.

(In real life, with my real name, I get the most odd spellings. They even got it wrong on my degree!)

---

### Post by LaRoza on 2008-02-02
Due to some suggestions in this thread, I have started a small GUI script for backing up and restoring packages.

It will not be part of the System Restore program, but I may add the option to run it from it.

It will make a list of installed packages, and save it to a file, and then be able to restore the system from that list.

It is not in Python, that is why it is not part of System Restore.

---

### Post by DamagePlan on 2008-02-02
This sounds neat LaRoza. What will the GUI backup script be coded in, if you don't mind me asking?

---

### Post by LaRoza on 2008-02-02
> **DamagePlan said:**
> This sounds neat LaRoza. What will the GUI backup script be coded in, if you don't mind me asking?

Bash.

It is finished, just need to do a little more testing.

---

### Post by ruy_lopez on 2008-02-03
> It is finished, just need to do a little more testing.


Sounds good. Care to share with us?

---

### Post by LaRoza on 2008-02-03
> **ruy_lopez said:**
> Sounds good. Care to share with us?

I have to run test it some more, which I am going to do in a VM. I am going to try to recreate what I expect it to fix. 

Give it a week at the most.

---

### Post by seventhc on 2008-02-24
I was curious as to the progress on this?
Any luck?

---

### Post by LaRoza on 2008-02-24
> **seventhc said:**
> I was curious as to the progress on this?
Any luck?

I actually stopped for no particular reason.

The development pretty far along, but I haven't worked on it in a while.

I will post the package restore script, as that works I think soon.

---

### Post by seventhc on 2008-02-24
Ok, thanks. :)

---

### Post by Vadi on 2008-02-24
Meanwhile, I'm using this awesome thing called TimeVault. It's somewhat similar.

---

### Post by seventhc on 2008-02-24
> **Vadi said:**
> Meanwhile, I'm using this awesome thing called TimeVault. It's somewhat similar.
That sounds interesting too, I'll be checking that out as well.
Never actually heard of it before.

---

### Post by LaRoza on 2008-08-06
Well, I submitted the project to sourceforge.net. It should be accepted/rejected within a few days. I will keep you all posted.

[https://sourceforge.net/projects/sysres/](https://sourceforge.net/projects/sysres/)

---

### Post by nvteighen on 2008-08-06
Isn't this thread necromancing, LaRoza? ;)

Seriously: good luck!

---

### Post by seventhc on 2008-08-06
> **LaRoza said:**
> Well, I submitted the project to sourceforge.net. It should be accepted/rejected within a few days. I will keep you all posted.

[https://sourceforge.net/projects/sysres/](https://sourceforge.net/projects/sysres/)
 This will be great, I hope they accept it. I can't check it now b/c permission denied. :(
Any idea on how long the approval process takes?

---

### Post by adam_kimber on 2008-08-06
> **PrivateVoid said:**
> Remember that you can take an inventory of installed packages with Synaptic that can be imported in Synaptic to re-install them as well... not sure if that is something you would want, but it would be appreciated by many I think.

I was going to suggest that instead of using synaptic you could use a dpkg command to save the current state of installed packages. Not sure if you require this in your program.

I have been working on a backup and restore script for my Ubuntu machine. I am no programmer so I have got rather stuck. I wanted to backup the main settings and my installed packages so if i needed to flatten for any reason I could get back to where i was very quickly. I can give you what I have so far (not much) if its any help. It currently backsup and restores to one state, does not do multiples.

---

### Post by LaRoza on 2008-08-06
> **nvteighen said:**
> Isn't this thread necromancing, LaRoza? ;)

Seriously: good luck!
No. It is completely on topic. Just took a while to finish (most of the time was inactivity).

> **seventhc said:**
> This will be great, I hope they accept it. I can't check it now b/c permission denied. :(
Any idea on how long the approval process takes?
1-3 days.

> **adam_kimber said:**
> I was going to suggest that instead of using synaptic you could use a dpkg command to save the current state of installed packages. Not sure if you require this in your program.

I have been working on a backup and restore script for my Ubuntu machine. I am no programmer so I have got rather stuck. I wanted to backup the main settings and my installed packages so if i needed to flatten for any reason I could get back to where i was very quickly. I can give you what I have so far (not much) if its any help. It currently backsup and restores to one state, does not do multiples.

Here is my shell script for making restore points for packages. It has a GUI, you have to have zenity for it to work.

It was originally going to be bundled with sysres, but it is separate, although it uses the same directory for restore points.
```

#!/bin/bash

#sysres: Linux system restore program.
#Copyright (C) 2008  LaRoza

#This program is free software: you can redistribute it and/or modify
#it under the terms of the GNU General Public License as published by
#the Free Software Foundation, either version 3 of the License, or
#(at your option) any later version.

#This program is distributed in the hope that it will be useful,
#but WITHOUT ANY WARRANTY; without even the implied warranty of
#MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#GNU General Public License for more details.

#You should have received a copy of the GNU General Public License
#along with this program.  If not, see <http://www.gnu.org/licenses/>.

nochange()
{
    zenity --info --text "Package Backup and Restore Halted -- No Changes Made";
    exit 0;
}

restore()
{
    if [ $UID -eq 0 ]
        then
        name=$(zenity --file-selection --text "Open file:" --filename ~/.system_restore/);

        zenity --question --text "Install all packages?";
        
        if [ $? -eq 0 ] 
        then

            if [ -f $name ]
            then
                zenity --info --text "File exists and ready";
                gksudo dpkg --set-selections < $name; dselect;
            else
                zenity --info --text "Not a file";
                nochange;
            fi

        else
            nochange;
        fi
    else
        zenity --info --text "You are not root";
        exit 0
    fi

    return;  
}
backup()
{
    saveas=$(zenity --entry --text "Save as:");
     
    if [ -e ~/.sysres/$saveas ]
    then  
        if [ -d ~/.sysres/$saveas ]
        then
            zenity --info --text "That is a directory";
            nochange;
        fi

        zenity --question --text "File exists, overwrite?";

        if [ $? -eq 0 ] 
        then
            dpkg --get-selections > ~/.sysres/$saveas;
        else
            exit;
        fi
        
    else
        dpkg --get-selections > ~/.sysres/$saveas;
    fi

    return;
}


main()
{
    ans=$(zenity  --list  --text "Package Backup and Restore" --radiolist  --column "Pick" --column "Option" TRUE "Backup" FALSE "Restore");

    if [ $? -eq 1 ]
    then
        nochange;
    else
        if [ $ans == "Backup" ] 
        then
            backup;
        elif [ $ans == "Restore" ]
        then
            restore;
        else
            nochange;
        fi
    fi
        
}

main;

```

---

### Post by adam_kimber on 2008-08-06
Fair enough! It seems to be neater and a little more GUI-rific than mine. It makes my script look silly in comparison. I will post it anyways incase it is of some remote help. 

```
 
#!/bin/bash

if [ -d $HOME/systemrestore ]
then
echo "Directory exists"
cd /$HOME/systemrestore
mkdir oldsettings
mv ubuntu-files sources.list xorg.conf sysctl.conf settings.tar.gz oldsettings/
echo "Saved old files"
sudo dpkg --get-selections > ubuntu-files
echo "Backed up installed programs"
cp /etc/apt/sources.list .
echo "Backed up Program Repos List"
cp /etc/X11/xorg.conf .
echo "Backed up display configuration"
cp /etc/sysctl.conf .
echo "Backup system settings"
tar -czf settings.tar.gz ~/.[a-z][A-Z]* --verbose --exclude="*.wmv" --exclude="*.avi" --exclude=".cache" --exclude=".beagle" --exclude=".googleearth/Cache/dbCache.dat" --exclude=".wine" --exclude=".cedega" --exclude=".thumbnails" --exclude=".winebak"
echo "Backed up user settings" 
else
mkdir $HOME/systemrestore
cd /$HOME/systemrestore
sudo dpkg --get-selections > ubuntu-files
echo "Backed up installed programs"
cp /etc/apt/sources.list .
echo "Backed up Program Repos List"
cp /etc/X11/xorg.conf .
echo "Backed up display configuration"
cp /etc/sysctl.conf .
echo "Backup system settings"
tar -czf settings.tar.gz ~/.[a-z][A-Z]* --verbose --exclude="*.wmv" --exclude="*.avi"  --exclude=".wine" --exclude=".cedega" --exclude=".thumbnails" --exclude=".winebak"
echo "Backed up user settings" 
fi

```

[Search Results]("https://sourceforge.net/search/?type_of_search=soft&type_of_search=soft&words=sysres") Does this mean that its not accepted? :(

---

### Post by LaRoza on 2008-08-06
> **adam_kimber said:**
> Fair enough! It seems to be neater and a little more GUI-rific than mine. It makes my script look silly in comparison. I will post it anyways incase it is of some remote help. 

That script isn't sysres, and only does packages.

> 
[Search Results]("https://sourceforge.net/search/?type_of_search=soft&type_of_search=soft&words=sysres") Does this mean that its not accepted? :(
It is still being processed. Barely 1 day! Give it some time. It is almost processed.

---

### Post by LaRoza on 2008-08-06
Its up!

[http://sourceforge.net/projects/sysres/](http://sourceforge.net/projects/sysres/)

---

### Post by Kadrus on 2008-08-06
I will be reading the source code in a minute,well done on finishing the project.

---

### Post by LaRoza on 2008-08-06
> **Kadrus said:**
> I will be reading the source code in a minute,well done on finishing the project.

Projects are never finished...

---

### Post by Kadrus on 2008-08-06
Well i think you got my point,projects will still be developed,imrpoved,bugs fixed,etc..

---

### Post by LaRoza on 2008-08-06
> **Kadrus said:**
> Well i think you got my point,projects will still be developed,imrpoved,bugs fixed,etc..

Yeah.

Now that it is up, I would like suggestions on its function, not the GUI! If anyone dislikes the GUI, write a better one. I'd gladly help in specs, but I won't code one.

---

### Post by Kadrus on 2008-08-06
Well as said in the read me file: > It works, but I am no gui designer. 
But the CLI program works fine,I think that someone might change the GUI to PyGTK,i would if i could,but i am already involved in a couple of projects.

---

### Post by adam_kimber on 2008-08-07
> **LaRoza said:**
> Its up!

[http://sourceforge.net/projects/sysres/](http://sourceforge.net/projects/sysres/)

Congrats :D

---

### Post by LaRoza on 2008-08-07
Anyone who got 0.6, get 0.7, as there was a bug in the first version in the GUI. I didn't realise while testing that several of the input boxes have a "cancel" and didn't take that into account, see, user input is a pain. I wasn't the one who discovered that

---

### Post by adam_kimber on 2008-08-07
> **Kadrus said:**
> Well as said in the read me file: 
But the CLI program works fine,I think that someone might change the GUI to PyGTK,i would if i could,but i am already involved in a couple of projects.

The GUI (0.7) works too. Just a couple of notes: 
- On backup, the GUI version exits and was not sure if it done anything! So maybe a note saying "Backup done, yay!" or something like that....
- In the .sysres folder there are obfuscated names for the files backed up. This might make for problematic manual restore if the program fails to restore. Things like, "You need to find the xorg.conf backup file..." might not be too easy for someone. While you can open them to find out their contents it might be easier to use just their names? Maybe with the same string as the folder has appended to the end? 
- There is now a sub folder in the /etc/apt/ directory called sources.list.d/ which has the added extra repos, I have the medibuntu repo in there as a file called the medibuntu.list . This should be backed up but with an option on restore of not restoring it as maybe a package from one of these might have borken the system. 

Adam

---

### Post by LaRoza on 2008-08-07
> **adam_kimber said:**
> The GUI (0.7) works too. Just a couple of notes: 
- On backup, the GUI version exits and was not sure if it done anything! So maybe a note saying "Backup done, yay!" or something like that....

The Unix way seems to be not to complain when things work. If a new GUI is made, perhaps it could be less dialogue-ish. But I won't do it.

> 
- In the .sysres folder there are obfuscated names for the files backed up. This might make for problematic manual restore if the program fails to restore. Things like, "You need to find the xorg.conf backup file..." might not be too easy for someone. While you can open them to find out their contents it might be easier to use just their names? Maybe with the same string as the folder has appended to the end? 

That is the md5sum of the filename, which is used to verify it.

> 
- There is now a sub folder in the /etc/apt/ directory called sources.list.d/ which has the added extra repos, I have the medibuntu repo in there as a file called the medibuntu.list . This should be backed up but with an option on restore of not restoring it as maybe a package from one of these might have borken the system. 


I will look into it.

---

### Post by red_Marvin on 2008-08-08
I'm working on a gtk frontend for this program, if anyone's interested.

Current progress:
Creation/Restoration/Deletion(single multiple points) should work even if not polished and/or properly tested yet.

LaRoza:
I'm thinking that it could be useful to implement functions to make the user able to not only add, but also view and delete which files that are restored instead of just adding them.
Maybe something like
Add -> add a file to the list
Delete -> delete a file in the list (Including/Excluding the default ones?)
Restore -> remove all non-default files in the list and make sure the default files are there.

Also: are file ownership/permissions preserved for the files that are restored?

---

### Post by LaRoza on 2008-08-08
> **red_Marvin said:**
> I'm working on a gtk frontend for this program, if anyone's interested.

Current progress:
Creation/Restoration/Deletion(single multiple points) should work even if not polished.

Thanks! If you need help, [email]laroza77@gmail.com[/email] (IM or Email) and I am LaRoza on #ubuntu-programming

---

### Post by LaRoza on 2008-08-08
> **red_Marvin said:**
> I'm working on a gtk frontend for this program, if anyone's interested.

Current progress:
Creation/Restoration/Deletion(single multiple points) should work even if not polished and/or properly tested yet.

LaRoza:
I'm thinking that it could be useful to implement functions to make the user able to not only add, but also view and delete which files that are restored instead of just adding them.
Maybe something like
Add -> add a file to the list
Delete -> delete a file in the list (Including/Excluding the default ones?)
Restore -> remove all non-default files in the list and make sure the default files are there.

That part of the program is simple, and not really developed. The real way it works is it just writes to list.rules (one one each line) so it would be easy to write something to edit it.

Deleting the customized settings would recreate the default list (the program checks for that list and if it doesn't exist, it makes a default one)

> 
Also: are file ownership/permissions preserved for the files that are restored?
It can only work if it is run as root, so it is written as root.

---

### Post by LaRoza on 2008-08-08
I am working on the add/remove files methods. Should be simple. I suggest not working on that part of the interface yet...

---

### Post by red_Marvin on 2008-08-08
I'll show what I've done so far (for comments/suggestions, **not for real use yet**):
I've added gui_gtk.py and modified sysres to default to it, but fallback to the original tk gui on an ImportError exception (I think that would be the result if pygtk isn't installed) or if --force-tk is used.

Edit0: forgot to attach the file.
Edit1: I haven't added any license info on my code since it's pre-release, but it is gpl (v3+).

---

### Post by LaRoza on 2008-08-08
> **red_Marvin said:**
> I'll show what I've done so far (for comments/suggestions, **not for real use yet**):
I've added gui_gtk.py and modified sysres to default to it, but fallback to the original tk gui on an ImportError exception (I think that would be the result if pygtk isn't installed) or if --force-tk is used.

Edit0: forgot to attach the file.
Edit1: I haven't added any license info on my code since it's pre-release, but it is gpl (v3+).

Looks good, better than what I could do.

I fixed up my work to allow adding and deleting restore rules. I only have the CLI interface done, as I feel your work will replace that option.

The new version isn't up yet. Let me know if you want it. It only affects "advanced"

Please use four spaces only, not eight spaces or tabs.

Also, add this to the top of the files you create:

```


################################################################################
##sysres-gui: GUI for sysres.
##Copyright (C) 2008  <Your name here>
##
##This program is free software: you can redistribute it and/or modify
##it under the terms of the GNU General Public License as published by
##the Free Software Foundation, either version 3 of the License, or
##(at your option) any later version.
##
##This program is distributed in the hope that it will be useful,
##but WITHOUT ANY WARRANTY; without even the implied warranty of
##MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
##GNU General Public License for more details.
##
##You should have received a copy of the GNU General Public License
##along with this program.  If not, see <http://www.gnu.org/licenses/>.
################################################################################

```

Thank you for your work. I hope we can make this more functional. Do you want to try to get the entire thing working with your GUI for the next release?

---

### Post by red_Marvin on 2008-08-09
> **LaRoza said:**
> The new version isn't up yet. Let me know if you want it. It only affects "advanced"
Yes please, then I could populate the advanced tab with widgets too. (Maybe "settings" is a better name?).

---

### Post by LaRoza on 2008-08-09
> **red_Marvin said:**
> Yes please, then I could populate the advanced tab with widgets too. (Maybe "settings" is a better name?).

Whatever you think is best for now. I wouldn't want to stifle your creativity.

I will upload the new files here (I'll have to wait, I have to change one thing I just remembered, and I am in Windows for an assignment I have to do)

---

### Post by napsy on 2008-08-09
If you need any help with the gtk+ front-end I will gladly help out. Just contact me with PM

I once had a similar project where I did a backup of desktop settings of all users and some system files, including the kernel image.

The gtk+ front-end was not a problem. The problem was designing a program that will run instead of the default init script (that means no /usr if yo have separate partition for that).

---

### Post by LaRoza on 2008-08-09
Here is the new version.

The changelog includes the changes I made. I changed the gui code to have four spaces for indents like all the other code. Please use four spaces for sysres.

---

### Post by adam_kimber on 2008-08-11
Hey the new Sysres looks good! I have a couple of points if you guys don't mind. The window when the GTK gui starts up is not quite the right size on my machine. Just stretching the bottom corner sorts this (this is really picky I know). Secondly how about an about tab? Things like the developers, what it does, liscense info etc?

PS do you want an icon?

---

### Post by red_Marvin on 2008-08-11
adam_kimber: Is it the width or the height that is wrong?
(The width is automatically set based on how much space the widgets "want", but I request a special height or otherwise it would be too short, since the widgets that take space are in scrollbar windows and can made smaller)

Good idea, the about tab, it should be easy to incorporate I'll put that on my to do list as well as tooltips.

--

The development from my part might slow down a little as I have other work too and I'm also currently rewriting my gui code since I wasn't really happy of the state of it before. (Although the new code might differ little for someone who's not me ;))

The real pain is the TreeView in the view tab (and coming in the advanced tab), since it's a quite flexible tool it also requires quite some code to set up to do even the simplest things.

---

### Post by LaRoza on 2008-08-11
> **adam_kimber said:**
> Hey the new Sysres looks good! I have a couple of points if you guys don't mind. The window when the GTK gui starts up is not quite the right size on my machine. Just stretching the bottom corner sorts this (this is really picky I know). Secondly how about an about tab? Things like the developers, what it does, liscense info etc?

I'll leave that up to the person doing the GUI (for anyone else, see the changelog, readme and license files)

In case it matters, I use xmonad which means the windows are automatically the size of the screen (if they are the only one open on that tag)

> 
PS do you want an icon?

I haven't considered that.



> **red_Marvin said:**
> 
The development from my part might slow down a little as I have other work too and I'm also currently rewriting my gui code since I wasn't really happy of the state of it before. (Although the new code might differ little for someone who's not me ;))

The real pain is the TreeView in the view tab (and coming in the advanced tab), since it's a quite flexible tool it also requires quite some code to set up to do even the simplest things.

Well, I won't be changing much, but if I do, I will attach it here (I will append a letter to the version, so sysres-0.8b would be the next one). It isn't an official release, so don't use it people! Get the one off sourceforge.net.

The 0.8 has some changes. It is all in the changelog (remember, year-month-day).

---

### Post by mssever on 2008-08-11
> **red_Marvin said:**
> The real pain is the TreeView in the view tab (and coming in the advanced tab), since it's a quite flexible tool it also requires quite some code to set up to do even the simplest things.
TreeView is the stuff of nightmares. Talk about an insanely over-engineered tool! It's what's delayed the GUI for my Net Responsibility config tool.

---

### Post by Reiger on 2008-08-11
> **LaRoza said:**
> Could you explain that? I know one can get all the packages installed with a command (forget it though) is there a a file to parse?

Once I get this to work (GUI issues and restore not finished now), I will be very open to adding to it and probably have a little page for it somewhere.

There is the command ```
aptitude reinstall [package-name]
``` ?
It could be quite useful to maintain a list of installed packages (just their name) and iterate over the list forcing a re-install.

Also, it would be quite neat to have the ability to add sources/remove sources based on preferences. Essentially a configuration file for this app itself (which in turn should be included in the to-do list).

---

### Post by LaRoza on 2008-08-11
> **Reiger said:**
> There is the command ```
aptitude reinstall [package-name]
``` ?
It could be quite useful to maintain a list of installed packages (just their name) and iterate over the list forcing a re-install.

Also, it would be quite neat to have the ability to add sources/remove sources based on preferences. Essentially a configuration file for this app itself (which in turn should be included in the to-do list).

Please read thread backwards ;) Here it the script for reinstall packages and making such restore points. Do not use it with sysres! It was written a while ago, and it will mess sysres up if used with it: [http://ubuntuforums.org/showpost.php?p=5535477&postcount=78](http://ubuntuforums.org/showpost.php?p=5535477&postcount=78)

I am not interested in making an editor for source lists. That is what synaptic is for (and what I use vim for)

---

### Post by adam_kimber on 2008-08-12
> **red_Marvin said:**
> adam_kimber: Is it the width or the height that is wrong?

Unfortunately its the width that is wrong. One of the widgets seems to enjoy being off the page. :P

---

### Post by MONODA on 2008-08-12
i used to use flyback, it is similar to your program but is dead now. You may want to check it out, it is on google code.

---

### Post by red_Marvin on 2008-08-12
> **adam_kimber said:**
> Unfortunately its the width that is wrong. One of the widgets seems to enjoy being off the page. :P

I don't that should be *possible* O_o anyway, I'm not using the same type of container widget in the version I'm working on, so hopefully the next release won't have this problem.

---

### Post by LaRoza on 2008-08-23
Ok, we now have a QT interface.

This is the sysres up to date. Please review your code to see if you it the way you want it before release. 

The run options are --cli, --qtk or --qt.

---

### Post by adam_kimber on 2008-08-23
gtkgui.py has an error in it. All it needed was a " at line 246 after OutofReach and before the )

```
self.bAboutDialog.set_copyright("Core program: Copyright (C) 2008 LaRoza\nGTK GUI (gtkgui.py): Copyright (C) 2008 Leo Bärring\nQT GUI (qtgui.py): Copyright (C) 2008 OutOfReach")
```

---

### Post by LaRoza on 2008-08-23
> **adam_kimber said:**
> gtkgui.py has an error in it. All it needed was a " at line 246 after OutofReach and before the )

```
self.bAboutDialog.set_copyright("Core program: Copyright (C) 2008 LaRoza\nGTK GUI (gtkgui.py): Copyright (C) 2008 Leo Bärring\nQT GUI (qtgui.py): Copyright (C) 2008 OutOfReach")
```

Thanks. That was me adding the QT dev...

Fixed.

---

### Post by adam_kimber on 2008-08-23
I thought I would create an icon for you in case you needed one. Here is my first draft. Comments appreciated!

---

### Post by LaRoza on 2008-08-23
> **adam_kimber said:**
> I thought I would create an icon for you in case you needed one. Here is my first draft. Comments appreciated!

Could it be simpler and less colourful? Perhaps black/white or greyscale?

---

### Post by red_Marvin on 2008-08-24
Did some minor changes, som might be "out of my jurisdiction" (IE editing files I'm not the maintainer of) so feel free to revert them.

[quote="Excerpt from the changelog"]
**    * gtkgui.py:**
    Minor code edit, nothing "visible".
        Replaced "[version number]" with "0.8" on line 236.
        License in about->about->license now is read from the file license instead of an embedded text string in gtkgui.py.
**    * about:**
    License information removed since the license is already visible in about->about->license.
    Some general purpose information added, (My goal is to keep it generic enough to make inclusion in all "access modes"
    possible and relevant if wanted).
**    * all:**
    Changed so only those files that are supposed to have execute permissions, qtgui.py has the correct #! setup but
    no code to handle if it is run as a separate program (IE handling if __name__ == "__main__") so I set it to -x
    for the moment.
**    * r:** Added rm *~ so it removes my gedit quicksaves too.[/quote]

---

### Post by chacham23 on 2008-08-24
What about Compiz setting?

---

### Post by Vishal Agarwal on 2008-08-24
SSH server settings ?

---

### Post by LaRoza on 2008-08-24
> **chacham23 said:**
> What about Compiz setting?

Or xmonad or wmii? WM settings are not universal ;) 

> **Vishal Agarwal said:**
> SSH server settings ?

You can add them to the program through the GUI's or through the command line.

---

### Post by LaRoza on 2008-08-24
sysres-0.8 is out! [http://sourceforge.net/projects/sysres/](http://sourceforge.net/projects/sysres/)

Thanks to the fine GUI developers who have worked on it, we have two GUI's, one in GTK+ and one in QT. The CLI is there as always.

A critical bug was fixed, and this version is the most complete version yet.

The next step may be to get a nice icon and .deb out, and make it double click and select in a menu type of thing for all the newbs (the actual targetted user for this)

If anyone is vaguely interested, you can double click the qtgui.py or gtkgui.py files to get the interfaces directly. Perhaps that will be of interest for packaging, I never made a .deb before.

---

### Post by red_Marvin on 2008-08-24
Yay!

Btw, the utf-8 coding tag was only added in my source because I wanted to be able to spell my name properly
(with an "ö"), a somewhat silly reason :).

---

### Post by cmay on 2008-08-24
> The next step may be to get a nice icon 

i think i have a cd whit back up on some stuff did where i among other things have about ten or fifteen icons i created.
if you have any interest in that i can go look for it and see if i can find it.

---

### Post by tuxxy on 2008-08-24
[http://www.faqs.org/docs/gazette/backup.html](http://www.faqs.org/docs/gazette/backup.html)

---

### Post by LaRoza on 2008-08-24
> **red_Marvin said:**
> Yay!

Btw, the utf-8 coding tag was only added in my source because I wanted to be able to spell my name properly
(with an "ö"), a somewhat silly reason :).

That is a perfectly valid reason.

---

### Post by red_Marvin on 2008-08-24
Yes perhaps, I noticed that you had added it to the coding standard file, guessed that it was because I put it in gtkgui.py and just thought I'd explain my reasons.

---

### Post by LaRoza on 2008-08-24
> **red_Marvin said:**
> Yes perhaps, I noticed that you had added it to the coding standard file, guessed that it was because I put it in gtkgui.py and just thought I'd explain my reasons.

Your reasons were obvious to me :-)

I am working on the .deb. It is going well, except for one thing. The license file isn't being opened...

Also, I think usability wise, the QT version is a bit better. Could your version mimic it a bit? (That version is based off your GTK+ work, and I used what I liked about yours to give feedback on it).

I will to avoid the license opening issue, make a variable (constant) in system_restore.py for the entire license, so you can use that for getting the license info instead of opening the file.

---

### Post by red_Marvin on 2008-08-24
> **LaRoza said:**
> Also, I think usability wise, the QT version is a bit better. Could your version mimic it a bit?
Sure, but I need more elaborate specifications on what you want changed, the things that differ between the versions, that I noticed are (please select one or more, or add your own :)):
1) Buttons beside the lists instead of underneath them
2) About/license/exit buttons at the bottom of the window (If you'd like that, should I put the license button thero or do you want me to continue to use the built in one in gtk.AboutDialog (like now)?)
3) Padding between widgets, increase?

---

### Post by LaRoza on 2008-08-24
> **red_Marvin said:**
> Sure, but I need more elaborate specifications on what you want changed, the things that differ between the versions, that I noticed are (please select one or more, or add your own :)):


Ah, yes. I should have been more clear. My (and yours, apparently) psychic powers are low :-)

> 
2) About/license/exit buttons at the bottom of the window (If you'd like that, should I put the license button thero or do you want me to continue to use the built in one in gtk.AboutDialog (like now)?)

I like that. I think you should get rid of the "About" tab (or whatever they are called) and just have a license and about button. Or they could be in that tab. I just don't like having an "About" window and an "About" button.

---

### Post by red_Marvin on 2008-08-24
I did a quick test with adding buttons to the bottom of the window, but since I have the "other" buttons close to the bottom too and they didn't align properly, it looked messy, however I might be able to add a menu to the top that can provide an interface like:

File
+-Exit

Help
+-Information (showing the contents of the about file)
+-About (popping up the about dialog)

License information could be kept in the about dialog (like now) or as another item in the help menu.

Either something like that, or I move the "other buttons" to be to the right of lists so the layouts don't interfer with each other.

Maybe even the whole tab system could be moved into a submenu, so that there is an item
Mode (or just continue adding to File, so Exit won't be alone)
+-Create
+-Edit
+-Settings

Well, anyhow, I should get some sleep, before I stop making sense altogether... if I haven't already...
Comments and ideas appreciated.

---

### Post by mc4100 on 2008-08-25
First, great job everyone! This project is progressing really well.
I just created a mock-up of System Restore that's based on the Transmission UI -- the simplist I could find...

Ok, let me explain how it would work: basically, the main view is of all the restore points in a list, and when one is highlighted then you can choose to backup from it, or remove it. "Add" simply creates a new restore point and puts it on the list ... "Create" and "Delete" would have been nicer, but Transmission already had those buttons and they seemed to fit quite well.

BTW, the screenshot didn't get the mouse (a "feature"), so just pretend there's a pointer on the Details button. ;) But of course, I haven't even explained what that is: just a way to see which files are in a restore point, since the rules might have changed, without having to go check the actual files.

Oops I just noticed, kindly ignore that one of the restore points is apparently from the future, I'm just an idiot. The window focus is off too ... I don't think I'm too good at this!
EDIT: Updated with a few things I liked (statusbar, search, etc)... I think it's done.

---

### Post by red_Marvin on 2008-08-25
That looks quite nice, I've thought of having the add button as a part of the view/restore section too, and will try it out on my next modification.
However, the multiline presentation, while it looks prettier than an ordinary list, I'll keep mine (at least for now) since I've implemented sorting based on name/date/time (just click at the column buttons)

By the way LaRoza, are we aiming on a full featured ubuntu package with this with localization support etc?

---

### Post by mc4100 on 2008-08-25
> **red_Marvin said:**
> That looks quite nice, I've thought of having the add button as a part of the view/restore section too, and will try it out on my next modification.
However, the multiline presentation, while it looks prettier than an ordinary list, I'll keep mine (at least for now) since I've implemented sorting based on name/date/time (just click at the column buttons)
Hey, you're (one of) the developers ... it's completely your decision. I actually liked your list, a lot; though here's my first ever feature request for sysres (yay): please make the columns re-sizable ... it's not insanely useful, just nice to have.
Also, I'm curious to how you're developing your design; are you following particular guidelines (like Gnome's HIG), or just what you feel is easiest to use/most productive/whatever ?

---

### Post by LaRoza on 2008-08-25
> **red_Marvin said:**
> 
By the way LaRoza, are we aiming on a full featured ubuntu package with this with localization support etc?

For now, just a lone project that tries to be useful. 

If we want to get more official (into repos and such) we'd have to look into the standards for our target (like GNOME, KDE, and packaging)

---

### Post by adam_kimber on 2008-08-25
I have created a couple of variants in greyscale for you. I am not sure how to simplify as its just as S made of two arrow.... Do you have something in mind?

---

### Post by mssever on 2008-08-25
As far as icons go, I vote for the icon mc4100 used. It's a stock icon, so it should always match the theme, yet it provides a good illustration of what the program does.

---

### Post by OutOfReach on 2008-08-25
> **mc4100 said:**
> First, great job everyone! This project is progressing really well.
I just created a mock-up of System Restore that's based on the Transmission UI -- the simplist I could find...

Ok, let me explain how it would work: basically, the main view is of all the restore points in a list, and when one is highlighted then you can choose to backup from it, or remove it. "Add" simply creates a new restore point and puts it on the list ... "Create" and "Delete" would have been nicer, but Transmission already had those buttons and they seemed to fit quite well.

BTW, the screenshot didn't get the mouse (a "feature"), so just pretend there's a pointer on the Details button. ;) But of course, I haven't even explained what that is: just a way to see which files are in a restore point, since the rules might have changed, without having to go check the actual files.

Oops I just noticed, kindly ignore that one of the restore points is apparently from the future, I'm just an idiot. The window focus is off too ... I don't think I'm too good at this!
EDIT: Updated with a few things I liked (statusbar, search, etc)... I think it's done.

That mockup looks nice actually, it looks very do-able nice and clean. :)
BTW I am the Qt dev for all of you who don't know.

---

### Post by LaRoza on 2008-08-25
> **adam_kimber said:**
> I have created a couple of variants in greyscale for you. I am not sure how to simplify as its just as S made of two arrow.... Do you have something in mind?

I like the first one :-)

Now I have to figure out how to use it...

---

### Post by adam_kimber on 2008-08-25
> **mssever said:**
> As far as icons go, I vote for the icon mc4100 used. It's a stock icon, so it should always match the theme, yet it provides a good illustration of what the program does.

Hey I liked his mock up too! But i have never seen that icon before. How can it be stock? Is that the reload icon? If so it varies a lot from theme to theme. A standard icon makes the program identifiable. :D

---

### Post by adam_kimber on 2008-08-25
> **LaRoza said:**
> I like the first one :-)

Now I have to figure out how to use it...

Yeah I have no idea about that either :lolflag:

---

### Post by OutOfReach on 2008-08-25
> **LaRoza said:**
> I like the first one :-)

Now I have to figure out how to use it...

It takes a few steps, nothing hard though (At least with Qt, I don't know how this is done in the GTK world). If you would like i can send you the modified project with the icon ready?

---

### Post by mssever on 2008-08-25
> **adam_kimber said:**
> Hey I liked his mock up too! But i have never seen that icon before. How can it be stock? Is that the reload icon? If so it varies a lot from theme to theme. A standard icon makes the program identifiable. :D
I like that as a standard icon. But the stock icon "reload" is close. Have you noticed that a number of apps have theme-dependent icons?

---

### Post by red_Marvin on 2008-08-25
I'm working on a new (hopefully prettier) gui, it's far from finished, but is complete enough to show how the gui will look.
I'll attach the wip for comments and suggestions.
To execute, run new-gtkgui.py

The current idea I'm working with is that this is the only tab normally open and that the advanced/preferences mode can be accessed in a separate window, that is created from File->Preferences (not implemented yet).

---

### Post by OutOfReach on 2008-08-25
Wow that looks good :), I too am re-working my Qt design, it's attached below, I only attached a picture though. I only rewrote the UI part of my script so most of the functions work (Create restore point, restore, the about box) but some are disfunctional.

---

### Post by mc4100 on 2008-08-25
For what it's worth, here's the gnome-session-reboot SVG icon (part of the icon theme [GNOME-colors]("http://www.gnome-look.org/content/show.php?content=82562") -- specifically, gnome-brave),

I've also put in a 128x128 desaturated .png
EDIT: and I've added my attempts at human/newhuman (all 128x128 .png)

---

### Post by OutOfReach on 2008-08-25
> **mc4100 said:**
> For what it's worth, here's the gnome-session-reboot SVG icon (part of the theme [GNOME-colors]("http://www.gnome-look.org/content/show.php?content=82562") -- specifically, gnome-brave),

I've also put in a 128x128 desaturated .png

WOW now that looks good.

---

### Post by adam_kimber on 2008-08-26
> **mc4100 said:**
> For what it's worth, here's the gnome-session-reboot SVG icon (part of the icon theme [GNOME-colors]("http://www.gnome-look.org/content/show.php?content=82562") -- specifically, gnome-brave),

I've also put in a 128x128 desaturated .png
EDIT: and I've added my attempts at human/newhuman (all 128x128 .png)

I like the grey on on the left. Makes my ickle icon look no so good :(

---

### Post by shifty2 on 2008-08-26
I think you should include some facility for diffing the restored files. I keep the majority of my files under git control, so when I bork them I can look back through the history and see what made it go wrong - a tool for diffing it will allow you to see *what* went wrong rather than just fixing it and moving on.

---

### Post by adam_kimber on 2008-08-26
> **shifty2 said:**
> I think you should include some facility for diffing the restored files. I keep the majority of my files under git control, so when I bork them I can look back through the history and see what made it go wrong - a tool for diffing it will allow you to see *what* went wrong rather than just fixing it and moving on.

That would be useful. Not only could you restore a previous working state but then analyse the problem. It would require backing up the non-working version though..... Take the following scenario. Your xorg.conf is borked. Won't start GDM/KDM. Use the CLI version to restore xorg.conf to working state but current (non-working) is lost.

---

### Post by duncon on 2008-08-26
I keep the mejority of my files under git controles SO the brank them I can look bark though the history what made.

==================================================

duncon

[Virginia Drug Addiction]("http://www.drugaddiction.net/virginia")

---

### Post by nvteighen on 2008-08-26
> **OutOfReach said:**
> It takes a few steps, nothing hard though (At least with Qt, I don't know how this is done in the GTK world). If you would like i can send you the modified project with the icon ready?

In GTK+ world:
```

gtk_window_set_icon_from_file(GtkWindow *window, const gchar *filename, GError **err);

```

Where window is the window, filename, the filename to be used and err, a place to store the error code (NULL if you don't want this).

Other methods also exist, but require using GdkPixbuf to store the image.

---

### Post by red_Marvin on 2008-08-27
New gtk gui finished:
New features are; restore point filtering and graceful reaction to if systerm_restore.py throws and RPException.
Screenshot and archive below.

EDIT: OutOfReach: Looking nice.

---

### Post by LaRoza on 2008-08-27
> **red_Marvin said:**
> New gtk gui finished:
New features are; restore point filtering and graceful reaction to if systerm_restore.py throws and RPException.
Screenshot and archive below:

I'll check it out!

Thanks.

---

### Post by LaRoza on 2008-08-28
Here is the work so far. The new gtk GUI is in this, and it includes the change in system_restore.py (I edited the GUI code to use it)

Instead of reading from the license file, use the *license* variable in system_restore.py

Thanks for the work on it GUI devs :-)

---

### Post by mssever on 2008-08-28
> **LaRoza said:**
> Attached Files 					 					 	[IMG]http://ubuntuforums.org/images/attach/gz.gif[/IMG] 	[sysres-0.9-08282008.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=83136&d=1219942827") (14.1 KB, 2 views)
One comment about your versioning scheme: I strongly prefer big-endian dates (YYYYMMDD) over little-endian (DDMMYYYY) or middle-endian (MMDDYYYY) for several reasons:

[LIST]
[*]Bid-endian dates sort properly, even when the sorter doesn't recognize them as dates (thus, I always use big-endian in filenames)
[*]Big-endian dates aviod confusion in an international context. Does 4/1/2008 mean April 1 or the 4th of January? To answer that question, you need to know the author's country of origin; even then, that might not be sufficient.
[/LIST]

---

### Post by LaRoza on 2008-08-28
> **mssever said:**
> One comment about your versioning scheme: I strongly prefer big-endian dates (YYYYMMDD) over little-endian (DDMMYYYY) or middle-endian (MMDDYYYY) for several reasons:


Shall we have a war over this? (Lilliput and Blefuscu reference)

I just put that name as the attachment to keep downloads logical for the devs (this is where we are sharing code). The changelog uses big endian dates (and the official versions don't use dates at all).

Now that you mentioned it, we shall from now on use your scheme (name-version-YYYYMMDD).

---

### Post by LaRoza on 2008-08-28
Current work (slightly different than the previous one! Devs use this, sorry about the quick changing)

The gtkgui.py and qtgui.py code have a few changes. Mainly, the use of the license and version variables in system_restore.py (so you don't have to manually update that part of the code)

---

### Post by red_Marvin on 2008-08-28
Nice.
But the egg should of course be opened at the big end, *everybody* knows that.

EDIT:: the hashbang line of gtkgui.py is garbled, it should of course read _#!/usr/bin/env python_
I must've done a sloppy search and replace-all.

---

### Post by LaRoza on 2008-08-28
> **red_Marvin said:**
> Nice.
But the egg should of course be opened at the big end, *everybody* knows that.

I am a vegan. I don't eat the ovulations of poultry (think about what you are doing next time.)

> 
EDIT:: the hashbang line of gtkgui.py is garbled, it should of course read _#!/usr/bin/env python_
I must've done a sloppy search and replace-all.

Yes, I noticed that. The entire program had a problem with "sysres", which was put as "sysysresys" or something. 

I think I fixed all the typos in your code (so use the one I put up to save yourself some trouble). I also fixed the shebang on my end.

---

### Post by mssever on 2008-08-28
> **LaRoza said:**
> I am a vegan. I don't eat the ovulations of poultry (think about what you are doing next time.)
So does that make you a neither-endian? :) Down with both Lilliput and Blefuscu!

---

### Post by LaRoza on 2008-08-28
> **mssever said:**
> So does that make you a neither-endian? :) Down with both Lilliput and Blefuscu!

Or a Both Endian. I'd fight for either if they pay me, ideally, both (watch A Fistful of Dollars)

---

### Post by OutOfReach on 2008-08-28
Sorry for teh delay of development, I just started school (ugh).
I am almost done though, with the new interface of course and a couple of new features, small ones, nothing extreme. :)

---

### Post by LaRoza on 2008-08-28
> **OutOfReach said:**
> Sorry for teh delay of development, I just started school (ugh).
I am almost done though, with the new interface of course and a couple of new features, small ones, nothing extreme. :)

Don't be sorry, it isn't like any of us are getting paid for this or have a deadline. :-)

You should have seen the delay of my development (look at start of thread...).

Take my few changes into account (you'll see it in your qtgui.py code, and in the changelog) for the new version.

---

### Post by OutOfReach on 2008-08-28
Yes, I've seen some changes and I'll happily implement them on my current development version. :)

---

### Post by LaRoza on 2008-08-28
> **OutOfReach said:**
> Yes, I've seen some changes and I'll happily implement them on my current development version. :)

The latest development is we changed languages to Java. I except a QT interface for the Java version by tomorrow.

</hellish_joke>

---

### Post by red_Marvin on 2008-08-28
Do anyone know if befunge has gtk bindings?

---

### Post by mssever on 2008-08-28
> **red_Marvin said:**
> Do anyone know if befunge has gtk bindings?
Bindings? Real Programmers don't need bindings.

---

### Post by OutOfReach on 2008-08-28
> **LaRoza said:**
> The latest development is we changed languages to Java. I except a QT interface for the Java version by tomorrow.

</hellish_joke>

:)

---

### Post by OutOfReach on 2008-09-01
Ok, I attached an updated package with the new qtgui.py, you can read the changelog to see what excatly I changed/added.
:)

---

### Post by LaRoza on 2008-09-01
> **OutOfReach said:**
> Ok, I attached an updated package with the new qtgui.py, you can read the changelog to see what excatly I changed/added.
:)

Responded within one minute of posting! I'm good...

When making updates on this thread, could you use the naming convention stated earlier? It would help when I am ungzipping them and help me keep track.

---

### Post by LaRoza on 2008-09-01
qtgui.py has an issue.

If you go to make a new restore point, and enter nothing, it doesn't do anything. It should have a default name of "default".

---

### Post by OutOfReach on 2008-09-01
> **LaRoza said:**
> Responded within one minute of posting! I'm good...

When making updates on this thread, could you use the naming convention stated earlier? It would help when I am ungzipping them and help me keep track.

Will do.

> **LaRoza said:**
> 
qtgui.py has an issue.

If you go to make a new restore point, and enter nothing, it doesn't do anything. It should have a default name of "default". 

I'm on it. :)

---

### Post by LaRoza on 2008-09-01
> **OutOfReach said:**
> I'm on it. :)

I wonder what it did do though. It didn't seem to do anything. Did it silently catch an exception? It would be helpful if all exceptions were shown for usability and debugging purposes.

---

### Post by OutOfReach on 2008-09-01
According to the code I wrote, if the string entered is empty, it just threw it away, it didn't do anything, literally. Anyways, that's fixed, newest version is attached.

---

### Post by LaRoza on 2008-09-01
> **OutOfReach said:**
> According to the code I wrote, if the string entered is empty, it just threw it away, it didn't do anything, literally. Anyways, that's fixed, newest version is attached.

That was fast. Thanks.

---

### Post by adam_kimber on 2008-09-01
Hey thanks for the latest version. I have a point for the GTK dev. (Please don't kill me :P) 

Usually GTK apps start where they were left. Yours starts in the top left. Not sure if that is because of running it from a command line or not. Plus the preferences follows the same behaviour. Usually preferences are centred on the parent window. However as it is the same size as the parent it might get confusing for the user. "Where has the window gone" scenarios. 

It is interesting to see the subtle differences appearing between the QT and GTK versions. :D I can play spot the difference if you want.......

On the restore part, when it pops up the "are you root?" question, could you make that similar to the "unlock" that Network Settings has? Or a password pop up? That would be cool.

---

### Post by LaRoza on 2008-09-01
> **adam_kimber said:**
> Hey thanks for the latest version. I have a point for the GTK dev. (Please don't kill me :P) 

Usually GTK apps start where they were left. Yours starts in the top left. Not sure if that is because of running it from a command line or not. Plus the preferences follows the same behaviour. Usually preferences are centred on the parent window. However as it is the same size as the parent it might get confusing for the user. "Where has the window gone" scenarios. 


Feedback is (usually) always appreciated (easy for me to say, I don't code the GUI's).

Try double click on "gtkgui.py" and see what happens and how it works. When we have shortcuts and icons, that is how it will be started.

---

### Post by speedkreature on 2008-09-04
Okay, so this is a pretty useful thing.  Except for work, I use Ubuntu exclusively so I'll get the hang of it sooner or later, but I'm still a bit of a novice.  I'm curious to know how one would schedule this to run weekly at startup (for example).
It would be more useful if this was something that could be set from within this program and it could automatically generate a file name.  At that point, you would select a restore point based on date rather than the file name.

Also, would it be possible to detect what environment your in so that if in KDE, it would start in QT or if using Xubuntu or Ubuntu it would start in GTK if no option was specified?  Don't know if that's a useful thing...probably a lot of coding for something that could be very simply set when creating or editing menu item properties, but I thought I'd mention it.

One of the things that always bothered me about the restore feature of Windows (last time I used it which was Windows XP SP1) was that if you installed software and it goofed up your PC, it wouldn't always remove/uninstall the software installed from the last restore point and you couldn't always uninstall the software...on some occasions, I would even forget when I installed software that was causing the problem; I would only remember when I noticed the problem started.  Sometimes that was a good thing, but sometimes it was a nuisance because you had to manually delete files and folders and clear out registry keys.  A feature like this would be fairly easy to implement (compile a list of installed packages and uninstall what changed or let the user select what to install from a list of what changed since the last restore point).

Oh, and great work!  It's a neat little program--very well put together and I really like the multiple interface options.

---

### Post by LaRoza on 2008-09-04
> **speedkreature said:**
> Okay, so this is a pretty useful thing.  Except for work, I use Ubuntu exclusively so I'll get the hang of it sooner or later, but I'm still a bit of a novice.  I'm curious to know how one would schedule this to run weekly at startup (for example).

There is no need, unless you are making system wide changes that often (which one shouldn't be doing).

If you wanted to, you could use cron. However, the feature where it can be run with only command line arguments hasn't been done (although it did exist at one point). I will have to redo that.

> 
It would be more useful if this was something that could be set from within this program and it could automatically generate a file name.  At that point, you would select a restore point based on date rather than the file name.

Windows does it by names and dates like this. I find that the most usable way. When I make restore points, I name them after what they hold so "prenewmonitor" would be the settings before I got the new monitor and fiddled with xorg.conf.

> 
Also, would it be possible to detect what environment your in so that if in KDE, it would start in QT or if using Xubuntu or Ubuntu it would start in GTK if no option was specified?  Don't know if that's a useful thing...probably a lot of coding for something that could be very simply set when creating or editing menu item properties, but I thought I'd mention it.

Actually, it would be simple, but if one is going to make a launcher, they'd just use the appropriate one so it doesn't matter. I don't use KDE or GNOME (or Xfce) so the interface is just a preference in my case (I like them both, but I use the command line version when I use it which I wrote)

> 
One of the things that always bothered me about the restore feature of Windows (last time I used it which was Windows XP SP1) was that if you installed software and it goofed up your PC, it wouldn't always remove/uninstall the software installed from the last restore point and you couldn't always uninstall the software...on some occasions, I would even forget when I installed software that was causing the problem; I would only remember when I noticed the problem started. 

This is not going to take the place of package managers, which do their jobs very well. Windows's problems are caused by the registry in almost all cases (and Windows System Restore is a compensation for that). Linux has no such flaw.

> 
Oh, and great work!  It's a neat little program--very well put together and I really like the multiple interface options.
Thanks, we have three interaces because three people worked on it :-)

Now that I have been reminded, I will have to remake the command line version with no menu's so it can be run in shell scripts or automated.

---

### Post by mssever on 2008-09-04
I've been following this thread from the beginning (approximately), but I just finally downloaded sysres for the first time. (My interest has been primarily academic, since I have no need personally for this program, but I know that many people will benefit from it.)
> **speedkreature said:**
> Also, would it be possible to detect what environment your in so that if in KDE, it would start in QT or if using Xubuntu or Ubuntu it would start in GTK if no option was specified?  Don't know if that's a useful thing...probably a lot of coding for something that could be very simply set when creating or editing menu item properties, but I thought I'd mention it.
I think that would be fairly easy to do. I propose adding a .desktop file. The file would run a very simple shell script that would detect the desktop, then exec sysres with the proper options. My thought is to test for the kicker process, since that's a good shibboleth for KDE. If kicker is running, start the Qt interface, else start the GTK interface. (I suppose you could also test for gnome-panel and Xfce's panel, but then you'd have to decide what to do for Xmonad, etc. I don't know of any DE other than KDE that uses Qt, and GTK is more likely to be installed than Qt.) I'd be willing to implement this, if you're interested.

Once we're dealing with a .desktop file, an installer enters the picture. I don't know what methods are typically used to install Python software. Perhaps it would be enough to grab the .deb source of an already-packaged program and simply copy that.

Another comment: The CLI version clears the screen before running. That's a Bad Thing (tm), since I often have existing state in my terminal that I like to refer back to. In some situations, the information can be kicked out of my scrollback and lost until I regenerate it. I can type clear easily enough if I want the screen cleared. (When less or vim clear the screen, they use a different method, which I don't understand, that essentially creates a new window instead of scrolling the screen.)

---

### Post by LaRoza on 2008-09-04
> **mssever said:**
> 
I think that would be fairly easy to do. I propose adding a .desktop file. The file would run a very simple shell script that would detect the desktop, then exec sysres with the proper options.

My thought is to test for the kicker process, since that's a good shibboleth for KDE. If kicker is running, start the Qt interface, else start the GTK interface. (I suppose you could also test for gnome-panel and Xfce's panel,

That could work.

>  but then you'd have to decide what to do for Xmonad, etc. I don't know of any DE other than KDE that uses Qt, and GTK is more likely to be installed than Qt.) I'd be willing to implement this, if you're interested.


It doesn't matter. xmonad doesn't have a desktop ;)

I was thinking of making a different .deb for default kde or gnome, but I like your idea. You can try it. If you do make it, name the script "launchsysres" or something. In case you didn't notice, one can launch the various interfaces with "sysres --[qt|gtk]" or by executing gtkgui.py or qtgui.py. Those files are probably going to be renamed to sysres-gtk and sysres-qt though because of this.

If you do do it, if the script is in Python, it should follow the code standards. If it is a shell script, then I trust you to keep it well formatted :-)

> 
Once we're dealing with a .desktop file, an installer enters the picture. I don't know what methods are typically used to install Python software. Perhaps it would be enough to grab the .deb source of an already-packaged program and simply copy that.

The installer is easy to make. I have already made a couple .deb's but they aren't ready for release.

> 
Another comment: The CLI version clears the screen before running.
I'll remove that. That is a side effect of when it used to use curses and that behavior wouldn't be a problem.

---

### Post by Mickeysofine1972 on 2008-09-05
Good Work!

What about a way to backup the system restore points so that a new install can restore the needed packages?

That way, when your package get accepted into the distro, (which I'm pretty sure it will), you can have an option in the newly installed OS to restore your favorite packages.

This could be an option for memory stick or a CD/DVD i think.

Mike

---

### Post by red_Marvin on 2008-09-05
**Mickeysofine1972:**

As far as I know (I work on the gtk gui, not the core) the purpose of sysres is not to back up whole packages or setups, but configuration files, like /etc/X11/xorg.conf and the like.

However if you really want to back up the restore points, I think that making an archive of the ~/.sysres folder would suffice.

---

### Post by mssever on 2008-09-05
I've made the .desktop file now, which should be installed in /usr/share/applications. It makes a few assumptions, which I wasn't able to fulfil myself since there's no installer:

[LIST=1]
[*]It assumes that sysres is on the user's PATH.
[*]It assumes that launchsysres lives in /usr/share/sysres.
[*]It assumes that there's an icon called sysres.(svg|png|xpm) somewhere on the icon path. If there's only one icon used, I recommend making it an SVG and putting it in /usr/share/pixmaps. However, most icons need minor adjustments to look good at all common sizes. So I recommend that individually-scaled icons (PNG) and an SVG icon be installed in the hicolor theme, which is the proper place for icons as I understand the spec. This item, of course, is largely aimed at the icon folks. I'm willing to help with this if needed.
[/LIST]
I don't have a KDE environment available right now, so I'm not able to test whether the .desktop file puts itself in the proper menu in KDE. In the absence of an installer, testers will have to manually install this stuff as described above.

Also, LaRoza, when I was looking for where to download sysres from, I noticed that there's no download link in the OP which points to the current version. I ended up having to search SourceForge to find it.
> **LaRoza said:**
> In case you didn't notice, one can launch the various interfaces with "sysres --[qt|gtk]" or by executing gtkgui.py or qtgui.py. Those files are probably going to be renamed to sysres-gtk and sysres-qt though because of this.
IMHO, it's cleaner to provide one right way to launch sysres (sysres) and drop the x bit from the individual GUI modules. If it were my project, sysres and launchsysres would be the only files with the x bit set.

---

### Post by OutOfReach on 2008-09-05
> **mssever said:**
> I've made the .desktop file now, which should be installed in /usr/share/applications. It makes a few assumptions, which I wasn't able to fulfil myself since there's no installer:

[LIST=1]
[*]It assumes that sysres is on the user's PATH.
[*]It assumes that launchsysres lives in /usr/share/sysres.
[*]It assumes that there's an icon called sysres.(svg|png|xpm) somewhere on the icon path. If there's only one icon used, I recommend making it an SVG and putting it in /usr/share/pixmaps. However, most icons need minor adjustments to look good at all common sizes. So I recommend that individually-scaled icons (PNG) and an SVG icon be installed in the hicolor theme, which is the proper place for icons as I understand the spec. This item, of course, is largely aimed at the icon folks. I'm willing to help with this if needed.
[/LIST]
I don't have a KDE environment available right now, so I'm not able to test whether the .desktop file puts itself in the proper menu in KDE. In the absence of an installer, testers will have to manually install this stuff as described above.

I can't seem to get it working, but I'm 90% sure that it's on my part.

On a side note, I have an idea. And I want to share it here and get your responses and get the thumbs up before I work on it. Here they are:
- Search for restore points in other (specified) partitions.
- Restore restore points ON other partitions.
- Backup files from OTHER partitions.

This could be useful for the following scenario:
You have changed your menu.lst/xorg.conf/etc, etc... You can't boot into (K|X)ubuntu, caused by the changes to the file(s). You boot into the LiveCD, you download SysRes wanting to restore the restore points on the other partition, but you soon find out that you can't.

(Not a) Good idea?

---

### Post by LaRoza on 2008-09-05
> **OutOfReach said:**
> I can't seem to get it working, but I'm 90% sure that it's on my part.

On a side note, I have an idea. And I want to share it here and get your responses and get the thumbs up before I work on it. Here they are:
- Search for restore points in other (specified) partitions.
- Restore restore points ON other partitions.
- Backup files from OTHER partitions.

(Not a) Good idea?

I will do that work later. It actually did that before along with pure command line arguments, but I removed it when I rewrote it (I still have the original work, even the version not in Python)

---

### Post by OutOfReach on 2008-09-05
> **LaRoza said:**
> I will do that work later. It actually did that before along with pure command line arguments, but I removed it when I rewrote it (I still have the original work, even the version not in Python)

Alright, cool. :D

---

### Post by LaRoza on 2008-09-05
> **OutOfReach said:**
> Alright, cool. :D

Unless you want to mess around with my code and we'll see whose version is better :-) but I don't this minor detail needs two hands working on it.

I will start the work on the week end, and hopefully get it down in one sitting.

---

### Post by mssever on 2008-09-06
> **OutOfReach said:**
> I can't seem to get it working, but I'm 90% sure that it's on my part.
What's the problem? I'd like to be able to be 100% sure the problem is on your part, not mine. :)

---

### Post by LaRoza on 2008-09-06
> **mssever said:**
> What's the problem? I'd like to be able to be 100% sure the problem is on your part, not mine. :)

sysres is going to be installed in /usr/local/, so you may want to assume that. I can't test the script as I do not have KDE or GNOME.

---

### Post by OutOfReach on 2008-09-06
> **mssever said:**
> What's the problem? I'd like to be able to be 100% sure the problem is on your part, not mine. :)

I put the launchsysres file in /usr/share/sysres/ and I put the .desktop file in /usr/share/applications, but were do I put the sysres folder? (The one with qtgui, gtkgui, etc etc)

---

### Post by LaRoza on 2008-09-06
> **OutOfReach said:**
> I put the launchsysres file in /usr/share/sysres/ and I put the .desktop file in /usr/share/applications, but were do I put the sysres folder? (The one with qtgui, gtkgui, etc etc)

In my installation, it just has to be in the $PATH. The code (as you see) adds to the path, and sysres will be in /usr/local/bin probably.

---

### Post by mssever on 2008-09-06
> **LaRoza said:**
> sysres is going to be installed in /usr/local/, so you may want to assume that. I can't test the script as I do not have KDE or GNOME.
I assumed /usr/share because [the spec]("http://www.debian.org/doc/debian-policy/ch-opersys.html#s9.1.2") explicitly forbids .deb packages from installing in /usr/local. If you still want me to change it, I will, but it will be in violation of the spec.

---

### Post by LaRoza on 2008-09-06
> **mssever said:**
> I assumed /usr/share because [the spec]("http://www.debian.org/doc/debian-policy/ch-opersys.html#s9.1.2") explicitly forbids .deb packages from installing in /usr/local. If you still want me to change it, I will, but it will be in violation of the spec.

In that case, it will be in /usr/share if we use a .deb.

---

### Post by LaRoza on 2008-09-06
I just started working on the custom restore point, and realised my code always had that function, I just didn't make an interface for it.

GUI devs, you'll just have to set the mode in "makeRestorePoint(self,point,mode="default")" to "custom" (really, anything) and it will use the absolute path of the restore point name. So if a user wants a restore point in /media/disk/ they will have to somehow send the value "/media/disk/$restore_point_name" to the function in "point". It may be easiest to have a directory select dialog and a "name of" dialog (or whatever) and just make an absolute path that way.

My new code will have this in the function "advanced".

---

### Post by LaRoza on 2008-09-06
New testing version up. The CLI version supports creating restore points and restoring from them in any specified location, the GUI's don't, but should work fine.

---

### Post by OutOfReach on 2008-09-07
Update, the Qt interface now supports backing up/restoring to/from custom locations. (Which can be accessed from SysRes>Advanced, or by pressing Ctrl+Shift+A)

---

### Post by LaRoza on 2008-09-07
> **OutOfReach said:**
> Update, the Qt interface now supports backing up/restoring to/from custom locations. (Which can be accessed from SysRes>Advanced, or by pressing Ctrl+Shift+A)

Nice work.

I have no complaints (and thanks for the error boxes, trying to restore without selecting a restore point has an error box, but I don't think it is neccessary to dumb down the error messages at the moment)

---

### Post by OutOfReach on 2008-09-07
> **LaRoza said:**
> Nice work.

I have no complaints (and thanks for the error boxes, trying to restore without selecting a restore point has an error box, but I don't think it is neccessary to dumb down the error messages at the moment)

Thanks. :)

---

### Post by anotherdisciple on 2008-09-07
Hey.... sorry if you already mentioned this, or if it's already implemented... but could you make the restore give you the option of which file you want to restore. Like say I want to restore my x-org, but I don't want to go back to my old sources.list or grub menu.

I like the idea and the work you have done so far... thanks!

---

### Post by mssever on 2008-09-08
Here's a patch against the version of sysresqt.py found in sysres-0.9-20080907.tar.gz. I changed a bunch of string literals to comments, since that's really what they are. Marking comments as comments allows syntax highlighters to correctly highlight comments. It also saves a (trivial) amount of resources by not creating string objects.

---

### Post by LaRoza on 2008-09-08
> **mssever said:**
> Here's a patch against the version of sysresqt.py found in sysres-0.9-20080907.tar.gz. I changed a bunch of string literals to comments, since that's really what they are. Marking comments as comments allows syntax highlighters to correctly highlight comments. It also saves a (trivial) amount of resources by not creating string objects.

Forgive my ignorance, but exactly how does one use that? Why not update the file? It isn't much bigger.

---

### Post by mssever on 2008-09-08
> **LaRoza said:**
> Forgive my ignorance, but exactly how does one use that? Why not update the file? It isn't much bigger.
```
cd src/dir
patch -p0 < sysresqt.py.patch.txt
```I had to look that up to answer your question. :) It's easier to make a patch (diff -u) than to remember how to apply one IMO. I made a patch so that the changes are clear. However, I'm attaching the file itself since you asked. I had to compress it since the forum doesn't like .py files that large.

---

### Post by LaRoza on 2008-09-08
> **anotherdisciple said:**
> Hey.... sorry if you already mentioned this, or if it's already implemented... but could you make the restore give you the option of which file you want to restore. Like say I want to restore my x-org, but I don't want to go back to my old sources.list or grub menu.

I like the idea and the work you have done so far... thanks!

You can customise the restore point creation to backup any file you want, and that includes removing unwanted ones.

At the moment, this program is much more flexible than Microsoft Windows System Restore, and takes up much less space (a few kb versus several GB). Windows just got pwned by three people on a forum...

---

### Post by LaRoza on 2008-09-08
> **mssever said:**
> ```
cd src/dir
patch -p0 < sysresqt.py.patch.txt
```I had to look that up to answer your question. :) It's easier to make a patch (diff -u) than to remember how to apply one IMO. I made a patch so that the changes are clear. However, I'm attaching the file itself since you asked. I had to compress it since the forum doesn't like .py files that large.

Thanks, that is much easier :-)

I'll keep the patch -p0 routine in mind though, thanks.

<rant>The bzip2 people think they are so better than gzip-pers. I'll show them...</rant>

---

### Post by CptPicard on 2008-09-08
> **LaRoza said:**
> 
<rant>The bzip2 people think they are so better than gzip-pers. I'll show them...</rant>

The *[Burrows-Wheeler transform]("http://en.wikipedia.org/wiki/Burrows-Wheeler_transform")* is remarkably efficient at arranging textual data in a way that then compresses efficiently using something like Huffman coding. The way it works is very interesting, I implemented it once for coursework...

---

### Post by LaRoza on 2008-09-08
> **CptPicard said:**
> The *[Burrows-Wheeler transform]("http://en.wikipedia.org/wiki/Burrows-Wheeler_transform")* is remarkably efficient at arranging textual data in a way that then compresses efficiently using something like Huffman coding. The way it works is very interesting, I implemented it once for coursework...

See, that is what I mean. You aren't content with good old fashioned gzip and have to introduce new fangled algorithms.

---

### Post by nvteighen on 2008-09-08
> **LaRoza said:**
> 
At the moment, this program is much more flexible than Microsoft Windows System Restore, and takes up much less space (a few kb versus several GB). Windows just got pwned by three people on a forum...

:D

Congrats!

---

### Post by LaRoza on 2008-09-08
> **nvteighen said:**
> :D

Congrats!

It was simple, considering we were doing it for convenience sake, not to overcome deliberately designed design flaws.

Windows's flaws come from its efforts to restrict users. Its bloat, its unstability, its waste of space could all be eliminated if they focused on making the operating system work, instead of not work.

---

### Post by Calabresi on 2008-09-08
I'd sugest that, that's real important I think, "Total System Permission Reset".

I didn't read all the thread, sorry if it's sugested already, if there's a way already to run a thing like this, I would be glad to know it.

Reason is, I have one DVD-RAM writer Benq DW1680 and one DVD-ROM reader Sony CRX320EE, Benq stop work like before, all related with HARD, before and now, it's not broked, works on Vista read and write and as I told was working in HARD before.

The permission are like this, in /DEV all related CD, DVD, RW links are ROOT own with lrw-rw---- and group=cdrom is all that right?

The /media folder with cdrom link and 2 cdrom0 (benq) and cdrom1 (Sony) folders I dont understand how it works, they keep changing it's permission behaviour when I insert and remove media's, supose it's normal, but as in floopy the folder follow the link permission right, e.g. if I change the link CDROM the folder CDROM0 change also, but not CDROM1.

I don't know how, but I strongly (sry my en, I know it's wrong someway, but...) believe that some update caused it sometime ago (2, 3 week's), I read in bug site that nautilus is being revised due a bug, can be it?

I hope I could make it clear

thank's in advance

---

### Post by LaRoza on 2008-09-08
> **Calabresi said:**
> I'd sugest that, that's real important I think, "Total System Permission Reset".

If you need to backup and restore previously working settings, sysres can do that.

> 
Reason is, I have one DVD-RAM writer Benq DW1680 and one DVD-ROM reader Sony CRX320EE, Benq stop work like before, all related with HARD, before and now, it's not broked, works on Vista read and write and as I told was working in HARD before.

What changed between it working and not working?

> 
I don't know how, but I strongly (sry my en, I know it's wrong someway, but...) believe that some update caused it sometime ago (2, 3 week's), I read in bug site that nautilus is being revised due a bug, can be it?

That might be it. I'd try a different file manager (try Thunar) to see if it can be used.

By the way, "strongly" was correct, but "broked" wasn't. It should be "it's not broken".

---

### Post by nvteighen on 2008-09-08
> **LaRoza said:**
> 
By the way, "strongly" was correct, but "broked" wasn't. It should be "it's not broken".

Hey, that *broked is an interesting case of paradigmatic assimilation (contrasted to *braked)! It's still using the correct past stem, but changing the ending to the regular one. If you consider that English verbs, -(e)d is the regular participle ending but constructed from the past stem (where the regular verbs have present stem = past stem), then the whole thing makes sense: brake- (present stem) > broke- (past stem) > *broked.

(In Linguistics, an asterisk (*) before a word, means that word is incorrect)

---

### Post by CptPicard on 2008-09-08
How about my favourite version, **b0rked*? :)

---

### Post by LaRoza on 2008-09-08
> **nvteighen said:**
> Hey, that *broked is an interesting case of paradigmatic assimilation (contrasted to *braked)! It's still using the correct past stem, but changing the ending to the regular one. If you consider that English verbs, -(e)d is the regular participle ending but constructed from the past stem (where the regular verbs have present stem = past stem), then the whole thing makes sense: brake- (present stem) > broke- (past stem) > *broked.

(In Linguistics, an asterisk (*) before a word, means that word is incorrect)

We shouldn't use words around you :-)

On this forum (and culture of the people therein), a "*" before a word (or anywhere at all) is a wild card.

> **CptPicard said:**
> How about my favourite version, **b0rked*? :)

+1

---

### Post by anotherdisciple on 2008-09-08
I'm just trying to think about forgetful people like me... haha! For instance, I would likely set up a restore point once a week. It would probably be one that makes a backup of everything.

Then, without thinking, I would upgrade to a new kernel, add something (or take something away) from my sources list, and change something in my Xorg. Then, I would find out that I severely messed up my Xorg. I know that I can restore it, but I want to keep my grub, sources, etc the same... only restore my xorg. However, the last restore point I made will reset all of those. Know what I mean?

Would it be possible to have it save all of those items by name/date, then when you go to restore, it gives you a list that says, what would you like to restore... Xorg?, GRUB?, Sources?, ALL? That would be cool. I'm not complaining about volunteer work... I appreciate what all of you are working on... I just wanted to throw in an outsider's point of view.

THANKS AGAIN!

---

### Post by Calabresi on 2008-09-08
> **LaRoza said:**
> If you need to backup and restore previously working settings, sysres can do that.

Nice, but I suppose that I need a sysres backup first. And I&#314;l read your full thread when I get home with time.


> What changed between it working and not working?

It was working fine, normal operation, reading, writing, now it keep trying to read the media CD or DVD, whatever burned or blank until timeout, it has a long timeout time.


> That might be it. I'd try a different file manager (try Thunar) to see if it can be used.

Will try thunar, but I can advance that Konqueror was not able also, btw, I saw that the Sony is not able to open some DVD content in file manager's without "gksu any-filemanager", tell me that I don't have enough permission to see the content, BUT! Is able to play the damn DVD with VLC.


> By the way, "strongly" was correct, but "broked" wasn't. It should be "it's not broken".

:D thanks

---

### Post by mssever on 2008-09-08
> **LaRoza said:**
> <rant>The bzip2 people think they are so better than gzip-pers. I'll show them...</rant>
Often, I try both to see which produces the best compression, since which one is the best depends on the input, and I don't know enough about how the respective algorithms work to accurately predict which will be best. In this particular case, I just started typing and bzip2 came out. I didn't run my tests until after I posted, when I discovered that bzip2 is slightly better for that file.
> **LaRoza said:**
> We shouldn't use words around you :-)

On this forum (and culture of the people therein), a "*" before a word (or anywhere at all) is a wild card.+1 nvteighen. I've seen the asterisk used many times to indicate a hypothetical word (often a hypothetical stem), but not on this forum. It's great having a linguist around to mix things up.

---

### Post by LaRoza on 2008-09-08
> **mssever said:**
> Often, I try both to see which produces the best compression, since which one is the best depends on the input, and I don't know enough about how the respective algorithms work to accurately predict which will be best. In this particular case, I just started typing and bzip2 came out. I didn't run my tests until after I posted, when I discovered that bzip2 is slightly better for that file.

The point is, there is no reason to use bzip2 over gzip. Anyone not using gzip is obviously a fanboy and that won't be tolerated.

</irrational>

> 
+1 nvteighen. I've seen the asterisk used many times to indicate a hypothetical word (often a hypothetical stem), but not on this forum. It's great having a linguist around to mix things up.

To nvteighen words meaning special have.

Analyze that.

---

### Post by red_Marvin on 2008-09-08
Even special words have meaning.

I am slowly working on updating the gtk version.

---

### Post by mssever on 2008-09-08
> **LaRoza said:**
> Anyone not using gzip is obviously a fanboy
What about females who use something other than gzip? How can they be fanboys? :)

---

### Post by LaRoza on 2008-09-08
> **mssever said:**
> What about females who use something other than gzip? How can they be fanboys? :)

I didn't see any females in this thread using it. Interestingly, only a girl can be a tomboy...

---

### Post by nvteighen on 2008-09-08
> **LaRoza said:**
> 
To nvteighen words meaning special have.

Analyze that.

(Sentence (Dative-Object nvteighen) (Subject words) (Accusative-Object meaning (Modifiers special)) (Verb have))

Which would yield a compiler error :p because English always places modifiers before the modified object.

(The Lisp-ish syntax is a remarkable feature from Chomsky... Did you know he worked at MIT at the same time and in the same department where McCarthy was designing Lisp? I don't know of any meeting between both, but maybe this is not coincidence... also given how Lisp seems to respect Chomsky's "Aspects of the Theory of Syntax" almost litterally...)

---

### Post by LaRoza on 2008-09-08
> **nvteighen said:**
> (Sentence (Dative-Object nvteighen) (Subject words) (Accusative-Object meaning (Modifiers special)) (Verb have))

Which would yield a compiler error :p because English always places modifiers before the modified object.

Not always.

> 
Once upon a **midnight dreary**, while I pondered, weak and weary,
Over many a quaint and curious volume of forgotten lore,
While I nodded, nearly napping, suddenly there came a tapping,
As of some one gently rapping, rapping at my chamber door.
"'Tis some visitor," I muttered, "tapping at my chamber door &#8212;
            Only this, and nothing more."


---

### Post by nvteighen on 2008-09-08
> **LaRoza said:**
> Not always.

You got me :p

---

### Post by OutOfReach on 2008-09-08
Interesting conversation you people are having here. ;)

[QUOTE=mssever]```
patch -p0 < sysresqt.py.patch.txt
```[/QUOTE]

I have never seen this technique before, seems very useful. And thanks for patching up sysresqt.py, I'm so used to creating strings as comments, gotta dump that habbit. :)

---

### Post by msserver on 2008-09-08
> **OutOfReach said:**
> Interesting conversation you people are having here. ;)
[quote=msserver]```
patch -p0 < sysresqt.py.patch.txt
```[/quote]hey tnx for sayin my name!!! but i didnt write that!!!

---

### Post by OutOfReach on 2008-09-08
> **msserver said:**
> hey tnx for sayin my name!!! but i didnt write that!!!

lol typo, that's what I get for typing fast.

---

### Post by mssever on 2008-09-08
> **OutOfReach said:**
> lol typo, that's what I get for typing fast.
I've been waiting for a chance to trot out that account. People frequently misspell my nick.

---

### Post by LaRoza on 2008-09-08
> **nvteighen said:**
> You got me :p

Your advanced knowledge can't keep up with English exceptions.

> **mssever said:**
> I've been waiting for a chance to trot out that account. People frequently misspell my nick.

Just don't use it often, dup accounts are technically not allowed: [http://ubuntuforums.org/member.php?u=628426](http://ubuntuforums.org/member.php?u=628426)

---

### Post by LaRoza on 2008-09-09
Updates:
[list]
[*] The next release (note to people following this, the code exchanged here is our way of exchanging. It is almost like getting CVS, but with less security as we have no commits and such) will not have a .deb installer, and will be focused on getting the features needed.
[*] The next release will be hosted at: savannah.nongnu.org, not sourceforge.net (no URL at this time)
[*] The next release and two will be aimed at getting this ready to be properly packages according to standards (whatever they are, people with experience in packaging, advice on structure is welcome.)
[*] We will be writing it in Java next, wait, never mind. Thanks to all the people contributing (especially the GUI devs...) and testing.
[/list]

---

### Post by mssever on 2008-09-09
> **LaRoza said:**
> 
[LIST]
[*]We will be writing it in Java next
[/LIST]
Why not write it in Whitespace? :)

---

### Post by LaRoza on 2008-09-09
> **mssever said:**
> Why not write it in Whitespace? :)

Too readable.

---

### Post by LaRoza on 2008-09-09
Restructured entire program for future .deb. Made a SystemRestore module.

Anyone doing any code, please use this (all function is the same, so anybody testing doesn't need to use this, although anyone interested in packaging should)

Attachment removed, see my next upload (same date, didn't want to confuse anyone)

---

### Post by LaRoza on 2008-09-09
> **adam_kimber said:**
> I have created a couple of variants in greyscale for you. I am not sure how to simplify as its just as S made of two arrow.... Do you have something in mind?

adam_kimber: I decided to use one of the icons (I resized it, but that hardly qualifies as work, although I mistook the image view window as one of the gimp windows and couldn't figure out why I couldn't do anything for a while...).

I got a nice desktop icon launcher thingy all set up.

Since I am using your art, could you tell us how you want your name in the credits?

---

### Post by mssever on 2008-09-09
I made a temporary installer. I also integrated the .desktop file and icon into the package. Here's the modified package and a diff.

I had to modify sysresgtk to handle the about file no longer being where it was expected. It's a kludge; any suggestions are welcome.

---

### Post by mssever on 2008-09-09
> **LaRoza said:**
> adam_kimber: I decided to use one of the icons (I resized it, but that hardly qualifies as work, although I mistook the image view window as one of the gimp windows and couldn't figure out why I couldn't do anything for a while...).

I got a nice desktop icon launcher thingy all set up.
You posted while I was working on my installer, etc. We might have duplicated work.

---

### Post by LaRoza on 2008-09-09
> **mssever said:**
> You posted while I was working on my installer, etc. We might have duplicated work.

Here is the icon I am using:
[[IMG]http://img253.imageshack.us/img253/7464/sysreslogogreyscalepf3.png[/IMG]](http://imageshack.us)
By [laroza](http://profile.imageshack.us/user/laroza)

---

### Post by mike1234 on 2008-09-09
> **LaRoza said:**
> Windows System Restore is the basis for this.

The settings are whatever the user decides save.

  

 You mean like aptoncd?

---

### Post by LaRoza on 2008-09-09
> **mssever said:**
> You posted while I was working on my installer, etc. We might have duplicated work.

Actually, we didn't really. I didn't get very far.

---

### Post by LaRoza on 2008-09-09
> **mike1234 said:**
> You mean like aptoncd?

No, like Windows System Restore.

Try it out ;)

---

### Post by LaRoza on 2008-09-09
> **mssever said:**
> 
I had to modify sysresgtk to handle the about file no longer being where it was expected. It's a kludge; any suggestions are welcome.

I had fixed that already (but I didn't update the file here.)

Here is everything updated (with your work and mine).

---

### Post by mike1234 on 2008-09-09
> **LaRoza said:**
> No, like Windows System Restore.

Try it out ;)

 What's Windows? :confused:

M.

---

### Post by mssever on 2008-09-09
With your version, when I run the installer, then sysres --gtk, I get the following: 
```
[COLOR=#0040d0]Traceback (most recent call last):
[/COLOR]  File [COLOR=#008000]"/usr/local/bin/sysres"[/COLOR], line [COLOR=#666666]35[/COLOR], in <module>
    SystemRestore[COLOR=#666666].[/COLOR]Interfaces[COLOR=#666666].[/COLOR]sysresgtk[COLOR=#666666].[/COLOR]main(rp)
  File [COLOR=#008000]"/usr/lib/python2.5/site-packages/SystemRestore/Interfaces/sysresgtk.py"[/COLOR], line [COLOR=#666666]403[/COLOR], in main
    prog [COLOR=#666666]=[/COLOR] MainProgram(rp)
  File [COLOR=#008000]"/usr/lib/python2.5/site-packages/SystemRestore/Interfaces/sysresgtk.py"[/COLOR], line [COLOR=#666666]294[/COLOR], in __init__
    textBuffer[COLOR=#666666].[/COLOR]set_text(sysres[COLOR=#666666].[/COLOR]about)
[COLOR=#0000ff]**AttributeError**[/COLOR]: 'module' object has no attribute 'about'

```Did you mean to call sysres.license, or is sysres.about missing? I couldn't figure out what you intended from looking at the code.

Also, if you--or someone--can get an SVG version of the icon, it'll look much better when scaled. Right now, it looks bad in my menu (I'm estimating that's 24x24).

---

### Post by OutOfReach on 2008-09-09
Question, the icon is supposed to be used for the Qt and GTK windows to, no?

---

### Post by mssever on 2008-09-09
> **OutOfReach said:**
> Question, the icon is supposed to be used for the Qt and GTK windows to, no?
It should be, IMO.

@LaRoza: I forgot to mention it earlier, but since my about file kludge is no longer necessary, you can remove line 50 from install.sh (the ln command), since that's now obsolete.

---

### Post by lisati on 2008-09-09
> **stevescripts said:**
> laroza 

sounds like (yet another) worthwhile effort. Keep up the good work!

Steve

+1

---

### Post by OutOfReach on 2008-09-09
Ok, because I just set it as the window icon the Qt interface, and as you can see in the attachment it isn't looking so hot. I don't know if you guys want to use a bit larger, higher res icon for the windows or what...?

---

### Post by LaRoza on 2008-09-09
> **mssever said:**
> It should be, IMO.

@LaRoza: I forgot to mention it earlier, but since my about file kludge is no longer necessary, you can remove line 50 from install.sh (the ln command), since that's now obsolete.

Here are the original images (use first): [http://ubuntuforums.org/showpost.php?p=5662253&postcount=133](http://ubuntuforums.org/showpost.php?p=5662253&postcount=133)

Ok, I should have it up to date. I forgot to give the updated system_restore.py as well.

---

### Post by LaRoza on 2008-09-09
> **OutOfReach said:**
> Ok, because I just set it as the window icon the Qt interface, and as you can see in the attachment it isn't looking so hot. I don't know if you guys want to use a bit larger, higher res icon for the windows or what...?

The original image is linked to in my above post.

If people want to use SVG, that is fine, but I don't know how to convert it, so I leave that up to those who know how. Also, feel free to edit it.

---

### Post by mssever on 2008-09-10
> **LaRoza said:**
> If people want to use SVG, that is fine, but I don't know how to convert it, so I leave that up to those who know how. Also, feel free to edit it.I'm working on it.

---

### Post by mssever on 2008-09-10
Here's an SVG.

EDIT: LaRoza, have you considered switching to some version control system? SVN is the one I know, but from what I hear, Bazaar might be more appropriate for the style of development going on in this thread. I think that using version control would simplify things greatly, now that several people are actively contributing.

---

### Post by LaRoza on 2008-09-10
> **mssever said:**
> Here's an SVG.

EDIT: LaRoza, have you considered switching to some version control system? SVN is the one I know, but from what I hear, Bazaar might be more appropriate for the style of development going on in this thread. I think that using version control would simplify things greatly, now that several people are actively contributing.

Once I get it approved on savannah.gnu.org and I learn how to use it.

---

### Post by nvteighen on 2008-09-10
Hey, this is great! Congrats to the devs! (Can you believe I hadn't downloaded this up to now? To busy with some strange projects of mine...)

But, I have a complain :)

When you execute a GUI version of sysres from terminal emulator, it doesn't give control to the shell back.

In other words, can't you do something like this, for example?:
1. Rename current "sysres" to "sysres.py"
2. Have a "sysres" shell script that executes "sysres.py --gtk &" (or --qt). For --cli, it would be overkill.

If I had *any* shell scripting skill I could have tried to write a fix and not bother you with this... :(

---

### Post by LaRoza on 2008-09-10
> **nvteighen said:**
> Hey, this is great! Congrats to the devs! (Can you believe I hadn't downloaded this up to now? To busy with some strange projects of mine...)


Glad you like it.

> 
But, I have a complain :)

When you execute a GUI version of sysres from terminal emulator, it doesn't give control to the shell back.

Most apps don't ;)

You can press "Ctrl + z" and then "bg" to put it in the background.

---

### Post by LaRoza on 2008-09-10
Lastest version (can't wait to get bzr or whatever set up!)

This has the icons and install script.

---

### Post by nvteighen on 2008-09-10
> **LaRoza said:**
> 
Most apps don't ;)

You can press "Ctrl + z" and then "bg" to put it in the background.

That doesn't work for GTK+, which takes control of interrupts. I don't know if Qt does the same.

Firefox, Nautilus and Epiphany do detach themselves from their terminal...

Of course, for debugging purposes it could be an obstacle rather than a useful feature... as you won't be able to g_print() (or whatever the PyGTK equivalent is) to show debugging messages (if you have any).

---

### Post by LaRoza on 2008-09-10
> **nvteighen said:**
> That doesn't work for GTK+, which takes control of interrupts. I don't know if Qt does the same.

Firefox, Nautilus and Epiphany do detach themselves from their terminal...

Of course, for debugging purposes it could be an obstacle rather than a useful feature... as you won't be able to g_print() (or whatever the PyGTK equivalent is) to show debugging messages (if you have any).

Run it from alt+f2 then, or use screen.

For debugging, we don't have bugs and I resent the implication that we are less than perfect.

---

### Post by Reiger on 2008-09-10
Q.e.d.? ;)

---

### Post by nvteighen on 2008-09-10
> **LaRoza said:**
> Run it from alt+f2 then, or use screen.

screen doesn't work either... as it just creates a new terminal.

Alt+F2 is the obvious thing, of course, but's a GUI accessing method. Actually, my "feature request" is looking somewhat absurd now to me...

btw, I see that Ctrl+Z works, if you focus to the terminal... but it interrupts the program (as it has to). The funny thing is that when you return control to SysRes... it detaches from its terminal :p

> For debugging, we don't have bugs and I resent the implication that we are less than perfect.

Great, what insecticide do you use? I have some bugs here and... :)

---

### Post by mssever on 2008-09-10
> **nvteighen said:**
> When you execute a GUI version of sysres from terminal emulator, it doesn't give control to the shell back.
I find the programs that do this to be annoying. Obviously daemons have to work that way, but GUIs should remain attached to their terminal. It's easy to type ```
sysres --gtk &
``` but it's not so easy to use job control on a program that detaches.

(A compromise would to make detaching an option.)

---

### Post by mssever on 2008-09-10
> **nvteighen said:**
> btw, I see that Ctrl+Z works, if you focus to the terminal... but it interrupts the program (as it has to). The funny thing is that when you return control to SysRes... it detaches from its terminal :p
I'm guessing that that's not what's really happening. When you hit ^Z, the program is suspended. You can resume it with either bg or fg. bg is equivalent to starting with &, and fg is equivalent to starting without &.

---

### Post by LaRoza on 2008-09-10
> **nvteighen said:**
> 
Alt+F2 is the obvious thing, of course, but's a GUI accessing method. Actually, my "feature request" is looking somewhat absurd now to me...

Yes, it is a GUI app (at least, for what you want.)

I am going to add another interface, to allow sysres to be used entirely from the command line (for automation, probably).

> 
Great, what insecticide do you use? I have some bugs here and... :)

I just test each bit of code as well go. I hardly edit at all without testing immediately.

---

### Post by mssever on 2008-09-10
I noticed that LaRoza provided a Hindi translation for the .desktop file. Let's get translations for other languages (since I know that we have a multilingual audience in this thread). Just provide the language code and the translations for these two strings (the name and the description): 

[LIST=1]
[*]System Restore
[*]Back up and restore important system files
[/LIST]

---

### Post by LaRoza on 2008-09-10
> **mssever said:**
> I noticed that LaRoza provided a Hindi translation for the .desktop file. Let's get translations for other languages (since I know that we have a multilingual audience in this thread). Just provide the language code and the translations for these two strings (the name and the description): 

[LIST=1]
[*]System Restore
[*]Back up and restore important system files
[/LIST]

I just wrote "sysres" in Devanagari, hardly a translation.

I have been told Hindi translations are weird on computers, so I don't think we should do them as they are probably used to English (English is the language "everyone" knows in India)

---

### Post by mssever on 2008-09-10
> **LaRoza said:**
> I just wrote "sysres" in Devanagari, hardly a translation.

I have been told Hindi translations are weird on computers, so I don't think we should do them as they are probably used to English (English is the language "everyone" knows in India)
Shows how much I know. :)

But seriously, Spanish, French, German, Dutch, etc., translations should be easy to get. And there are a lot of people who only know Spanish--though they won't benefit from sysres until it spreads beyond this English-only forum. :)

---

### Post by Reiger on 2008-09-10
Dutch translations for string (1) and (2); following the wicked mutilation-of-language-practice -- the path of which has been cleared by armies of underpaid (babelfish ?) translators working on Microsoft files; or just in keeping with the custom:
1) Systeem herstel
2) Back up en herstel belangrijke systeem bestanden.

---

### Post by LaRoza on 2008-09-10
I wrote the command line argument interface, so it can be used in a single command. It cannot add or remove files or delete anything at the moment.

---

### Post by OutOfReach on 2008-09-10
Quick update, Qt interface now uses sysres.svg as the window icon and it now uses functools to reduce (some) code redundancy. I also fixed some minor but annoying bug in the Advanced dialog.
I will get rid of any other code redundancy in later updates.

---

### Post by Kadrus on 2008-09-10
> **mssever said:**
> Shows how much I know. :)

But seriously, Spanish, French, German, Dutch, etc., translations should be easy to get. And there are a lot of people who only know Spanish--though they won't benefit from sysres until it spreads beyond this English-only forum. :)
I could translate to French and Arabic,although I am too lazy,and writing on an Arabic Keyboard is a pain :p

---

### Post by nvteighen on 2008-09-11
> **mssever said:**
> I noticed that LaRoza provided a Hindi translation for the .desktop file. Let's get translations for other languages (since I know that we have a multilingual audience in this thread). Just provide the language code and the translations for these two strings (the name and the description): 

[LIST=1]
[*]System Restore
[*]Back up and restore important system files
[/LIST]

I interpret the verbs in (2) as imperative forms. If you are meaning something else, please tell me.

Spanish:
1. Recuperación del sistema
2. Resguarde y recupere archivos de sistema importantes.

German:
1. System Wiederherstellung
2. Sichere und wiederherstelle wichtige Systemdateien.

Euskara Batua (Unified Basque... why not?):
1. Sistema berreskurapena
2. Babestu eta berreskuratu sistema-fitxategi garrantzitsuak.
(If someone here is a native Basque-speaker or "euskaldun", please review this)

Sadly, Ancient Greek and Latin don't seem to fit here...

---

### Post by Orange_and_Green on 2008-09-11
Dear Mr./Ms. LaRoza, Dear sysres developing team,

I found this thread on the forums and I was fascinated by your project. I just downloaded the latest version and tried it on my system and I was very impressed by it.

I have developed a program that automatically generates package restore scripts (see [this thread]("http://ubuntuforums.org/showthread.php?t=915712")). I understand that the purpose of your work is a bit different from mine, and on top of that, we have written our tools in different languages... Still, do you think it would be worthwhile to consider merging the two projects into a common one?

I would be very glad to hear your opinions on this matter.

I thank you for your kindness and dedication in developing open and free software. This really is true Ubuntu spirit!=D>

I wish you all a nice day:KS

---

### Post by mssever on 2008-09-11
> **nvteighen said:**
> I interpret the verbs in (2) as imperative forms. If you are meaning something else, please tell me.
Hmm. I used an imperative based on what I perceived to be the most common. But I suppose the the meaning is really more along the lines of an ancient Greek present indicative. Or maybe an English present tense. Somewhere in there. I don't know enough Spanish to know how the comments in .desktop files are typically rendered in Spanish/German/Basque. The best thing IMO would be to follow the tense in most common use.

---

### Post by nvteighen on 2008-09-11
> **Orange_and_Green said:**
> Dear Mr./Ms. LaRoza, Dear sysres developing team,

I found this thread on the forums and I was fascinated by your project. I just downloaded the latest version and tried it on my system and I was very impressed by it.

I have developed a program that automatically generates package restore scripts (see [this thread]("http://ubuntuforums.org/showthread.php?t=915712")). I understand that the purpose of your work is a bit different from mine, and on top of that, we have written our tools in different languages... Still, do you think it would be worthwhile to consider merging the two projects into a common one?

I would be very glad to hear your opinions on this matter.

I thank you for your kindness and dedication in developing open and free software. This really is true Ubuntu spirit!=D>

I wish you all a nice day:KS
I've looked at both codes and have an idea that might work... but it will require a major rewrite of aptautosave.

The idea is this: transform aptautosave's core into a shared library and design an API that way that LaRoza can use it in Python... of course, that means to write a Python binding for aptautosave... and use it as a plugin or dependency or whatever. That way, you have both projects standing by their own and still working together.

Then, the aptautosave "program" would be rewritten into a C program that calls the shared library.

Problems: 
1) aptautosave's code is a mess (also, the way you handle temporary files may be dangerous); I'm sorry to say that but it's true, so rewriting it into a shared library could be a pain. Anyway, I'd be glad to help on that.
2) We need someone to write a Python binding. I have a good level of Python, but have no clue on how that's done.

An alternative would be a system call from SysRes to execute aptautosave... if you want to have a very loose integration.

But I really see the advantage of joining forces, but as both programs are meant for different purposes, I think they should remain separate, an the "aptautosave as shared library" approach could be great to make this tool available to other projects too. Of course, it's up to you, the developers to decide on that...

Thoughts?

---

### Post by nvteighen on 2008-09-11
> **mssever said:**
> Hmm. I used an imperative based on what I perceived to be the most common. But I suppose the the meaning is really more along the lines of an ancient Greek present indicative. Or maybe an English present tense. Somewhere in there. I don't know enough Spanish to know how the comments in .desktop files are typically rendered in Spanish/German/Basque. The best thing IMO would be to follow the tense in most common use.

In Spanish and Basque, the usual thing is an imperative. But German is then wrong

So, German:
1) German:
1. System Wiederherstellung
2. Sichern und wiederherstellen von wichtigen Systemdateien. (using the infinitive, which is the common usage and also keeps thing "undefined" enough as you did in English)

---

### Post by Orange_and_Green on 2008-09-11
Dear nvteighen,

thank you very much for your suggestion. I agree on the general benefit of transforming aptautosave into a shared library with just a small "runner" executable. I'm going to start thinking about an interface that could be usable by other programs like sysres.

I agree the code is very linear and maybe difficult to read (that's why I tried to comment nearly on every line), since I actually started programming this as a tool to use on my own, before realising it might be helpful to other people as well. Time to re-think it modularly I guess :p

I was wondering if you could explain to me why the tempfiles are a bad idea. Basically, I use them to catch any "answer" stream from a shell command (like the output of ls, for example). Is there a better way to do this? I would be very happy to learn something about "good linux-programming style" as I'm pretty self-taught, unfortunately. Shamefully, I know nothing about python either...

At present, aptautosave gets its job done. I would like it to be an elegant, professionally coded program one day, and I'm ready to invest work on this. Thank you all well in advance for your support.

Have a nice day,

---

### Post by Orange_and_Green on 2008-09-11
Maybe I can help with a few languages...&#12288;I am native only for Italian though...

Italian:
1) Ripristino di sistema
2) Esegue il backup e il ripristino di importanti file di sistema.

Japanese: 
1) &#12471;&#12473;&#12486;&#12512;&#12398;&#24489;&#20803;
2) &#22823;&#20999;&#12394;&#12471;&#12473;&#12486;&#12512;&#12501;&#12449;&#12452;&#12523;&#12434;&#12496;&#12483;&#12463;&#12450;&#12483;&#12503;&#12539;&#24489;&#20803;&#33268;&#12375;&#12414;&#12377;&#12290;

French:
1) Restauration du système
2) Sauvegarde et restaure d'importants fichiers du système.

---

### Post by LaRoza on 2008-09-11
> **Orange_and_Green said:**
> Dear Mr./Ms. LaRoza, Dear sysres developing team,

I found this thread on the forums and I was fascinated by your project. I just downloaded the latest version and tried it on my system and I was very impressed by it.


> **nvteighen said:**
> An alternative would be a system call from SysRes to execute aptautosave... if you want to have a very loose integration.

But I really see the advantage of joining forces, but as both programs are meant for different purposes, I think they should remain separate, an the "aptautosave as shared library" approach could be great to make this tool available to other projects too. Of course, it's up to you, the developers to decide on that...


I already wrote a script for that, and it was originally designed to work with sysres, but I haven't kept up with it (although the only thing it needs is to store its points in the custom directories, and in a subdirectory that is ignored by listRestorePoints())

[http://ubuntuforums.org/showpost.php?p=5535477&postcount=78](http://ubuntuforums.org/showpost.php?p=5535477&postcount=78)

---

### Post by nvteighen on 2008-09-11
> **Orange_and_Green said:**
> 
I was wondering if you could explain to me why the tempfiles are a bad idea. Basically, I use them to catch any "answer" stream from a shell command (like the output of ls, for example). Is there a better way to do this? I would be very happy to learn something about "good linux-programming style" as I'm pretty self-taught, unfortunately. Shamefully, I know nothing about python either...


You're creating tempfiles assigning them a name that just by chance doesn't conflict with another tempfiles there might exist.

Use tmpfile() or friends. Then you fclose() as usual. Look at this link to see some Standard Library's functions that you may use:
[http://www.gnu.org/software/libtool/manual/libc/Temporary-Files.html](http://www.gnu.org/software/libtool/manual/libc/Temporary-Files.html)

What may be a bit difficult is to get the generated tempfile's filename...

The "Linux way" to catch commands output, if I'm not wrong, would be to use pipe functions to get interaction between processes... but I'm not familiar with them.

---

### Post by Orange_and_Green on 2008-09-11
Oh I see. Thank you nvteighen. I am glad I could learn something new.:KS Will do from now on.

---

### Post by Orange_and_Green on 2008-09-11
> **LaRoza said:**
> I already wrote a script for that, and it was originally designed to work with sysres, but I haven't kept up with it (although the only thing it needs is to store its points in the custom directories, and in a subdirectory that is ignored by listRestorePoints())

Dear LaRoza,

(I'll leave the Mr./Ms. as I think it looks a little silly... sorry about that, I didn't mean to be impolite:))

Many many thanks for your reply.
Reading the thread I originally had had that impression, but I didn't find that functionality either on the version I downloaded from the ubuntu forums nor on the one from sourceforge so I assumed I had got something wrong.

It's OK I guess. I want to follow nvteighen's advice and create a shared library anyway. Looks fun and I will surely learn lots of new programming tricks which is always a bonus. For starters, I guess I'm gonna bury my nose in books as to how to write a good shared library in the first place:)

As you do not seem to need it for your project, I'll feel free to take my time:-\"

Kudos on sysres, I think it's a really nice project and I hope to see it in the main repositories (maybe even the default installation)one day. Keep up the good work:)

---

### Post by LaRoza on 2008-09-11
> **Orange_and_Green said:**
> Dear LaRoza,

(I'll leave the Mr./Ms. as I think it looks a little silly... sorry about that, I didn't mean to be impolite:))

Hm...

Do you think it would be impolite because I have a title in Hindi and in Indian culture, the use of Mr./Ms. is impolite (in this case it would I think)?

I am not Indian, so it wouldn't be impolite :-)

> 
Kudos on sysres, I think it's a really nice project and I hope to see it in the main repositories (maybe even the default installation)one day. Keep up the good work:)

Thanks. The way it looks is not my work (except for the CLI version and command line argument interface). The core of it is my work though, and surprisingly, it has changed very little since the beginning.

I don't think it would work in a default install, because it shouldn't be used a lot (only people fiddling), but I may be overestimating the common user...

---

### Post by LaRoza on 2008-09-11
Big news!

We are on launchpad (using bazaar):

[http://bazaar.launchpad.net/~laroza/%2Bjunk/sysres/](http://bazaar.launchpad.net/~laroza/%2Bjunk/sysres/)

Tutorial on bazaar: [http://doc.bazaar-vcs.org/latest/en/mini-tutorial/index.html](http://doc.bazaar-vcs.org/latest/en/mini-tutorial/index.html)

From now on, pull from launchpad and push to it (don't upload files here for others to use)

---

### Post by OutOfReach on 2008-09-11
Cool, as I am now heading to school I will read the tutorial in about 6 hrs.

---

### Post by LaRoza on 2008-09-11
> **OutOfReach said:**
> Cool, as I am now heading to school I will read the tutorial in about 6 hrs.

Here is the page for it (it is really simple to do) [https://code.launchpad.net/~laroza/](https://code.launchpad.net/~laroza/)

Bazaar is a distributed version control system (like git, not cvs). Anyone here can create their own branches (in fact, if you are going to work on code, you should) then merge with the main branch on launchpad (easy to do, just create your branch and setup bzr: [http://doc.bazaar-vcs.org/latest/en/mini-tutorial/index.html](http://doc.bazaar-vcs.org/latest/en/mini-tutorial/index.html) and do the commands on the page: [https://code.launchpad.net/~laroza/](https://code.launchpad.net/~laroza/)) Remember to get that branch first before working on it. It includes all the work posted here. If anyone did any work (like with the translations, or un published work) get that branch and work from there. It shouldn't be that different, but it has all the changes.

Note, there are no package downloads yet, but there will be (starting with the .tar.gz and soon a .deb)

---

### Post by LaRoza on 2008-09-11
Here is a tarball of the project so far (run install script) and a .deb (double click).

It is the first .deb for it released, so testing is appreciated!

---

### Post by nvteighen on 2008-09-11
Why haven't you created a project in Launchpad...? I'm very new to it and still don't get how it works.

---

### Post by cszikszoy on 2008-09-11
Looks great LaRoza.

I suggest creating a project in Launchpad for the System Restore Utility.  Upload your code there.  This way other users can branch the code and associate their branches with your project.

---

### Post by LaRoza on 2008-09-11
> **nvteighen said:**
> Why haven't you created a project in Launchpad...? I'm very new to it and still don't get how it works.

> **cszikszoy said:**
> Looks great LaRoza.

I suggest creating a project in Launchpad for the System Restore Utility.  Upload your code there.  This way other users can branch the code and associate their branches with your project.

[https://launchpad.net/sysres](https://launchpad.net/sysres)

Ok, got it. I am new to launchpad, so advice is welcome

---

### Post by red_Marvin on 2008-09-11
Do I understand this correctly?: I should create a branch, where I submit my changes, and then from time to time you will merge (select parts of) my branch with the main project?
I've never used version control systems before, so my knowledge is quite limited. I think I have a launchpad account though. -- edit: Yes I do, I even remembered the password.

On another note though: Would it be a good idea to centralize all user visible text strings in a central file to ease translation, or how is it done on "big" projects, like ooo/firefox/ubuntu?

---

### Post by LaRoza on 2008-09-11
> **red_Marvin said:**
> Do I understand this correctly?: I should create a branch, where I submit my changes, and then from time to time you will merge (select parts of) my branch with the main project?
I've never used version control systems before, so my knowledge is quite limited. I think I have a launchpad account though. -- edit: Yes I do, I even remembered the password.

On another note though: Would it be a good idea to centralize all user visible text strings in a central file to ease translation, or how is it done on "big" projects, like ooo/firefox/ubuntu?

In theory yes, but I am still learning and this bzr is pissing me off.

I suggest you create your own branch (name it after the GUI toolkit or yourself or something). This goes for anyone doing work (unless you want to post your work here, like if you are updating one file and aren't doing much development).

I don't know about translations, although launchpad has a section on that, I don't understand it. (Besides, it is only the launcher isn't it that is getting more than one language?)

---

### Post by cszikszoy on 2008-09-11
> **LaRoza said:**
> I don't know about translations, although launchpad has a section on that, I don't understand it. (Besides, it is only the launcher isn't it that is getting more than one language?)

For internationalization you should use python's gettext module.

[http://docs.python.org/lib/module-gettext.html](http://docs.python.org/lib/module-gettext.html)

Also, there is a pretty good bzr tutorial here:
[http://www.justuber.com/blog/2007/04/25/how-to-use-bazaar-and-launchpad-for-hosting-your-code/](http://www.justuber.com/blog/2007/04/25/how-to-use-bazaar-and-launchpad-for-hosting-your-code/)

If you'd just like to play around with bzr / launchpad you can always use their staging server: [https://staging.launchpad.net/](https://staging.launchpad.net/)

Changes made to the staging server not saved, so don't worry about messing something up.

---

### Post by nvteighen on 2008-09-11
Some conclusions I've drawn from Launchpad's docs.

1. The branches are "private proprierty", in the sense that they're the place where people/team work on code.
2. The branches are then merged by the project mantainers into milestones and releases within a serie, which are development lines of the project... there are different criteria for what's considered a "serie".
3. The "trunk" series is the ever-unstable serie where you should place code in development. People should branch from there to work on the latest code.
4. To publish the program, you have to set a release and then allow download from the "download" section.

It doesn't seem that difficult, though the terminology is a bit confusing to me at first...

---

### Post by LaRoza on 2008-09-11
> **nvteighen said:**
> 
3. The "trunk" series is the ever-unstable serie where you should place code in development. People should branch from there to work on the latest code.

So far, that is the only code there.

> 
4. To publish the program, you have to set a release and then allow download from the "download" section.
Ah. Thanks. I will soon add the tarball for download. The .deb will be reserved for 1.0. I hope to have it completely newb friendly by then (download, double click, use)

> 
It doesn't seem that difficult, though the terminology is a bit confusing to me at first...

You're a linguist (or student of it), you'll figure it out. :-)

If any of the dev's are having trouble with bazaar/launchpad, just upload it here and I'll figure it out...

---

### Post by mssever on 2008-09-11
Has anyone had any success pushing to bazaar? I created a branch with no problem, but now that I want to push to it, I'm having problems. ```
$ bzr push lp:~scott.severance/sysres/mssever
bzr: ERROR: Transport operation not possible: http does not support mkdir() 
``` That's the command that my branch page says to use, so I don't know what's wrong. Note that this is my first time using bzr.

---

### Post by LaRoza on 2008-09-11
> **mssever said:**
> Has anyone had any success pushing to bazaar? I created a branch with no problem, but now that I want to push to it, I'm having problems. ```
$ bzr push lp:~scott.severance/sysres/mssever
bzr: ERROR: Transport operation not possible: http does not support mkdir() 
``` That's the command that my branch page says to use, so I don't know what's wrong. Note that this is my first time using bzr.

That is what was pissing me off. It kept doing that to me as well.

I see the branch is there, I just kept trying until it showed up...

---

### Post by mssever on 2008-09-11
> **mssever said:**
> Has anyone had any success pushing to bazaar? I created a branch with no problem, but now that I want to push to it, I'm having problems. ```
$ bzr push lp:~scott.severance/sysres/mssever
bzr: ERROR: Transport operation not possible: http does not support mkdir() 
``` That's the command that my branch page says to use, so I don't know what's wrong. Note that this is my first time using bzr.
I found the solution: [https://answers.edge.launchpad.net/bzr/+question/24695](https://answers.edge.launchpad.net/bzr/+question/24695)

It turns that you have to do ```
bzr launchpad-login your_login
```first. Though I can't figure out for the life of me why they don't give a useful error message.

---

### Post by LaRoza on 2008-09-11
> **mssever said:**
> I found the solution: [https://answers.edge.launchpad.net/bzr/+question/24695](https://answers.edge.launchpad.net/bzr/+question/24695)

It turns that you have to do ```
bzr launchpad-login your_login
```first. Though I can't figure out for the life of me why they don't give a useful error message.

Ah! Great.

Thanks.

I agree. Launchpad is too silent...

(There is no known way to delete a series...)

---

### Post by mssever on 2008-09-11
I just sent a merge request. I'm wondering if Launchpad automatically notifies you of the request, or if I need to manually notify you.

---

### Post by LaRoza on 2008-09-11
> **mssever said:**
> I just sent a merge request. I'm wondering if Launchpad automatically notifies you of the request, or if I need to manually notify you.

No, I am notified.

I pushed your changes into the trunk myself, so I didn't merge.

This isn't so hard, once you figure out you have to do that login thing...

If anyone needs help, post here.

Run:

```

bzr branch lp:sysres

```

To get the current code. Create your own branches like mssever did, for your work (perhaps mssever should describe what he did for best results)

---

### Post by mssever on 2008-09-11
> **LaRoza said:**
> (perhaps mssever should describe what he did for best results)Here's what I did, but I don't know whether it's the best way.

[LIST=1]
[*]Go to the sysres code page: [https://code.edge.launchpad.net/sysres](https://code.edge.launchpad.net/sysres)
[*]Click "register a branch"
[*]cd to the parent directory where you want to keep your sysres directory
[*]```
bzr branch lp:sysres
cd sysres
bzr launchpad-login your_launchpad_username
```
[*]Make changes as you desire. To commit your changes, type bzr commit. Unlike SVN, committing only updates your local copy.
[*]When you're ready to upload your changes, use the bzr push command listed on your branch's Launchpad page. For example, I did ```
bzr push lp:~scott.severance/sysres/mssever
``` Once you've sucessfully pushed once, you can omit the target, and just do bzr push.
[*]To notify LaRoza that your changes are ready to be merged, go to your branch's Launchpad page and click "Propose for merging into another branch."
[/LIST]

---

### Post by mssever on 2008-09-11
> **LaRoza said:**
> I pushed your changes into the trunk myself, so I didn't merge.Any particular reason? It seems to me that merging is cleaner.

---

### Post by red_Marvin on 2008-09-11
I've managed to create a branch/project (I'm a little shaky on the terminology) at [https://code.launchpad.net/~insomninja/+junk/sysres-gtk](https://code.launchpad.net/~insomninja/+junk/sysres-gtk).
What I did was

[FONT="monospace"]projectroot$ bzr init
$ bzr push lp:~insomninja/+junk/sysres-gtk
$ bzr add
$ bzr commit -m "Initial import"
$ bzr push lp:~insomninja/+junk/sysres-gtk[/FONT]

Note that this is more or less just me fooling around trying to learn bzr, and while the files in the branch are real, they are nowhere finished for any kind of release.

---

### Post by mssever on 2008-09-11
> **red_Marvin said:**
> I've managed to create a branch/project (I'm a little shaky on the terminology) at [https://code.launchpad.net/~insomninja/+junk/sysres-gtk]("https://code.launchpad.net/%7Einsomninja/+junk/sysres-gtk").
If you create a branch from [http://code.launchpad.net/sysres](http://code.launchpad.net/sysres) , then it will automatically show up as related to sysres. I think that's a cleaner approach. My interpretation (and keep in mind that I'm just learning, too) is that the +junk branches are primarily useful for stuff not related to an existing project.

EDIT: I just noticed that your branch doesn't preserve prior revisions. That's a Bad Thing. I think the instructions you followed were for new projects, not existing ones.

---

### Post by red_Marvin on 2008-09-11
New branch created: [https://code.launchpad.net/~insomninja/sysres/gtk-frontend](https://code.launchpad.net/~insomninja/sysres/gtk-frontend)

However, should I keep copies of all other sysres files in that branch too, and not only those I work on, and if so how would I go on about updating them from the main sysres branch without overwriting my own .bzr directory or the files I work on?

---

### Post by OutOfReach on 2008-09-11
OK, so as far as I understand, I have to register a branch (or whatever the correct term is), upload updates to that branch, and then it will be merged to the main project?

---

### Post by mssever on 2008-09-11
> **red_Marvin said:**
> New branch created: [https://code.launchpad.net/~insomninja/sysres/gtk-frontend]("https://code.launchpad.net/%7Einsomninja/sysres/gtk-frontend")

However, should I keep copies of all other sysres files in that branch too, and not only those I work on, and if so how would I go on about updating them from the main sysres branch without overwriting my own .bzr directory or the files I work on?

> **OutOfReach said:**
> OK, so as far as I understand, I have to register a branch (or whatever the correct term is), upload updates to that branch, and then it will be merged to the main project?
If you've never used version control before, I guess this is probably confusing. I've used SVN before, so maybe I assumed too much knowledge.

Create your branches following the instructions I posted earlier. If your branch doesn't contain the full history all the way back to LaRoza's initial upload, you've done something wrong.

Once you have your branch set up right, then just make changes as necessary. Use bzr commit to "save" your changes and bzr push to upload your changes. I don't know yet the command to get other people's changes, since no one has made changes since mine. But when you run that command, your local copy will automatically be updated. So there's no need to keep any other copies of sysres, because bzr will do the right thing automatically. Also, a full history is kept, so you can undo any changes.

Hope this helps.

EDIT: Type bzr help commands for a list of commands. Type bzr help command for help with a particular command.

EDIT 2: bzr diff and bzr status are very handy commands. Also, preface filesystem commands with bzr: e.g., bzr rm somefile, bzr mv file new_name. If you add a new file, do bzr add new_file. bzr revert is your panic button, which will revert all changes since your last commit.

---

### Post by OutOfReach on 2008-09-11
Yes I am new to this version control thing. :)

So I have a question when registering my branch. When it says Branch Type, do I leave it to the default (Mirrored)?.
Also, what should I put for the Branch URL?

---

### Post by red_Marvin on 2008-09-11
I think I've got it enough to get to work on the code.

[FONT="monospace"]bzr branch lp:sysres [COLOR="Gray"]# get the current sysres tree[/COLOR]
cd sysres
bzr push lp:~insomninja/sysres/gtk-frontend [COLOR="Gray"]# register a branch[/COLOR][/FONT]
[COLOR="Green"]...do some work...[/COLOR]
[FONT="monospace"]bzr commit -m "some comment" [COLOR="Gray"]# save the session offline[/COLOR]
bzr push lp:~insomninja/sysres/gtk-frontend [COLOR="Gray"]# upload the changes (will this download upstream changes too?)[/COLOR][/FONT]

Did I get it right this time?

---

### Post by OutOfReach on 2008-09-11
Ok, it looks like I created a new branch.
[https://code.edge.launchpad.net/~outofreach137/sysres/qt-frontend](https://code.edge.launchpad.net/~outofreach137/sysres/qt-frontend)

Now what exactly do I upload? The entire updated project, or just the file I am working on?

---

### Post by LaRoza on 2008-09-11
> **mssever said:**
> Any particular reason? It seems to me that merging is cleaner.

Yes, I pulled yours, and pushed it before I had seen the merge request.

Also, how do I merge? There is an option to queue it, and mark as merged, but no way to merge!

---

### Post by LaRoza on 2008-09-11
> **OutOfReach said:**
> Ok, it looks like I created a new branch.
[https://code.edge.launchpad.net/~outofreach137/sysres/qt-frontend](https://code.edge.launchpad.net/~outofreach137/sysres/qt-frontend)

Now what exactly do I upload? The entire updated project, or just the file I am working on?

Pull the sysres code:

```

bzr branch lp:sysres

```

Edit it, commit it, then push it into your branch.

---

### Post by LaRoza on 2008-09-11
> **red_Marvin said:**
> I think I've got it enough to get to work on the code.

[FONT="monospace"]bzr branch lp:sysres [COLOR="Gray"]# get the current sysres tree[/COLOR]
cd sysres
bzr push lp:~insomninja/sysres/gtk-frontend [COLOR="Gray"]# register a branch[/COLOR][/FONT]
[COLOR="Green"]...do some work...[/COLOR]
[FONT="monospace"]bzr commit -m "some comment" [COLOR="Gray"]# save the session offline[/COLOR]
bzr push lp:~insomninja/sysres/gtk-frontend [COLOR="Gray"]# upload the changes (will this download upstream changes too?)[/COLOR][/FONT]

Did I get it right this time?

Use this to get the current work after doing yours:

[http://doc.bazaar-vcs.org/latest/en/mini-tutorial/index.html#updating-your-branch-from-the-main-branch](http://doc.bazaar-vcs.org/latest/en/mini-tutorial/index.html#updating-your-branch-from-the-main-branch)

When you push it (the final one), it will go into your branch.

---

### Post by OutOfReach on 2008-09-11
Ahh, ok thank you for the clarification LaRoza, as I said I'm a total noob to version control.

---

### Post by LaRoza on 2008-09-11
> **OutOfReach said:**
> Ahh, ok thank you for the clarification LaRoza, as I said I'm a total noob to version control.

Some am I. I only "know" because I probably spent more time fiddling with it this day.

---

### Post by LaRoza on 2008-09-11
Since we're new, please remember to merge with the trunk before committing! So after you are done with your work, and ready to commit, run a "bzr merge" to get the latest trunk's work.

Also, you can subscribe to the trunk, but I am not sure what that means (email notifications on changes, etc)

---

### Post by red_Marvin on 2008-09-11
The gtk gui is now updated, comments and suggestions are appreciated.
The main feature is the implementation of custom directory selection.
[https://code.launchpad.net/~insomninja/sysres/gtk-frontend](https://code.launchpad.net/~insomninja/sysres/gtk-frontend)
bzr branch lp:~insomninja/sysres/gtk-frontend

---

### Post by LaRoza on 2008-09-11
> **red_Marvin said:**
> The gtk gui is now updated, comments and suggestions are appreciated.
The main feature is the implementation of custom directory selection.
[https://code.launchpad.net/~insomninja/sysres/gtk-frontend](https://code.launchpad.net/~insomninja/sysres/gtk-frontend)
bzr branch lp:~insomninja/sysres/gtk-frontend

When selecting a directory, it is choosing the previous one for some reason. I ran it from "gtksys" directory with all the code, and it opened the file select box in gtksys, when I selected the parent directory "laroza", my home, it was still created in gtksys.

It requires one to type in the name or do more clicking than needed it seems.

---

### Post by red_Marvin on 2008-09-11
Hmm, not really sure what you mean, I suppose it is the custom folder select dialog?

As far as I've noticed, the only difference between single clicking and double clicking on the folder you want to select, and then pressing ok
is that double clicking will first show the contents of the folder.

EDIT0, hmm, do you mean that the updating of the internal variable that holds the path is delayed?
EDIT1, I found one error, see if the newest commit works better.
EDIT2, merging before committing generates an error, the new version should be uploaded now
EDIT3, Good night.

---

### Post by LaRoza on 2008-09-11
> **red_Marvin said:**
> 
EDIT0, hmm, do you mean that the updating of the internal variable that holds the path is delayed?
EDIT1, I found one error, see if the newest commit works better.
EDIT2, merging before committing generates an error, the new version should be uploaded now
EDIT3, Good night.

Thanks.

Yes, I do have been doing that also. We'll get the hang of it...

Good work and good night :-)

---

### Post by red_Marvin on 2008-09-12
If you think that the interface for custom directory functionality is good, and if the bug you discovered was fixed (If not please elaborate on what causes it and I'll see what I can do), I think that my updates are mature enough to be accepted upstream.
Is this when I should "Propose for merging into another branch"?

---

### Post by LaRoza on 2008-09-12
> **red_Marvin said:**
> If you think that the interface for custom directory functionality is good, and if the bug you discovered was fixed (If not please elaborate on what causes it and I'll see what I can do), I think that my updates are mature enough to be accepted upstream.

I do not think there was a bug. I was just unused to how the GUI worked... (Yes, I get confused by GUI's, Linux gets to you like that if you let it...)

> 
Is this when I should "Propose for merging into another branch"?
Yes, but I already did.

Remember to:

```

bzr merge lp:sysres

```

To get the lastest changes in the trunk before committing. The way I see it, nothing should break unless we all start fiddling with the same files, or if I change something in system_restore.py, which I won't do without notifying everyone of what is changed if you all need to know.

---

### Post by nvteighen on 2008-09-12
There's a huge design issue here that may destroy everything in future. Sysres is an "Exception hell" where RPException handles it absolutely all like a dictator: either implementation exceptions whether interface exceptions.

The Core code should **not** have any error defined message, just pass an error code and let the interfaces handle that however they want. That will make translations easier and gives much more freedom to GUI-designers.

The "half-best" solution is to create an ErrMsg exception class at Core for interface use.

The best solution is to use return values, but that would require a big rewrite of the Core and, subsequently, of the interfaces.

Also, I really hate how you raise RPException for "file not found" or "permission denied" errors when there's IOError already for that. Just let the exception propagate and catch it as IOError on the main function.

I was working on the code on Rev 9. But I see you have merged other branches so I don't know what to do, as I was modifying system_restore.py

---

### Post by LaRoza on 2008-09-12
> **nvteighen said:**
> 
The best solution is to use return values, but that would require a big rewrite of the Core and, subsequently, of the interfaces.

Also, I really hate how you raise RPException for "file not found" or "permission denied" errors when there's IOError already for that. Just let the exception propagate and catch it as IOError on the main function.

You know, the main thing before release any code on this thread was I had to rewrite it to use exceptions, rather than return values (which I had originally used).

The main reason the exceptions work that way was because of the way the return values worked.

> 
I was working on the code on Rev 9. But I see you have merged other branches so I don't know what to do, as I was modifying system_restore.py

Not much has changed, but you can create another branch for this? You can merge now, and see what changed. Not much has changed, except a few things in sysres. You can merge, but not commit (view changes with "bzr diff") if it would break.

If you look at the blue prints, having a .deb and everything working as planned is the goal of 1.0. Perhaps better design and multilingual support should be the goal of 2.0? Can you all add blue prints?

---

### Post by nvteighen on 2008-09-12
My branch is:
lp:~evigo/sysres/sysres

Other change I did was to make the CLI compliant to the core's version of mine. Now, working for GTK+. I doubt I can do something for Qt, as I don't know the API (well, I never worked with PyGTK, always the pure C API... but I'm fine).

EDIT: Hey, 1006 posts!

---

### Post by LaRoza on 2008-09-12
> **nvteighen said:**
> My branch is:
lp:~evigo/sysres/sysres

Other change I did was to make the CLI compliant to the core's version of mine. Now, working for GTK+. I doubt I can do something for Qt, as I don't know the API (well, I never worked with PyGTK, always the pure C API... but I'm fine).

EDIT: Hey, 1006 posts!

I will look at your work. Thank you. 

I will use the other series that is so far empty for this work.

Congratulations on the posts, I don't know if 1006 is a special number though. (Oh, 1032 thanks for me ;))

---

### Post by mssever on 2008-09-12
> **LaRoza said:**
> The way I see it, nothing should break unless we all start fiddling with the same files, or if I change something in system_restore.py, which I won't do without notifying everyone of what is changed if you all need to know.
In general, bzr will do the right thing when it comes to different people changing stuff. The only problem occurs when people make incompatible changes.
> **nvteighen said:**
> The best solution is to use return values, but that would require a big rewrite of the Core and, subsequently, of the interfaces.I disagree. I think that exceptions provide more flexibility and safety than return codes (which seems awfully C-ish). I think the ideal would be to set up a hierarchy of exceptions, that way calling code can catch specific errors or a specific class of errors. So ```
[COLOR=#008000]**class**[/COLOR] [COLOR=#0000ff]**SysresError**[/COLOR]([COLOR=#d2413a]**StandardError**[/COLOR]):
    [COLOR=#ba2121]*'''Base class for all exceptions in sysres'''*[/COLOR]
    [COLOR=#008000]**pass**[/COLOR]

[COLOR=#008000]**class**[/COLOR] [COLOR=#0000ff]**CoreError**[/COLOR](SysresError):
    [COLOR=#ba2121]*'''Base class for all exceptions specific to the core'''*[/COLOR]
    [COLOR=#008000]**pass**[/COLOR]

[COLOR=#008000]**class**[/COLOR] [COLOR=#0000ff]**RulesFileError**[/COLOR](CoreError):
    [COLOR=#ba2121]*'''Error with the rules.list file'''*[/COLOR]
    [COLOR=#008000]**pass**[/COLOR]

[COLOR=#008000]**class**[/COLOR] [COLOR=#0000ff]**RestorePointError**[/COLOR](CoreError):
    [COLOR=#ba2121]*'''Error with the restore point'''*[/COLOR]
    [COLOR=#008000]**pass**[/COLOR]

etc...
```> I was working on the code on Rev 9. But I see you have merged other branches so I don't know what to do, as I was modifying system_restore.pyJust do a merge, and let bzr figure out what to do. Odds are, it'll automatically figure out the right thing.

> **LaRoza said:**
> Not much has changed, but you can create another branch for this? You can merge now, and see what changed. Not much has changed, except a few things in sysres. You can merge, but not commit (view changes with "bzr diff") if it would break.It appears that the bzr style is to use different branches for different areas of work. But yes, merging should be sufficient.

> Can you all add blue prints?Yes.

---

### Post by LaRoza on 2008-09-12
> **mssever said:**
> In general, bzr will do the right thing when it comes to different people changing stuff. The only problem occurs when people make incompatible changes.

Just do a merge, and let bzr figure out what to do. Odds are, it'll automatically figure out the right thing.

Yes, there are incompatible changes. If anyone uses the code here, it will break.

It will be in the unstable series, which will be aimed at 2.0.

> 
It appears that the bzr style is to use different branches for different areas of work. But yes, merging should be sufficient.


He could have merged, but it wouldn't have added anything. I don't think he needs to pull at all from the trunk now for the unstable series.

---

### Post by nvteighen on 2008-09-12
> **mssever said:**
> 
I disagree. I think that exceptions provide more flexibility and safety than return codes (which seems awfully C-ish). I think the ideal would be to set up a hierarchy of exceptions, that way calling code can catch specific errors or a specific class of errors. So ```
[COLOR=#008000]**class**[/COLOR] [COLOR=#0000ff]**SysresError**[/COLOR]([COLOR=#d2413a]**StandardError**[/COLOR]):
    [COLOR=#ba2121]*'''Base class for all exceptions in sysres'''*[/COLOR]
    [COLOR=#008000]**pass**[/COLOR]

[COLOR=#008000]**class**[/COLOR] [COLOR=#0000ff]**CoreError**[/COLOR](SysresError):
    [COLOR=#ba2121]*'''Base class for all exceptions specific to the core'''*[/COLOR]
    [COLOR=#008000]**pass**[/COLOR]

[COLOR=#008000]**class**[/COLOR] [COLOR=#0000ff]**RulesFileError**[/COLOR](CoreError):
    [COLOR=#ba2121]*'''Error with the rules.list file'''*[/COLOR]
    [COLOR=#008000]**pass**[/COLOR]

[COLOR=#008000]**class**[/COLOR] [COLOR=#0000ff]**RestorePointError**[/COLOR](CoreError):
    [COLOR=#ba2121]*'''Error with the restore point'''*[/COLOR]
    [COLOR=#008000]**pass**[/COLOR]

etc...
```Just do a merge, and let bzr figure out what to do. Odds are, it'll automatically figure out the right thing.

I partially disagree. I mean, yes exceptions give you more flexibility, but creating an army of highly-specific exceptions breakes code re-use. Also, most try...except blocks can be easily rewritten to use IOError instead of a new exception. (and let the OS tell what the error is).

Anyway, if people like my changes, there's the branch. Ah, I also forgot to tell the "help" has been moved out from the core to the sysres.py launcher.

---

### Post by LaRoza on 2008-09-12
New series, "unstable" with another branch in it (unstable). This code is for the next version and should not be pulled for current work, although for now we don't need much done for 1.0, just packaging and touch ups where people feel appropriate.

---

### Post by LaRoza on 2008-09-12
> **nvteighen said:**
> 
Anyway, if people like my changes, there's the branch. Ah, I also forgot to tell the "help" has been moved out from the core to the sysres.py launcher.

There is no sysres.py file...

Also, I used your branch to start the unstable series. The code was missing two important features, the ability to use the --cli option and the -h|--help and I fixed that.

---

### Post by mssever on 2008-09-12
> **LaRoza said:**
> New series, "unstable" with another branch in it (unstable). This code is for the next version and should not be pulled for current work, although for now we don't need much done for 1.0, just packaging and touch ups where people feel appropriate.
Are you working on packaging right now? I ask because I could use some packaging experience and would be willing to take a stab at it. Whether or not I'd be successful is another thing entirely! From my previous experience, I've found that difficult. I don't want to duplicate work, though.

---

### Post by LaRoza on 2008-09-12
> **mssever said:**
> Are you working on packaging right now? I ask because I could use some packaging experience and would be willing to take a stab at it. Whether or not I'd be successful is another thing entirely! From my previous experience, I've found that difficult. I don't want to duplicate work, though.

I do want this work to be duplicated. Your install script was much better than mine and we "duplicated" efforts on that, but thinkfully you never saw mine...

I did the package before, earlier in this thread. 

Here they are: [http://ubuntuforums.org/showpost.php?p=5768671&postcount=282](http://ubuntuforums.org/showpost.php?p=5768671&postcount=282)

(Code is old in that, but that is just my practicing).

I am not so good at it. I just use debianpackagemaker...

I'd appreciate any help on packaging.

When naming packages, use 

"sysres_"<version>-<date>.deb

So: sysres_0.9-20080913.deb

---

### Post by nvteighen on 2008-09-12
Ok, some news:

1) My branch has some changes. It's proposed for merge into unstable.
2) We may need a Core API; you never know: what if someone wants to write a ncurses interface? Also to keep things in order. Blueprint posted.

A question:
I'm much more fond of core developing and backend oddities rather than interfaces and applications for the end-user. I have rewritten the CLI and GTK+ interfaces from unstable to comply with the new core; Qt's still uncompliant. Should I stop touching the interfaces and get right to creating a better API, no matter what happens with the interfaces?

I mean, I'm working for unstable. You guys are working for trunk to get a usable product for users while I'm thinking in future developers. The unstable core can change quickly and trying to make the interfaces compliant in unstable may be quite a nightmere.

Ideas?

EDIT: btw, this is the first time I work on a open source project and I'm enjoying it a lot! Surely I'll learn a lot, so thanks to LaRoza for releasing this!

---

### Post by LaRoza on 2008-09-12
> **nvteighen said:**
> Ok, some news:

1) My branch has some changes. It's proposed for merge into unstable.
2) We may need a Core API; you never know: what if someone wants to write a ncurses interface? Also to keep things in order. Blueprint posted.

Ok, I will merge it (even if it breaks, its unstable for a reason).

Is there an official way to write an API? It should be simple. 

> 
Should I stop touching the interfaces and get right to creating a better API, no matter what happens with the interfaces?

You can if you want, although I recommend keeping the CLI interface working, so everyone has something to use/copy.

What do you want to change exactlY? The API is pretty good I think. Only the error handling needs work right?

The only addition I can think of is for a package restore feature (which would be relatively simple, and likely be an entire different file)

> 
I mean, I'm working for unstable. You guys are working for trunk to get a usable product for users while I'm thinking in future developers. The unstable core can change quickly and trying to make the interfaces compliant in unstable may be quite a nightmere.

What exactly are you changing? The functions and general use should be the same...right?

> 
EDIT: btw, this is the first time I work on a open source project and I'm enjoying it a lot! Surely I'll learn a lot, so thanks to LaRoza for releasing this!
First time for me too.

---

### Post by nvteighen on 2008-09-12
> **LaRoza said:**
> Ok, I will merge it (even if it breaks, its unstable for a reason).

Thank you.

> 
Is there an official way to write an API? It should be simple. 
An html document should be enough I think...

> You can if you want, although I recommend keeping the CLI interface working, so everyone has something to use/copy.

Ok. So, CLI would be a test suit.

> hat do you want to change exactlY? The API is pretty good I think. Only the error handling needs work right?

(...)

The only addition I can think of is for a package restore feature (which would be relatively simple, and likely be an entire different file)


What exactly are you changing? The functions and general use should be the same...right?

The project is relatively small, so there's nothing too much to fix. Just some details. For example, I profoundly disagree with having any default behaivor defined in the core (like the default files to be backed up: fstab, menu.lst, xorg.conf, sources.list). IMO, that should go into the interfaces... even if the "official" interfaces all provide the same defaults.

So, my aim now is to make the core be as most reusable and extensible as possible. The error handling system was for sure the most important thing, but it still has the quirk of restricting the value it can take to a string. What I want is to have a generic show() method that fires up what you want to show the error message, no matter whether GUI or text.

Please, mssever and the other guys working at the "top", tell me if you're noticing some repetitive pattern when coding, as it might be a symptom of some hole in the core API.

---

### Post by LaRoza on 2008-09-12
> **nvteighen said:**
> 
An html document should be enough I think...

XHTML you mean. I will work on it.

> 
The project is relatively small, so there's nothing too much to fix. Just some details. For example, I profoundly disagree with having any default behaivor defined in the core (like the default files to be backed up: fstab, menu.lst, xorg.conf, sources.list). IMO, that should go into the interfaces... even if the "official" interfaces all provide the same defaults.

I see what you mean. Perhaps the "defaults" can be arguments to the constructor.

<edit>

See changes. They are removed, and are supplied to the constructor. Merge with unstable to see it.

Branch 1.0 created. This is primarily aimed at the inclusion of a .deb with the release. Pull from it if you are doing packaging.

---

### Post by LaRoza on 2008-09-12
sysres 0.9 Final is released.

It has an easy to use install script, but not a .deb.

[https://launchpad.net/sysres/trunk/0.9](https://launchpad.net/sysres/trunk/0.9)

---

### Post by OutOfReach on 2008-09-12
Should I pull from lp:sysres or lp:sysres/unstable?

---

### Post by LaRoza on 2008-09-12
> **OutOfReach said:**
> Should I pull from lp:sysres or lp:sysres/unstable?

lp:~laroza/sysres/1.0 or lp:sysres

(They are the same, at the moment.)

I suggest 1.0 if you want to work on "now" work, unstable for the future.

Soon, lp:sysres will have the "unstable" code, and 1.0 work with be in 1.0. 1.0 shouldn't be much different from 0.9, just with a .deb, so if you don't see anything you want to change, you might want to work on unstable, as that is going to break the interfaces (although not in a big way, mostly with error handling), use cli.py as the model, as that should be kept up to date.

---

### Post by OutOfReach on 2008-09-12
Ok, Thank you for the informing. :)

---

### Post by LaRoza on 2008-09-12
> **OutOfReach said:**
> Ok, Thank you for the informing. :)

Well, it is better than me changing lp:sysres to the unstable code and completely wrecking everything because y'all didn't know you were supposed to use lp:~laroza/sysres/1.0 :-)

If you have any troubles with bzr, let us know. We have (I have...) spent a lot of time working with it now...

---

### Post by mssever on 2008-09-12
I don't know what happened, but the merge I tried to do from lp:~scott.severance/sysres/packaging to lp:~scott.severance/sysres/mssever hasn't happened. So, I'm requesting a merge from lp:~scott.severance/sysres/packaging through revision 18. This is a modification of the install system to comply with the Debian Python Policy, and a prequel to packaging.

My Internet connection will probably be unreliable for the next several days due to Hurricane Ike. I'm far enough inland that I don't anticipate damage, but the forcasts predict a lot of rain and a bit of wind (45-50 MPH), which will probably disrupt my satellite Internet.

---

### Post by OutOfReach on 2008-09-12
Ok, i've made some changes from the 1.0 branch, I merged from that branch, commited, and when I tried to push the changes to my branch, it says ```
bzr: ERROR: Transport operation not possible: http does not support mkdir()
```
So I tried: ```
bzr launchpad-login outofreach137
``` and it gives me ```
bzr: ERROR: The user outofreach137 has not registered any SSH keys with Launchpad.
```

---

### Post by mssever on 2008-09-12
> **OutOfReach said:**
> ```
bzr: ERROR: The user outofreach137 has not registered any SSH keys with Launchpad.
```Go to [https://launchpad.net/~outofreach137/+editsshkeys]("https://launchpad.net/%7Eoutofreach137/+editsshkeys") and add your SSH key.

---

### Post by LaRoza on 2008-09-12
Register you SSH keys. Just go to your page and check out the guides. That at least is straight forward.

(You don't need to install anything, just run the commands)

---

### Post by LaRoza on 2008-09-12
> **mssever said:**
> I don't know what happened, but the merge I tried to do from lp:~scott.severance/sysres/packaging to lp:~scott.severance/sysres/mssever hasn't happened. So, I'm requesting a merge from lp:~scott.severance/sysres/packaging through revision 18. This is a modification of the install system to comply with the Debian Python Policy, and a prequel to packaging.

I pulled the packaging stuff long ago and added it (check the code to make sure).

I do merges without being asked sometimes...

Pull from 1.0 to get everything together.

> 
My Internet connection will probably be unreliable for the next several days due to Hurricane Ike. I'm far enough inland that I don't anticipate damage, but the forcasts predict a lot of rain and a bit of wind (45-50 MPH), which will probably disrupt my satellite Internet.
Hope everything goes smoothly.

Now that most of you are here, pull from lp:~laroza/sysres/1.0 for current work. Although lp:sysres is the same at the moment, it will be the same as unstable soon.

---

### Post by cszikszoy on 2008-09-12
> **OutOfReach said:**
> Ok, i've made some changes from the 1.0 branch, I merged from that branch, commited, and when I tried to push the changes to my branch, it says ```
bzr: ERROR: Transport operation not possible: http does not support mkdir()
```So I tried: ```
bzr launchpad-login outofreach137
``` and it gives me ```
bzr: ERROR: The user outofreach137 has not registered any SSH keys with Launchpad.
```

Well the "No Sh!t" answer is that you need to register a SSH key with launchpad :)

This is quite trivial actually.  Follow this link:

[https://edge.launchpad.net/~YOUR_LP_USER_NAME/+editsshkeys](https://edge.launchpad.net/~YOUR_LP_USER_NAME/+editsshkeys)

Where YOUR_LP_USER_NAME is well... your launchpad user name.

At the bottom it has a box where you can enter your SSH key and import it.

If you don't know how to generate SSH keys look here:
[https://wiki.edubuntu.org/DocumentationTeam/SystemDocumentation/Repository#Generating%20SSH%20keys](https://wiki.edubuntu.org/DocumentationTeam/SystemDocumentation/Repository#Generating%20SSH%20keys)

---

### Post by OutOfReach on 2008-09-12
Alright, thanks for the help guys I managed to push to my branch. I really need to get more experience with this :/.

---

### Post by LaRoza on 2008-09-12
> **OutOfReach said:**
> Alright, thanks for the help guys I managed to push to my branch. I really need to get more experience with this :/.

You'll get it quickly. We all did, and it was our first time (mine with any sort of version control system)

[http://doc.bazaar-vcs.org/latest/en/mini-tutorial/index.html#updating-your-branch-from-the-main-branch](http://doc.bazaar-vcs.org/latest/en/mini-tutorial/index.html#updating-your-branch-from-the-main-branch)

---

### Post by LaRoza on 2008-09-12
> **OutOfReach said:**
> Alright, thanks for the help guys I managed to push to my branch. I really need to get more experience with this :/.
Never mind, you did...

---

### Post by OutOfReach on 2008-09-12
EDIT: Ok nevermind then. :P

---

### Post by LaRoza on 2008-09-12
Big update. Do not pull from lp:sysres except to get "unstable" code.

Use: lp:~laroza/sysres/1.0 to do development for the next release.

---

### Post by nvteighen on 2008-09-13
> **LaRoza said:**
> Big update. Do not pull from lp:sysres except to get "unstable" code.

Use: lp:~laroza/sysres/1.0 to do development for the next release.
Great. That was something I wanted to request, but you were faster!

Launchpad doc recommends to have a stable "unstable" serie and to branch stable code from it.

---

### Post by LaRoza on 2008-09-13
> **nvteighen said:**
> Great. That was something I wanted to request, but you were faster!

When I originally set it up, I was happy to get it to work at all. 

Now that I can use it with no problems (and it is very easy to use, even the merge of unstable with 1.0 wasn't hard), I saw how sloppy the design was (also, like some people, this is my first project not done by myself and my first time using any sort of version control)

If anyone does try to merge with lp:sysres (and has 1.0, or 0.9 like branches), they won't be able to without doing a couple more steps anyway.

---

### Post by LaRoza on 2008-09-14
I wrote up a man page (easier than I thought, but hell of a syntax), it is in 1.0, but I don't know how such things are installed...

---

### Post by mssever on 2008-09-14
> **LaRoza said:**
> I wrote up a man page (easier than I thought, but hell of a syntax), it is in 1.0, but I don't know how such things are installed...
By "1.0", do you mean lp:sysres/testing? I'll add the man page to the installer.

I've debianized sysres, but for some reason, it's only installing directories, not files. I'm working on the branch lp:~scott.severance/sysres/packaging. If anyone knows what's wrong, I'd love to hear. I don't think the lintian errors are relevant, and I don't know how to fix them, anyway. (I haven't Googled yet...)

Here's the debuild -S output: ```
 dpkg-buildpackage -rfakeroot -d -us -uc -S
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package sysres
dpkg-buildpackage: source version 0.9
dpkg-buildpackage: source changed by Scott Severance <scott@scottseverance.us>
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
#-/usr/bin/make clean
dh_clean 
 dpkg-source -b sysres-0.9
dpkg-source: building sysres in sysres_0.9.tar.gz
dpkg-source: building sysres in sysres_0.9.dsc
 dpkg-genchanges -S >../sysres_0.9_source.changes
dpkg-genchanges: including full source code in upload
dpkg-buildpackage: source only upload: Debian-native package
Now running lintian...
E: sysres_0.9_source.changes: bad-distribution-in-changes-file hardy
W: sysres source: dh-make-template-in-source debian/sysres.doc-base.EX
W: sysres source: dh-make-template-in-source debian/manpage.sgml.ex
W: sysres source: dh-make-template-in-source debian/preinst.ex
W: sysres source: dh-make-template-in-source debian/postrm.ex
W: sysres source: dh-make-template-in-source debian/manpage.xml.ex
W: sysres source: dh-make-template-in-source debian/watch.ex
W: sysres source: dh-make-template-in-source debian/postinst.ex
W: sysres source: dh-make-template-in-source debian/menu.ex
W: sysres source: dh-make-template-in-source debian/sysres-default.ex
W: sysres source: dh-make-template-in-source debian/prerm.ex
W: sysres source: dh-make-template-in-source debian/manpage.1.ex
Finished running lintian.
Now signing changes and any dsc files...
 signfile sysres_0.9.dsc Scott Severance <scott@********>

 signfile sysres_0.9_source.changes Scott Severance <scott@******>

Successfully signed dsc and changes files
```

Here's the pbuilder output: ```
I: using fakeroot in build.
Current time: Sun Sep 14 20:27:52 CDT 2008
pbuilder-time-stamp: 1221442072
Building the build Environment
 -> extracting base tarball [/var/cache/pbuilder/base.tgz]
 -> creating local configuration
 -> copying local configuration
 -> mounting /proc filesystem
 -> mounting /dev/pts filesystem
-> Mounting /home/scott/bin/install/pbuilder/result
 -> policy-rc.d already exists
Obtaining the cached apt archive contents
Installing the build-deps
Executing hook: tmp/hooks/D70results
 ! Package scribes (filename ./scribes_0.3.2.6-1_all.deb) is repeat;
   ignored that one and using data from ./scribes_0.3.2.6-1scott1_all.deb !
 ! Package php-pear (filename ./php-pear_5.1.2-1ubuntu3.4~scott1_all.deb) is repeat;
   ignored that one and using data from ./php-pear_5.1.2-1ubuntu3.4scott1_all.deb !
 ** Packages in archive but missing from override file: **
  audacity curl db4.5-doc db4.5-util debhelper diatheke gnomesword
  libcurl3 libcurl3-dbg libcurl3-gnutls libcurl4-gnutls-dev libcurl4-
  openssl-dev libdb4.5 libdb4.5++ libdb4.5++-dev libdb4.5-dev
  libdb4.5-java libdb4.5-java-dev libdb4.5-tcl libsword-dev libsword6
  php-pear po4a scribes specto toppler

 Wrote 26 entries to output Packages file.
Ign file: ./ Release.gpg
Ign file: ./ Release
Ign file: ./ Packages
Get:1 http://archive.ubuntu.com gutsy Release.gpg [191B]
Hit http://archive.ubuntu.com gutsy Release                                                                                   
Hit http://archive.ubuntu.com gutsy/main Packages                                                                             
Hit http://archive.ubuntu.com gutsy/restricted Packages                                                                       
Hit http://archive.ubuntu.com gutsy/universe Packages                                                                         
Hit http://archive.ubuntu.com gutsy/multiverse Packages                                                                       
Fetched 1B in 9s (0B/s)                                                                                                       
Reading package lists... Done
 -> user script /var/cache/pbuilder/build//16308/tmp/hooks/D70results finished
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  dh-make cvs gettext-doc
Recommended packages:
  curl wget lynx libmail-sendmail-perl libcompress-zlib-perl
The following NEW packages will be installed:
  debhelper file gettext html2text intltool-debian libmagic1 po-debconf python-support
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.2kB/2714kB of archives.
After unpacking 10.8MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com gutsy/main python-support 0.6.4ubuntu1 [25.2kB]
Fetched 25.2kB in 1s (12.8kB/s)        
Selecting previously deselected package libmagic1.
(Reading database ... 12297 files and directories currently installed.)
Unpacking libmagic1 (from .../libmagic1_4.21-1_i386.deb) ...
Selecting previously deselected package file.
Unpacking file (from .../archives/file_4.21-1_i386.deb) ...
Selecting previously deselected package python-support.
Unpacking python-support (from .../python-support_0.6.4ubuntu1_all.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-3build1_i386.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.16.1-2ubuntu3_i386.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.35.0+20060710.1_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_1.0.9_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_5.0.51ubuntu3_all.deb) ...
Setting up libmagic1 (4.21-1) ...

Setting up file (4.21-1) ...
Setting up python-support (0.6.4ubuntu1) ...

Setting up html2text (1.3.2a-3build1) ...

Setting up gettext (0.16.1-2ubuntu3) ...

Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up po-debconf (1.0.9) ...
Setting up debhelper (5.0.51ubuntu3) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  fakeroot
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/111kB of archives.
After unpacking 442kB of additional disk space will be used.
Selecting previously deselected package fakeroot.
(Reading database ... 12868 files and directories currently installed.)
Unpacking fakeroot (from .../fakeroot_1.7.1ubuntu1_i386.deb) ...
Setting up fakeroot (1.7.1ubuntu1) ...

Copying back the cached apt archive contents
 -> new cache content python-support_0.6.4ubuntu1_all.deb added
Copying source file
    -> copying [sysres_0.9.dsc]
    -> copying [./sysres_0.9.tar.gz]
Extracting source
gpg: new configuration file `/tmp/buildd/.gnupg/gpg.conf' created
gpg: WARNING: options in `/tmp/buildd/.gnupg/gpg.conf' are not yet active during this run
gpg: Signature made Mon Sep 15 01:26:17 2008 UTC using DSA key ID 515CB2D7
gpg: Can't check signature: public key not found
dpkg-source: extracting sysres in sysres-0.9
dpkg-source: unpacking sysres_0.9.tar.gz
 -> Building the package
W: no hooks of type A found -- ignoring
dpkg-buildpackage: source package is sysres
dpkg-buildpackage: source version is 0.9
dpkg-buildpackage: source changed by Scott Severance <scott@scottseverance.us>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 0.9
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
#-/usr/bin/make clean
dh_clean 
 dpkg-source -b sysres-0.9
dpkg-source: warning: unknown information field 'Homepage' in input data in general section of control info file
dpkg-source: building sysres in sysres_0.9.tar.gz
dpkg-source: building sysres in sysres_0.9.dsc
 debian/rules build
#dh_testdir
# Add here commands to configure the package.
#touch configure-stamp
#dh_testdir
# Add here commands to compile the package.
#/usr/bin/make
#docbook-to-man debian/sysres.sgml > sysres.1
#touch build-stamp
 fakeroot debian/rules binary
#dh_testdir
# Add here commands to configure the package.
#touch configure-stamp
#dh_testdir
# Add here commands to compile the package.
#/usr/bin/make
#docbook-to-man debian/sysres.sgml > sysres.1
#touch build-stamp
dh_testdir
dh_clean
dh_testroot
dh_installdirs
dh_installdeb
# Add here commands to install the package into debian/sysres.
# /usr/bin/make DESTDIR=/tmp/buildd/sysres-0.9/debian/sysres install
DESTDIR=/tmp/buildd/sysres-0.9/debian//usr ./install.sh /usr
`about' -> `/tmp/buildd/sysres-0.9/debian//usr/share/doc/sysres/about'
`changelog' -> `/tmp/buildd/sysres-0.9/debian//usr/share/doc/sysres/changelog'
`code_standards' -> `/tmp/buildd/sysres-0.9/debian//usr/share/doc/sysres/code_standards'
`COPYING' -> `/tmp/buildd/sysres-0.9/debian//usr/share/doc/sysres/COPYING'
`README' -> `/tmp/buildd/sysres-0.9/debian//usr/share/doc/sysres/README'
`AUTHORS' -> `/tmp/buildd/sysres-0.9/debian//usr/share/doc/sysres/AUTHORS'
`SystemRestore' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore'
`SystemRestore/Interfaces' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore/Interfaces'
`SystemRestore/Interfaces/arguments.py' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore/Interfaces/arguments.py'
`SystemRestore/Interfaces/sysresqt.py' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore/Interfaces/sysresqt.py'
`SystemRestore/Interfaces/__init__.py' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore/Interfaces/__init__.py'
`SystemRestore/Interfaces/images' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore/Interfaces/images'
`SystemRestore/Interfaces/images/properties.png' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore/Interfaces/images/properties.png'
`SystemRestore/Interfaces/images/delete-all.png' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore/Interfaces/images/delete-all.png'
`SystemRestore/Interfaces/images/restore.png' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore/Interfaces/images/restore.png'
`SystemRestore/Interfaces/images/application-exit.png' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore/Interfaces/images/application-exit.png'
`SystemRestore/Interfaces/images/add.png' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore/Interfaces/images/add.png'
`SystemRestore/Interfaces/images/about.png' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore/Interfaces/images/about.png'
`SystemRestore/Interfaces/images/preferences.png' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore/Interfaces/images/preferences.png'
`SystemRestore/Interfaces/qrc_resources.py' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore/Interfaces/qrc_resources.py'
`SystemRestore/Interfaces/sysresgtk.py' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore/Interfaces/sysresgtk.py'
`SystemRestore/Interfaces/cli.py' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore/Interfaces/cli.py'
`SystemRestore/Interfaces/compoundwidgets.py' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore/Interfaces/compoundwidgets.py'
`SystemRestore/__init__.py' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore/__init__.py'
`SystemRestore/Core' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore/Core'
`SystemRestore/Core/__init__.py' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore/Core/__init__.py'
`SystemRestore/Core/system_restore.py' -> `/tmp/buildd/sysres-0.9/debian//usr/share/sysres/SystemRestore/Core/system_restore.py'
`sysres' -> `/tmp/buildd/sysres-0.9/debian//usr/bin/sysres'
`sysres.svg' -> `/tmp/buildd/sysres-0.9/debian//usr/share/pixmaps/sysres.svg'
`sysres.desktop' -> `/tmp/buildd/sysres-0.9/debian//usr/share/applications/sysres.desktop'
Modifying search path...
rm -f /tmp/buildd/sysres-0.9/debian//usr/share/sysres/install_log /tmp/buildd/sysres-0.9/debian//usr/share/sysres/install_created_directories || true
dh_pysupport
dh_compress
dh_fixperms
#dh_clean
dh_gencontrol
dpkg-gencontrol: warning: unknown information field 'C Homepage' in input data in general section of control info file
dpkg-gencontrol: warning: unknown substitution variable ${python:Depends}
dh_md5sums
dh_builddeb
dpkg-deb: building package `sysres' in `../sysres_0.9_all.deb'.
 dpkg-genchanges
dpkg-genchanges: including full source code in upload
dpkg-buildpackage: full upload; Debian-native package (full source is included)
W: no hooks of type B found -- ignoring
Copying back the cached apt archive contents
 -> unmounting /home/scott/bin/install/pbuilder/result filesystem
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> cleaning the build env 
    -> removing directory /var/cache/pbuilder/build//16308 and its subdirectories
Current time: Sun Sep 14 20:28:33 CDT 2008
pbuilder-time-stamp: 1221442113
```NOTE: I'm running Hardy, not Gutsy, but my pbuilder tarball is gutsy, and due to my limited bandwidth, I'm loath to switch it--and it shouldn't matter.

---

### Post by LaRoza on 2008-09-14
> **mssever said:**
> By "1.0", do you mean lp:sysres/testing? I'll add the man page to the installer.

Yes, I forgot about that and have been calling it lp:~laroza/sysres/1.0

> 
I've debianized sysres, but for some reason, it's only installing directories, not files. I'm working on the branch lp:~scott.severance/sysres/packaging. If anyone knows what's wrong, I'd love to hear. 

I can't help directly, but my package I made worked (used [http://code.google.com/p/debianpackagemaker/downloads/list](http://code.google.com/p/debianpackagemaker/downloads/list))

---

### Post by pavel989 on 2008-09-14
how does it save stuff? into one text file?/ is it encrypted or something? im just asking out of curiosity. cuz like this can start taking up a lot of space, and it can be messed with.


but its a great idea.

---

### Post by LaRoza on 2008-09-15
> **pavel989 said:**
> how does it save stuff? into one text file?/ is it encrypted or something? im just asking out of curiosity. cuz like this can start taking up a lot of space, and it can be messed with.

The API documentation (see the announcements [https://launchpad.net/sysres](https://launchpad.net/sysres)) explains it mostly.

It is not encrypted, but the files are securely named (so one could use it to do /home/laroza/importantfile.text and /home/mssever/importantfile.text without any conflicts)

A single restore point in .sysres results in 4 kilobytes of storage needed.


> 
but its a great idea.

More than an idea...

---

### Post by mssever on 2008-09-15
Just a thought: For parsing the command line arguments, have you considered the optparse module? The more options sysres supports, the greater the benefit to using optparse.

---

### Post by LaRoza on 2008-09-15
> **mssever said:**
> Just a thought: For parsing the command line arguments, have you considered the optparse module? The more options sysres supports, the greater the benefit to using optparse.

Probably, but I don't see the arguments growing much. Perhaps adding delete in there, but it is not a priority. That is a rather "advanced" use and the target user is going to be using the GUI's. I wrote the CLI first because I didn't care about how it looked and wanted it to work, and I wrote the command line arguments for myself actually :-)

---

### Post by OutOfReach on 2008-09-15
> **mssever said:**
> Just a thought: For parsing the command line arguments, have you considered the optparse module? The more options sysres supports, the greater the benefit to using optparse.

I'm all for optparse, it's flexible and more powerful (or so they say).

---

### Post by LaRoza on 2008-09-15
> **OutOfReach said:**
> I'm all for optparse, it's flexible and more powerful (or so they say).

I'll look into it.

If I add any arguments, I'll think about using it more.

---

### Post by OutOfReach on 2008-09-15
If you would like, I can cover that for you. (If you are planning on using it)

---

### Post by LaRoza on 2008-09-15
> **OutOfReach said:**
> If you would like, I can cover that for you. (If you are planning on using it)

I'll handle it. It is the interface I use (not the GUI's...) so I should take the time to work on the fourth interface for this program :-)

---

### Post by LaRoza on 2008-09-15
Upon further review, I don't think getopts will work very well.

---

### Post by mssever on 2008-09-15
> **LaRoza said:**
> Upon further review, I don't think getopts will work very well.There's a difference between getopts and optparse.

---

### Post by LaRoza on 2008-09-15
> **mssever said:**
> There's a difference between getopts and optparse.

Amazing how going to another page can lose something.

I'll look into it, but right now I am going to bed.

---

### Post by nvteighen on 2008-09-15
Ok, conflict -> first branch divergence. I've merged trunk new changes up to rev. 35.

LaRoza: Why is help() now inside the core again? Can you please explain me why did you do that? I just don't want to merge things into my branch that I don't understand.

---

### Post by nvteighen on 2008-09-15
Btw, I've noticed something regarding restore point conflicts... well, they are impossible! As the restore point is named using the timestamp, it's absolutely impossible to set two restore points with the very same filename if you use a SysRes-client application... Of course, unless you play with the system time... or you rename the restore points by hand, etc. but an application just can't cover any silly thing a user does with his/her computer.

Maybe we can reduce a big amount of code regarding error handling because of this: removing RPException, remove a lot of try...except blocks on GUI modules and increasing the code readability. ErrMsg would be a facility interface coders can have to centralize error messaging.

I'll be working on this and, if possible, will publish some test suits for ErrMsg'ing in GUI modules.

---

### Post by OutOfReach on 2008-09-15
We could probably remove some unnecessary except blocks, but not all since we wouldn't want uncaught exceptions.

---

### Post by nvteighen on 2008-09-15
> **OutOfReach said:**
> We could probably remove some unnecessary except blocks, but not all since we wouldn't want uncaught exceptions.
The problem is not the amount, but what and where we're catching. Most of the errors that propagate from the core are IOError exceptions that IMO, should be caught by interfaces.

---

### Post by LaRoza on 2008-09-15
> **nvteighen said:**
> Ok, conflict -> first branch divergence. I've merged trunk new changes up to rev. 35.

LaRoza: Why is help() now inside the core again? Can you please explain me why did you do that? I just don't want to merge things into my branch that I don't understand.

It is just there to keep the function working without having to deal with it. The help() function should put the output of the helptext variable (so any interface can use it), but that doesn't exist in trunk yet.

The reason it was moved out of sysres was to prevent it from calling the Python help() function (try it).

I was thinking of getting rid of help() and have a file with all the constants (version, license, helptext, etc) that any interface could use (see sysres -h would manually print SystemRestore.Constants.helptext or whatever)

---

### Post by LaRoza on 2008-09-15
> **nvteighen said:**
> Btw, I've noticed something regarding restore point conflicts... well, they are impossible! As the restore point is named using the timestamp, it's absolutely impossible to set two restore points with the very same filename if you use a SysRes-client application... Of course, unless you play with the system time... or you rename the restore points by hand, etc. but an application just can't cover any silly thing a user does with his/her computer.

I'll be working on this and, if possible, will publish some test suits for ErrMsg'ing in GUI modules.

Yes, conflicts were the first concern of mine. Most of my time was making sure restore points didn't conflict and that files wouldn't conflict (so if someone added two files with the same name, but different locations, there wouldn't be any confusion). I think I solved any chance of that.

Hack away... :-)

> **nvteighen said:**
> The problem is not the amount, but what and where we're catching. Most of the errors that propagate from the core are IOError exceptions that IMO, should be caught by interfaces.

My original version used return values, so the methods of SystemRestore's return value would have to be checked. I later changed it to exceptions which drastically reduced the code.

---

### Post by LaRoza on 2008-09-15
> I always forget to update the changelog, is it really needed now when we use bzr?

Yes, it is.

---

### Post by LaRoza on 2008-09-15
Remember to merge with lp:~laroza/sysres/1.0 if you are aimed at after you do work. If people start diverging too far, merging will be a nightmare.

Also, I just did a lot to trunk, and I am sure I broke the QT interface (as did anyone else doing work on that, because of the changes and our inability to update it).

---

### Post by nvteighen on 2008-09-15
> **LaRoza said:**
> It is just there to keep the function working without having to deal with it. The help() function should put the output of the helptext variable (so any interface can use it), but that doesn't exist in trunk yet.

The reason it was moved out of sysres was to prevent it from calling the Python help() function (try it).

I was thinking of getting rid of help() and have a file with all the constants (version, license, helptext, etc) that any interface could use (see sysres -h would manually print SystemRestore.Constants.helptext or whatever)

The problem is that the help function should be interface-specific... I mean, each interface could work differently... And nobody will use the core directly, unless the user is a developer (and there the API doc is the help).

Or am I missing the point of what you want the help() to be?

---

### Post by LaRoza on 2008-09-15
> **nvteighen said:**
> The problem is that the help function should be interface-specific... I mean, each interface could work differently... And nobody will use the core directly, unless the user is a developer (and there the API doc is the help).

Or am I missing the point of what you want the help() to be?

And it now is. See the latest changed. help() and any version of it doesn't exist in 1.0 and in trunk.

---

### Post by nvteighen on 2008-09-15
Ok, LaRoza, I've merged from trunk. "Differences" between you and me solved as I sorta see what you're trying to do.

Anyway, the constants interface does much more sense than having them "hardcoded" inside the core.

---

### Post by mssever on 2008-09-15
> **LaRoza said:**
> The reason it was moved out of sysres was to prevent it from calling the Python help() function (try it).Why not rename it print_help()?

> I was thinking of getting rid of help() and have a file with all the constants (version, license, helptext, etc) that any interface could use (see sysres -h would manually print SystemRestore.Constants.helptext or whatever)The optparse module can automatically generate the help text, which means one less file to maintain. Otherwise, I think that each of those constants should be in individual plain text files and read in when necessary. That would provide maximum flexibility.

> **LaRoza said:**
> Yes, it is.We're going to have to do something to tame the changelog beast, since there are now three separate changelogs: The original one, the bzr one, and the Debian package one. We could try autogenerating the changelog, or maybe you could impose a changelog policy and not merge unless that policy is followed. I don't know what the answer is, but I think the current situation is broken.

> **LaRoza said:**
> Remember to merge with lp:~laroza/sysres/1.0 if you are aimed at after you do work. If people start diverging too far, merging will be a nightmare.I'd like to make a suggestion here, based in part on a discussion this morning in #ubuntu-programming. I think that the official branch situation is too complex. These ideas come roughly from GNOME:

[LIST=1]
[*]lp:sysres/stable and lp:sysres/testing should be abolished.
[*]lp:sysres (aka trunk) should be the development focus from which we all merge. There should be a policy that trunk should never be broken in a major way. Large-scale changes, or those that cause major breakage should happen in other branches, which aren't granted special status in the lp:sysres namespace. There might be occasions when it would be beneficial for us to merge from each other's branches, or to form a separate special-purpose common branch. But it shouldn't be in the lp:sysres namespace, and it should be temporary. (This would also suggest that you should maintain a separate branch for your work, as well, and merge into trunk as appropriate.)
[*]There should be a policy that those who make changes are responsible for ensuring a clean merge into trunk. That way, if people diverge too far, it's their fault. They should be able to merge from trunk and resolve the conflicts that way.
[*]When it's time for a release, trunk should be feature frozen, and the focus should be on fixing any bugs that need to be fixed. Then, lp:sysres/1.1 (or whatever) should be branched off and used for the release. Changes should be limited to critical bugfixes.
[*]There might be benefit in starting a sysres group if we decide that we want multiple people to have write access to a branch for some purpose.
[/LIST]

---

### Post by nvteighen on 2008-09-15
> **mssever said:**
> 
I'd like to make a suggestion here, based in part on a discussion this morning in #ubuntu-programming. I think that the official branch situation is too complex. These ideas come roughly from GNOME:

[LIST=1]
[*]lp:sysres/stable and lp:sysres/testing should be abolished.
[*]lp:sysres (aka trunk) should be the development focus from which we all merge. There should be a policy that trunk should never be broken in a major way. Large-scale changes, or those that cause major breakage should happen in other branches, which aren't granted special status in the lp:sysres namespace. There might be occasions when it would be beneficial for us to merge from each other's branches, or to form a separate special-purpose common branch. But it shouldn't be in the lp:sysres namespace, and it should be temporary. (This would also suggest that you should maintain a separate branch for your work, as well, and merge into trunk as appropriate.)
[*]There should be a policy that those who make changes are responsible for ensuring a clean merge into trunk. That way, if people diverge too far, it's their fault. They should be able to merge from trunk and resolve the conflicts that way.
[*]When it's time for a release, trunk should be feature frozen, and the focus should be on fixing any bugs that need to be fixed. Then, lp:sysres/1.1 (or whatever) should be branched off and used for the release. Changes should be limited to critical bugfixes.
[*]There might be benefit in starting a sysres group if we decide that we want multiple people to have write access to a branch for some purpose.
[/LIST]

+1 

The idea behind bzr's way to do things is that people can mess with the code, break things, commit to their branch and then request things to be merged into the parent branch without messing anything else.

But, what it will be difficult is how to deal the transition to that workflow. I really would go for giving priority to trunk, as anyway code not compatible with the new core will be useless in the near future.

---

### Post by LaRoza on 2008-09-15
> **mssever said:**
> Why not rename it print_help()?

In case you didn't see the code yet, there is no function to print it out (in the SystemRestore module).

Instead, I moved all non core code from non system_restore.py, and put it in SystemRestore/Constants. The license, help, version and...the other variable I can't remember is in there.

> 
We're going to have to do something to tame the changelog beast, since there are now three separate changelogs: The original one, the bzr one, and the Debian package one. We could try autogenerating the changelog, or maybe you could impose a changelog policy and not merge unless that policy is followed. I don't know what the answer is, but I think the current situation is broken.

I agree. When I first made the launchpad sysres, I was happy to get it to work. Then I decided to fix it up based on the lack of original design.

Now I have to make it work.

> 
[LIST=1]
[*]lp:sysres/stable and lp:sysres/testing should be abolished.
[*]lp:sysres (aka trunk) should be the development focus from which we all merge. There should be a policy that trunk should never be broken in a major way. Large-scale changes, or those that cause major breakage should happen in other branches, which aren't granted special status in the lp:sysres namespace. There might be occasions when it would be beneficial for us to merge from each other's branches, or to form a separate special-purpose common branch. But it shouldn't be in the lp:sysres namespace, and it should be temporary. (This would also suggest that you should maintain a separate branch for your work, as well, and merge into trunk as appropriate.)
[*]There should be a policy that those who make changes are responsible for ensuring a clean merge into trunk. That way, if people diverge too far, it's their fault. They should be able to merge from trunk and resolve the conflicts that way.
[*]When it's time for a release, trunk should be feature frozen, and the focus should be on fixing any bugs that need to be fixed. Then, lp:sysres/1.1 (or whatever) should be branched off and used for the release. Changes should be limited to critical bugfixes.
[*]There might be benefit in starting a sysres group if we decide that we want multiple people to have write access to a branch for some purpose.
[/LIST]

1. stable is the release code, and shouldn't change. All work is aimed at 1.0 and the future. Perhaps we should get rid of it.
2. Way too late. Trunk is broken in many ways (in a good way, as the core is improving, just the interfaces...) The problem (if it is) is that I and you (and the GUI devs) are working towards 1.0, while the trunk is new and exciting. I do maintain a separate branch for my work, but it is not hosted on launchpad. 
3. I agree. I do not merge into trunk or into any other branch unless it has already pulled the changes. 
4. A problem is that trunk is not aimed at 1.0 and is very different. Should we keep trunk up to date with that or with what is aimed at the next release? After we do 1.0, which was essentially packaging and touchups, we'll have an easier time of it I think.

---

### Post by LaRoza on 2008-09-15
> **nvteighen said:**
> 
The idea behind bzr's way to do things is that people can mess with the code, break things, commit to their branch and then request things to be merged into the parent branch without messing anything else.


It is all your fault you know ;)

Since I am not doing the packaging, I am focused on both branches for 1.0 and trunk. After 1.0, we will have an easier time of it, because we'll all be using trunk.

---

### Post by LaRoza on 2008-09-15
> **mssever said:**
> ...

I see you have "This branch is for code ready to be merged with trunk. I try to keep it free of major bugs." for [https://code.launchpad.net/~scott.severance/sysres/mssever](https://code.launchpad.net/~scott.severance/sysres/mssever)

Is that true? trunk is full of major bugs (interface related) and I can't see how you are doing work on that...

---

### Post by mssever on 2008-09-15
> **LaRoza said:**
> 1. stable is the release code, and shouldn't change. All work is aimed at 1.0 and the future. Perhaps we should get rid of it.
2. Way too late. Trunk is broken in many ways (in a good way, as the core is improving, just the interfaces...) The problem (if it is) is that I and you (and the GUI devs) are working towards 1.0, while the trunk is new and exciting. I do maintain a separate branch for my work, but it is not hosted on launchpad. 
3. I agree. I do not merge into trunk or into any other branch unless it has already pulled the changes. 
4. A problem is that trunk is not aimed at 1.0 and is very different. Should we keep trunk up to date with that or with what is aimed at the next release? After we do 1.0, which was essentially packaging and touchups, we'll have an easier time of it I think.
My comments were mostly geared for post-1.0. But I still think that names like stable and testing are somewhat confusing for those of use who have not yet been assimilated. :) And what happens once there have been several releases? That's why I think that there should be lp:sysres/0.9, lp:sysres/1.0, lp:sysres/1.1, etc. But in the future, those branches should only be created at release time.

Specifically re: 4: I think that was a mistake. It would have been better, IMO, to either: make the changes and fix the breakage before 1.0; or let nvteighen make his changes, and have people pull from him if they're working on his new stuff, and make one big merge when appropriate. Of course, that's water under the bridge now, but perhaps we can learn something for next time. I don't think that any of us have been in a multi-person project before, so mistakes are to be expected.

---

### Post by mssever on 2008-09-15
> **LaRoza said:**
> I see you have "This branch is for code ready to be merged with trunk. I try to keep it free of major bugs." for [https://code.launchpad.net/~scott.severance/sysres/mssever]("https://code.launchpad.net/%7Escott.severance/sysres/mssever")

Is that true? trunk is full of major bugs (interface related) and I can't see how you are doing work on that...
I guess that's not quite accurate. It's tracking testing, not trunk. But it took me quite a while to figure out your naming scheme.

It should be ready to merge with testing, aka 1.0.

---

### Post by LaRoza on 2008-09-15
> **mssever said:**
> My comments were mostly geared for post-1.0. But I still think that names like stable and testing are somewhat confusing for those of use who have not yet been assimilated. :) And what happens once there have been several releases? That's why I think that there should be lp:sysres/0.9, lp:sysres/1.0, lp:sysres/1.1, etc. But in the future, those branches should only be created at release time.

We will remove the names soon. However, I can't really delete a series (for some reason).

We will have stable changed to 0.9 and testing changed to 1.0.

---

### Post by LaRoza on 2008-09-15
> **mssever said:**
> I guess that's not quite accurate. It's tracking testing, not trunk. But it took me quite a while to figure out your naming scheme.

It should be ready to merge with testing, aka 1.0.

Ah, ok. I don't even know my scheme....

First time doing such things you know...

So your code (already merged into 1.0) is ready (from your POV) for packaging and release?

Could you make the .deb and upload it here so I can test it?

testing (1.0) will be frozen if this is all ready.

---

### Post by mssever on 2008-09-15
> **LaRoza said:**
> First time doing such things you know...Mine too.

> So your code (already merged into 1.0) is ready (from your POV) for packaging and release?Yes.

---

### Post by LaRoza on 2008-09-15
> **mssever said:**
> 
Yes.

Could you upload it?

---

### Post by mssever on 2008-09-15
> **LaRoza said:**
> Could you upload it?
I don't understand. I've already pushed my branch and you've merged it.

---

### Post by mssever on 2008-09-15
> **LaRoza said:**
> Could you make the .deb and upload it here so I can test it?
I didn't see your edit. I'll post the deb in a little bit.

---

### Post by LaRoza on 2008-09-15
> **mssever said:**
> I didn't see your edit. I'll post the deb in a little bit.

Well, I started to do it, but I got:

```

debuild -S -sa
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
#-/usr/bin/make clean
#dh_clean 
 dpkg-source -b sysres-1.0
dpkg-source: building sysres in sysres_1.0.tar.gz
dpkg-source: building sysres in sysres_1.0.dsc
 dpkg-genchanges -S -sa
dpkg-genchanges: including full source code in upload
dpkg-buildpackage (debuild emulation): source only upload: Debian-native package
Now signing changes and any dsc files...
 signfile sysres_1.0.dsc Scott Severance <scott@scottseverance.no.spam.us>
gpg: skipped "Scott Severance <scott@scottseverance.no.spam.us>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available
debsign: gpg error occurred!  Aborting....
debuild: fatal error at line 1174:
running debsign failed
~/sysreswork/sysres-1.0$

```

Perhaps you are missing a step or there is a file you don't need in there?

---

### Post by mssever on 2008-09-15
> **LaRoza said:**
> Well, I started to do it, but I got:
That's because you don't have my GPG private key. :) debuild tries to sign the package using the email address given in debian/changelog. I get that same error, too, because I'm not willing to post an un-mangled e-mail address where spambots can harvest it. And signing is only necessary to get the package into the universe (in which case it would be signed by a MOTU, presumably).

The changes I merged in today broke the deb, so I'm trying to track down the problem.

---

### Post by LaRoza on 2008-09-15
> **mssever said:**
> That's because you don't have my GPG private key. :) debuild tries to sign the package using the email address given in debian/changelog. I get that same error, too, because I'm not willing to post an un-mangled e-mail address where spambots can harvest it. And signing is only necessary to get the package into the universe (in which case it would be signed by a MOTU, presumably).

The changes I merged in today broke the deb, so I'm trying to track down the problem.

I figured as much, but then those instructions are for you then not the rest of us ;)

---

### Post by mssever on 2008-09-15
> **LaRoza said:**
> I figured as much, but then those instructions are for you then not the rest of us ;)
I guess I should clarify them a bit. The instructions are for everyone, but the way .deb files work, the person who builds the source package (debuild -S) is also supposed to add an entry to debian/changelog. I don't know quite how the various packaging GUIs work, but the ones I've used before generate packages that violate policy. Once we get the changelog issue stramlined, it should be possible to write a release script to simplify this process. (Normally, upstream doesn't bother with packaging. But, we're upstream, and we need a .deb...)

I'm getting the following traceback from sysres when installed by the .deb: ```
Traceback (most recent call last):
  File "/usr/bin/sysres", line 95, in <module>
    start_gtk(rp)
  File "/usr/bin/sysres", line 65, in start_gtk
    SystemRestore.Interfaces.sysresgtk.main(rp)
  File "/usr/share/sysres/SystemRestore/Interfaces/sysresgtk.py", line 494, in main
    prog = MainProgram(rp)
  File "/usr/share/sysres/SystemRestore/Interfaces/sysresgtk.py", line 367, in __init__
    textBuffer.set_text("".join(open("about", "r").readlines()))
IOError: [Errno 2] No such file or directory: 'about'
```I don't know this code very well, but the problem apparently is that the about file is installed in /usr/share/doc/sysres, and sysres doesn't know to look there. For some reason that I can't explain, the install script works fine. Since I'm not very familiar with that portion of the code, perhaps someone could suggest a fix.

---

### Post by mssever on 2008-09-15
> **mssever said:**
> Since I'm not very familiar with that portion of the code, perhaps someone could suggest a fix.
I've got a fix in lp:~scott.severance/sysres/mssever ready for merging. Here's a .deb built from my branch.

---

### Post by OutOfReach on 2008-09-15
Is there anything that I can help with? Or anything needs fixing? I'm feeling a little out of place here. :redface:

---

### Post by LaRoza on 2008-09-15
> **mssever said:**
> I don't know this code very well, but the problem apparently is that the about file is installed in /usr/share/doc/sysres, and sysres doesn't know to look there. For some reason that I can't explain, the install script works fine. Since I'm not very familiar with that portion of the code, perhaps someone could suggest a fix.

I fixed it.

That looks like a weird conflict, as that was fixed a while ago I think.

In short, all constants are in SystemRestore.Constants namespace now, although they used to be in SystemRestore.Core.system_restore. I fixed it. 1.0 should be good to go now.

---

### Post by LaRoza on 2008-09-15
> **OutOfReach said:**
> Is there anything that I can help with? Or anything needs fixing? I'm feeling a little out of place here. :redface:

At the moment, 1.0 should be done as far as code goes. 

Right now, the focus should be on the .deb for 1.0, and the work in trunk.

GUI devs...you have to do some reading as a lot is changing. sysresgtk.py has been updated a bit by the people doing the work on the core, but sysresqt.py hasn't been touched...

Pull from lp:sysres

---

### Post by LaRoza on 2008-09-15
> **mssever said:**
> I've got a fix in lp:~scott.severance/sysres/mssever ready for merging. Here's a .deb built from my branch.

Sorry about that...

Your fix (whatever it was) wasn't the same optimal one I had so I am guess you did something less elegant no offense.

This problem should have been fixed (I remember doing it).

The current branch code is already.

---

### Post by OutOfReach on 2008-09-15
> **LaRoza said:**
> At the moment, 1.0 should be done as far as code goes. 

Right now, the focus should be on the .deb for 1.0, and the work in trunk.

GUI devs...you have to do some reading as a lot is changing. sysresgtk.py has been updated a bit by the people doing the work on the core, but sysresqt.py hasn't been touched...

Pull from lp:sysres

Ok, I'll pull from lp:sysres and get to work (if there is any)

---

### Post by LaRoza on 2008-09-15
> **OutOfReach said:**
> Ok, I'll pull from lp:sysres and get to work (if there is any)

There should be...

The error handling has been redone a bit, so you'll have to look into that. I haven't followed that much, but it seems like it should give you more flexibility.

---

### Post by OutOfReach on 2008-09-15
Thanks. I'll take a peep at the GTK interface and the core to follow up on changes.

---

### Post by mssever on 2008-09-15
> **LaRoza said:**
> Sorry about that...

Your fix (whatever it was) wasn't the same optimal one I had so I am guess you did something less elegant no offense.

This problem should have been fixed (I remember doing it).

The current branch code is already.
I had several conflicts on that file. I might have resolved them wrong. At any rate, here's a deb from my current revision. It should be identical to 1.0. I hope.

By the way, no need to apologize for criticizing my code. That's what peer review is about. :)

---

### Post by LaRoza on 2008-09-15
> **mssever said:**
> I had several conflicts on that file. I might have resolved them wrong. At any rate, here's a deb from my current revision. It should be identical to 1.0. I hope.

By the way, no need to apologize for criticizing my code. That's what peer review is about. :)

Thanks. I merged your recent changes (I noticed sysres wasn't executable) with the current 1.0 code.

I am mostly apologising for not reading your code and making assumptions :-)

---

### Post by LaRoza on 2008-09-15
Ok, I tested out the .deb and everything seems to work as well as it does (meaning, no new issues).

I pushed a minor change into lp:sysres/1.0 and once that is deb-ified, we'll release and celebrate and do our best to break trunk...

Thanks for all the help. I get the feeling some are doing more work than I did...

Also, perhaps it would be nice to have a script or more exact instructions on making the .deb?

I'll try to do it but I may fail...

---

### Post by OutOfReach on 2008-09-15
Ok, I'm pretty much finished with the updating on the Qt interface, I've pushed the changes to my branch.

---

### Post by mssever on 2008-09-15
> **LaRoza said:**
> Thanks for all the help. I get the feeling some are doing more work than I did...Success is getting others to do your work for you.... :)

> Also, perhaps it would be nice to have a script or more exact instructions on making the .deb?
Yes, I've been thinking about a release script. I use one for Net Responsibility, and it simplifies things greatly, even though it's badly-written. I'll have to think about how best to accomplish that.

Here's the latest debian package. I'm including both the source and binary packages. If you can set up a PPA for sysres, then we can upload the source package and let Launchpad build and publish the .debs for us. Plus, we get a repo. Of course, any one of us can set up our own PPAs. I have one, though I haven't put anything there yet. But one specifically for sysres would be more elegant.

---

### Post by LaRoza on 2008-09-15
> **mssever said:**
> Y
Here's the latest debian package. I'm including both the source and binary packages. If you can set up a PPA for sysres, then we can upload the source package and let Launchpad build and publish the .debs for us. Plus, we get a repo. Of course, any one of us can set up our own PPAs. I have one, though I haven't put anything there yet. But one specifically for sysres would be more elegant.

I have one on launchpad.

I have one set up. I will try to get it working (something new to learn...)

---

### Post by LaRoza on 2008-09-16
I have good news everyone...

sysres-1.0 didn't restore at all, and since I had tested that code and it had worked I hadn't tested it again. A user found it.

The files weren't being written back. Actually, it will delete the files if ran.

I immediately removed the downloads

The current lp:sysres/1.0 has the current code and needs to be repackaged.

The program was malicious with this bit of code missing...

---

### Post by OutOfReach on 2008-09-16
Wow, malicious?
Glad the user caught it before it could spread.

---

### Post by LaRoza on 2008-09-16
> **OutOfReach said:**
> Wow, malicious?
Glad the user caught it before it could spread.

I swear that wasn't in there before. (Actually, I found it was malicious).

I am going to go over the bzr logs to see how it happened.

Until then, pull from lp:sysres (for unstable) or lp:sysres/1.0

mssever, since you are the one with the packaging knowledge... :-)

---

### Post by OutOfReach on 2008-09-16
Might it be possible that it was caused by a merge gone wrong?

---

### Post by LaRoza on 2008-09-16
I found where it changed. It was before using bzr, but after I had shared code.

Since I used the latest code of each version for my personal archive, I do not have the history.

---

### Post by LaRoza on 2008-09-16
> **OutOfReach said:**
> Might it be possible that it was caused by a merge gone wrong?

No, it happened before I used bzr. It could have happened during any of the file sharing here. It was probably an innocent edit, but it resulted in the files being opened (in write mode, which deletes content or creates files)

I had not tested the restore feature at all because I knew it worked and the calling was the same.

From now one, I will test it much more where it counts...

---

### Post by OutOfReach on 2008-09-16
Ah, well I guess we should test the program from top to bottom before releasing it next time, eh?

---

### Post by mssever on 2008-09-16
> **LaRoza said:**
> mssever, since you are the one with the packaging knowledge... :-)Your wish is my command. :)

I bumped the version number to make it easier for any users who might still have sysres installed to upgrade. There's a small change in lp:~scott.severance/sysres/mssever for merging into lp:sysres/1.0.

On an unrelated note, I've been going through the core API to try to learn my way around, and I've done a fair amount of work on documenting it. I added the API doc to the source tree, but my major focus is the docstrings themselves. (I'm a bit concerned that an external APT doc could end up outdated after a while, and I think that docstrings would have a better chance of staying up to date. Plus, there exist tools to auto-generate API documentation in HTML format from the docstrings.) In the process, I found a few bugs, and several places where I wasn't sure what the code was intended to do. I marked all the spots with the string FIXME, which vim nicely highlights. Those sections would benefit from input from those who know that codebase better. My changes are in my new main branch, lp:~scott.severance/sysres/main, which is ready for merging into trunk.

---

### Post by LaRoza on 2008-09-16
> **mssever said:**
> Your wish is my command. :)

Thanks. I was mortified about that bug...

Also, I noticed a bug in the GTK interface when restoring. I'll explore that later (it does restore, but says it doesn't and has a typo in the message box...).

To test this facet, remove all the default files from the rules and add a test file. 

> 
I bumped the version number to make it easier for any users who might still have sysres installed to upgrade. There's a small change in lp:~scott.severance/sysres/mssever for merging into lp:sysres/1.0.

Merging..

> 
On an unrelated note, I've been going through the core API to try to learn my way around, and I've done a fair amount of work on documenting it. I added the API doc to the source tree, but my major focus is the docstrings themselves. (I'm a bit concerned that an external APT doc could end up outdated after a while, and I think that docstrings would have a better chance of staying up to date. Plus, there exist tools to auto-generate API documentation in HTML format from the docstrings.) In the process, I found a few bugs, and several places where I wasn't sure what the code was intended to do. I marked all the spots with the string FIXME, which vim nicely highlights. Those sections would benefit from input from those who know that codebase better. My changes are in my new main branch, lp:~scott.severance/sysres/main, which is ready for merging into trunk.
I'll look into it.

---

### Post by OutOfReach on 2008-09-16
My branch (lp:~outofreach137/sysres/qt-frontend) is also ready for a merge into the trunk.

---

### Post by LaRoza on 2008-09-16
> **mssever said:**
> 
On an unrelated note, I've been going through the core API to try to learn my way around, and I've done a fair amount of work on documenting it. I added the API doc to the source tree, but my major focus is the docstrings themselves. (I'm a bit concerned that an external APT doc could end up outdated after a while, and I think that docstrings would have a better chance of staying up to date. Plus, there exist tools to auto-generate API documentation in HTML format from the docstrings.) In the process, I found a few bugs, and several places where I wasn't sure what the code was intended to do. I marked all the spots with the string FIXME, which vim nicely highlights. Those sections would benefit from input from those who know that codebase better. My changes are in my new main branch, lp:~scott.severance/sysres/main, which is ready for merging into trunk.

```

def restoreToDefault(self):
        '''Deletes the log and rules files. FIXME: Why?'''
        os.remove(self.log)
        os.remove(self.rules)

```

Because it is customizable and I don't want to put it on the burden of the user to remember what the defaults where.

```

def listRestorePoints(self,dirt="default",custom=False):
        """Lists restore points in directory
        
        Arguments:
            dirt:   FIXME: This appears to serve the same purpose as mode does in
                    self.makeRestorePoint(), only with a different name. The names
                    should be standardized to a name that describes what it does.
                    Also, dirt does nothing if it is set to anything other than
                    "default".
            custom: If False (the default), delete the files list.rules and
                    log.log. FIXME: Why is it useful to delete files in a list
                    method?
        """

```
dirt stands for "directory", because dir was highlighted (paranoia from JavaScript and PHP, large global namespaces. If the editor highlights it, don't use it).

If it is not given, it is assumed it is a default restore point (in ~/.sysres) and is assigned to the variable "self.sysres" which is the location of that directory. If it is not set, it is used as it is (because it is a directory for a custom restore point area)

The files are removed because they will show up as restore points (or cause other issues). I may have fixed this problem in the listing methods recently. These files are not made in custom restore points, so they don't need to be deleted from the list.


```

class SystemRestore:
    """System Restore Class
    
    This class handles the configuration and state for sysres.
    
    Properties:
        home:   The name of the user's home directory
        sysres: The name of the sysres configuration directory, ~/.sysres
        rules:  The name of the rules file
        log:    The name of the log file
        root_configuration_files: A list of filenames to backup/restore FIXME: Is this correct?
        extra:  FIXME: What's this for? It appears to be the same as self.root_configuration_files
    """

```

root_configuration_files used to be hard coded into the program (and was a list of the default files to be backed up). It is named "root" because the files are not writable by the user without root permissions.

extra used to have another name, local_configuration_files which were writable by the user. The default list is written to the log if it doesn't exist (restoreToDefault() will delete it, wiping any custom rules and causing the default ones to be written back when sysres is run). Now, the file list for restore points is read from a list within the restore point.

---

### Post by Def13b on 2008-09-16
First things first, this program is great so thanks to all of you that are working on it.

Now, I've been trying to follow this as you all do you magic to see how a project develops over time and hopefully learn a few things, something I noticed while reading system_restore.py is it imports both sys and time, neither of which appear to be used in the code, I was wondering if this is something that was from an earlier version or am I missing something?

---

### Post by nvteighen on 2008-09-16
> **LaRoza said:**
> Thanks. I was mortified about that bug...

Also, I noticed a bug in the GTK interface when restoring. I'll explore that later (it does restore, but says it doesn't and has a typo in the message box...).


Wait a bit, what bug in GTK+? The popup windows that don't appear on "Permission denied"? I was tracking that one, but as I wasn't sure if it was fixed at stable or not, I didn't want to bring up a false alarm.

By the way, I expect to have a major revision for the new core, because I fear for a very subtle but nasty bug at ErrMsg, so be prepared for a new breakage :)

---

### Post by LaRoza on 2008-09-16
> **Def13b said:**
> 
Now, I've been trying to follow this as you all do you magic to see how a project develops over time and hopefully learn a few things, something I noticed while reading system_restore.py is it imports both sys and time, neither of which appear to be used in the code, I was wondering if this is something that was from an earlier version or am I missing something?

So far you will have learned:

[list]
[*] It takes one person to start a project, but it greatly benefits from others
[*] Version control can be a pain, especially when you are new to it...
[*] Bugs...
[*] Code that isn't perfect (you are right, time and sys aren't used, will edit code. Thanks)
[*] The last person to find bugs is the original programmer.
[/list]

---

### Post by LaRoza on 2008-09-16
> **nvteighen said:**
> Wait a bit, what bug in GTK+? The popup windows that don't appear on "Permission denied"? I was tracking that one, but as I wasn't sure if it was fixed at stable or not, I didn't want to bring up a false alarm.

By the way, I expect to have a major revision for the new core, because I fear for a very subtle but nasty bug at ErrMsg, so be prepared for a new breakage :)

No, in 1.0(.1).

---

### Post by LaRoza on 2008-09-16
Ok, since this is aimed at Ubuntu users, using gtk, the gtk version needs to be better.

So far:

[list]
[*] Running as root. The menu entry should be run as root, as it is impossible to do without using a custom launcher, alt + f2/terminal and "gkusudo". This is probably something for the installer.
[*] Making restore points and looking for them. The CLI version looks for them and makes them in ~./sysres. The GTK version doesn't. If run as root, it makes them in /root/.sysres
[*] Restoring. Restoring has no errors and gives false errors when the custom files are writable as the user (although it does restore them)
[/list]

---

### Post by nvteighen on 2008-09-16
Guys and gals,

well, my fears were completely unfounded... moreover, the ErrMsg system is way more powerful than I thought! But it has a little minor syntax flaw caused by forcing Python to be Lisp (the way to execute ErrMsg involves something like this **e.force()(args...)**). I'll code a little wrapper that allow people to delay arguments together with the function, but essentially it will be just some fancy interface to help people not used to closures and lazy evaluation, so no breakage will occur and you might use the system you like more.

btw, LaRoza, every merge you do makes RPException reappear... :p

---

### Post by LaRoza on 2008-09-16
> **nvteighen said:**
> btw, LaRoza, every merge you do makes RPException reappear... :p

The definition or the use of it?

---

### Post by nvteighen on 2008-09-16
> **LaRoza said:**
> The definition or the use of it?
Thank God, just the definition :)

---

### Post by red_Marvin on 2008-09-16
> **LaRoza said:**
> [list]
[*] Making restore points and looking for them. The CLI version looks for them and makes them in ~./sysres. The GTK version doesn't. If run as root, it makes them in /root/.sysres
[*] Restoring. Restoring has no errors and gives false errors when the custom files are writable as the user (although it does restore them)
[/list]

I only use system_restore's homegrown built in methods for creating/listing/restoring (;p) I'm not saying that it isn't a bug bug, but it could be that my nongtk code is a little old, since I'm quite confused about which branch I should base sysres-gtk on, and being in a dante's merge/commit/conflict inferno right now.

Should I base my work on sysres/sysres or sysres/1.0?

---

### Post by LaRoza on 2008-09-16
> **red_Marvin said:**
> 
Should I base my work on sysres/sysres or sysres/1.0?

Well, I would like 1.0 fixed up, that should be the priority for this.

The interfaces for the trunk are important, but not as important as we have a lot of time.

It may be due to the use of gksudo, but the program isn't run with that. The false error when restoring is also an issue.

Replicate by:

[list]
[*] Customise the rules by adding a file in your $HOME (a test file)
[*] Make a restore point.
[*] Change that file.
[*] Try to restore.
[/list]

It will restore it, but it will say it didn't and you get an error. The CLI interface doesn't do this.

That should be the first fix.

---

### Post by LaRoza on 2008-09-16
> **nvteighen said:**
> Thank God, just the definition :)

I make sure it is gone when I do any pushing into trunk.

Another thing for the interfaces, when editing rules, any IO errors are ignored (although printed to terminal). When I run the program as root, the list.rules and log.log were owned by root, so they can't be changed by the user. The GUI's ignore this, the GTK one (sorry to pick on you). The QT interface ignores the exceptions, but doesn't remove the file from the list. The GTK one ignores the errors, but it seems like it is working.

---

### Post by OutOfReach on 2008-09-16
> **LaRoza said:**
> 
Another thing for the interfaces, when editing rules, any IO errors are ignored (although printed to terminal). When I run the program as root, the list.rules and log.log were owned by root, so they can't be changed by the user. The GUI's ignore this, the GTK one (sorry to pick on you). The QT interface ignores the exceptions, but doesn't remove the file from the list. The GTK one ignores the errors, but it seems like it is working.

Can you elaborate on that, please? I'm sorry for being pushy but I don't really understand this, and I don't want to go and end up 'fixing' the wrong thing.

---

### Post by LaRoza on 2008-09-16
> **LaRoza said:**
> Replicate by:

[list]
[*] Customise the rules by adding a file in your $HOME (a test file)
[*] Make a restore point.
[*] Change that file.
[*] Try to restore.
[/list]


> **OutOfReach said:**
> Can you elaborate on that, please? I'm sorry for being pushy but I don't really understand this, and I don't want to go and end up 'fixing' the wrong thing.

Do the above list, but as root (wipe ./sysres first, to emulate a first time use).

Now, run sysres as user, and try to edit the rules. (run from terminal to see the issues)

---

### Post by LaRoza on 2008-09-16
The root permissions issue is related to gksudo. When using sudo, it doesn't happen, but when gksudo is used...

The only problem is we can't use sudo from a launcher.

---

### Post by OutOfReach on 2008-09-16
Ok, I changed the rules list, made a backup, changed the original file, and when I try to restore (as root):
I get a ```
ValueError: list.index(x): x is not in list
```


And when I run as a regular user again and try to edit the rules I get an IOError that the permission was denied when trying to change the rules file.

These two things were supposed to happen, no?

---

### Post by LaRoza on 2008-09-16
> **OutOfReach said:**
> Ok, I changed the rules list, made a backup, changed the original file, and when I try to restore (as root):
I get a ```
ValueError: list.index(x): x is not in list
```

And when I run as a regular user again and try to edit the rules I get an IOError that the permission was denied when trying to change the rules file.

Yes.

> 
These two things were supposed to happen, no?
No. It is supposed to work ;)

I found it is the use of gksudo that does it. I am not sure of a solution. My initial idea was to have the launcher just launch with gksudo, but then it wouldn't work with the cli versions (which don't have this problem).

We need to somehow record the users home while running it with gksudo...

Alternatively, we could have it recorded when it is installed, where the users home is.

---

### Post by LaRoza on 2008-09-16
Ok, the gksudo thing has a work around.

If sysres is run with gksudo, it will set the user as "/root".

I did something evil. If the user's home is "/root", the constructor for SystemRestore will be halted.

Now, to fix this (only the GUI's have to do this and I don't know the toolkits, sorry) it should be simple.

Two new functions were added:

[list]
[*] listUsers(): Will return a list of users.
[*] setUserName(<name>): Will fix the internal structure of the SystemRestore object so the program can continue.
[/list]

So, for the GUI devs:

When sysres is run with gksudo, you will need to manually set the user immediately. This should be in the form of a popup that has a list of users to select (the names will be returned by listUsers() and the selected name should be passed to setUserName(<name>).

It should fix the issue. We could lie and say it is a feature to help it support more than one user, but it is a work around, although simple.

After this is done, the shortcut should run sysres with gksudo.

---

### Post by OutOfReach on 2008-09-16
Ok, I'll check it out. And do what I must

---

### Post by LaRoza on 2008-09-16
> **OutOfReach said:**
> Ok, I'll check it out. And do what I must

It shouldn't be too hard I hope. Just immediately do that bit as soon as the GUI starts. For added usability, you could test to see if it is needed, but since the GUI's will be run with gksudo anyway, I don't think it is, unless people are going to be running this from the terminal.

I added something else. You can test to see if it is needed, by checking to see if rp.halt is True.

So, in psuedo code:

```

#before anything is done with the passed RestorePoint object
if rp.halt:
    selection = makeSelectionBox(listUsers())
    rp.setUserName(selection)
#contine as normal

```

makeSelectionBox would be just a popup box with a list returned by SystemRestore.Core.system_restore.listUsers() and return the selected user.

---

### Post by mssever on 2008-09-16
> **LaRoza said:**
> dirt stands for "directory", because dir was highlighted (paranoia from JavaScript and PHP, large global namespaces. If the editor highlights it, don't use it).Do you mind if I change the variable name here and in the related methods (where I presume mode means the same) to 'directory'? IIRC, Python tends to frown on abbreviations, and it took me quite a while to decipher some of the abbreviations in the core, since I haven't been assimilated.

> The files are removed because they will show up as restore points (or cause other issues). I may have fixed this problem in the listing methods recently. These files are not made in custom restore points, so they don't need to be deleted from the list.That would be worth a test. Personally, I don't like functions that have undocumented side-effects. At the minimum, I'll add that to the documentation.


> root_configuration_files used to be hard coded into the program (and was a list of the default files to be backed up). It is named "root" because the files are not writable by the user without root permissions.

extra used to have another name, local_configuration_files which were writable by the user. The default list is written to the log if it doesn't exist (restoreToDefault() will delete it, wiping any custom rules and causing the default ones to be written back when sysres is run). Now, the file list for restore points is read from a list within the restore point.So should these be documented like that, or refactored out, or changed to private (name beginning with an underscore)?
> **LaRoza said:**
> Ok, the gksudo thing has a work around.

If sysres is run with gksudo, it will set the user as "/root".

I did something evil. If the user's home is "/root", the constructor for SystemRestore will be halted.
Actually, there's a better solution. Running ```
gksudo env
```shows that gksudo sets the environment variable SUDO_USER to the username of the user running the program.  So you can forget about messing with this in the UIs and handle it in Core: ```
if 'SUDO_USER' in os.environ:
    self.username = os.environ['SUDO_USER']
else:
    self.username = os.environ['USER']
self.home = os.path.expanduser('~%s' % self.username)
```With this information, you can also chown files as appropriate. I'll change the launcher to use gksudo.

Oh, a wrinkle: KDE uses kdesu, not gksudo. I guess we'll have to detect KDE once again...

---

### Post by LaRoza on 2008-09-16
> **mssever said:**
> Do you mind if I change the variable name here and in the related methods (where I presume mode means the same) to 'directory'? IIRC, Python tends to frown on abbreviations, and it took me quite a while to decipher some of the abbreviations in the core, since I haven't been assimilated.

Any interal names you can change, don't do a global search and replace though. As they are short, they often are in the middle of other words...

> 
So should these be documented like that, or refactored out, or changed to private (name beginning with an underscore)?

They could be changed to private if you want. There is no reason why anything outside the class should know about them.

> 
Actually, there's a better solution. Running ```
gksudo env
```shows that gksudo sets the environment variable SUDO_USER to the username of the user running the program.  So you can forget about messing with this in the UIs and handle it in Core: ```
if 'SUDO_USER' in os.environ:
    self.username = os.environ['SUDO_USER']
else:
    self.username = os.environ['USER']
self.home = os.path.expanduser('~%s' % self.username)
```With this information, you can also chown files as appropriate. I'll change the launcher to use gksudo.


Oh, good. We'll use that. 

GUI devs, wait...

> 
Oh, a wrinkle: KDE uses kdesu, not gksudo. I guess we'll have to detect KDE once again...
Yeah, but I have faith in you. Perhaps the launcher will need to use that script of yours again.

---

### Post by OutOfReach on 2008-09-16
Ok, we'll wait. I haven't really started any work on the interface yet (filled up to the face with homework).

---

### Post by LaRoza on 2008-09-16
> **OutOfReach said:**
> Ok, we'll wait. I haven't really started any work on the interface yet (filled up to the face with homework).

Actually, since I updated 1.0 just now, it should work. All other bugs are free to stomp.

Merge and edit as you will.

---

### Post by OutOfReach on 2008-09-16
Thanks for the heads up. I'll get to work as soon as I can (might be later though, as I said I have terrible homework)

---

### Post by LaRoza on 2008-09-16
> **OutOfReach said:**
> Thanks for the heads up. I'll get to work as soon as I can (might be later though, as I said I have terrible homework)

I just had a final myself.

Have fun with the homework.

Right now, there is nothing critical. I want to get the launcher made with gksudo/kdesu or whatever they use, a new .deb. and a new release.

It is amazing how many problems come up when people who are not programmers get their hands on it...

---

### Post by OutOfReach on 2008-09-16
> **LaRoza said:**
> 
Have fun with the homework.


Easier said than done. ;)

---

### Post by LaRoza on 2008-09-16
> **OutOfReach said:**
> Easier said than done. ;)

Well, of course. I am over here with a break coming up.

---

### Post by OutOfReach on 2008-09-16
Lucky, just started school again, and my next break isn't until December. :(

---

### Post by mssever on 2008-09-16
Hooray! Another bug!

I created a restore point named ```
test2 -- with added files
```and the UIs all display incorrect data.

```
~/programming/projects/sysres/main:$ sysres --cli
What do you want to do?

    1 - CREATE a restore point
    2 - RESTORE from a restore point
    3 - DELETE existing restore points
    4 - ADVANCED
    5 - EXIT
2
Restore points: 


1 test1     Created on: 2008-09-16    at: 22:45:53.530077

2 test2      Created on:     at: with


Restore from restore point number: 
```

---

### Post by mssever on 2008-09-16
> **LaRoza said:**
> It is amazing how many problems come up when people who are not programmers get their hands on it...
Then we shouldn't let them use it! :)

Seriously, though, I suppose I have difficulty testing this since I really have no need for sysres myself.

---

### Post by OutOfReach on 2008-09-17
Hmm, to solve that bug how about checking if the time and date are integers (or floats)? And if they're not ints (or floats) either spit out an exception or just display some other data.

---

### Post by mssever on 2008-09-17
> **OutOfReach said:**
> Hmm, to solve that bug how about checking if the time and date are integers (or floats)? And if they're not ints (or floats) either spit out an exception or just display some other data.I haven't really looked at the code for this, but I suspect that a) the bug is in Core; and b) it has to do with either improper validation of the restore point names or improper parsing of them.

On another front, I've made a number of changes that can be merged to trunk, including a fix for several bugs that could cause data loss in certain (probably unlikely) situations. As usual, the source is lp:~scott.severance/sysres/main. 1.0 can merge just revision 57 to get the updated .desktop file and related changes.

I'm working on a build script to simplify the .deb creation process.

---

### Post by LaRoza on 2008-09-17
> **mssever said:**
> Then we shouldn't let them use it! :)

Seriously, though, I suppose I have difficulty testing this since I really have no need for sysres myself.

I neither need it, although I have used it, I only use the CLI interface.

> **mssever said:**
> I haven't really looked at the code for this, but I suspect that a) the bug is in Core; and b) it has to do with either improper validation of the restore point names or improper parsing of them.

I think it is just what way it is formatted. In the meantime, why are you making names with spaces? <edit> I fixed it.

> 
I'm working on a build script to simplify the .deb creation process.

Good.

---

### Post by mssever on 2008-09-17
> **LaRoza said:**
> I think it is just what way it is formatted. In the meantime, why are you making names with spaces? <edit> I fixed it.
Because names with spaces are more readable. Validation should filter out anything that's unacceptable. You should see my filenames. I use all sorts of characters in filenames to ensure that the filename accurately reflects its contents. For example, If I'm writing a document, I might call it "2008-09-17 - Is This the Document Title?.odt". Unix filenames can include any character except / and \0, so I take full advantage of that. Any program that can't handle my filenames is broken, and tab completion saves me from actually having to type my filenames in full. From a user's perspective (not a programmer's), I'd apply that same reasoning to restore point names.

(when I program, I follow the filename conventions for the language I'm using)

---

### Post by LaRoza on 2008-09-17
> **mssever said:**
> Because names with spaces are more readable. Validation should filter out anything that's unacceptable. You should see my filenames. I use all sorts of characters in filenames to ensure that the filename accurately reflects its contents. For example, If I'm writing a document, I might call it "2008-09-17 - Is This the Document Title?.odt". Unix filenames can include any character except / and \0, so I take full advantage of that. Any program that can't handle my filenames is broken, and tab completion saves me from actually having to type my filenames in full. From a user's perspective (not a programmer's), I'd apply that same reasoning to restore point names.

(when I program, I follow the filename conventions for the language I'm using)

The spaces weren't the problem. I fixed the problem. Technically, the rule should be no "--" in file names, but to make things simple it just changes them to __.

```

~/sysreswork/1.0$ls
about  AUTHORS  changelog  code_standards  COPYING  debian  file name  install.sh  launchsysres  man1  r  README  sysres  sysres.desktop  sysres.svg  SystemRestore  uninstall.sh
~/sysreswork/1.0$
```
How many items are listed?

---

### Post by mssever on 2008-09-17
> **LaRoza said:**
> ```

~/sysreswork/1.0$ls
about  AUTHORS  changelog  code_standards  COPYING  debian  file name  install.sh  launchsysres  man1  r  README  sysres  sysres.desktop  sysres.svg  SystemRestore  uninstall.sh
~/sysreswork/1.0$
```How many items are listed?17. But a machine would say 18.
This is why ls isn't suitable for machine-parsing (unless you use one of the --quoting-style options). However, in practice that ambiguity has never caused me a problem, since the names are sufficiently distinguishable for a human.

---

### Post by LaRoza on 2008-09-17
> **mssever said:**
> This is why ls isn't suitable for machine-parsing (unless you use one of the --quoting-style options). However, in practice that ambiguity has never caused me a problem, since the names are sufficiently distinguishable for a human.

Maybe that is the problem...

I can't stand spaces in file names.

Anyway, I hope the latest 1.0 code works. If it does, I'll let you know when it can be repacked for a working release.

---

### Post by mssever on 2008-09-17
> **LaRoza said:**
> Maybe that is the problem...

I can't stand spaces in file names.Yet more evidence that you're a bot? :)

> Anyway, I hope the latest 1.0 code works. If it does, I'll let you know when it can be repacked for a working release.
I hope I'll have a rough draft of the build script finished soon. But I'm about to head to bed now.

---

### Post by nvteighen on 2008-09-17
Multi-replying:

> **red_Marvin said:**
> (...) since I'm quite confused about which branch I should base sysres-gtk on, and being in a dante's merge/commit/conflict inferno right now.

Should I base my work on sysres/sysres or sysres/1.0?

That's a big issue. There shouldn't be any merge/commit/conflict inferno... That just slows development and causes frustration... specially to you, GUI devs. (Yeah, I'm pretty safe for now, in the "trunk cloud"... except for the merges from stable).

> **LaRoza said:**
> I make sure it is gone when I do any pushing into trunk.

Just for you to know. Always do a 'bzr diff' before commiting and check what's going to change. You're probably first changing things and then merging-commiting, which can cause fatal issues. First merge, check the diff, commit **to the proper revision** (use 'bzr commit -r' to specify a special revision) and then change.

> **LaRoza said:**
> 
Yeah, but I have faith in you. Perhaps the launcher will need to use that script of yours again.

Why not just different packages? (mssever reads this and gets crazy... :))
1. sysres-common: core + cli
2. sysres-gtk (dependent on sysres-common): sysresgtk with its own Launcher.
3. sysres-qt (dependent on sysres-common): sysresqt with its own Kicker.

Yeah, that adds a problem for that random user that likes to use KDE apps on GNOME and viceversa... even when native implementations exist for each DE. and needs a Launcher for sysres-qt or a Kicker for sysres-qt...

> **mssever said:**
> Then we shouldn't let them use it! :)

Seriously, though, I suppose I have difficulty testing this since I really have no need for sysres myself.

Me too. Plus the hassle that is to use Qt apps in GNOME... there's always a library missing (and for some reason there doesn't seem to be a Qt metapackage as libgtk2.0-0 for GTK+).

---

### Post by nvteighen on 2008-09-17
By the way, I've noticed that people are demanding for an explanation of how ErrMsg. It is written, merged in trunk since long, at the API documentation for trunk.

---

### Post by LaRoza on 2008-09-17
> **nvteighen said:**
> 
Just for you to know. Always do a 'bzr diff' before commiting and check what's going to change. You're probably first changing things and then merging-commiting, which can cause fatal issues. First merge, check the diff, commit **to the proper revision** (use 'bzr commit -r' to specify a special revision) and then change.

Well, I don't know about then, but now it worked out. Didn't know it had a -r, thanks.

> 
Why not just different packages? (mssever reads this and gets crazy... :))
1. sysres-common: core + cli
2. sysres-gtk (dependent on sysres-common): sysresgtk with its own Launcher.
3. sysres-qt (dependent on sysres-common): sysresqt with its own Kicker.

Well, it works now, so it doesn't need to get more complicated.

---

### Post by nvteighen on 2008-09-17
Well, it works just because of a random coincidence.

I'm not kidding. The module importing tree is dissastrous. sysres should not have access to the core, as it is just a launcher module. If you happen to change an import statement at the module, the whole thing blows up.

The import statements on the interfaces get overriden because of that. Also, because of the directory structure, where Core and Interfaces are "sibling packages" in Python jargon. But, to implement that type of packaging, you need to play with the PYTHONDIR environment variable and that implies to transform the current "sysres" Python script into a Shell script. After sorting that, the packages have to be set up using the __init__.py files.

Also, if you happen to test an interface module without passing through "sysres", it throws an ImportError. This is a symptom of modularity lack: a module at "top-level" cannot determine essential functionality of a "lower level".

Sysres's current architecture is this:
```

        sysres---------------
           |                |
=======GUI APIs=======      |
  |      |     |     |      |
GTK+    CLI   Args   Qt     |
  |      |     |     |      |
=======Core API=======      |
     |           |          |
   Cons        Core---------|
     |                      |
     |----------------------|

```
(== shows an interface barrier
 -- or | shows interaction between modules)

So, in very few words: it's a circular architecture. Yes, now it' doesn't hurt, because the only "interaction" between "sysres" and the Core is just to define the default_files at starting up. But, that's almost like still having the default_files defined at the Core: the interfaces are forced to have that defaults and, if we happen to implement the APT restorer (which means a new Core module, not an interface), that will bring a lot of trouble.

lp:~evigo/sysres/sysres currently contains an alternative, but I recognize the SystemRestore directory is now a mess. It works and the import tree is fixed. I've got rid of the circular issue and cut off sysres from the Core. I didn't know if it was wise to request a merge, so I highly recommend you to look at it before merging into trunk.

And the Constants, well, I still believe they should not be part of the Core. But of course, they're just help data and information for user... So, it has no influence over runtime. I haven't touched them in my latest commit.

---

### Post by LaRoza on 2008-09-17
> **nvteighen said:**
> 
I'm not kidding. The module importing tree is dissastrous. sysres should not have access to the core, as it is just a launcher module. If you happen to change an import statement at the module, the whole thing blows up.

You are right. This is probably due to the original design of it being only two files.

Why does it seem the worst code is from the past?

> 
Also, if you happen to test an interface module without passing through "sysres", it throws an ImportError. This is a symptom of modularity lack: a module at "top-level" cannot determine essential functionality of a "lower level".

The interfaces should make the RestorePoint object on their own (right?).

The default files could be passed to the interfaces and the interfaces could make the object themselves.

> 
lp:~evigo/sysres/sysres currently contains an alternative, but I recognize the SystemRestore directory is now a mess. It works and the import tree is fixed. I've got rid of the circular issue and cut off sysres from the Core. I didn't know if it was wise to request a merge, so I highly recommend you to look at it before merging into trunk.

I will look at it, but it seems like it shouldn't be complicated.

Ok, it should be all good now. Sorry, I didn't look at your code, but SystemRestore is not a mess and the changes are simple and it fixes all the problems that were mentioned. In short:
[list]
[*] A new module, Interfaces
[*] rp = SystemRestore(default_files) removed from sysres and each interface makes their own when they are run.
[/list]

---

### Post by nvteighen on 2008-09-17
> **LaRoza said:**
> You are right. This is probably due to the original design of it being only two files.

Why does it seem the worst code is from the past?

We're suffering the "MS effect"!

> The interfaces should make the RestorePoint object on their own (right?).

The default files could be passed to the interfaces and the interfaces could make the object themselves.

You got it.

The core just has to give functionality. That's it. The interfaces use it like they want... As this is the "Official SysRes", all interfaces should work the same, use the same defaults, etc., but as this is Free Software anyone should be able to create something completely different using the Core.

For example, there's still the issue whether we implement an APT restorer or not. I have been doing some research and have some ideas on it (there are some design questions regarding which backend to use I'm not clear about), but if the SysRes Team doesn't implement it, any random outsider should be able to 'bzr branch lp:sysres' and start that project implementing it on the Core without a major rewrite... ideally, without rewrite.

---

### Post by LaRoza on 2008-09-17
> **nvteighen said:**
> We're suffering the "MS effect"!


No, we are taking less than 7 years to deliver, and we have the actual features that we told people about.

> 
You got it.

The core just has to give functionality. That's it. The interfaces use it like they want... As this is the "Official SysRes", all interfaces should work the same, use the same defaults, etc., but as this is Free Software anyone should be able to create something completely different using the Core.

All interfaces in trunk should do it now (whether they work beyond that, is up to how much the core has changed...)

Check it out.

> 
For example, there's still the issue whether we implement an APT restorer or not. I have been doing some research and have some ideas on it (there are some design questions regarding which backend to use I'm not clear about), but if the SysRes Team doesn't implement it, any random outsider should be able to 'bzr branch lp:sysres' and start that project implementing it on the Core without a major rewrite... ideally, without rewrite.

Well, it should ideally, be simple to use. It doesn't require much work interface-wise and would just be a "save as" and "save where" thing.

---

### Post by nvteighen on 2008-09-17
> **LaRoza said:**
> No, we are taking less than 7 years to deliver, and we have the actual features that we told people about.

I was talking about legacy code...


> All interfaces in trunk should do it now (whether they work beyond that, is up to how much the core has changed...)

Check it out.

Well... it's a progress (actually, exactly the same I did), but that creating an Interface directory doesn't solve the problem that you need to start using sysres to launch a UI module (try executing cli.py or whatever): you get an ImportError, not an error because of an undefined value (a non-passed parameter). In other words, the UIs are dependent of the "sysres" launcher...

Please, take a look at my branch and you'll see what I've done. In my fix I have also given all interface modules a way to fire up without the launcher with no default files (for development purposes; that should be changed).

---

### Post by LaRoza on 2008-09-17
> **nvteighen said:**
> 
Well... it's a progress (actually, exactly the same I did), but that creating an Interface directory doesn't solve the problem that you need to start using sysres to launch a UI module (try executing cli.py or whatever): you get an ImportError, not an error because of an undefined value (a non-passed parameter). In other words, the UIs are dependent of the "sysres" launcher...

Please, take a look at my branch and you'll see what I've done. In my fix I have also given all interface modules a way to fire up without the launcher with no default files (for development purposes; that should be changed).

Oh, we decided against having the interfaces themselves set as executable, although they may be coded that way, they aren't supposed to be run by themselves.

---

### Post by nvteighen on 2008-09-17
> **LaRoza said:**
> Oh, we decided against having the interfaces themselves set as executable, although they may be coded that way, they aren't supposed to be run by themselves.

Wait... then I'm missing a point. 

What's exactly "sysres" job? Isn't it intended to be a command-line launcher... or "umbrella" that allows you to fire up the "correct" interface (or the chosen one) with some default settings by using the same command? (btw, I still wonder why sysres is written in Python instead of a shell script...)

Otherwise, what you're doing is to tight-integrate the "launcher" with the GUI... in other words, another dictator all interfaces have to obey... And any interface not complying with it won't ever work under that launcher. If you change sysres, you may have to change the interfaces...

Instead, if you made the interfaces independent (I mean: that no code in an interface module has to call code from sysres), changing sysres should not harm the interfaces' code.

Thoughts?

P.S.: I'll not going to merge anything into my branch until I understand what you are trying to do.

---

### Post by LaRoza on 2008-09-17
> **nvteighen said:**
> Wait... then I'm missing a point. 

Yes, sysres is not a command line launcher, it is the program. The rest of the modules are just good design.

> 
What's exactly "sysres" job? Isn't it intended to be a command-line launcher... or "umbrella" that allows you to fire up the "correct" interface (or the chosen one) with some default settings by using the same command? (btw, I still wonder why sysres is written in Python instead of a shell script...)

It is the program. Yes, it is short, but that is because of the design and not having everything mashed together.

> 
Otherwise, what you're doing is to tight-integrate the "launcher" with the GUI... in other words, another dictator all interfaces have to obey... And any interface not complying with it won't ever work under that launcher. If you change sysres, you may have to change the interfaces...

The launcher is now "launchsysres", a shell script.

> 
Instead, if you made the interfaces independent (I mean: that no code in an interface module has to call code from sysres), changing sysres should not harm the interfaces' code.

Any program can use the Core, but in sysres, the focus of the program is sysres.

> 
P.S.: I'll not going to merge anything into my branch until I understand what you are trying to do.
Well, you are trying to write four different programs with one interface each instead of one program with four interfaces.

The intent is not to have SystemRestore being used by different interfaces, but to make one program called sysres that is flexible and functional.

---

### Post by nvteighen on 2008-09-17
> **LaRoza said:**
> 
Well, you are trying to write four different programs with one interface each instead of one program with four interfaces.

The intent is not to have SystemRestore being used by different interfaces, but to make one program called sysres that is flexible and functional.

Thanks, now I see. My fears were that this was effectively some kind of issue like the ones we had before.

If it was a project managed by me, I would undoubtfully go for the "1 interface for 4 programs". I find it to be a better design.

But, as you're the boss :), and this seems to be non-critical (we hope not), I'll merge and so I keep my branch not too much diverged.

---

### Post by LaRoza on 2008-09-17
> **nvteighen said:**
> Thanks, now I see. My fears were that this was effectively some kind of issue like the ones we had before.

If it was a project managed by me, I would undoubtfully go for the "1 interface for 4 programs". I find it to be a better design.

But, as you're the boss :), and this seems to be non-critical (we hope not), I'll merge and so I keep my branch not too much diverged.

Well, my goal was to write a system restore program for Ubuntu that is newb friendly. The CLI interface was the best I could do (I don't do GUI programming). The command line argument interface was built almost entirely for me. The GTK and QT interfaces are the "only" interfaces that really matter. So instead of having four interfaces, we have two, a QT and GTK. We could have two different versions, one QT and one GTK, but having them together is trivial and very flexible.

I think you meant "1 program for 4 interfaces" didn't you?

After this gets done and works, I forsee little work on it (from a functional point of view). It already does exactly what I wanted it to do.

Anything else is extra and I am really not a fan of adding features.

---

### Post by nvteighen on 2008-09-17
I had to revert to my branch rev. 32. In other words, step down from your changes in trunk and persist on mine.

Yes, the code in trunk works... but it breaks with any little fix (not feature) you do. For example, after I merged your changes, I discovered a piece of redundant code (a double import: Constants). One module imported exactly the same as sysres... for nothing, as all of us know that if the same module is imported twice, the second import doesn't count. So, I deleted the second one and... crash... the whole thing just stopped to work because the second import was of the form: import ... as ... and the sysres' was from ... import *.

The idea is to have people working "on their own" and connect them by an interface (sysres). If I write sysresgtk, I have to know that "my" import is which will do the work, not someone else's.

Otherwise, debugging will be impossible... as it is. And mind you that there are still unsolved issues like popups not appearing in GTK+. For example, in stable, run sysres without root privileges and restore a restore point... it should output a "Permission error" somehow, but it just doesn't show anything.

SICP has a whole chapter on this (of course, in Scheme). [http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-13.html#%_chap_2](http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-13.html#%_chap_2) Specially read this example, a rather complex system managed by interfacing "bottom-up"-wise: [http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-18.html#%_sec_2.5](http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-18.html#%_sec_2.5)

---

### Post by LaRoza on 2008-09-17
> **nvteighen said:**
> 
The idea is to have people working "on their own" and connect them by an interface (sysres). If I write sysresgtk, I have to know that "my" import is which will do the work, not someone else's.


So what we should remove all the imports from sysres?

I see a possible fix. It can be changed so the argument version is the default interface called and it can handle --help and everything.

This would allow sysres to only import the interface code and the interfaces could work independantly.

---

### Post by LaRoza on 2008-09-17
Ok, trunk has been fixed (at least, that which was broken).

All the interface code should stand on their own after main() is called and they are given the information needed (default_files).

About 1.0. I want to get this packaged, tested and deployed (I have a few disappointed people...).

It will be 1.0.2. The current lp:sysres/1.0 is good, except for one small problem. Run it from the terminal: "./sysres --gtk", and try to restore a restore point (note, use the default files and don't run as root).

It doesn't give a popup error and an except is thrown, possibly a minor coding error.

Since the new launcher launches with gksudo, this isn't essential.

If you (GTK dev) do not have the time at the moment to fix that, that is OK as it should only show up when not run as root and it will be run as root by default now. Just let me know :-)

Everyone can focus on trunk if they want to.

Thanks for all the help everyone!

(nvteighen: I hope you find current trunk acceptable now)

---

### Post by mssever on 2008-09-17
> **nvteighen said:**
> That's a big issue. There shouldn't be any merge/commit/conflict inferno... That just slows development and causes frustration... specially to you, GUI devs. (Yeah, I'm pretty safe for now, in the "trunk cloud"... except for the merges from stable).I experienced it when I switched my main branch from 1.0 to trunk.

> Why not just different packages? (mssever reads this and gets crazy... :))
1. sysres-common: core + cli
2. sysres-gtk (dependent on sysres-common): sysresgtk with its own Launcher.
3. sysres-qt (dependent on sysres-common): sysresqt with its own Kicker.That's ideal, although there should also be a sysres-cli package which sysres-common recommends. I made a single package because all the documentation said that multi-binary packages is much more complicated and should only be attenpted by experienced people.

My implementation, though, has some worrying edge cases. Consider someone who runs some DE/WM other than KDE, and who has python-qt4 but not python-gtk. The current situation will load the GTK interface, which will raise an ImportError. And if they launched it via a menu, they'll get no error message. Or, what about someone who runs KDE without having python-qt4 (which is fairly new), but they have python-gtk? The deb will be installed because the python-gtk meets the dependency, but sysres will find kicker running and try to start the Qt interface, which will fail. And there are several more edge cases along those lines.

I think that there are several things that could be done to solve that. Multiple packages would help, especially if used in conjucntion with /etc/alternatives. But also, we should probably add something like the following to sysres: ```
if __name__ == '__main__':
    try:
        # all the stuff in the if block goes here
    except StandardError, e:
        if os.environ['DISPLAY']: #Check for X
            import tkinter as tk # tkinter is part of the stdlib, so we're guaranteed to have it. It's pretty much the only non-evil use of tk.
            # pop up a tk dialog with an error message and a traceback.
            # It could be enhanced by detecting the specific ImportErrors and handling
            # them properly. This is where Ruby's retry statement would be handy.
        raise
```
> Me too. Plus the hassle that is to use Qt apps in GNOME... there's always a library missing (and for some reason there doesn't seem to be a Qt metapackage as libgtk2.0-0 for GTK+).Installing python-qt4 got me everything I needed.

> **nvteighen said:**
> For example, there's still the issue whether we implement an APT restorer or not. I have been doing some research and have some ideas on it (there are some design questions regarding which backend to use I'm not clear about), but if the SysRes Team doesn't implement it, any random outsider should be able to 'bzr branch lp:sysres' and start that project implementing it on the Core without a major rewrite... ideally, without rewrite.We need to share our ideas on this (though I don't have time right now to write them up). I think that this should be considered an essential part of sysres, because restoring all the installed packages is the most difficult part of restoring a system--particularly if you end up reinstalling for some reason.


<off-topic>I wonder how much I've missed. I kept getting called away while writing this post, so I've been in this window for several hours and unaware of any more-recent discussion</off-topic>

---

### Post by mssever on 2008-09-17
> **LaRoza said:**
> I see a possible fix. It can be changed so the argument version is the default interface called and it can handle --help and everything.
I've long wondered why that wasn't already the default. It makes a lot more sense to me.
> **LaRoza said:**
> About 1.0. I want to get this packaged, tested and deployed (I have a few disappointed people...).I've been holding off on packaging 1.0.2 until I get the build script written--which is taking longer than I expected. Do you want me to go ahead and package it manually, or wait until I get the script finished (hopefully by late tonight)?

---

### Post by LaRoza on 2008-09-17
> **mssever said:**
> I've long wondered why that wasn't already the default. It makes a lot more sense to me.
I've been holding off on packaging 1.0.2 until I get the build script written--which is taking longer than I expected. Do you want me to go ahead and package it manually, or wait until I get the script finished (hopefully by late tonight)?

The reason why: "sysres" used to be the interface. Remember, the versions we use make sense, I just didn't share 0.1 to 0.7 :-) I still have them.

We'll wait until we hear from the GTK dev. If it is something he can do easily, we'll wait for that, but if not, we'll package it up. You may get your scripts done by then. There is no immediate hurry; we aren't well known yet.

> **mssever said:**
> 
My implementation, though, has some worrying edge cases. Consider someone who runs some DE/WM other than KDE, and who has python-qt4 but not python-gtk. The current situation will load the GTK interface, which will raise an ImportError. And if they launched it via a menu, they'll get no error message. Or, what about someone who runs KDE without having python-qt4 (which is fairly new), but they have python-gtk? The deb will be installed because the python-gtk meets the dependency, but sysres will find kicker running and try to start the Qt interface, which will fail. And there are several more edge cases along those lines.

There is a problem with that. Poll for the forum. Ask for those only who don't want to edit text files or understand them. (These are the ones who want System Restore).

Now ask them what DE they use (and ask if they know what one is). ;)

This is aimed at GUI *buntu users. We have all bases covered, except for those using something like OzOS (which is user friendly), but that wouldn't have a menu anyway.

> 
I think that there are several things that could be done to solve that. Multiple packages would help, especially if used in conjucntion with /etc/alternatives. But also, we should probably add something like the following to sysres: 

It wouldn't work; python-tk isn't installed by default on any of the *buntu's.

> 
<off-topic>I wonder how much I've missed. I kept getting called away while writing this post, so I've been in this window for several hours and unaware of any more-recent discussion</off-topic>

Not much.

---

### Post by OutOfReach on 2008-09-17
I pull from lp:sysres right?
And would anyone mind filling me in to what has happened during the last 2 pages? :)

---

### Post by LaRoza on 2008-09-17
> **OutOfReach said:**
> I pull from lp:sysres right?
And would anyone mind filling me in to what has happened during the last 2 pages? :)

lp:sysres/1.0 only needs GTK work, and is almost ready.

lp:sysres is trunk, and has a lot of changes. Error handling is the big thing now.

nvteighen is yelling at me for being imperfect :-)

---

### Post by OutOfReach on 2008-09-17
> 
nvteighen is yelling at me for being imperfect

Ahh, the usual. I joke, I joke.


> 
lp:sysres is trunk, and has a lot of changes. Error handling is the big thing now.

Ok so that's a confirmation to pull from lp:sysres?

---

### Post by LaRoza on 2008-09-17
> **OutOfReach said:**
> Ahh, the usual. I joke, I joke.


That is what happens when a person comes into the team with a fresh start. I was here (obviously) from the beginning. My variable names make sense (although they are influenced by JavaScript and PHP...)

> 
Ok so that's a confirmation to pull from lp:sysres?

Yes, if you don't have anything you want to do in 1.0 (which is frozen, except for bug fixes).

In case you don't know, you can copy a branch with:

```

bzr branch lp:sysres sysres-trunk

```

Attempting to merge it with the old work will be...painful. I think.

---

### Post by OutOfReach on 2008-09-17
Thanks, I'll work and upload my changes to my branch later. (Launchpad is currently down for maintenance)

---

### Post by LaRoza on 2008-09-17
> **OutOfReach said:**
> Thanks, I'll work and upload my changes to my branch later. (Launchpad is currently down for maintenance)

The GUI's should stand on their own now. Only changes to system_restore.py should cause any issues. At the moment, the API's are almost the same except for errors.

Also, SystemRestore.Constants has useful information in it so you don't have to hardcode values. Use what you will. The current code is editted to use it I think.

---

### Post by mssever on 2008-09-18
> **LaRoza said:**
> This is aimed at GUI *buntu users. We have all bases covered, except for those using something like OzOS (which is user friendly), but that wouldn't have a menu anyway.Hopefully, if it tries to be user-friendly, it still uses .desktop files to provide whatever GUI method it uses. I run IceWM on my server, and it uses its own custom menu format, which means I have to manually configure the menus. Several other WMs I've used have also been that way, and frankly, that's a dumb way of doing things. All WMs or DEs that have a GUI way of launching programs should generate whatever lists they generate using .desktop files.

Plus, I did call those situations edge cases.

> It wouldn't work; python-tk isn't installed by default on any of the *buntu's.I didn't believe you until I checked it out. I wonder what other parts of the Python stdlib are missing from a default *buntu? Kinda defeats the purpose if a stdlib if you can't count on it being present.

> **LaRoza said:**
> Attempting to merge it with the old work will be...painful. I think.Indeed. When I switched to trunk, I merged it to preserve the packaging work I'd done in 1.0. I had 7 conflicts to resolve.



I've finished the build script (well, it works, but it's really ugly and messy). It's in the branch lp:~scott.severance/sysres/build_script. I put it in a branch of its own because I don't think that a .deb build script really belongs in the source distribution. Feel free to merge it if you disagree.

It took longer to write than I'd anticipated since I initially wrote it in Ruby to take advantage of the fact that Ruby is more convenient for a shell script-type approach such as I was taking (due without the disadvantages of shell scripts). I ended up having to rewrite it in Python because it requires expect and there's no Ruby expect lib in the repos. So it's still ugly Python, since I was trying to use Python like a shell script. But it works, and others are welcome to clean it up if they don't like it.

Oh, one other thing: To save time, I assumed that the people running the script are intelligent, so I did very little input validation. Read the --help message.

---

### Post by nvteighen on 2008-09-18
> **LaRoza said:**
> 
(nvteighen: I hope you find current trunk acceptable now)

Acceptable... no, actually, nice job, but some issues:
1) You lost the Qt interface somehow in the process :p (just merge from my branch to restore it)
2) sysres now broken. This is something I expected to happen. The fix is to properly set the package tree so import at interfaces knows where to look at for the Core (it is related to setting __path__ and __all__ in the __init__.py files... but I just don't understand Python docs on this)... As they're yielding an ImportError because of the non-found Core, sysres tells you that PyGTK or PyQt aren't installed... even if I try to start the CLI :p

(luckily, this is just the trunk. I hope stable works, no matter how the code looks like...)

> **LaRoza said:**
> 
nvteighen is yelling at me for being imperfect :-)

I know you're joking. But I feel some of posts were a bit rude. Sorry if I was.

---

### Post by LaRoza on 2008-09-18
> **nvteighen said:**
> Acceptable... no, actually, nice job, but some issues:
1) You lost the Qt interface somehow in the process :p (just merge from my branch to restore it)
2) sysres now broken. This is something I expected to happen. The fix is to properly set the package tree so import at interfaces knows where to look at for the Core (it is related to setting __path__ and __all__ in the __init__.py files... but I just don't understand Python docs on this)... As they're yielding an ImportError because of the non-found Core, sysres tells you that PyGTK or PyQt aren't installed... even if I try to start the CLI :p

Hmm...

Well, in theory it was perfect.

I try to fix trunk.

Oh, it was simpler than we though. Somehow, __init__.py never made it into Interfaces.

The issue with the errors is they are saying os.stderr doesn't exist? Doesn't it?

<edit>
Ok. Fixed interfaces starting up (Qt was importing wrong, I don't know why... Not looking at log; no point in pointing fingers ;)
os.stderr is still not working for some reason on my system.

> 
(luckily, this is just the trunk. I hope stable works, no matter how the code looks like...)

It does. Except for that one GTK interface issue which won't exist with the new launcher.

> 
I know you're joking. But I feel some of posts were a bit rude. Sorry if I was.
No, I want people to be blunt. Just like I am.

---

### Post by LaRoza on 2008-09-18
> **nvteighen said:**
> 
2) sysres now broken. This is something I expected to happen. The fix is to properly set the package tree so import at interfaces knows where to look at for the Core (it is related to setting __path__ and __all__ in the __init__.py files... but I just don't understand Python docs on this)... As they're yielding an ImportError because of the non-found Core, sysres tells you that PyGTK or PyQt aren't installed... even if I try to start the CLI :p

Everything starts now.

__init__.py files are not complicated. They just have to be there. In the interfaces directory, there was no such file.

The CLI, arguments, QT and GTK start now.

The QT interface had its imports changed for some reason. I am also not happy with the QT imports (from import *) but since it only affects that file, I am not going to manually change it.

---

### Post by LaRoza on 2008-09-18
> **mssever said:**
> 
I didn't believe you until I checked it out. I wonder what other parts of the Python stdlib are missing from a default *buntu? Kinda defeats the purpose if a stdlib if you can't count on it being present.

It confuses me also. PyGTK is there (Ubuntu uses it) though in the GTK DE's.

> 
Oh, one other thing: To save time, I assumed that the people running the script are intelligent, so I did very little input validation. Read the --help message.

What? You didn't write a bullet proof build script :-)

---

### Post by nvteighen on 2008-09-18
Hurray, trunk works!... at least until someone (i.e. me) puts his/her hands on it and everything breaks apart again.

---

### Post by nvteighen on 2008-09-18
> **mssever said:**
> 
I didn't believe you until I checked it out. I wonder what other parts of the Python stdlib are missing from a default *buntu? Kinda defeats the purpose if a stdlib if you can't count on it being present.


If I'm not wrong, Ubuntu ships with "python-core" (or similar) installed, not "python". The same as happens with vi(m), where "vim-tiny" is the default.

It's a bit annoying.

---

### Post by LaRoza on 2008-09-18
> **nvteighen said:**
> Hurray, trunk works!... at least until someone (i.e. me) puts his/her hands on it and everything breaks apart again.

First nice thing you said about me all day :-)

> **nvteighen said:**
> If I'm not wrong, Ubuntu ships with "python-core" (or similar) installed, not "python". The same as happens with vi(m), where "vim-tiny" is the default.

It's a bit annoying.

A bit?!

---

### Post by Rui Pais on 2008-09-18
> **LaRoza said:**
> 
This is aimed at GUI *buntu users. We have all bases covered, except for those using something like OzOS (which is user friendly), but that wouldn't have a menu anyway.


Hi :)
I'm very interested in this.

In fact it should work like honey on OzOS, since it is a slim (X)Ubuntu base and a highly system-independent DE (all implemented in a single folder). 
We have already self made tools for backup and restore DE, so with a System Restore application, in our case, we will have *really* all our bases covered :D

Menu implementations on e17 follows freedesktop.org standards, so what works for gnome or xfce4 usually works on e17. 
And that's the case...

The only thing that don't shows it's icon, since it's a svg.
Can you include a png image too (with same name so .desktop would not require changes on Icon)?

Just a "contribution" for desktop file, Pt translation:
> Name[pt]=Recuperação do sistema
Comment[pt]=Salvaguarda e recupera ficheiros importantes do sistema


Some bugs (vers 1.0.1 deb):
If i select 'Use custom directory' and change Add files to Defaults choice, it seems to ignore the new adds. On Default directory works correctly.

> **LaRoza said:**
> 
There is no immediate hurry; we aren't well known yet.


Ahh the fame... well that i can't offer, but since it's a GPL project I'm thinking in include it by default on OzOS repos and future versions.
Thank you.

---

### Post by OutOfReach on 2008-09-18
@LaRoza on imports. Do you mean how the Qt interface imports the Qt modules or the sysres core modules? I changed the way the Qt interface imports the Sysres Core module in the last update (see my branch).

If you do mean the way the Qt interface import Qt modules than I'll happily change the way the importing is done.

---

### Post by LaRoza on 2008-09-18
> **Rui Pais said:**
> Hi :)
I'm very interested in this.

In fact it should work like honey on OzOS, since it is a slim (X)Ubuntu base and a highly system-independent DE (all implemented in a single folder). 
We have already self made tools for backup and restore DE, so with a System Restore application, in our case, we will have *really* all our bases covered :D

Ah, good. It will work on any Linux (meaning: run and do what it is told), but to use the gui's you need python-qt4 or python-gtk (or whatever it is called, it is installed by default on Ubuntu). The CLI version could conceivably run in Windows, but it wouldn't work in the same way.

> 
The only thing that don't shows it's icon, since it's a svg.
Can you include a png image too (with same name so .desktop would not require changes on Icon)?

We'll try to get it in for 1.0.2.

> 
Some bugs (vers 1.0.1 deb):
If i select 'Use custom directory' and change Add files to Defaults choice, it seems to ignore the new adds. On Default directory works correctly.

That really depends on what GUI you are using, and I don't do squat for the GUI's :-)

I use the CLI version, which I wrote, and has no bugs. (Because it is CLI and more linear)

> 
Ahh the fame... well that i can't offer, but since it's a GPL project I'm thinking in include it by default on OzOS repos and future versions.
Thank you.

Please wait until 1.0.2. 1.0.1 has some bugs (that looks like an IP address of a sort, too many .)

The code of 1.0.1 and 1.0.2 is not for the future, so any work you do would best be done with trunk, however, trunk has a few issues with the GUI's related to error handling because the driving force behind that started while work was being done on 1.0 and 0.9 and the GUI devs haven't seen it yet (well, at least, not developing with yet)

---

### Post by LaRoza on 2008-09-18
> **OutOfReach said:**
> @LaRoza on imports. Do you mean how the Qt interface imports the Qt modules or the sysres core modules? I changed the way the Qt interface imports the Sysres Core module in the last update (see my branch).

If you do mean the way the Qt interface import Qt modules than I'll happily change the way the importing is done.

No, for sysres Core. 

It is fixed in trunk though. Merge with it remember.

For the importing of the other things, the interfaces are now independant of everything, so as long as it works and you can maintain it, it is fine.

---

### Post by Rui Pais on 2008-09-18
> **LaRoza said:**
> Ah, good. It will work on any Linux (meaning: run and do what it is told), but to use the gui's you need python-qt4 or python-gtk (or whatever it is called, it is installed by default on Ubuntu). The CLI version could conceivably run in Windows, but it wouldn't work in the same way.


We'll try to get it in for 1.0.2.


That really depends on what GUI you are using, and I don't do squat for the GUI's :-)

I use the CLI version, which I wrote, and has no bugs. (Because it is CLI and more linear)


Here, on OzOS i run both from command line and menu and always get the gtk version...
It would be nice if would have some way of run desired interface with a flag ot a different start script (like: sysres -g or sysres-gtk)
For such kind of actions I usually prefer the CLI too (it's weird restore a system from a running DE...)

Another useful thing would be the ability of add full directory to default to backup, instead of single files, for things like user tune of pm/acpi for suspend or HD parking issues or the simpler case of sources.list implemented on /etc/apt.sources.d/*.list

> **LaRoza said:**
> 
Please wait until 1.0.2. 1.0.1 has some bugs (that looks like an IP address of a sort, too many .)

The code of 1.0.1 and 1.0.2 is not for the future, so any work you do would best be done with trunk, however, trunk has a few issues with the GUI's related to error handling because the driving force behind that started while work was being done on 1.0 and 0.9 and the GUI devs haven't seen it yet (well, at least, not developing with yet)

Ok. No problem at all.
(Let me know if you need help testing or packaging.)

---

### Post by LaRoza on 2008-09-18
> **Rui Pais said:**
> Here, on OzOS i run both from command line and menu and always get the gtk version...
It would be nice if would have some way of run desired interface with a flag ot a different start script (like: sysres -g or sysres-gtk)


```
sysres --qt
```
There are four options:

[list]
[*] sysres --cli
[*] sysres --gtk
[*] sysres --qt
[/list]

The fourth is done by command line arguments only (no interface) for ease of use for...me (I wrote it entirely for me) and has several options.

> 
Another useful thing would be the ability of add full directory to default to backup, instead of single files, for things like user tune of pm/acpi for suspend or HD parking issues or the simpler case of sources.list implemented on /etc/apt.sources.d/*.list

The way it works, it wouldn't be able to do a directory. By its design, it doesn't. It is meant to be a system restore, not a backup program.

> 
Ok. No problem at all.
(Let me know if you need help testing or packaging.)

Testing of lp:sysres/1.0 would be beneficial, you can run it from the directory completely. Do you use bzr?

Packaging is covered by mssever but any suggestions (non of us are packagers, and he is new to it) are helpful.

---

### Post by Rui Pais on 2008-09-18
> **LaRoza said:**
> ```
sysres --qt
```
There are four options:

[list]
[*] sysres --cli
[*] sysres --gtk
[*] sysres --qt
[/list]

The fourth is done by command line arguments only (no interface) for ease of use for...me (I wrote it entirely for me) and has several options.

Ah silly me! i not even tried the obvious (i'm tired...)


> **LaRoza said:**
> 
The way it works, it wouldn't be able to do a directory. By its design, it doesn't. It is meant to be a system restore, not a backup program.

Yes, i understand.

> **LaRoza said:**
> 
Testing of lp:sysres/1.0 would be beneficial, you can run it from the directory completely. Do you use bzr?

Packaging is covered by mssever but any suggestions (non of us are packagers, and he is new to it) are helpful.

Ok i'll try it the source with bzr.
I'll check package. Look quite good. 
My only suggestion, as i said, would be both png and svg icons to cover a large number of DEs and maybe a .desktop file or a mini script to run the cli version independently of DE... but maybe kind of redundant...
i see it recommends python-gtk it should be python-gtk2 or if python-gtk it's fromother non-ubuntu version recommends/depends on both :
Recommends: python-gtk2|python-gtk 
on control file.

---

### Post by mssever on 2008-09-18
First, a comment about the recent file reshuffling: It appears to me (though I can't be certain) that the files were moved, then added back in to bzr. I say that, because those files have completely lost their history. Furthermore, doing things like this can in some cases cause merge conflicts that would otherwise be avoided. Bazaar has a command to prevent this situation and allow bzr to keep track of renames: [FONT=Courier New]bzr mv[/FONT]. The idea is, all filesystem operations should be done with bzr commands whenever such a command is available.

> **Rui Pais said:**
> The only thing that don't shows it's icon, since it's a svg.
Can you include a png image too (with same name so .desktop would not require changes on Icon)?I'll work on that. I'm a bit surprised, though, that e17 doesn't support SVG. Perhaps it's showing its age.
> Just a "contribution" for desktop file, Pt translation:Thanks I added it to my main branch. LaRoza, my branch has some things for merging into trunk. Also, you can take just revision 62 and merge it into 1.0 to get the updated translation.

> **LaRoza said:**
> Please wait until 1.0.2. 1.0.1 has some bugs (that looks like an IP address of a sort, too many .)Is 1.0.2 ready for release now? The launchsysres script will workaround the bug you mentioned, and it's in 1.0.
> **Rui Pais said:**
> (Let me know if you need help testing or packaging.)
If you have experience with packaging, I'd appreciate a code review (feel free to be blunt). I'm the packager, and it's my first time. I've also been toying with the idea of creating separate packages, like nvteighen suggested: sysres-common, sysres-qt, sysres-gtk, sysres-cli (sysres-common should probably recommend sysres-cli, sysres-gtk | sysres-qt, and of course all the interface packages would depend on sysres-common). As this is an area in which I have no experience, suggestions, criticisms and/or code would be welcome. For packaging, you can track lp:sysres or my main branch, lp:~scott.severance/sysres/main.

---

### Post by mssever on 2008-09-18
> **Rui Pais said:**
> i see it recommends python-gtk it should be python-gtk2 or if python-gtk it's fromother non-ubuntu version recommends/depends on both :
Recommends: python-gtk2|python-gtk 
on control file.
Could you elaborate a bit? What is the advantage of depending on python-gtk2 over python-gtk? <Later...> I just looked, and apparently python-gtk is a virtual package. But python-gtk2 doesn't provide it, so what does? I'll change the dependency as you recommended.

---

### Post by OutOfReach on 2008-09-18
Conflicts are such a pain. Even when I use bzr resolve it still leaves some ====TREE things in some files, really annoying.

As a note to LaRoza: I hope you don't mind me doing this (tell me if you do), but I am changing the core logging a bit, as it currently is the core only writes out the name of the restore point when it is created, which can seem a little confusing to an average user. I am changing it so it writes something like:
```
[16:44:59.028179] Created: /home/username/.sysres/Backups--2008-09-18 16:44:56.729055
``` so that it will be more 'readable' to the average user looking through it.

---

### Post by mssever on 2008-09-18
> **OutOfReach said:**
> Conflicts are such a pain. Even when I use bzr resolve it still leaves some ====TREE things in some files, really annoying.
I'm not sure what you're doing, but here's how I handle conflicts. For the sake of this post, let's assume that the conflict is in changelog (which is where they seem to crop up the most for me).
```
meld changelog.*
# meld will show you a three-way diff, which you can use to determine what should
# happen. Usually, *.OTHER is the proper file to use. Meld allows editing in case that
# should be necessary.
# Assuming you're resolving in favor of changelog.OTHER (possibly with some edits):
mv changelog{.OTHER,}
bzr resolve changelog
```And you're done...unless you have more conflicts to resolve.

---

### Post by OutOfReach on 2008-09-18
> **mssever said:**
> I'm not sure what you're doing, but here's how I handle conflicts. For the sake of this post, let's assume that the conflict is in changelog (which is where they seem to crop up the most for me).
```
meld changelog.*
# meld will show you a three-way diff, which you can use to determine what should
# happen. Usualy, *.OTHER is the proper file to use. Meld allows editing in case that should
# be necessary.
# Assuming you're resolving in favor of changelog.OTHER (possibly with some edits):
mv changelog{.OTHER,}
bzr resolve changelog
```And you're done...unless you have more conflicts to resolve.

All this time I've just been doing bzr resolve and manually removing all the gunk that was left over. I will try that next time a conflict(s) come up. Thanks :D

---

### Post by LaRoza on 2008-09-18
> **mssever said:**
> First, a comment about the recent file reshuffling: It appears to me (though I can't be certain) that the files were moved, then added back in to bzr. I say that, because those files have completely lost their history. Furthermore, doing things like this can in some cases cause merge conflicts that would otherwise be avoided. Bazaar has a command to prevent this situation and allow bzr to keep track of renames: [FONT=Courier New]bzr mv[/FONT]. The idea is, all filesystem operations should be done with bzr commands whenever such a command is available.

That explains a lot. Thanks.

> 
I'll work on that. I'm a bit surprised, though, that e17 doesn't support SVG. Perhaps it's showing its age.

The icon is in there now.

> 
Thanks I added it to my main branch. LaRoza, my branch has some things for merging into trunk. Also, you can take just revision 62 and merge it into 1.0 to get the updated translation.


> 
Is 1.0.2 ready for release now? The launchsysres script will workaround the bug you mentioned, and it's in 1.0.
We need it to install the .png files as well. When it can do that, it will be ready I guess.

---

### Post by red_Marvin on 2008-09-19
Sorry for not updating, I've created a new branch sysres/gtk-frontend-1.0 on which I will aim to adress the problems with the gtk interface.

I should get time to work on it today in the weekend.

---

### Post by nvteighen on 2008-09-19
> **mssever said:**
> First, a comment about the recent file reshuffling: It appears to me (though I can't be certain) that the files were moved, then added back in to bzr. I say that, because those files have completely lost their history. Furthermore, doing things like this can in some cases cause merge conflicts that would otherwise be avoided. Bazaar has a command to prevent this situation and allow bzr to keep track of renames: [FONT=Courier New]bzr mv[/FONT]. The idea is, all filesystem operations should be done with bzr commands whenever such a command is available.


Thanks... I used Nautilus to reshuffle everything... :p

---

### Post by nvteighen on 2008-09-19
Ok, I have the branch I was working on as ~evigo/sysres/design and marked it as "Merged". I don't think to do any much work there.

I also reverted for historical reasons. It seems that when marking as "merged" the best practice is to leave things as they were... Think of a "closed" branch.

Now I'll focus a bit on the GTK+ frontend and see what's happening.

---

### Post by anotherdisciple on 2008-09-19
Has anyone tried to bug Canonical and see if this, or something like this could be in the default installations of *ubuntu?

Is that reasonable or a long shot?

---

### Post by mssever on 2008-09-19
I've built packages now for 1.0.2 (attached). The requisite changes should be merged into 1.0 from ~scott.severance/sysres/mssever. In the process, I discovered that we need to dynamically set the version number from either the build script or the installer. The .deb for 1.0.1 probably incorrectly reports the version as 1.0. 1.0.2 is correct, but only because I manually fixed it.

Please, let's make the this the last release of the 1.0 series, and base 1.1 off trunk. The version issue would be solved more simply if I didn't have to find an automated solution that will work for both trunk and 1.0, since they've diverged so much.

I also discovered another bug: In 1.0.2, making a restore point with -- in the name now fails silently. It shouldn't fail, and nothing should ever fail silently. I can't test in trunk, since trunk is currently broken (can't load any interface), and I haven't investigated as to the cause. Regardless of the cause, we need to re-think our exception handling. The ImportError is getting caught and the message "You must have Py(GTK|Qt) installed" is printed, even though the ImportError is definitely not related to pygtk or pyqt.

> **nvteighen said:**
> Thanks... I used Nautilus to reshuffle everything... :pI didn't realize that anyone used Nautilus while programming.

> **anotherdisciple said:**
> Has anyone tried to bug Canonical and see if this, or something like this could be in the default installations of *ubuntu?

Is that reasonable or a long shot?
I think it would be good, but IMHO we have a way to go. The GUIs don't follow the HIG, and sysres isn't sufficiently comprehensive or automatic. Installing a script in /etc/cron.weekly would go a long way toward solving the automatic problem, but to be sufficiently comprehensive would require a lot of thought about what exactly should be restored by default and what shouldn't. Also, how should we handle conflicts?

---

### Post by markp1989 on 2008-09-19
very good idea, i would like it if it could back up the init scripts , basicaly theses folders /etc/rc*.d

---

### Post by LaRoza on 2008-09-19
> **anotherdisciple said:**
> Has anyone tried to bug Canonical and see if this, or something like this could be in the default installations of *ubuntu?

Is that reasonable or a long shot?

Not for a while, no. I know OzOS is considering it, once I give them the green light that the release is ready.

> **mssever said:**
> I've built packages now for 1.0.2 (attached). The requisite changes should be merged into 1.0 from ~scott.severance/sysres/mssever. In the process, I discovered that we need to dynamically set the version number from either the build script or the installer. The .deb for 1.0.1 probably incorrectly reports the version as 1.0. 1.0.2 is correct, but only because I manually fixed it.

I don't know what you mean. The version is in SystemRestore/Constants/__init__.py

> 
Please, let's make the this the last release of the 1.0 series, and base 1.1 off trunk. The version issue would be solved more simply if I didn't have to find an automated solution that will work for both trunk and 1.0, since they've diverged so much.

If it works we will. 1.0.x should work, even if the code isn't the best.

> 
I also discovered another bug: In 1.0.2, making a restore point with -- in the name now fails silently. It shouldn't fail, and nothing should ever fail silently. I can't test in trunk, since trunk is currently broken (can't load any interface), and I haven't investigated as to the cause. Regardless of the cause, we need to re-think our exception handling. The ImportError is getting caught and the message "You must have Py(GTK|Qt) installed" is printed, even though the ImportError is definitely not related to pygtk or pyqt.

It isn't a bug. It is a kludge. It doesn't fail either, it changes them to __.

Trunk's interfaces are expected to be broken, except for the CLI one.

> 
I didn't realize that anyone used Nautilus while programming.

I didn't realise anyone used Nautilus.

> Also, how should we handle conflicts?
Conflicts with what?

---

### Post by LaRoza on 2008-09-19
> **markp1989 said:**
> very good idea, i would like it if it could back up the init scripts , basicaly theses folders /etc/rc*.d

Give file names ;) sysres isn't a backup program and only supports files.

---

### Post by LaRoza on 2008-09-19
> **mssever said:**
> I've built packages now for 1.0.2 (attached). The requisite changes should be merged into 1.0 from ~scott.severance/sysres/mssever. In the process, I discovered that we need to dynamically set the version number from either the build script or the installer. The .deb for 1.0.1 probably incorrectly reports the version as 1.0. 1.0.2 is correct, but only because I manually fixed it.

There is no icon used with the menu entry installer.

---

### Post by mssever on 2008-09-19
> **mssever said:**
> trunk is currently broken (can't load any interface), and I haven't investigated as to the cause.
Found and fixed in my main branch. The installer hadn't been updated to handle the recent file shuffling. Also, sysres was a bit over-ambitious in catching ImportErrors. I dialed that back a bit, though there's probably a more optimal solution.
> **LaRoza said:**
> It doesn't fail either, it changes them to __.Actually, it *does* fail. Try it. It's supposed to change them to __, but what actually happens is that you enter the name, hit OK, the dialog closes, and the restore point doesn't show up.
> Conflicts with what?If you've created a restore point, then change one of the tracked files, then restore, how to we know whether to keep or overwrite a change?

> **LaRoza said:**
> There is no icon used with the menu entry installer.
There should be, and it works for me. Do you have the icons in /usr/share/icons/hicolor/*/apps? It may be that your system's cache hasn't been updated, since we used to keep the icon in /usr/share/pixmaps when we only had an SVG icon.

If we end up having to call gtk-update-icon-cache, I'll need advice as how to do that. It should presumably be in a maintainer script. Those are currently auto-generated, so I don't know how to add that to the script while maintaining the benefits of auto-generation.

---

### Post by LaRoza on 2008-09-19
> **mssever said:**
> 
Actually, it *does* fail. Try it. It's supposed to change them to __, but what actually happens is that you enter the name, hit OK, the dialog closes, and the restore point doesn't show up.

I see it now. It worked in trunk. I fixed that bug. Current lp:sysres/1.0 has the correct code.

> 
If you've created a restore point, then change one of the tracked files, then restore, how to we know whether to keep or overwrite a change?

I don't understand. The point of sysres is to overwrite those changes. It restores to that particular time. It isn't a version control system for system files.

> 
There should be, and it works for me. Do you have the icons in /usr/share/icons/hicolor/*/apps? It may be that your system's cache hasn't been updated, since we used to keep the icon in /usr/share/pixmaps when we only had an SVG icon.

If you get it, I'll take your word for it. I rarely use GNOME anyway.

---

### Post by mssever on 2008-09-19
> **LaRoza said:**
> I see it now. It worked in trunk. I fixed that bug. Current lp:sysres/1.0 has the correct code.
Here's a corrected package.

---

### Post by LaRoza on 2008-09-19
> **mssever said:**
> Here's a corrected package.

Thanks. I see it uses the -- modification code, but does it use the latest merge of the GTK changes?

---

### Post by Vadi on 2008-09-19
I didn't realize someone was actually working on this... but [http://www.savemyconf.com/](http://www.savemyconf.com/) seems to be promising. Alpha though atm.

Edit: sorry, that's for the installed programs, not configuration files.

---

### Post by LaRoza on 2008-09-19
> **Vadi said:**
> I didn't realize someone was actually working on this... but [http://www.savemyconf.com/](http://www.savemyconf.com/) seems to be promising. Alpha though atm.

I would never use that...

Do you really want people getting your personal files? Especially configuration files?

---

### Post by red_Marvin on 2008-09-19
I'm doing a some small commits, for each change in the code more or less, but I would like to know what the current issues with the gtk implementation are.
I haven't been able to reproduce the errors in post [423](http://ubuntuforums.org/showpost.php?p=5821272&postcount=423), and the ones mentioned in [472](http://ubuntuforums.org/showpost.php?p=5821272&postcount=472) should be fixed.
I'm continuing tests for 423 for a while though.

---

### Post by LaRoza on 2008-09-19
> **red_Marvin said:**
> I'm doing a some small commits, for each change in the code more or less, but I would like to know what the current issues with the gtk implementation are.
I haven't been able to reproduce the errors in post 423, and the ones mentioned in 472 should be fixed.
I'm continuing tests for 423 for a while though.

The main thing is to make sure it restores when it is supposed to.

The errors in 423 are no longer present, because of the new launcher and core code.

Please try the .deb given above and let us know if you think you are done.

---

### Post by mssever on 2008-09-19
> **LaRoza said:**
> Thanks. I see it uses the -- modification code, but does it use the latest merge of the GTK changes?
I merged with 1.0 right before I built the package, so it includes whatever was there at the time.

---

### Post by red_Marvin on 2008-09-19
The gtk code in the deb is not the latest (but that's what I expected, it being a few posts up), and I don't know if it is supposed to install a launcher in the gnome menu, because it doesn't, it is a strange error,
when I before the deb tried the install.sh a menu entry was put there, the first time, but not again after I uninstalled and reinstalled.
It's not a killall gnome-panel or log out/in problem, since I've tried those, but I don't know if it is a sysres bug or perhaps a gnome bug.

As for the maturity of my own code, I think it is ready for upstream, if you can confirm that the post 472 bug is fixed and no new has appeared.

EDIT, I need to update the changelog... I always forget that!

---

### Post by Vadi on 2008-09-19
savemyconf just saves the packages you installed, not configuration files like this program.

And yes... I'm not paranoid. I enabled statistics on the software sources tab too. It's all anonymized :)

---

### Post by mssever on 2008-09-19
> **Vadi said:**
> I didn't realize someone was actually working on this... but [http://www.savemyconf.com/](http://www.savemyconf.com/) seems to be promising. Alpha though atm.

Edit: sorry, that's for the installed programs, not configuration files.
The website doesn't really explain what it does (we can write it off on that basis alone). It appears that it's something along the lines of a configuration/program backup site. But doing it as a website seems incredibly silly to me. To do it right, you need filesystem access, and that can't be done from a website without a browser plugin or something like that.

---

### Post by Vadi on 2008-09-19
Yeah, you install a lil thing that runs and gets the listing.

But, being in alpha, the website doesn't want to accept results atm.

---

### Post by LaRoza on 2008-09-19
> **mssever said:**
> I merged with 1.0 right before I built the package, so it includes whatever was there at the time.

Ok. Sorry for being a pain. Perhaps we need a more...professional? form of communication?

> **red_Marvin said:**
> The gtk code in the deb is not the latest (but that's what I expected, it being a few posts up), and I don't know if it is supposed to install a launcher in the gnome menu, because it doesn't, it is a strange error,
when I before the deb tried the install.sh a menu entry was put there, the first time, but not again after I uninstalled and reinstalled.
It's not a killall gnome-panel or log out/in problem, since I've tried those, but I don't know if it is a sysres bug or perhaps a gnome bug.

The menu entry will be in Applications->System Tools.

> 
EDIT, I need to update the changelog... I always forget that!

We all do it seems. mssever and I are also time travelers apparently.

Ok, could it be packaged one last time, we'll test it, and then, focus on trunk solely.

---

### Post by OutOfReach on 2008-09-19
[QUOTE=LaRoza]Perhaps we need a more...professional? form of communication?[/QUOTE]

I think that we can all safely agree on that.

---

### Post by LaRoza on 2008-09-19
> **OutOfReach said:**
> I think that we can all safely agree on that.

Perhaps we can get ourselves a wiki or something.

---

### Post by mssever on 2008-09-19
> **red_Marvin said:**
> The gtk code in the deb is not the latest (but that's what I expected, it being a few posts up), and I don't know if it is supposed to install a launcher in the gnome menu, because it doesn't, it is a strange error,
when I before the deb tried the install.sh a menu entry was put there, the first time, but not again after I uninstalled and reinstalled.
Have you done a thorough check of the menu? It's weird that you aren't seeing it. Also, verify that /usr/share/applications/sysres.desktop exists.
> **Vadi said:**
> Yeah, you install a lil thing that runs and gets the listing.
OK, so what's the point of a whole webapp? All you need is to keep a file with a package listing.
> **LaRoza said:**
> Ok. Sorry for being a pain. Perhaps we need a more...professional? form of communication?Perhaps a third-party subforum? We could also benefit by filing bugs on Launchpad's bug tracker--which is designed for the purpose. We can create a branch for each bug, and tie it to the bug report.
> Ok, could it be packaged one last time, we'll test it, and then, focus on trunk solely.Will do. I'll hold off for a bit to give red_Marvin time to test the icon.

---

### Post by OutOfReach on 2008-09-19
A wiki is a very nice idea, but I think we should also have some kind of 'organized' meetings to discuss things because some of us cannot keep up with all these things since we are not on all the time (me for example). Just brainstorming. :)

---

### Post by red_Marvin on 2008-09-19
The desktop file exists, but no menu entry.

---

### Post by LaRoza on 2008-09-19
> **OutOfReach said:**
> A wiki is a very nice idea, but I think we should also have some kind of 'organized' meetings to discuss things because some of us cannot keep up with all these things since we are not on all the time (me for example). Just brainstorming. :)

IRC?

We could easily hold it in #ubuntu-programming as that is not busy.

> **red_Marvin said:**
> The desktop file exists, but no menu entry.

And I don't get the icon. mssever, perhaps this is a more complex issue?

---

### Post by OutOfReach on 2008-09-19
> **LaRoza said:**
> IRC?

We could easily hold it in #ubuntu-programming as that is not busy.


I have no problem with IRC as long as you guys are in agreement with it.

---

### Post by red_Marvin on 2008-09-19
I'm often online (nick: insomninja), but irc should not be used for messages that need to be persistent over time, even with some sort of logging, there probably would be too much noise to be useful in that respect, but for quick discussion I'm all for it.

---

### Post by LaRoza on 2008-09-19
> **red_Marvin said:**
> I'm often online (nick: insomninja), but irc should not be used for messages that need to be persistent over time, even with some sort of logging, there probably would be too much noise to be useful in that respect, but for quick discussion I'm all for it.

I agree. IRC is best for periodic meetings to keep everyone together.

We'll use this thread (obviously) for now.

---

### Post by mssever on 2008-09-19
> **LaRoza said:**
> IRC?

We could easily hold it in #ubuntu-programming as that is not busy.Or, how about registering #sysres? I think a combination of IRC for real-time discussion, a forum somewhere where we can have multiple threads, and using Launchpad for bugs/feature requests would be great.

> And I don't get the icon. mssever, perhaps this is a more complex issue?I'm thinking that people are experiencing caching problems. Dropping the .desktop file in /usr/share/applications should be enough according to the spec, and it works for me. I had icon problems a while back, the last time I messed with the icons. I don't remember what changes caused them, but at some point I ended up rebooting, and that solved my icon problem. I guess the ideal thing here would be to test on several non-development machines (probably VMs). While I might be wrong, I don't think that this is strictly a bug in sysres. I think its a bug in gnome-panel, or whatever's responsible for handling .desktop files.

Also, do things work fine under KDE?

EDIT: I suspect that the caching problems are due to frequent development-related changes. In other words, I'd be surprised if the end users experienced them.

---

### Post by LaRoza on 2008-09-19
> **mssever said:**
> Or, how about registering #sysres? I think a combination of IRC for real-time discussion, a forum somewhere where we can have multiple threads, and using Launchpad for bugs/feature requests would be great.

I am working on a forum (get AdBlock/Block Content ready...)

[http://laroza.19.forumer.com](http://laroza.19.forumer.com)

Register (please use names that we know, your name here, from the changelog/credits or your other commonly used names)

> 
I'm thinking that people are experiencing caching problems. 

Also, do things work fine under KDE?

EDIT: I suspect that the caching problems are due to frequent development-related changes. In other words, I'd be surprised if the end users experienced them.

That is why I am hesitant to label it a bug.

---

### Post by OutOfReach on 2008-09-19
> **LaRoza said:**
> I am working on a forum (get AdBlock/Block Content ready...)

[http://laroza.19.forumer.com](http://laroza.19.forumer.com)

Register (please use names that we know, your name here, from the changelog/credits or your other commonly used names)


Nice job, LaRoza I'll register right now (I'll be using OutOfReach).

---

### Post by LaRoza on 2008-09-19
> **mssever said:**
> 
Also, do things work fine under KDE?

Installed KDE to test it.

Icons show up fine, starts up fine, no problems.

Perhaps we should call it "ksysres" when it is running in KDE?

---

### Post by mssever on 2008-09-20
> **LaRoza said:**
> I am working on a forum (get AdBlock/Block Content ready...)Ads? What ads? (Presumably due to Adblock Plus, which I've already installed.) Two observations: First, I can't seem to find where to set my avatar. I don't know if this is one of PHPBB's user-unfriendly (mis)features, or if I'm just blind...

Second, it might be best to put the sysres Users forum at the top where our millions of users can find it easily. :)

> **LaRoza said:**
> Perhaps we should call it "ksysres" when it is running in KDE?Well, sysres really isn't a KDE app. It just happens to have a Qt interface. KDE apps follow certain patterns, which we don't follow.

---

### Post by mssever on 2008-09-20
Here's the--hopefully final--1.0.2. I tried to post it in the new forum, but apparently it doesn't allow file attachments.

---

### Post by LaRoza on 2008-09-20
> **mssever said:**
> Ads? What ads? (Presumably due to Adblock Plus, which I've already installed.) Two observations: First, I can't seem to find where to set my avatar. I don't know if this is one of PHPBB's user-unfriendly (mis)features, or if I'm just blind...
No avatars are enabled at the moment.

> 
Second, it might be best to put the sysres Users forum at the top where our millions of users can find it easily. :)

Easily? If our dear users can't find it, they shouldn't be using the forum ;) 


> 
Well, sysres really isn't a KDE app. It just happens to have a Qt interface. KDE apps follow certain patterns, which we don't follow.
I was making fun of KDE :-)

---

### Post by mssever on 2008-09-20
> **LaRoza said:**
> No avatars are enabled at the moment.
Then I'll make that a feature request. I often recognize people more by avatar than nick (except for the people who use generic avatars or frequently change them), so I think avatars are quite handy.

---

### Post by LaRoza on 2008-09-20
> **mssever said:**
> Then I'll make that a feature request. I often recognize people more by avatar than nick (except for the people who use generic avatars or frequently change them), so I think avatars are quite handy.

They should be enabled now.

---

### Post by nvteighen on 2008-09-20
Well, the forum is a great idea. I register under 'emvigo'

I'm a bit lost on what's going on here... as development is now focused on releasing 1.0. Can anybody please tell me what is the status of the GUIs in trunk with respect to stable? I mean, have bugfixes been ported or not?

EDIT: GUI devs, please check out my post for you at the new forum.

---

### Post by nvteighen on 2008-09-20
Dissasters...

For some reason, there's legacy code leaking into trunk again... Even code to catch RPException at the Qt module.

So, to ease things I have registered a new branch: lp:~sysres-interfaces/sysres/interfaces and registered it under the "SysRes Interface Team" so any member can commit to that branch.

I've added insomninja/red_Marvin and OutofReach as team members. So you have write permissions to that branch.

(And by the way, Teams have mailing lists!)

---

### Post by red_Marvin on 2008-09-20
I just recieved a notice about this in the mail: [gtk bug blueprint](https://blueprints.launchpad.net/sysres/+spec/gtk-version-like-cli-interface). Is this the ghost of the 423 bug and my very intermittent mail checking skills, or is it something new?

EDIT0: If not, is the user unfriendliness a product of the bug, or do you want anything else/additional changed?

EDIT1: I've just registered to the sysres forums: my nick is LeoB

---

### Post by OutOfReach on 2008-09-20
> **nvteighen said:**
> 
For some reason, there's legacy code leaking into trunk again... Even code to catch RPException at the Qt module.

Did you pull from qt-frontend, because it was fixed there...

---

### Post by nvteighen on 2008-09-20
> **OutOfReach said:**
> Did you pull from qt-frontend, because it was fixed there...
I don't know from where... I think it was from trunk.

---

### Post by nvteighen on 2008-09-20
OK, we have an Interfaces Team... we'll use Centralized Versioning (CVS/SVN style) **inside** that team, so the commands will be a bit different (update/commit vs. merge/commit/push cycle). I think it's the best, as it is meant to be a single branch for we three members in the very same area, so Distributed Versioning seems overkill there to me.

Read [http://laroza.19.forumer.com/viewtopic.php?p=13#13](http://laroza.19.forumer.com/viewtopic.php?p=13#13) to understand why I took that approach.

But anyway, if that goes wrong, Bazaar allows you to switch between Versioning modes in an amazingly easy way.

---

### Post by LaRoza on 2008-09-20
> **nvteighen said:**
> Well, the forum is a great idea. I register under 'emvigo'

Added to developers group. Developers should have mod rights in the developer forums (so you can make stickies and such). If you do, I have no idea. I prefer vBulletin for this kind of stuff...

> 
I'm a bit lost on what's going on here... as development is now focused on releasing 1.0. Can anybody please tell me what is the status of the GUIs in trunk with respect to stable? I mean, have bugfixes been ported or not?

1.0 has been released to be tested. See [https://launchpad.net/sysres/trunk/1.0](https://launchpad.net/sysres/trunk/1.0) (1.0.2 is the latest). Now that "works", we are focusing on trunk. I have no idea about the GUI's in trunk.

> **nvteighen said:**
> Dissasters...

So, to ease things I have registered a new branch: lp:~sysres-interfaces/sysres/interfaces and registered it under the "SysRes Interface Team" so any member can commit to that branch.

I've added insomninja/red_Marvin and OutofReach as team members. So you have write permissions to that branch.

What a disaster(!).

I guess I am not allowed in the team :(. ;) I guess the CLI and command line argument interfaces don't need special attention.


> **red_Marvin said:**
> I just recieved a notice about this in the mail: [gtk bug blueprint](https://blueprints.launchpad.net/sysres/+spec/gtk-version-like-cli-interface). Is this the ghost of the 423 bug and my very intermittent mail checking skills, or is it something new?


I think that is the old bug. It should be marked as fixed. Doing now.

---

### Post by nvteighen on 2008-09-20
> **LaRoza said:**
> Added to developers group. Developers should have mod rights in the developer forums (so you can make stickies and such). If you do, I have no idea. I prefer vBulletin for this kind of stuff...

Thank you.


> 1.0 has been released to be tested. See [https://launchpad.net/sysres/trunk/1.0](https://launchpad.net/sysres/trunk/1.0) (1.0.2 is the latest). Now that "works", we are focusing on trunk. I have no idea about the GUI's in trunk.

Perfect. So, its now turn for the new core, right?

> What a disaster(!).
Oh, thanks... For some strange reason I keep writing *dissaster, even if I know the etymology 

> 
I guess I am not allowed in the team :(. ;) I guess the CLI and command line argument interfaces don't need special attention.

I knew You're allowed, but you have to request it. I did that in order to have some control over who can contribute there, as it is not the main development place and it's a team that is devoted to a highly specific issue.

In other words, I explicitly wanted a Savannah style where only members have commit access. Of course, everyone can branch from the Team's code and start its own parallel branch.

---

### Post by LaRoza on 2008-09-20
> **nvteighen said:**
> 
Perfect. So, its now turn for the new core, right?

Yes. Finally.

> 
Oh, thanks... For some strange reason I keep writing *dissaster, even if I know the etymology 

What is the etymology? 

> 
In other words, I explicitly wanted a Savannah style where only members have commit access. Of course, everyone can branch from the Team's code and start its own parallel branch.

I know, I was pretending to be hurt. :-)

---

### Post by nvteighen on 2008-09-21
> **LaRoza said:**
> Yes. Finally.
OK. Please, merge trunk from ~evigo/sysres/core, as I had to "fix" something at the core. (actually, add a feature, but an optional one, so we don't break anything).

> What is the etymology?
A quite funny one: From Italian *dis-astro*, lit. meaning "not-starry" in the sense that's not favored by the starts according astrology.

---

### Post by mssever on 2008-09-22
Here's 1.0.3.

---

### Post by Rui Pais on 2008-09-22
> **mssever said:**
> Here's 1.0.3.

Hi mssever.

I tried the 1.0.3 and it seems to work ok.

The only thing that don't look correct it's the app icon, that don't appear when (at least on gtk) graphical interface runs. No luck neither on OzOS nor with gnome from Ubuntu.

btw. icons are a little over complex on this last 2 debs... the full set of sizes seems a bit too heavier for an app that user it's suppose to run once in a while. Just a thought.



One side note, my comment on my previous post about python-gtk on 'Recommendations' was only based on that was already there. 

As far as i see it is not need it at all. 
On Ubuntu its' only the python-gtk2 and the same for plain debian. 
On Debian the old package was called python-gtk-1.2, so at most you would need to change to that if you want to offer support for old python-gtk versions under Debian.

---

### Post by mssever on 2008-09-22
> **Rui Pais said:**
> I tried the 1.0.3 and it seems to work ok.I should have provided the context for this. Discussion of this bug took place here: [http://laroza.19.forumer.com/viewtopic.php?t=10](http://laroza.19.forumer.com/viewtopic.php?t=10)

> The only thing that don't look correct it's the app icon, that don't appear when (at least on gtk) graphical interface runs. No luck neither on OzOS nor with gnome from Ubuntu.I'm not sure I know what you mean by "app icon", but there are some oddities with the icons. They don't seem to work right until after you log out and back in. It seems that a) stale caches get used; and b) caches fail to notice the new icons that are installed in some circumstances. If you know of a solution, I'd love to hear it.

> btw. icons are a little over complex on this last 2 debs... the full set of sizes seems a bit too heavier for an app that user it's suppose to run once in a while. Just a thought.That's a consequence of including PNG support, since I now have to include a PNG rendered at each icon size. I don't know all the icon sizes used, so I included one for many of the sizes in use on my system. I know that the apps will scale the icon if necessary, but PNG icons look bad when scaled (that's the argument for SVG). My preference would be to drop the PNGs altogether in favor of SVG, but since you said that e17 doesn't handle SVG, then there's a need for the PNGs. Suggestions are welcome.

---

### Post by red_Marvin on 2008-09-22
> **Rui Pais said:**
> The only thing that don't look correct it's the app icon, that don't appear when (at least on gtk) graphical interface runs. No luck neither on OzOS nor with gnome from Ubuntu.

Do you mean the logo that (for some window managers and styles) show up in the window title bar, and in the window list part of the (gnome-)panel? If so I have added code to show the sysres logo now.

---

### Post by Rui Pais on 2008-09-22
> **mssever said:**
> 
I'm not sure I know what you mean by "app icon", but there are some oddities with the icons. They don't seem to work right until after you log out and back in. It seems that a) stale caches get used; and b) caches fail to notice the new icons that are installed in some circumstances. If you know of a solution, I'd love to hear it.


> **red_Marvin said:**
> Do you mean the logo that (for some window managers and styles) show up in the window title bar, and in the window list part of the (gnome-)panel? If so I have added code to show the sysres logo now.

Thats right, the one on title bar (at least it appears on plain gnome and e17). Glad to hear you managed to make it show :)
Thanks.



> **mssever said:**
> I should have provided the context for this. Discussion of this bug took place here: [http://laroza.19.forumer.com/viewtopic.php?t=10](http://laroza.19.forumer.com/viewtopic.php?t=10)

That's a consequence of including PNG support, since I now have to include a PNG rendered at each icon size. I don't know all the icon sizes used, so I included one for many of the sizes in use on my system. I know that the apps will scale the icon if necessary, but PNG icons look bad when scaled (that's the argument for SVG). My preference would be to drop the PNGs altogether in favor of SVG, but since you said that e17 doesn't handle SVG, then there's a need for the PNGs. Suggestions are welcome.

Uhmm i see. But i don't think such way should be needed. 
You can just implemented plain SVG for gnome/xfce/kde user and just add a single PNG on /usr/share/pixmaps/ with the same name as SVG version (sysres.png on this case) for deal with e17 needs.
The only place that e17 searches for icon it's that place from line Icon=iconname on desktop file to add icon to menu. Can be a standard 48x48 image (but any other size works).
All other icons will not be used anyway. 
That make things simpler and i think it can satisfy everyones needs and preferences.

---

### Post by mssever on 2008-09-23
> **Rui Pais said:**
> Uhmm i see. But i don't think such way should be needed. 
You can just implemented plain SVG for gnome/xfce/kde user and just add a single PNG on /usr/share/pixmaps/ with the same name as SVG version (sysres.png on this case) for deal with e17 needs.
The only place that e17 searches for icon it's that place from line Icon=iconname on desktop file to add icon to menu. Can be a standard 48x48 image (but any other size works).
All other icons will not be used anyway. 
That make things simpler and i think it can satisfy everyones needs and preferences.Hmm.. I wonder if Gnome/KDE/Xfce automatically prefer /usr/share/pixmaps/foo.svg over /usr/share/pixmaps/foo.png. Because the problem with only providing a PNG at a single resolution is that it scales poorly--that's why I converted our original icon from PNG to SVG in the first place. I suppose I could delete some of the icon sizes, though. I just need to figure out which ones.

---

### Post by mssever on 2008-09-23
<off-topic>@Rui Pais:

I just downloaded Oz OS to give it a whirl (and to test directly on it) and found some bugs. I couldn't find a link on your site to your bug tracker. I tried registering on the forum, but I encountered problems, so I'm posting here since I noticed that you're an admin on the cafélinux forum and I know you're watching this thread.

Forum registration issues:

[LIST=1]
[*]The TOS says in part: > you agree to never give your password out to another person **except an administrator**, for your protection and for validity reasons Note the part I bolded. No educated person would ever give their password to anyone, including an admin. There are no scenarios in which an admin would need to know a user's password, though a simple SQL query might reveal it--depending on how the password is stored. So I can't agree to the terms of service.
[*]After correctly filling out my registration info, I got an error message complaining that I hadn't selected an avatar. However, I'd left the setting on its default, "(no pic)" which is should be valid, because a) the UI gives no indication that it's invalid; and b) requiring a stock avatar at registration time is unreasonable. Why should I select a stock avatar only to replace it with a custom one immediately after registration?
[*]After randomly picking an avatar, I re-submitted. This time, I got an error about my password being too short. Again, there are several issues with this:
[LIST=1]
[*]The validator should report all errors at once, instead of one at a time. Who knows how many other things it didn't like? I don't, since this is when I got tired of fighting the forum and gave up.
[*]The UI didn't stipulate any password rules. Therefore, it's a bug not to accept whatever password I provide.
[*]Enforcing an eight-character minimum is over-zealous security. First, the worst case scenario if a user's password is compromised is that the user gets banned. It's not like there's anything on a public forum that requires high security. Second, the password is submitted in cleartext over HTTP, so anyone who wants to snoop for passwords can do so. Any site that cares about security should be using SSL or TLS. Third, enforcing an eight-character minimum doesn't necessarily increase security anyway. Which is more secure: "password" (eight characters) or "dY5h~8" (six characters)? Any sensible attacker would try a dictionary attack before brute force.
[/LIST]
 
[/LIST]

OzOS bugs (what I set out to report) I'm running the latest Oz OS (0.5) on VirtualBox 1.6.4 (Ubuntu Hardy host):

[LIST=1]
[*]When I ran the live CD, I kept getting sudo prompts, and the password wasn't made obvious. (I know that the website states that the password is blank, but that doesn't help me when I'm staring at a password prompt that I wasn't expecting--since Ubuntu live CDs never prompt for a password.) I don't know how Ubuntu handles this, but setting ```
thelivecduser ALL=(ALL) NOPASSWD: ALL
``` in /etc/sudoers would go a long way.
[*]The launcher icons on the left edge of the screen have no tooltips, forcing the user to try to guess what they do.
[*]When usplash displays a message, it does so in a box with a blue background, such that the text is nearly impossible to read. Example: When you reboot the live CD, it prompts you  to eject the CD. Except the prompt is extremely difficult to read.
[*]Switching VirtualBox to fullscreen causes all my other VMs to adjust their screen resolution, but not Oz. It's possible that's a VirtualBox issue, though.
[/LIST]
</off-topic>

---

### Post by Rui Pais on 2008-09-23
> **mssever said:**
> Hmm.. I wonder if Gnome/KDE/Xfce automatically prefer /usr/share/pixmaps/foo.svg over /usr/share/pixmaps/foo.png. Because the problem with only providing a PNG at a single resolution is that it scales poorly--that's why I converted our original icon from PNG to SVG in the first place. I suppose I could delete some of the icon sizes, though. I just need to figure out which ones.

Yes png scales badly, but i don't see where scales occur on such case.
It will be on main menus that it's almost fixed in size. Desktop icons are the only place that icon appears bigger, but i doubt that users create a desktop launcher for such an administrative tool...

I tried and made different png and svg icons and, under gnome, systems seems to always prefer the svg versions (that btw don't shows on menus, but appears ok on alacarte and when set icon on desktop). 
Put the launcher on gnome-panel seems to go back to png version (it looks for 48x48 resol.) no matter if there's a full png set implemented or just svg one (some parts of gnome stills relies on png only? I don't know...)

Anyway, if you feel better only implementing a SVG, that's OK.
(I can add an extra pixmap for desktop, no problem.)

---

### Post by Rui Pais on 2008-09-23
Here the OzOS thread on Ubuntu forum:
[http://ubuntuforums.org/showthread.php?t=623803](http://ubuntuforums.org/showthread.php?t=623803)
(maybe some UF staff can move these two post there)

> **mssever said:**
> <off-topic>@Rui Pais:

I just downloaded Oz OS to give it a whirl (and to test directly on it) and found some bugs. I couldn't find a link on your site to your bug tracker. I tried registering on the forum, but I encountered problems, so I'm posting here since I noticed that you're an admin on the cafélinux forum and I know you're watching this thread.

Forum registration issues:

[LIST=1]
[*]The TOS says in part:  Note the part I bolded. No educated person would ever give their password to anyone, including an admin. There are no scenarios in which an admin would need to know a user's password, though a simple SQL query might reveal it--depending on how the password is stored. So I can't agree to the terms of service.
[*]After correctly filling out my registration info, I got an error message complaining that I hadn't selected an avatar. However, I'd left the setting on its default, "(no pic)" which is should be valid, because a) the UI gives no indication that it's invalid; and b) requiring a stock avatar at registration time is unreasonable. Why should I select a stock avatar only to replace it with a custom one immediately after registration?
[*]After randomly picking an avatar, I re-submitted. This time, I got an error about my password being too short. Again, there are several issues with this:
[LIST=1]
[*]The validator should report all errors at once, instead of one at a time. Who knows how many other things it didn't like? I don't, since this is when I got tired of fighting the forum and gave up.
[*]The UI didn't stipulate any password rules. Therefore, it's a bug not to accept whatever password I provide.
[*]Enforcing an eight-character minimum is over-zealous security. First, the worst case scenario if a user's password is compromised is that the user gets banned. It's not like there's anything on a public forum that requires high security. Second, the password is submitted in cleartext over HTTP, so anyone who wants to snoop for passwords can do so. Any site that cares about security should be using SSL or TLS. Third, enforcing an eight-character minimum doesn't necessarily increase security anyway. Which is more secure: "password" (eight characters) or "dY5h~8" (six characters)? Any sensible attacker would try a dictionary attack before brute force.
[/LIST]
 
[/LIST]

Thanks for the report, mssever!
I'll pass it to the ones who take care of that part.
(I confess that it's the first time i see anyone have problem to register! 
I thought that part was automatically done and care by SMF underneath, and so equal on any forum that use SMF...)


> **mssever said:**
> 
OzOS bugs (what I set out to report) I'm running the latest Oz OS (0.5) on VirtualBox 1.6.4 (Ubuntu Hardy host):

[LIST=1]
[*]When I ran the live CD, I kept getting sudo prompts, and the password wasn't made obvious. (I know that the website states that the password is blank, but that doesn't help me when I'm staring at a password prompt that I wasn't expecting--since Ubuntu live CDs never prompt for a password.) I don't know how Ubuntu handles this, but setting ```
thelivecduser ALL=(ALL) NOPASSWD: ALL
``` in /etc/sudoers would go a long way.
[*]The launcher icons on the left edge of the screen have no tooltips, forcing the user to try to guess what they do.
[*]When usplash displays a message, it does so in a box with a blue background, such that the text is nearly impossible to read. Example: When you reboot the live CD, it prompts you  to eject the CD. Except the prompt is extremely difficult to read.
[*]Switching VirtualBox to fullscreen causes all my other VMs to adjust their screen resolution, but not Oz. It's possible that's a VirtualBox issue, though.
[/LIST]
</off-topic>
Again thanks for these.
1- I'll try that!! You  can't imagine the hours I've lost searching for a way to fix that (pasing from default ubuntu to e17 creates that issue). 
I tried endless combination, specially with groups, on sudoers file... but 'thelivecduser'?? who would remember such thing? where that "user" came from?
Many thanks for the tip! I'll let you know if it works.

2- Never though on that. The ibar icon set (quicklauncher) it's quite universal, all well known, but it should tell something to new users.
I'll give it a try on next version.

3- That's unfortunately another thing i can find a way to fix. The blue color appears after change the default usplash... although there is such color on neither usplash themes or any reference/image that i saw on conf files...

4- Don't know, a VB issue maybe. I'll discuss this with Aubrey, that do the tests on VM. He never mention it, at least that i remember.

Thanks

---

### Post by LaRoza on 2008-09-23
> **mssever said:**
> 
[*]After correctly filling out my registration info, I got an error message complaining that I hadn't selected an avatar. However, I'd left the setting on its default, "(no pic)" which is should be valid, because a) the UI gives no indication that it's invalid; and b) requiring a stock avatar at registration time is unreasonable. Why should I select a stock avatar only to replace it with a custom one immediately after registration?


I had a problem with that also. It is a UI problem. "No pic" seemed lack a perfectly valid choice.

> 
[*]Any sensible attacker would try a dictionary attack before brute force.

I am not sensible :(

---

### Post by mssever on 2008-09-23
> **Rui Pais said:**
> I tried and made different png and svg icons and, under gnome, systems seems to always prefer the svg versions (that btw don't shows on menus, but appears ok on alacarte and when set icon on desktop).Have you tried testing this after logging out and back in? (Or maybe killing gnome-panel is sufficient.) That sounds like the caching issue that's been bugging me.
> Put the launcher on gnome-panel seems to go back to png version (it looks for 48x48 resol.) no matter if there's a full png set implemented or just svg one (some parts of gnome stills relies on png only? I don't know...)

Anyway, if you feel better only implementing a SVG, that's OK.
(I can add an extra pixmap for desktop, no problem.)I see several options here:

[LIST=1]
[*]Maintain the status quo. The .deb is only 287 KiB, which really isn't much. The unpacked source is 1.2 MiB; the icons only account for 3.6% of the total (see screenshot, based on my current snapshot of trunk). I don't know the installed size, but it probably isn't much smaller. The only things I can think of off the top of my head that DON'T get installed are (un)install.sh and the debian directory--though some files from the debian directory end up installed anyway if you use the deb.
[*]Prune out uncommon icon sizes (after finding a way to determine which sizes are common and which aren't--though I'd guess that 192x192 probably isn't very common). If this can be done satisfactorily, it's probably better than option 1.
[*]Switch to one png and one svg. I don't like this because of the scaling issues, and because Rui Pais discovered that some parts of Gnome prefer a png of the wrong size over an svg--which I consider a bug. Badly-scaled images annoy me; it's one of my pet peeves.
[*]Only ship an SVG, and let downstream add whatever PNGs they want. This would simplify our lives, but complicate things for downstream. And if they're going to repackage anyway, they could just as easily remove icons.
[/LIST]
Of the options, my preference is either 1 or 2. The only one I really don't like is 3. What do other people think (especially LaRoza)?

---

### Post by LaRoza on 2008-09-23
> **mssever said:**
> 
Of the options, my preference is either 1 or 2. The only one I really don't like is 3. What do other people think (especially LaRoza)?


I would say "4", if not for the possibility of OzOS including it. They could repackage it for themselves though.

I like simplicity. It is simplist, to me, to just have an SVG. If SVG's aren't supported, then it should have a .png. If it doesn't support png's, then stop using Windows.

I would be interested in the OzOS people. Just having an .svg (like before) was the best solution for scaling. Would you be willing to customise the installer for OzOS?

---

### Post by mssever on 2008-09-23
> **Rui Pais said:**
> Here the OzOS thread on Ubuntu forum:
[http://ubuntuforums.org/showthread.php?t=623803](http://ubuntuforums.org/showthread.php?t=623803)
(maybe some UF staff can move these two post there)
I didn't realize there was such a thread, though I have to admit I didn't look. Yes, mods can feel free to move the related posts there.

> (I confess that it's the first time i see anyone have problem to register! 
I thought that part was automatically done and care by SMF underneath, and so equal on any forum that use SMF...)Well, often people who have such problems won't go out of their way to let someone know. It's also true that I could have kept going and eventually registered. But it was late, and I was getting annoyed. Usability is something I care about, though I'm probably too critical since some of my projects also have major usability issues, judging from bug reports I've gotten.

> I tried endless combination, specially with groups, on sudoers file... but 'thelivecduser'?? who would remember such thing? where that "user" came from?That's just a metasyntactic variable, since I don't remember the username on the live CD. For example, here's most of the sudoers file I use on my main system. You'll notice that my main login name is scott: ```
Defaults        !lecture,tty_tickets,!fqdn,insults

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
scott ALL=(ALL) NOPASSWD: ALL
```

> 2- Never though on that. The ibar icon set (quicklauncher) it's quite universal, all well known, but it should tell something to new users.I got a big surprise when I clicked the icon that appeared to configure users and groups (because that's what that icon means on my system), and I though X had crashed. I eventually realized that it was the new session icon, which is such an uncommon thing that I didn't expect it to be in the quicklaunch area.

Configuring the icon area does allow tooltips, I discovered, but since the tooltips are centered on the buttons, they sometimes run off-screen.

> 3- That's unfortunately another thing i can find a way to fix. The blue color appears after change the default usplash... although there is such color on neither usplash themes or any reference/image that i saw on conf files...I hate it when stuff is inadequately documented. I did think of something, though: Have you tried getting the source of, say, both Ubuntu's and Kubuntu's usplash config, then diffing the two? That should tell you all the tweaks they made.

> 4- Don't know, a VB issue maybe. I'll discuss this with Aubrey, that do the tests on VM. He never mention it, at least that i remember.Hmm... I can't seem to increase the screen resolution at all. Something's screwy here. And the fact that xorg.conf no longer contains useful video settings means that all my X knowledge is obsolete. displayconfig-gtk is the only way I can find to mess with such settings, and it only offers me the choice between 800x600 and 640x480. I wish I knew what magic Ubuntu and Kubuntu use here.

---

### Post by mssever on 2008-09-23
> **LaRoza said:**
> If SVG's aren't supported, then it should have a .png. If it doesn't support png's, then stop using Windows.When you changed your tagline to "On vacation," I thought that meant that you wouldn't be posting here. :)

I wonder what's so difficult about supporting SVGs. After all, the entire reason for this discussion is that e17 is the only active DE (if you can call e17 that) that I know of that doesn't support SVG. I know that it's quite an old project, but why hasn't that been added?

---

### Post by LaRoza on 2008-09-23
> **mssever said:**
> When you changed your tagline to "On vacation," I thought that meant that you wouldn't be posting here. :)

Sort of. I am on much less (today I have been on the longest, more than a couple minutes) and am not moderating. Mostly taking a break from being online.

> 
I wonder what's so difficult about supporting SVGs. After all, the entire reason for this discussion is that e17 is the only active DE (if you can call e17 that) that I know of that doesn't support SVG. I know that it's quite an old project, but why hasn't that been added?
Probably because people are using .png's. Things will never move forward without a push. (IE6 doesn't support pngs, people didn't use them. People got fed up and starting to using them, IE supports .png's)

---

### Post by Rui Pais on 2008-09-24
> **mssever said:**
> 
That's just a metasyntactic variable, since I don't remember the username on the live CD. For example, here's most of the sudoers file I use on my main system. You'll notice that my main login name is scott: ```
Defaults        !lecture,tty_tickets,!fqdn,insults

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
scott ALL=(ALL) NOPASSWD: ALL
```


:(
Ohh I see. Too bad, i thought that would solve the problem...
Of course the above, set NOPASSWD:ALL for wizard (the username of liveCD) was the first thing i tried. Regrettably it don't work when it run from live. 
I tried too set no passwords for wizard group, for users group, nothing seems to work. It always ask for password!
I really loved to know how to solve this...

---

### Post by Rui Pais on 2008-09-24
> **mssever said:**
> 
I wonder what's so difficult about supporting SVGs. After all, the entire reason for this discussion is that e17 is the only active DE (if you can call e17 that) that I know of that doesn't support SVG. I know that it's quite an old project, but why hasn't that been added?

Uhmm... am i detecting a DE/WM war emerging here? :(

In fact fluxbox, at least the one from ubuntu repos, doesn't support SVG on menus and i imagine other *boxs too.

e17 it's not an old project. It's constantly changing. 
One of it's goals it's precisely that. Provide excellent graphics quality, but on it's own way, by edje files (supporting inclusively animation!) and an excellent support for image rendering (just a curiosity Enlightenment image rendering library, imlib2, it's the default one used by most distros, ubuntu included, a bit of Enlightenment on most Linux boxes).
But for some reason it moved some time ago to freedesktop.org specifications, implementing the horrid *.desktop files, instead conf file with a list of apps even simpler then fluxbox, and generic image support instead of edje files.

The SVG support exists after all. 
It's my fault (i don't use SVG based on bad experiences on past, some bad themes, icons too hard to edit...) i forget to keep an eye on it for support. 
Not that someone ask for it, btw...
I recompiled with SVG support and compared. Size didn't grow and didn't notice any slow down or collateral effect, so i'll add SVG support on next version of e17-svn and OzOS release.

That don't solve the real issues here (e17 was not one):
-Gnome-panel don't seems to use SVG 
-Fluxbox (others?) don't support SVG on menus
-Although with png the line Icon=sysres works, with SVG icons only seems to require Icon=sysres.svg (on both Gnome and e17 menus)
-Eventual cache issues (i didn't noted those, but noted that png changes are immediate while on SVG sometimes seems requires logout)
 
I don't understand why not simply add, besides the sizes already implemented, a standard 48x48 png version on pixmaps. 
It's common practice for almost all applications.

---

### Post by LaRoza on 2008-09-24
> **Rui Pais said:**
> Uhmm... am i detecting a DE/WM war emerging here? :(

Yes. xmonad and wmii are the best. ratpoison is good for when they aren't. These don't deal with messy icons and such, and have no menues (except the perfect dmenu).

> 
I recompiled with SVG support and compared. Size didn't grow and didn't notice any slow down or collateral effect, so i'll add SVG support on next version of e17-svn and OzOS release.

Ah, that is good.

> 
That don't solve the real issues here (e17 was not one):
-Gnome-panel don't seems to use SVG 
-Fluxbox (others?) don't support SVG on menus
-Although with png the line Icon=sysres works, with SVG icons only seems to require Icon=sysres.svg (on both Gnome and e17 menus)
-Eventual cache issues (i didn't noted those, but noted that png changes are immediate while on SVG sometimes seems requires logout)
 
I don't understand why not simply add, besides the sizes already implemented, a standard 48x48 png version on pixmaps. 
It's common practice for almost all applications.

Our focus is on distros that beginners will use, because beginners will be using sysres (any advanced user wouldn't use the GUI's anyway, from my point of view).

So, GNOME, Xfce, KDE and E17 are the targets (Englightenment recently added, because of your interest and I am a fan of the project, although I don't use it much).

There are cache issues, which are compounded by the developers constantly changing and we can't tell how things will look for a fresh install.

We'll figure it out. If a single 48x48 png is all we need, why not? mssever, theory aside, would that cause any problems?

---

### Post by Rui Pais on 2008-09-24
> **LaRoza said:**
> Yes. xmonad and wmii are the best. ratpoison is good for when they aren't. These don't deal with messy icons and such, and have no menues (except the perfect dmenu).


That's not a DE war. It's your preferences list. 
Everyone have the right to have they preferred tools (and different uses requires different tools...)

Useless "this is better, that sucks" fights, i pass. 
I don't have the patience not want to waste my time on such things.



> **LaRoza said:**
> These don't deal with messy icons and such, and have no menues (except the perfect dmenu).
Excuse me, don't know dmenu... but i'm quite convinced that anything that it's not *.desktop or xml it's perfect ;)


> **LaRoza said:**
> 
Our focus is on distros that beginners will use, because beginners will be using sysres (any advanced user wouldn't use the GUI's anyway, from my point of view).

So, GNOME, Xfce, KDE and E17 are the targets (Englightenment recently added, because of your interest and I am a fan of the project, although I don't use it much).

There are cache issues, which are compounded by the developers constantly changing and we can't tell how things will look for a fresh install.

We'll figure it out. If a single 48x48 png is all we need, why not? mssever, theory aside, would that cause any problems?

As i said, e17 it's not in fact the issue then (my bad not compile with librsvg-dev... not need in old times). It will work with only svg.

The issues are some gnome parts related (ignoring then the fluxbox case) and any other stuff on system that may rely on quite standardized path /usr/share/pixmaps/.png icons for define icons/images.

---

### Post by LaRoza on 2008-09-24
> **Rui Pais said:**
> That's not a DE war. It's your preferences list. 
Everyone have the right to have they preferred tools (and different uses requires different tools...)
You are right. It is a WM war.

> 
Useless "this is better, that sucks" fights, i pass. 
I don't have the patience not want to waste my time on such things.

Excuse me, don't know dmenu... but i'm quite convinced that anything that it's not *.desktop or xml it's perfect ;)


I was joking of course. But that is what I use (and the issues don't exist)

> 
The issues are some gnome parts related (ignoring then the fluxbox case) and any other stuff on system that may rely on quite standardized path /usr/share/pixmaps/.png icons for define icons/images.

I am sure mssever will look into that I am sure. I haven't looked into packaging myself.

---

### Post by mssever on 2008-09-29
Sorry I haven't responded for a while. I've been busy with other stuff the last several days--and will be for several more days.> **Rui Pais said:**
> Uhmm... am i detecting a DE/WM war emerging here? :(I hope not. I asked because I didn't know. I used enlightenment years ago, then left it, so I don't know much about its current state.
> The SVG support exists after all.That's good to hear.

> That don't solve the real issues here (e17 was not one):
-Gnome-panel don't seems to use SVGIt does, at least if SVG is the only format available
> -Although with png the line Icon=sysres works, with SVG icons only seems to require Icon=sysres.svg (on both Gnome and e17 menus)Icon=sysres works for me with both PNG and SVG, with the caching caveat already mentioned.
> I don't understand why not simply add, besides the sizes already implemented, a standard 48x48 png version on pixmaps. 
It's common practice for almost all applications.
I suppose I could do that, since it might be necessary in order to work around broken apps (the way I'm currently doing things is correct according to the freedesktop.org spec, which Gnome supposedly supports). I'll give it a try.
> **LaRoza said:**
> We'll figure it out. If a single 48x48 png is all we need, why not? mssever, theory aside, would that cause any problems?
Probably not. My objections have been because it theoretically *should* work the way I set it up. But apparently, theory and practice aren't working out to be the same.

---

### Post by LaRoza on 2008-09-29
> **mssever said:**
> 
Probably not. My objections have been because it theoretically *should* work the way I set it up. But apparently, theory and practice aren't working out to be the same.

We'll figure it out.

I haven't done much myself either, but I will update trunk and change a few things soon. We have our own IRC channel now, #sysres (announced on forum).

---

### Post by bobmct on 2008-10-01
So, having just read through all the pages of this thread, either I missed the mention of a download or there wasn't one (blurry eyes).  Can someone please advise the URL to download and try this tool?  I too just completed a manual restore by hand (OUCH)!

Thanks - Bob

---

### Post by LaRoza on 2008-10-01
> **bobmct said:**
> So, having just read through all the pages of this thread, either I missed the mention of a download or there wasn't one (blurry eyes).  Can someone please advise the URL to download and try this tool?  I too just completed a manual restore by hand (OUCH)!

Thanks - Bob

I'll make sure the first post has the information, but you can get it at [https://launchpad.net/sysres](https://launchpad.net/sysres)

Or on softpedia. [http://linux.softpedia.com/get/System/System-Administration/Sysres-41254.shtml](http://linux.softpedia.com/get/System/System-Administration/Sysres-41254.shtml)

EDIT: The first post already had the information.

---

### Post by bobmct on 2008-10-01
Dang!  Missed that.  
Thank you.:D

---

### Post by snova on 2008-10-06
I didn't know what to do with it, so I put it here. You probably gave instructions somewhere along the 58 pages of this thread, but I haven't seen it.

This is a minor patch against revision 73 (?) of the trunk, which I checked out sometime yesterday.

Changes:

[LIST]
  [*] The Interfaces package was moved to SystemRestore.Interfaces. There was probably a reason why you had it the way it was, but I didn't know it.
  [*] Moved around two internal packages. SystemRestore.Constants.__init__ is now SystemRestore.constants, ditto for SystemRestore.Core.system_restore (now SystemRestore.core). There was probably a reason why you had that the way it was, too. But there are so few files right now it seemed unnecessary.
  [*] All sources were udpated to reflect the above changes.
  [*] Duplicated constants were removed from sysres.
  [*] sysres now checks to see that it can import the rest of itself correctly before doing anything else.
  [*] A small clarification in SystemRestore.constants.
[/LIST]

My editor contributed too, in the form of removing trailing spaces in every file I opened. Fortunately diff has the -b option, or this patch would be substantially larger.

Anyway, of all these changes, maybe the last three are acceptable, given that the first three change things that were probably the way they were for a good reason.

If you don't like patches, I have intentions of uploading the branch to Launchpad sometime later.

Well, here goes... My first contribution to the Linux world. It's three kilobytes... *click*

---

### Post by LaRoza on 2008-10-06
> **snova said:**
> I didn't know what to do with it, so I put it here. You probably gave instructions somewhere along the 58 pages of this thread, but I haven't seen it.

This is a minor patch against revision 73 (?) of the trunk, which I checked out sometime yesterday.

Trunk wasn't changed recently so that is the most up to date trunk

> 
[LIST]
  [*] The Interfaces package was moved to SystemRestore.Interfaces. There was probably a reason why you had it the way it was, but I didn't know it.
  [*] Moved around two internal packages. SystemRestore.Constants.__init__ is now SystemRestore.constants, ditto for SystemRestore.Core.system_restore (now SystemRestore.core). There was probably a reason why you had that the way it was, too. But there are so few files right now it seemed unnecessary.
  [*] All sources were udpated to reflect the above changes.
  [*] Duplicated constants were removed from sysres.
  [*] sysres now checks to see that it can import the rest of itself correctly before doing anything else.
  [*] A small clarification in SystemRestore.constants.
[/LIST]

Uh-oh.

Interfaces was moved out of SystemRestore a while ago, sorry, for a very good reason. The modules should stay focused on their purpose.

The module structures were the result of some planning and we can't change them. They are made to allow certain extensions.

Sorry. Please use our forum: [http://laroza.19.forumer.com/index.php](http://laroza.19.forumer.com/index.php) for discussing the code structures.

To ease contributions, you should use bzr and launchpad, like the rest of us. That way, you can maintain your own branch and request mergers when appropriate.

> 
If you don't like patches, I have intentions of uploading the branch to Launchpad sometime later.

Well, here goes... My first contribution to the Linux world. It's three kilobytes... *click*

We can't accept it at the moment, but future help is welcome. Please check our forum and the launchpad page (blueprints, also).

We also have an irc channel, but we haven't used it yet.

---

### Post by snova on 2008-10-06
> **LaRoza said:**
> Trunk wasn't changed recently so that is the most up to date trunk


Oh, good.

> **LaRoza said:**
> Uh-oh.

Interfaces was moved out of SystemRestore a while ago, sorry, for a very good reason. The modules should stay focused on their purpose.

The module structures were the result of some planning and we can't change them. They are made to allow certain extensions.

I thought so.

> **LaRoza said:**
> Sorry. Please use our forum: [http://laroza.19.forumer.com/index.php](http://laroza.19.forumer.com/index.php) for discussing the code structures.

Oh, there it is. Thank you, now I know where to go.

> **LaRoza said:**
> To ease contributions, you should use bzr and launchpad, like the rest of us. That way, you can maintain your own branch and request mergers when appropriate.

I intend to, but I'm still figuring Launchpad out. I know bzr well enough, though. Is there any particular convention for naming personal branches? All I know so far is that it'll be called lp:~snova/sysres/SOMETHING. For now I'm just going to call it "trunk", since I'm not doing anything specific enough to warrant a better name yet.

> **LaRoza said:**
> We can't accept it at the moment, but future help is welcome. Please check our forum and the launchpad page (blueprints, also).

We also have an irc channel, but we haven't used it yet.

Ah well. Unfortunately I'm having problems accessing the forum right now, so I can't find out why things are the way they are just yet.

As to the IRC channel, I took a look at that earlier and there was a robot and one other person there.

Just a quick question- are there any preferences as to whitespace on blank lines? Because my editor is configured to remove them, and it doesn't seem to want to let me leave them alone. :)

Well, I'll revert most of my changes for now, but I have a few ideas left over.

Thanks!

Edit: Uh oh, it's not working... Didn't I see something earlier today about a temporary Launchpad Code downtime? I thought that wasn't supposed to happen for two and a half hours! Oh wait, timezones... Rats.

---

### Post by mssever on 2008-10-06
> **snova said:**
> I intend to, but I'm still figuring Launchpad out. I know bzr well enough, though. Is there any particular convention for naming personal branches? All I know so far is that it'll be called lp:~snova/sysres/SOMETHING. For now I'm just going to call it "trunk", since I'm not doing anything specific enough to warrant a better name yet.
There's no naming convention. You own your own namespace; feel free to use it as you see fit. I personally call my primary general-purpose 'main', but that's just me.

---

### Post by snova on 2008-10-06
> **mssever said:**
> There's no naming convention. You own your own namespace; feel free to use it as you see fit. I personally call my primary general-purpose 'main', but that's just me.

Well, I knew about the namespace thing, I just wondered if there was a general pattern that everybody else followed. It doesn't look like it.

I just wish I could branch the trunk! I think Launchpad's down right now.

---

### Post by LaRoza on 2008-10-06
> **snova said:**
> 
I intend to, but I'm still figuring Launchpad out. I know bzr well enough, though. Is there any particular convention for naming personal branches? All I know so far is that it'll be called lp:~snova/sysres/SOMETHING. For now I'm just going to call it "trunk", since I'm not doing anything specific enough to warrant a better name yet.

No

> 
Ah well. Unfortunately I'm having problems accessing the forum right now, so I can't find out why things are the way they are just yet.

This one or mine?

> 
As to the IRC channel, I took a look at that earlier and there was a robot and one other person there.

That person used autojoin, we usually hang out in #ubuntu-programming.

> 
Just a quick question- are there any preferences as to whitespace on blank lines? Because my editor is configured to remove them, and it doesn't seem to want to let me leave them alone. :)

As long as the visual code structure is the same and logical, any excess whitespace is an accident or a result of moving things around probably.


> **snova said:**
> Well, I knew about the namespace thing, I just wondered if there was a general pattern that everybody else followed. It doesn't look like it.


No, we call them whatever. Releases have their own names (just the version though).

---

### Post by OutOfReach on 2008-10-07
Continued from: [http://laroza.19.forumer.com/viewtopic.php?p=97](http://laroza.19.forumer.com/viewtopic.php?p=97)

Here's the updated package (note: if you are not a developer please do not download this, read the link above)

---

### Post by LaRoza on 2008-10-29
[http://laroza.19.forumer.com/index.php](http://laroza.19.forumer.com/index.php)

For all people watching this thread...

We are going to get everything together. Right now, core works (however, testers will be very welcome! Test --cli only at the moment, or work on improving GUI interfaces).

We need to get everything working for testing. The interfaces must work. The packaging must work. And the installer must work.

It will be tested on Intrepid Ibex as well, although I don't think there will be any issues.

---

### Post by nvteighen on 2008-10-29
> **LaRoza said:**
> 

We need to get everything working for testing. The interfaces must work. The packaging must work. And the installer must work.


In other words: we must get back to work! :)

I'll look at this at the weekend.

EDIT: Btw, As the Sysres-Interfaces team just didn't work, would someone mind if I request the Launchpad admins to delete it?

---

### Post by LaRoza on 2008-10-29
> **nvteighen said:**
> In other words: we must get back to work! :)

I'll look at this at the weekend.

Yes, sulking time is over for all of us :-)

> 
EDIT: Btw, As the Sysres-Interfaces team just didn't work, would someone mind if I request the Launchpad admins to delete it?
Perhaps that is something you should put in the Interfaces forum? Or launchpad's whiteboard for that team?

---

### Post by BrentNewland on 2008-10-30
I hope you guys can bang out something which might get into Jaunty!

BTW, did you get my PM about suggestions?

---

### Post by LaRoza on 2008-10-30
> **BrentNewland said:**
> I hope you guys can bang out something which might get into Jaunty!

BTW, did you get my PM about suggestions?

Yes, I did. Some of the suggestions were outside the scope of sysres, but your feedback is very welcome.

If you want to get more involved, you can use the forum for the project and get involved on launchpad. Making blueprints on launchpad would make suggestions more tangible and posting on the forum would get more developers involved.

---

### Post by indecisive on 2008-11-15
Hullo, LaRoza!

     I am a proficient Python developer and would like to contribute to your project.  Where should I begin?  Also, what do you intend to do with sysres in the long term?

---

### Post by jimi_hendrix on 2008-11-15
> **indecisive said:**
> Hullo, LaRoza!

     I am a proficient Python developer and would like to contribute to your project.  Where should I begin?  Also, what do you intend to do with sysres in the long term?

laroza got banned from here...you need to contact her a different way

---

### Post by indecisive on 2008-11-15
Really?  Why?
Never mind.

---

### Post by nvteighen on 2008-11-15
I'm involved on the project. Let's see:

0. Install Bazaar (sudo apt-get install bzr).

1. Learn how to use it (and what a Version Control System is, if you never used one). Use this official 5-minute tutorial: [http://doc.bazaar-vcs.org/bzr.dev/en/mini-tutorial/index.html](http://doc.bazaar-vcs.org/bzr.dev/en/mini-tutorial/index.html) It's quite simple to use; yes, I'll describe some commands here below, but it's much better that you know what you're doing instead of just copying commands.

2. Create a Launchpad accout and set it up (you could skip the PGP keys step). [https://launchpad.net](https://launchpad.net)

3. Branch from trunk to get the latest release code:
```

bzr branch lp:sysres

```

4. Code... code... code...

5. Create a revision of your changes:
```

bzr commit -m "Some useful message here, please"

```

6. Upload your changes to the project's codebase:
```

bzr push lp:~(your-username)/sysres/(choose-branch-name)

```

It's quite advisable that you visit your branch's webpage and fill in the details. It'll be located at [https://launchpad.net/~(username)/sysres/(branch-name](https://launchpad.net/~(username)/sysres/(branch-name))

7. If some change occurs to the trunk and you want to include into your branch:
```

bzr merge lp:sysres

```

This also works with any branch, but it's not usual to merge from elsewhere than the trunk.

8. If you want your changes be merged into the trunk. You have to fill a Request for Merge. This is done via the branch's webpage. Anyone can vote on your code, but only LaRoza will be able to accept or reject it... and merge your changes into the release code.

We have a forum for Sysres (and Pyctactoe, my project): [http://laroza.19.forumer.com/](http://laroza.19.forumer.com/)

---

### Post by ryniek on 2010-04-10
> **LaRoza said:**
> sysres has obtained its original goal. It now has all the features and a .deb installer, plus an icon and menu entry.

For the code, see [https://launchpad.net/sysres](https://launchpad.net/sysres)

For the .deb, you can get 1.0 here: [https://launchpad.net/sysres/trunk/1.0](https://launchpad.net/sysres/trunk/1.0)

The future holds uncertainity, and we hope to enhance it without any feature creep.

Good job  :)

---

