---
title: "backup issues"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by vinceUUUU on 2008-05-14
Hello

I wonder if anybody could help me out with the Flyback tool in Linux?

it is a backup tool...(snapshot)

Flyback mentions that is often used with external hard drives...but it's perfectly feasible to use your same system hard drive

there is a list of included and excluded directory's for flyback to back up.....on my machine...

i want to back up my entire Linux computer..so i give the include list my root directory symbol........../..........

i have created a directory called Fback in the root...to store the backup file.....


....when Flyback does the backup it forgets to exclude it's own backup file from things....so it gets caught in an endless loop of backing up...

basically i can't get flyback to exclude the backup directly from it's own backup process...(because they both exist in root..../...)


the backup directory resides within root and root has already been put in the include list of flyback......(flyback sees the include list before it sees the exclude list)

the help files try to explain how includes and excludes are done but it does not work for me

any ideas

thanks

Vince.

---

### Post by Het Irv on 2008-05-14
I haven't used Flyback before, so I really can't help you If you want to use that program.  But.... Check the link in my sig (QuickStart).  This is a full featured backup/restore Swiss Army Knife of a program.  The link is to our own forums, because there was a fuss about the fact that the program is closed source.  I use the same name and avatar on those fourms so if you have any questions, feel free to ask.  

Sorry for not really answering your posted question, but QuickStart really is that good.

EDIT: I looked though the Google Code page for Flyback and have one question:  Do the check boxes indicate which files are being backed-up?

---

### Post by vinceUUUU on 2008-05-14
Hello

yes....the checkboxes indicated what is being backed up

the thing about Flyback is that it is a "snapshot" style system

my understanding is that taking snapshots is very fast...because Flyback only sees files that have changed...

So, if you are backing up an entire Linux system....it takes a while for the first snapshot...(20 minutes)....but after this, any subsequent snapshots should be much quiker...because very little may have changed on your system...

i am not sure if my understanding is correct...but other such tools seam to operate very quikly...

windowsXP had a snapshot idea called "system restore"....this operated almost instantly....

also virtualbox has a snapshot feature that can snapshot an entire Linux system instantly..

as the name suggests....snapshot....means it's quik...

quik start is great but it takes 20 minutes to back up my entire system each time...not 20 seconds...

i am not sure if my understanding is correct....but when thinking of other snapshot ideas out there...they all seam to operate very quikly...

the problem i have with Flyback is that it can't ignore it's own backup file.....so it's starts a never ending loop of backing up itself...once it meets that file

it shoul dbe simple to exclude that directory...but my efforts are not working...

it will be a simple command to avoid this problem....but i don't know the command right now...

what i have noticed is that Flyback first starts up with a list of excludes already there....some of those directory's are common to all linux distros.....so if i simply point my backup file to go into one of those directory's on my system.....it should all work...

ofcourse there are a few directory's in linux that are wastefull to backup....so tools exclude them in lists....

anyhow thanks

Vince.

---

### Post by Het Irv on 2008-05-14
Okay, yeah QuickStart might be a little heavy for what you want to do then.  Do you have an external source, puting the backup there should work.  Or putting it into one of the aforementioned autoexculde folder.  You might want to let the Devloper of the program know about the problems you are having so he can fix it in later versions.

---

### Post by vinceUUUU on 2008-05-14
Hello

yes , there is a small USB pen drive here....1 gigabyte

the distro that i use is called Antix...it is a debian distro and it is small...(160 megs on CD)

probably my Antix does not take more than a 1 giga byte...

so in theory, i can use Flyback by sending the backup file to the USB pen drive.....it should work correctly...

however, it would be good to know how to do it all on one hard disc drive...maybe

your right...i have informed the developer about my issue......maybe he has a simple answer to my issue... or maybe he will further improve the Flyback tool.

to be honest, it is most likely to be down to my lack of experience with Linux....typing directory's and arguments at command lines....can get the better of me...

however i really do feal that it is worth persuing this Flyback thing...

the reason i say this is because a few years ago i got frustrated with windows...it often got bugs off the internet, malware, bad software installs....the system would quikly get buggy...and this was annoying...

eventually i found a tool for windows called Shadow User. This tool was able to creat a DUMMY hard drive inside RAM.....the windows system would then sit inside a DUMMY session called a shadow session...

Any windows activity during a shadow session is never commited to hard drive...it just happens in the dummy hard drive....so the user is effetively using a virtual windows...

should a user wish to DUMP a windows session..they just rebooted and everything was lost...and the system remained unchanged..

should a user wish to committ a file to hard drive.......they simply right clicked it and committed it.....should a user wish to save the entire windows shadow session for ever....they clicked save session and rebooted the PC...

this tool was a revelation for me in using windows computers....and the following 3 years have resulted in ZERO problems with Msoft windows computers and software...

you see how valuable a good tool can be....

everybody i ask about similar Linux ideas or alternatives does NOT have the answer....there are no similar shadow tools out there for linux...or if there is....nobody knows about them here...

there is also no similar system to the winXP "system restore" feature or rolling back.... 

Linux answers to the above tend to be longer winded...and not so simple...

i feel that a shadow tool for Linux would be indispensible for new Linux users...and would solve fathoms of new user nerves and concerns about using linux....

maybe the shadow tool can be ported to Linux?....after all, both systems use a simple hard drive and partition...so in theory it would work the same....

there is another shadow tool that is identical and free...called Returnill.

i want a foolproof system for Linux...like shadow....but it has not been forthcoming....

the closest totally fool proof way is to use a virtualbox and make a clone of your existing system and use snapshots in there...

but my machine is not fast enough for virtualbox's to run well...and it's not the ideal solution anyhow...

the reason i now use the Antix distro is because it is so small and quik to install that once my system has got into a right mess..i just flaten the whole PC and put Antix back on again....

i never had to flatten a windows PC in the last 3 years...this is how good shadow user is..

anyhow....hopefully Flyback is closer now....

thanks anyhow

Vince.

---

