---
title: "Problems with rsync on Netgear Ultra4 NAS"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by smgendler on 2012-11-11
I thought I'd post this because this has been a problem for me for months: failed backup to a NAS.  I've been using ubuntu for a couple of years, but I consider myself a beginner.  

I have thousands of audio files I've ripped (rubyripper is an excellent secure ripper, but, as you'll see it hosed me up with the automatic filename naming from freedb).  I have used a bunch of different backup utilities, deja dup, unison, others, to try to back up my files.  Invariably, the files don't back up completely, though they do back up OK when I was using deja dup and backing my files to a second internal drive on my PVR. My latest fiasco: I started with a different approach yet again a couple weeks ago trying to get rsync to work on my Netgear Ultra4.  What I wasn't getting is that to get it to work, you have to put an rsync server on the source to be backed up.  [This article]("http://nwlinux.com/how-to-configure-and-ubuntu-rsync-server/") was helpful doing that, as was  [this article on the Netgear forum]("http://www.readynas.com/forum/viewtopic.php?f=31&t=64577") that said that I had to spend 99 cents for a plugin to get rsync to work over ssh.  Anyway, the backup was still failing.  Permission denied errors.  Of course I had to pull the manuals for chown, chmod and other utilities that I'm lousy at.  Still no fix.

Then I noticed, and I don't know why, that the files that weren't copying to the NAS had a ":" in the middle of the filename.  The colons were there because they were in the names of the tracks in freedb, which rubyripper uses to suggest names for the tracks.  My head still hurts from the slap I gave my forehead. Did a search and replace for the ":" character in my filenames and that appears to have worked.  I used a utility called krename, which is a really cool batch rename tool.  The backup is being initiated from the Ultra4, all is right with the world.

So, lesson learned: don't slap your head so hard.

---

### Post by papibe on 2012-11-11
Hi smgendler.

The ':' is a forbidden character on NTFS only under Windows. The implementation under Linux allows it. 

My guess is Netgear's implementation is not the standard used by most Linux distributions.

Just a thought.
Regards

---

