---
title: "A Fix for DVDRip in Ubuntu 5.10"
date: 2005-11-13
forum: Outdated Tutorials &amp; Tips
---

### Post by eris on 2005-11-13
If you're like me, you've wanted to get 'dvdrip' and 'transcode' working on Breezy (5.10) but you couldn't get any further than ripping the DVD.  As soon as dvdrip tries to take a preview snapshot for cropping it freezes up.

This happened to me before and I was never able to resolve the issue.  Well, seeing as I'm a systems engineer I finally decided that it was dvdrip or me.  I spent most of yesteday nailing down the issues.   This was particularly hard because there are actually two issues involved and they both involve transcode locking up when trying extract a preview snapshot.

The basic problems appears to be:

1. Since 5.10 uses a relatively new version of glib (I'm running 2.8.x I believe) this confuses transcodes command line parser (actually tccats I believe).  For some reason transcode needs the directory path passed to it with a trailing slash.  If dvdrip does not pass a trailing slash in the VOB directory path, transcode/tccat locks up and can't even begin to look for the snapshot frame.  You will see this problem when you select 'debug' from the dvdrip menu and examine the shell command that dvdrip runs to snapshot the preview.  You will see that it doesn't include a trailing slash.  (Confirm this by running that command in a command line by itself.  Add a "-q 2" or "-q 8" debug flag to transcodes command line to get additional debug output.  Transcode will complain about it finding glibc and something about "corruption" and then hang.  This assumes you have a dvd already ripped.)

2. Transcode works by spawning off various plugins modules for input, output and processing.  These are apparently handled by a threading mechanism that is a bit sensitive to kernel versions.  I'm not sure of all the particulars, but I've seen it launch it's plugins and then go to sleep waiting forever for the plugins to handshake properly.  Don't ask me because I didn't have time to go through the source code.  I  verified this both by turning on '-q 8' debug on the command line and by running an strace and watching transcode sit forever in a continous nanosleep wait loop for something to happen.

FIXES:


Before you get all excited if this will work for you, let me state that it worked for me, but your mileage may vary etc.  Here is my system setup:

Ubuntu 5.10
512MB RAM
Athlon 1GHz CPU
20G Main Drive
400G SATA Drive
NVidia FX5200 Video/128MB RAM
VIA ICE Sound
Kernel Version: 2.6.12-9 K7

1. To fix the VOB path problem, simply go into the correct module in DVDRIP and append a "/" to the formatted string concatenation for the vob path.  Hang on and I'l hunt it down for you:

in /usr/share/perl5/Video/DVDRip/Title.pm

around line 472 you should see a line that looks like this:

$vob_dir = sprintf("%s/%03d", $self->project->vob_dir, $self->nr);

Edit this line (you will need to be root, of course).  Save a backup copy of this file in case you flub it.  This sprintf is where dvdrip formats the vob subdirectory path that it creates for the rip output.  Simply insert a '/' right after "03d", like this:

$vob_dir = sprintf("%s/%03d/", $self->project->vob_dir, $self->nr);

Only modify this line and then save the file.  The path issue shold be fixed.

2.  The second thing that needs to be done is to make transcodes thread synchronization work with your kernel and libraries.  The patch for this is to define an environment variable thusly: LD_ASSUME_KERNEL=2.2.5.  You only want this to be active for transcode, so you could patch the transcode call inside of dvdrip (the cleaner way), or you could do like I did and create a wrapper around transcode by:

   a. Become root
   b. Make sure transcode is *not* running and rename the transcode binary to transcode.bin, thusly:  mv /usr/bin/transcode /usr/bin/transcode.bin
   c. Create a small bash shell wrapper using your favorite editor.  This will run instead of the normal transcode binary.  The contents follow:

-----cut here------
#!/bin/bash
env LD_ASSUME_KERNEL=2.2.5 /usr/bin/transcode.bin "$@"
-----cut here------

(Obviously don't include the ---cut here--- comments ;-)

Save this file as /usr/bin/transcode.

Make this script executable by running the following command as root:

# chmod +x /usr/bin/transcode

Those two changes should make DVDRip work mostly correctly under Ubuntu Breezy.  Don't assume these fixes are clean or comprehensive, but seeing that noone else seems to be fixing it, consider this hack an early patch.

Also remember that if you upgrade or remove transcode that you will need to move your new script to 'transcode.wrapper', move the transcode.bin back to transcode and then apt-get remove it.

If you have any further info, please feel free to post.

Good luck,

(eris)

---

### Post by angrylittleman on 2005-11-13
Sweet, I can't wait to try this!!!!  Thanks!!

alm

---

### Post by eris on 2005-11-16
No problem.  My AI professor used to classify problems by the number of pipes of whatever he was smoking that week.  On a scale of 1-5 this was about a 3.  So smoke 'em if 'ya got 'em.

Also, most people will understand what I meant when upgrading transcode that you need to move the files back to where they belong before and after the upgrade process.  I only specified the *before* portion.  

Also, when I get the energy I'm going to copy this thread to the transcode guys and see if they can nail down the problem with it.  I also had this problem in a vanilla debian release I used to use for MythTV.  I don't know if it's a Debian packager who is forgetting something or if it has more to do with GCC 4.0 etc.

Good luck to you all.  I'd appreciate hearing about your experiences with this patch.

---

### Post by angrylittleman on 2005-11-17
Thanks, this how to worked for me!!!

---

### Post by Mad Marty on 2006-02-07
You sir, are a legend!  My experience was that it wasn't locking up, but was giving an error saying it couldn't extract that frame, and only then for some films.  Other DVDs went through perfectly.

I really appreciate the time you put in to solve this problem - thank you very much!

Kudos and good karma and all that.

Cheers again!

Martin

---

### Post by i3dmaster on 2006-02-07
Great tips!

---

### Post by m4dd0c on 2006-02-27
This fix worked excellent. Great job!

---

