---
title: "Attempting to discern a way forward with Lubuntu and &quot;musE&quot;."
date: 2016-09-08
forum: New to Ubuntu
---

### Post by jummeday on 2016-09-08
Hello forum!:
     Hello.  I am an unemployed person with a background in music and education who has attempted to reconcile modular home studio equipment
with music software on Windows computers.  In recent years, I have explored the Linux milleaux, hoping to manage simple internet 
connections in a better way than with Windows.   The "musE" music program is the continuing priority of my  Lubuntu desktop .  However,    the "trusty tar"
I was using stopped its security updates.  I attempted to update my hardware "HWE", as recommended in the following communique; "Starting 
Aug 4, 2016, systems using an interim HWE Stack older than the Xenial HWE Stack will no longer receive software and security updates for the
 kernel and, if you're running it, the graphics stack.  We encourage all HWE Stack users on Ubuntu 14.04 to update to the final Ubuntu 16.04
 Xenial HWE Stack or fully upgrade to the Ubuntu 16.04 LTS release." I verified I was affected.  I then tried to update to 16.04.1
     However, although I had advanced my musE installation concept without resolving fundamental issues, these updates had zero positive impact
on the resolution of these issues with the highest priority of the Lubutu desktop: musE.  I had resolved a "timer" issue, had been able to use
a midi keyboard and interface temporarily, but never was able to use a default soft synth which was supposed to run "out of the box", and 
could not acheive "jack" integration by following basic install instructions as a user, not a compiler.  I decided to go "whole hog", and reformatted 
the Lubuntu desktop to dos, which allowed me to "secure erase"  the Lubuntu drive with a cd disc utility.  ( I was using an entire 80G sata for the
Lubuntu desktop). 
      I then downloaded, burned, and installed the 16.04.1 LTS with the  Kernel: Linux 4.4.0-36-generic (i686) on my Emachines t5212 pentium d computer. 
 I did get dual processing, which was previously impossible, but the Lubuntu dvd disc install would not allow me encryption, or advanced 
formatting options, and although I selected "daily" for security updates on the desktop, the software updater kept reverting to "never".  I went on 
to attempt the priority musE install, but access was completely blocked, due to the fact that a critical file "libmuse_core.so" was said to be missing. 
 I reinstalled musE, adding the recommended "jack d" which came with associated dependencies,but the results were the same:  running "sudo muse" 
brings up a message about the missing file, and program access is unavailable from a terminal, or from the program menu.  I have a musE forum chain started,
but I decided to consult Ubuntu first.  
      I have several thoughts about this:  
1) I downloaded Lubuntu from what I thought was a secure Windows 8 computer.  I transferred the .iso to the t5212 computer as a data file burned
to an incremental data dvd-r.  I then cut/copied the .iso data file to the 2nd of 2 physical drives on the t5212, where I run win732 pro, and burned the .iso.
This was done primarily on the basis of a desire to avoid networking in my particular situation, and the convenience of centralization on the t5212
computer.  I did not run a sha sum or md5 on this .iso Lubuntu download.    Should I try another Lubuntu 16.04.1 download to my current Lubuntu desktop,
run shasum and/or md5, and then reinstall the operating system and try musE again?  
2) Or could it be that musE cannot collaborate with this distribution, and I should go backwards to an earlier distribution?  But if I do this, where security 
updates are unavailable, I would have to abandon my dream of running the internet on the same partition as a music software program!!  This goal is a 
high priority of the entire endeavor and has been completely unacheivable on any of my Windows operating system partitions, in my recent 
circumstances.  On the t5212, the win7pro32 drive runs the internet, but has no music software.  I am running the "Realtek hd mother board audio codec
as Alsa" on Lubuntu, but physically unplugging it on windows, and saving the disablement in the bios when I run the windows drive.
3)  Strictly  speaking, I did not configure musE before I attempted to open musE the first time on this new 16.04.1 Lubuntu installation.  My impression is 
that one would normally "see what it is doing:  ex.: does the new distribution give musE its timing frequency without workaround? does its internal "jack" show up?
 So one would then use a terminal and use install workarounds that musE gives on its web-site.  This desktop also presented a message one time about "turning
on the sound system", but I could not locate any further reference that related.  I did not attempt any playback in the other default music/audio programs after I 
found musE blocked in association with the missing musE file terminal message.  I do intend to pursue technical details with musE directly after I can
 clarify the matters I have addressed in this communication.
4)  On KDE Mini-me, which I also use, I was advised that if I used a "VESA safe mode" on a Live disc, I should have better results with sound.  However, I am not currently
running any music sound on an on-line capable and actively on-line KDE mine-me partition.  I noticed that the first install option of 4 or 5 options on my 16.04.1 Lubuntu
disc that  is presented early in the disc install process is similiar to what KDE Mini-me presents on its install disc.  I am not interested in any elaborate display activity; rather
I would like  intelligible display that does not foul up on-computer sound- in- preparation. Should I use that option I am mentioning if and when I reinstall Lubuntu?  Is there
an issue with the HWE graphics stack?
Sincerely, Evan Mundy

---

### Post by mörgæs on 2016-09-10
Hi, welcome to the fora.
People are not likely to read through such a wall of text. Better to write a question which spans only one or two sentences.

[https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by Bucky Ball on 2016-09-10
> **mörgæs said:**
> Hi, welcome to the fora.
People are not likely to read through such a wall of text. Better to write a question which spans only one or two sentences.

[https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

+1. And one question per thread, please. You could edit this down to one question and if there are others, post new threads. It will avoid confusion and increase your chances of support.

Welcome to the forums. :)

PS: Not sure where you're up to, but on 14.04 LTS

```
sudo apt-get update
sudo apt-get dist-upgrade
```

... should take you to the latest 14.04.*.

---

### Post by jummeday on 2016-09-16
Thank you for your welcome and links.  I have explored "old hardware" and  links I found within. I will have to re-read some of this and digest it fully to relate to the new information coherently.  Here is the reduced single question: ( I realize I should contact musE about this, but, anyway:)How would I go about locating "libmuse_core.so" the missing file from my attempted musE installation on Lubuntu?
Sincerely, Evan

---

### Post by ian-weisser on 2016-09-16
A missing library file is usually trivial to reinstall...but you said you already tried that.

How, exactly, did you install musE the first time?
If you didn't install from the Ubuntu repositories (Software Center), then please link to the instructions you did follow.
Is a broken musE currently installed on your system?

You wrote that you tired reinstalling musE. Please open a terminal and try again. Show us the complete output of that terminal session.
Error messages in context help a lot.

---

### Post by jummeday on 2016-09-25
Hello.  (I am hoping this is not considered a dissertation and is regarded as "congenial".)   I have further examined a musE 
install process.  I must answer the question:  Is the musE program capable of running normally on the particular computer 
where I have installed it?  If it is; then what went wrong?  Is it capable of running properly on Xenial, on this computer?  What 
is required in the way of setup, if it is so capable?  A cursory review of the Ubuntu info links does not show me that I cannot 
use the computer I am using to expect a viable musE. 
     I have not found a workaround that solves the "missing libmuse-core.so"  terminal message-response to a "sudo muse"
program open attempt.  The musE program will not open from the Sound & Video menu.  However, I located the file in question
on the computer in "user(usr?)/lib-linux-gnu/muse/modules/libmuse-core.so".   Terminal help seems to indicate this is a kernel 
module, but it is not listed in the System profiler.  When I attempt to write the musE core module line to the core modules
section, the line will not write;  I find that everything in the core module text file is blocked by the # sign, and no text which is 
visually readable lists any of 5 default modules mentioned by terminal help.  In an earlier post I mentioned that I had installed
"root" on "Trusty Tahr", before I followed the instructions that led to my Xenial install.  This turned out to be a program  called
"root", not necessarily the full access associated with sudo/root/administration privilege.  My impression was that this situation
was in effect a green light for meddling.  I am now using a basic firewall on Xenial.   Could this firewall cause the terminal to be 
unable to read the necessary libmuse-core.so, which exists (as a text file) and is readable visually in the file system?  I would prefer 
to know whether some other process besides the firewall  is involved before I change the new firewall settings or uninstall it to
get results.
    I am also confused by the musE web-site install instructions.  These instructions lump installation and compiling together. 
So the question is: if you are experiencing what I am experiencing, or even normally:  would you enter the lines given in musE 
install instructions  for qt and for jack, in a terminal?  These lines include a reference to "dev" &/or "developer".  I steadfastly
retain my role as Mr. user, however.  But additionally, in Xenial; the Xenial vers. of Qt and Jack used in musE,  listed in the Synaptic
Package Manager; show lists of dependencies that have conflicts. Do I uninstall Qjackctl that I imagined earlier was relevant? Is
it all so tangled up that you could never unravel it anymore, so you should put up a fresh OS??  The libqt4  area has installed a
couple of 'em that are for developers, and relate primarily (it seems) to networking.   As a naive, I wanted to have the internet,
but run musE off-line.  Should I give up the ghost?? Throw in the towel??  I found that my previous "Trusty Tahr", which I configured 
with inconclusive musE access; is supported through 5/17, but is said to have dispensed with security updates.   It is my impression 
that without security updates, a naive such as myself would be at sea.  So backdating my OS to acheive a musE integration also seems 
frought.  As I stage my initiative, I am not really or readily able to assign the process to a higher specification motherboard, or 
upgrade equipment on the motherboard in use.  What should a young man who is 65 do??

P.S.:  I wrote this before reading the last post.  If it is not edifying, I would gladly paste terminal information mentioned! 
Sincerely, Evan Mundy

---

### Post by ian-weisser on 2016-09-25
While your long, long stories are very interesting, 
they do not include enough useful information for us to help you.

You seem to be spinning in circles.
Forums like this work best if you stick to one main question (like "how can I install musE?").
We can help you better if you answer our questions. We cannot see what is on your screen.

---

### Post by verymadpip on 2016-09-26
Hi there.
From what I can tell muse is available in synaptic package manager.
It should have been as simple as installing it with a couple of clicks from there.

It sounds like things are in a wee bit of a mess to me.
I'd be tempted to reinstall Lubuntu 16.04.1 (doesn't take too long), do all the updates, & see if muse will install from synaptic at that point.
If that doesn't work immediately, pop back in here for help before starting to hack around under the hood.

Good luck :-)

---

### Post by QLee on 2016-09-26
I apologise for my wall of text reply but at least I used some spaces.

Emachines t5212

Dual core Pentium D 2.66 MHz

Came with 1GB memory, upgradeable to 2GB

ATI Radeon Xpress 200 shared video memory

Specifications show 200GB HDD but you mentioned an 80GB drive, so maybe you have two drives in your box.

Those are the basic specifications that you should identify when you post for help with that computer.

-------

Your computer is not a very powerful unit and especially if you haven't yet upgraded the memory to 2GB, I suspect that it will always underperform with what you are trying to achieve. It might not process the things you want to do quickly enough to be useful. You can still try to see if it will work for you. There are people here who know more than I do about multimedia processing and you will be able to post specific questions in the multimedia section of the forums after you've got a working install.

Try to avoid getting impatient with wanting your midi to work and take things one step at a time. Answer questions asked by people trying to help, if you don't do that, they may stop trying to help because it is too difficult to help someone without relevant data. You have already attracted the attention of a couple of very knowledgable posters who want to help you.

I'm not sure from your post if you currently have a working Lubuntu. Perhaps you could consider getting 16.04 working as your "question" for this thread.

-------

A suggestion on how to proceed:

1. Reinstall 16.04, which, if I read your "wall of text correctly", you were able to "get dual processing". (I assume that means a system dual booting with Windows).

2. Post back here if you have problems with the 16.04 installation but get it working well first before trying to install anything else. 

3. As poster verymadpip stated, MusE is available in the package repositories and that would be the one you should use (because you haven't answered, we don't know where you got the one you tried to use). Also suggested was using synaptic package manager to install MusE and that would likely be the easiest way for you to install it, (no compiling or anything that a "user" couldn't do).


By the way, Evan, many of the helpers on these forums are older than 65, that does not necessarily have to be an obstacle.

I wish you good luck also.

---

### Post by jummeday on 2016-09-28
Hello. I am posting quickly simply to inform you that I will follow advice for reinstalling 16.04.  I did previously install musE from the synaptic, or at least in a recent uninstall-reinstall.  I'll get back to you all!
Sincerely, EM

---

### Post by jummeday on 2016-10-03
"Keeping you posted":
     I am about to reinstall Xenial/Lubuntu 16.04.1, but brfore I do: I am wondering whether the warnings  a program I used called "rkhunter" are result merely  from a Synaptic update process, or are directly related to my inability to acheive a workable musE install:

```
sudo rkhunter -c --rwo
Warning: The command '/usr/bin/lwp-request' has been replaced by a script: /usr/bin/lwp-request: a /usr/bin/perl -w script, ASCII text executable
Warning: The file properties have changed:
         File: /sbin/ifdown
         Current hash: d97284de3b32c7805340aadf1a62ee31d6414b3538117658c7db000679dea87a
         Stored hash : 050b861180b2a92db1446c57fa58dcc8546c6d4400d137dbf537da2231ad2634
         Current inode: 2097215    Stored inode: 2097212
         Current file modification time: 1473846650 (14-Sep-2016 05:50:50)
         Stored file modification time : 1473266805 (07-Sep-2016 12:46:45)
Warning: The file properties have changed:
         File: /sbin/ifup
         Current hash: d97284de3b32c7805340aadf1a62ee31d6414b3538117658c7db000679dea87a
         Stored hash : 050b861180b2a92db1446c57fa58dcc8546c6d4400d137dbf537da2231ad2634
         Current inode: 2097208    Stored inode: 2097214
         Current file modification time: 1473846651 (14-Sep-2016 05:50:51)
         Stored file modification time : 1453662538 (24-Jan-2016 14:08:58)
Warning: The file properties have changed:
         File: /sbin/init
         Current hash: 4d3e77d848f54f1d9de36b2f126e78e9243bb595d060ea8e44982aca92824449
         Stored hash : 3b59cc54712091c076aa6d169cc257f281e9d4496f2315354c22c97dcc93e158
         Current inode: 2097252    Stored inode: 2097215
         Current file modification time: 1473241297 (07-Sep-2016 05:41:37)
         Stored file modification time : 1473266805 (07-Sep-2016 12:46:45)
Warning: The file properties have changed:
         File: /sbin/runlevel
         Current hash: 26aa8fa7e23d4cabadc89f4ddedd3787e5c4975694a1e2d7671864995f964d8c
         Stored hash : f515cebeb11b0ad9f23bf07245b79e12c2878ae80f87a14e69f2b3c727bf1cdf
         Current inode: 2097248    Stored inode: 2097327
         Current file modification time: 1473241297 (07-Sep-2016 05:41:37)
         Stored file modification time : 1473266806 (07-Sep-2016 12:46:46)
Warning: The file properties have changed:
         File: /bin/systemd
         Current hash: 4d3e77d848f54f1d9de36b2f126e78e9243bb595d060ea8e44982aca92824449
         Stored hash : 3b59cc54712091c076aa6d169cc257f281e9d4496f2315354c22c97dcc93e158
         Current inode: 1838302    Stored inode: 1835166
         Current file modification time: 1473241296 (07-Sep-2016 05:41:36)
         Stored file modification time : 1473266744 (07-Sep-2016 12:45:44)
Warning: The file properties have changed:
         File: /bin/systemctl
         Current hash: 26aa8fa7e23d4cabadc89f4ddedd3787e5c4975694a1e2d7671864995f964d8c
         Stored hash : f515cebeb11b0ad9f23bf07245b79e12c2878ae80f87a14e69f2b3c727bf1cdf
         Current inode: 1838267    Stored inode: 1835165
         Current file modification time: 1473241311 (07-Sep-2016 05:41:51)
         Stored file modification time : 1468340799 (12-Jul-2016 12:26:39)
Warning: The file properties have changed:
         File: /lib/systemd/systemd
         Current hash: 4d3e77d848f54f1d9de36b2f126e78e9243bb595d060ea8e44982aca92824449
         Stored hash : 3b59cc54712091c076aa6d169cc257f281e9d4496f2315354c22c97dcc93e158
         Current inode: 4332756    Stored inode: 4330207
         Current file modification time: 1473241313 (07-Sep-2016 05:41:53)
         Stored file modification time : 1468340801 (12-Jul-2016 12:26:41)
Warning: Suspicious file types found in /dev:
         /dev/shm/pulse-shm-492683719: data
         /dev/shm/pulse-shm-4055489178: data
         /dev/shm/pulse-shm-2087571581: data
         /dev/shm/ecryptfs-jdhgyeibsm-Private: ASCII text
```

---

### Post by Bucky Ball on 2016-10-03
Please use ```
 tags. They have been added to your last post. See green link in my signature at the bottom of this post or edit your last post and see what I've done. Thanks.

I'd say whatever this means:

[code]Warning: The command '/usr/bin/lwp-request' has been replaced by a script: /usr/bin/lwp-request: a /usr/bin/perl -w script, ASCII text executable
```

... would be your issue.

---

### Post by ian-weisser on 2016-10-03
Neither.
All of those 'Warning' messages look like ordinary usage.
rkhunter is well-known for generating large numbers of false positives.

I recommend against using rkhunter until you have a better understanding of how your system works.

---

### Post by jummeday on 2016-10-03
Reply to Bucky and Ian:
   It sounds like "the warning" is not something I have a particular tactic to deal with,  and since its relationship to my overarching goal of a musE install may be indirect at best, I'll probably go ahead and get rid of the entirety with a reinstall.  In my last reinstall,  I formatted to dos, then used a utility called "Secure Erase", and then used my .iso dvd burn to create the current debacle.  So I have now burned a newly downloaded Lubuntu .iso to Dvd, on this Linux desktop instead of retreiving the download from a Win8 computer.  I have reviewed an article about desktop installs, but they don't mention same-OS overwrites. I have run md5 and sha sum 256 on the .iso and the dvd disc. This approach is not an update.  So when I run a similiar install compared to my last Lubuntu install,  I expect to "wipe the slate clean",  but will the overwrite leave some kind of unfortunate residue, despite any formatting, so you _should_ actually "Secure Erase" your Lubuntu drive? 
Sincerely, EM

---

### Post by ian-weisser on 2016-10-03
You don't need to do anything about those warnings. Nothing at all. Rather than reinstall, it is usually much easier to simply uninstall rkhunter...or (better) take the time to learn to use it.

An ordinary (non-secure-erase) install leaves no 'unfortunate residue'.
Secure Erase merely attempts to prevent forensic recovery of your data (from the days before encryption).
Do not 'format to dos'. That's for windows. Use Linux tool to format a Linux partition. The Ubuntu installer will do that for you.

It's perfectly all right to overwrite an Ubuntu install with another Ubuntu install if you really want to.
The hard part for you (the human) is simply to ensure that the installer is overwriting the correct partition. Don't accidentally overwrite your Windows partition.
Save your install media for a week or two until your new system is set up properly, so you need not download another.

---

### Post by yetimon_64 on 2016-10-03
> **ian-weisser said:**
> You don't need to do anything about those warnings. Nothing at all. Rather than reinstall, it is usually much easier to simply uninstall rkhunter...or (better) take the time to learn to use it. ...

+1.

@OP, to get rid of the first error regarding /usr/bin/lwp-request you need to edit the config file for rkhunter as root. "sudo -H gedit /etc/rkhunter.conf" (in terminal without the quotation marks) will let you do so. **Edited:** changed the command to sudo -H as gksu and gksudo are obsolete.

I have included the scriptwhitelist section from my rkhunter.conf file for you to compare with below, you will notice the entry for lwp-request in there as well ...
> ```
#
# Allow the specified commands to be scripts.
#
# This is a space-separated list of filenames. The option may
# be specified more than once. The option may use wildcard
# characters.
#
SCRIPTWHITELIST=/bin/egrep
SCRIPTWHITELIST=/bin/fgrep
SCRIPTWHITELIST=/bin/which
SCRIPTWHITELIST=/usr/bin/groups
SCRIPTWHITELIST=/usr/bin/ldd
SCRIPTWHITELIST=/usr/bin/lwp-request
SCRIPTWHITELIST=/usr/sbin/adduser
SCRIPTWHITELIST=/usr/sbin/prelink
SCRIPTWHITELIST=/usr/bin/unhide.rb
```

On saving the file and rerunning the rkhunter test you won't see that error showing any more.

The last errors regarding /dev/shm/pulse-shm-* and /dev/shm/ecryptfs-jdhgyeibsm-Private: ASCII text errors can be removed from output by editing the next section for "ALLOWDEVFILE". I will post mine for you to compare with ...
> ```
#
# Allow the specified files to be present in the /dev directory,
# and not regarded as suspicious.
#
# This is a space-separated list of pathnames. The option may
# be specified more than once. The option may use wildcard
# characters.
#
#ALLOWDEVFILE="/dev/shm/pulse-shm-*"
#ALLOWDEVFILE="/dev/shm/sem.ADBE_*"
ALLOWDEVFILE="/dev/.udev/rules.d/root.rules*"
```
For /dev/shm/pulse-shm-* just remove the "#" symbol at the start of the first line above (or add the line if not there by default).
Then in your case to this section add ...
```
ALLOWDEVFILE="/dev/shm/ecryptfs-jdhgyeibsm-Private*"
```
... to the ALLOWDEVFILE  section, save the file and exit. On re-running the test those errors will be gone as well.

The main list of errors regarding "Warning: The file properties have changed:" will be removed after issuing the command...
```
sudo rkhunter --propupd
```
File properties will always regularly change on system updates, dependent on which actual files the update alters.
There is a means with using a script to check the sha1sum is correct for the file if you absolutely must, but generally that is a lot of work to constantly check when updates happen so often (I'll post the script below in the last code box, I save it in /home/$USER/bin as "testfile"). These "errors" are all perfectly normal, with practice and understanding rkhunter a bit more you will save the bother of "reinstalling" a system for what is absolutely normal output, that unfortunately can scare the living daylights out of new users of the program.

The script I use if I need to check "Warning: The file properties have changed:" ...
```
#!/bin/bash

PACKPATH=$(zenity --entry --text="Package Path")
PACKAGE=$(dpkg -S ${PACKPATH} | sed 's/\:.*//g')

mkdir $HOME/packtest
cd $HOME/packtest/
aptitude download ${PACKAGE}
dpkg -x ./${PACKAGE}*.deb ${PACKAGE}

TEST1D=$(sha1sum $HOME/packtest/${PACKAGE}/${PACKPATH} | sed 's/\/.*//g')
TEST1P=$(sha1sum ${PACKPATH} | sed 's/\/.*//g')

if [ "${TEST1D}" = "${TEST1P}" ]
then
    zenity --info --text "SHA1 OK:\n\n${TEST1D}\n\n${TEST1P}"
else
    zenity --info --text "SHA1 Failed:\n\n${TEST1D}\n\n${TEST1P}"
fi

rm -r $HOME/packtest
```***Originally sourced from a post on these forums another member posted. Sorry to the member as I can't remember who actually posted this little gem of a script. I altered it to only check the sha1sum, the original script also checks the sha256sum as well but as rkhunter only notes sha1sum I removed the extra checking.***

This script downloads the actual file in question from the repositories and runs sha1sum on the file. It compares the file you input into zenity with the sha1 checksum from the repos for that file and if it comes back as "SHA1 OK" you are safe to update the rkhunter properties with the "sudo rkhunter --propupd" command posted above.

After these 3 main changes, file properties, the script white list entry, and the 2 /dev/shm errors, you should get no more errors running rkhunter (at least until the next system update :)) 

Regards, yeti.

---

### Post by jummeday on 2016-10-04
Wow! Things are getting complex for the naive!  I don't have a printer installed, so would you mind if I copied the text of the last 2 posts to a text file, so I can work with it on an unconnected desktop?  But still, allow me to ask:  which approach (reinstall Lubuntu, or concretize details of the Lubuntu premise) would most quickly lead to a fully-functional musE install, in your opinion?
Sincerely, EM

---

### Post by ian-weisser on 2016-10-04
The fastest, simplest way:

1) Install (or reinstall) *buntu 16.04. The flavor of Ubuntu depends upon your personal taste and the age of your hardware.

2) One terminal command: 'sudo apt install muse'.  Or you can install muse from the Ubuntu Software Center

---

### Post by jummeday on 2016-10-05
(To Yetimon_64)
Thanks so much for all this detailed information.  After reading your footnotes, I would conclude that the method I use for coherence (and safety(?)):  either put up a text file from a copy of your post and then work with that off-line, or print the text and work with that text, also off-line: are acceptable to you. But if you would relate your preference: do you expect or require an on-line process while working with your post on my desktop, or it is a given that you accept a copy to my off-line text file? Upon your reply, I would procede to implement your recommendations.
Sincerely, EM

---

### Post by yetimon_64 on 2016-10-05
> **jummeday said:**
> ... so would you mind if I copied the text of the last 2 posts to a text file, so I can work with it on an unconnected desktop? ...

You're free to copy any info from this site for "offline" use for yourself as far as I'm aware. I do it all the time when working on problems. There is no restriction on the use of this info as far as I know. I believe if you copy to another website you should give credit to this site, but for your own use there would be no problem. Any information posted here is for public consumption. 
[B]
Edit:[/B] I just noted the lubuntu tag on this thread, when you copy the post above change the "gedit" command to whichever editor is standard on lubuntu. cheers, :-)

**Edit **2: just a bit more info from a bit of checking of the forum policy; all user contributions are covered by the [Creative Commons Attribution Share Alike 4.0 International License]("https://creativecommons.org/licenses/by-sa/4.0/") which means in your usage case mentioned you can :"copy and redistribute the material in any medium or format"

Regards, yeti.

---

### Post by jummeday on 2016-10-07
To the two recent posters:

 
(This ended up being a kind of grump's
manifesto):

 
	I found that my Lubuntu terminal could
not follow out the initial stage of the suggestions regarding
&#8220;rkhunter&#8221;: reason unknown.  This was the straw that broke the
camel's back.

 
	To my way of thinking, there was no
solid scheme that I read and interpreted for a desktop OS overwrite
(not an add-on OS).  I was also concerned that I had not fulfilled
criteria for reasonable internet operation.&#8220;Bit-Torrent&#8221; seemed
possible, but I had uninstalled all the Bit-Torrent packages as I
attempted a musE install.  


 
	So I did indeed &#8220;secure erase&#8221; the
physical SATA drive, and ran my recent Lubuntu download .iso from
dvd-r.

 
	I ran the OS installation with F6
&#8220;free software&#8221; checked.  Later during setup, I found the same
exclusion with default encryption I mentioned earlier in my thread. 
I opted to manually partition with

 
something like   &#8220;use for drive
encryption&#8221;.  There are other related aspects of the setup that I
won't mention now.

 
	When I reached the desktop, all or
most all of software I thought was open source and free I 
had previously tried to use was missing
from the package manager. Kafkaesque.  So we (I) would have to
download from the respective web-sites despite advice to the
contrary.

 
	Whether anyone believes it or not;  I
continue to be incapable of paying anything at this point in time for
any of my open-process usages.  I also feel that I cannot afford to
root around extensively on the internet  on this particular Lubuntu
computer, so I am relying primarily on unpaid forum exchanges 
and off-line on computer help: (&#8220;h&#8221;)
to get up to speed.

 
	So the semi-preliminary feasibility of
my initiative is still in question, preceding my goal of working with
a musE program on a &#8220;Linux-alone&#8221; physical drive while
maintaining an internet connection, but never opening a music program
while on-line.   I believe I mentioned that I am also running a
separate physical drive on the Lubuntu computer, which remains
physically unconnected to the computer during use of the Lubuntu
drive.  This is an alternating drive that is not on grub boot.

 
This other drive runs Win732 with an
internet connection, but with only one, text-based, internet
priority. I am hoping that this approach does not create off-putting
variables for a Lubuntu process. And the reverse.

 
	I am still hoping that the competitive
identifications and/or cheer- leading of others do not define my
inability  to correlate and make concrete given information to
complete a Linux music install process on the basis of described
&#8220;defaults&#8221;, and that I am not merely muddle-headed.

 
	I am not prepared to consider, for
example: putting an &#8220;Ubuntu Studio&#8221; on open space on a 64-bit
Windows computer (if at all), or realigning an existing 64-bit
Windows computer to &#8220;all-Linux&#8221; until I further asses my experience
with this 32-bit computer I am using.  I believe this computer can
accept a 64-bit processor, so I may change to one later if such a
processor is actually available, and is found to be an &#8220;almost
absolute&#8221; condition of realistic usage.

 
Sincerely, EM

---

### Post by jummeday on 2016-10-09
Another to the posters!:   
 Since my last post, I reinstalled Lubuntu without any optional variations: encryption and manual partitioning, during setup.   The restrictions on the 
network setup on the new desktop prior to a first package update reminded me of kde mini-me, which I also use.   muse recommends using "blackbox",
not the kde-gnome Window manager as the pre-install or pre-open preferred approach for muse, but it seems as if the template for operation 
is set/relatively unalterable in Lubuntu, without immediate option for intended variation.  I downloaded, installed blackbox and used terminal and modified
"default applications for lx session" without evidence of an active blackbox: it seemed active in name only.    muse recommends examining "cron jobs". 
Cron was found to include a section called "popularity contest" on my new desktop.  According  to grouch analysis, It seemed possible that 
some language in "cron" tried to cleverly obscure rationals for meddling which may be considered conventional by the conceptualizing
parties.   Then (subsequently) there was no known avenue to disable the screensaver (another recommendation).  Maybe my "light-locker" disable does that
(?). (No, it doesn't.)   However, according to my experience, it seems doubtful that when I previously attempted to install muse and the result was  incomplete
functionality,  that a lack of obsevance of these particular recommendations I have described in this post determined the way in which the muse install(s)
were discrepant with the muse-provided descriptions of the muse defaults.
    If I am unsure of whether or not I should update a string related to jack and qt ( found in muse on-line install instructions) and then enter it in the terminal
 to possibly get a good install of muse, can anyone tell me if such a string is essential, or must I go to the muse forum for an answer about this matter? ?  
 How could I know if entering that string might ruin a potentially good install without further remedy or recourse on this desktop? ( I had hoped to establish 
"prereqs" or "fundamentals" in an OS before referring back to the muse forum.) 
Sincerely, EM

---

### Post by ian-weisser on 2016-10-09
On a plain-vanilla *buntu 16.04 install, you should get complete functionality with one simple command: 'sudo apt install muse'.
You should not need to 'download' any recommends or other dependencies.
You should not need to muddle with jack or qt settings.
The entire install to a functioning muse, including settings and dependencies, should be handled by the package manager.
Anything other result, in the Debian/Ubuntu community, is considered a bug. 

Since you apparently fiddled with your system several ways (and are still fiddling with it) before installing muse, I doubt you can file any useful bugs at this point.

---

### Post by Bucky Ball on 2016-10-09
As above. Install Lubuntu, install Synaptic Package Manager, open the latter, search for and install Muse, done.

---

### Post by jummeday on 2016-10-11
To the posters:
Hello. In a new, fresh Lubuntu/Xenial install, prior to any muddling or tweaking, I followed Ian's
earlier instructions. I again attempted a musE install, from the terminal,  on my new, "generic/
graphical-type" desktop, and again; the same restriction which excludes any access
to the muse program was given in the LX terminal of Lubuntu.   You may recall from an earlier
post that this had to do with the missing file: "libmuse-core.so".  I then impetuously 
completely removed musE, and decided I would run Skype "instead", but I found that
a Skype of a type was an option, but was  "dis-aggregated" and incomprehensible 
to the naive.  I have again installed rkhunter, clamav, and firewalld.  I  attempted to
initiate the rkhunter editing sequence, but again the first lines to edit the config do not 
produce the expected acccess to editing the config.   I also decided to update my kde mini-me
installation on another computer, where I was running Skype, but the resulting
process was "unmanagable".  (a euphemism for perceived and counter-productive meddling
going on).  So I secure erased that installation.  Would anybody weigh in on whether 
a Kde-mini-me would more likely produce a viable muse install on the first pass?
If so: why?  (Skype would not have a home,  since, in proximity to muse; I am not confident that
variables it presents would not negatively impact the music/muse priority.)
Would you try to use the latest kde mini-me distribution, or would you still use the older distribution,
and not ever use the package update process?  Keep in mind that these developements
impact my goal of personally reconciling a serious music creation and processing software 
platform and internet access on the  same linux partition (without any ability to "spend-around"
at this time.)
Sincerely, EM

---

### Post by Bucky Ball on 2016-10-11
If you want direct responses, or any responses, I advise you start avoiding 'wall of text' posts and use some paragraphs and punctuation. You'll greatly help your chances of support.

---

### Post by yetimon_64 on 2016-10-11
> **jummeday said:**
> ... but again the first lines to edit the config do not 
produce the expected acccess to editing the config.... 

Please re-read my edit to my post [[COLOR=#0000ff]--here--[/COLOR]]("https://ubuntuforums.org/showthread.php?t=2336467&p=13553253#post13553253") I specified that you should change that command ...
> ...to whichever editor is standard on lubuntu.
I originally made a mistake with that command,  sorry. Please try again with the correct editor for lubuntu. As I noted in my second post (post #20) that I missed noting the lubuntu tag on the thread. Did you change the editor to suit your lubuntu install ? (I don't use lubuntu and as such don't know the correct editor to put into that command for you.)

> If you want direct responses, or any responses, I advise you start avoiding **'wall of text'** posts and use some paragraphs and punctuation.

A huge +1 to that statement from Bucky Ball. That has discouraged my reading of your posts and responding much earlier here. I certainly was very lucky to note the first quote above in your "wall of text".

---

### Post by verymadpip on 2016-10-12
Hi everyone.  I apologise for my ridiculously unclear post earlier.
**I have no interest or desire to use muse at all by the way**.
This is what I was trying to say:

I think the OP's libmuse_core.so error might be a bug of some kind, despite the fiddling :D 
I tested earlier & got the same error. (On a fairly vanilla Xubuntu 16.04 install).

**To OP:**
It looks like someone here found a way of getting muse to work:
[https://ubuntuforums.org/showthread.php?t=2320668](https://ubuntuforums.org/showthread.php?t=2320668)
(Albeit in 15.10)

As an aside, IIRC, the default text editor in Lubuntu is leafpad.  (That seemed to be an issue elsewhere in the thread).

Edited to add:
Found a bug on launchpad for this
[https://bugs.launchpad.net/ubuntu/+source/muse/+bug/1596486](https://bugs.launchpad.net/ubuntu/+source/muse/+bug/1596486)
Appears to have a workaround in it too.

---

### Post by jummeday on 2016-10-12
Thank you so much for every post.  I revised my approach to the internet- still fairly basic-  so I feel a bit more confident I can 
"root around" without losing my Xenial basics.  I examined the links in the last post, but they are not immediatly comprehensible to
me.  AS to the LX terminal:  the basic commands and help are on a different basis than my last Xenial/Lubuntu install, so I'll have to
retreive them or gather them before I go ahead. I do see a relationship between the editing process related to "coremodules", and to rkhunter.
I should note that libmuse-core.so was located in a different location on my computer than any location I have read about(in a cursory fashion) on the 
two links from verymadpip.
Sincerely, EM

---

### Post by verymadpip on 2016-10-13
Hi jummeday.
I think the launch command is given in reply #2 on the launchpad page I linked.
My Xubuntu box is at my Mum's house, so I'll try this out when I go to see her later :)

Edited to add:
Yup.
If I issue
```
export LD_LIBRARY_PATH=:/usr/lib/x86_64-linux-gnu/muse/modules:$LD_LIBRARY_PATH
muse
```
That's 2 separate commands - run them one line at a time.

I get a couple of warnings (jack & then timing frequency), but if I simply okay them Muse actually launches.

---

### Post by jummeday on 2016-10-23
Hello to the posters.  Just a quick note to say that I have not forgotten about 
this thread, but that I am attempting to focus my attention on local
computer basics before I return to the thread in a concentrated manner.
Sincerely, EM

---

### Post by verymadpip on 2016-10-23
Hi jummeday.
Just something to note:
The first command I used is specific to a 64 bit OS.
A 32 bit OS will be slightly different, but I expect the file to be in the same location.

P.S. I'm glad you've not forgotten about this :-)

---

