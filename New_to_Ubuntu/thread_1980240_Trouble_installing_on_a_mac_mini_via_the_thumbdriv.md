---
title: "Trouble installing on a mac mini via the thumbdrive"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by mjulius17744 on 2012-05-14
I have a mac mini [intel] with a non-working cd/dvd and so I have been attempting to install ubuntu using the instructions for installing via USB stick:

[https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick)

Everything goes fine [i.e. I follow the instructions to the letter] until I finish when the thumbdrive becomes unreadable to the computer.  I have done this multiple times with the same outcome.  However, there are a few points that aren't clear and so I am wondering if I am making mistakes somewhere in the process.

1. I am using a camera SIM card in a reader attached to the USB [I don't think that this would be a problem but I'll mention it anyhow].

2. There is no mention of how to partition & erase the drive before installing.  I have tried to partition as both a GUID boot and standard Apple Partition Map.  Which should I use?

3. The instruction state that first you must convert the .iso to an .img. and the instructions say that apple tends to append a .dmg to the end [which it did].  Should I strip off the .dmg from the end of the file first?

I have tried these in combination with each other [.dmg with GUID partition table, without partition table, .img with and without, etc] but frankly I am at a place where I need more guidance.

After the process is over I eject [via command line] the drive. Shut the computer down, plug it back in and when I start it back up with the option key I only see the HD on the options.  As soon as it is in OSX it tells me that it can't read the thumbdrive.  I can only access it through the disk utility.

What am I doing wrong?

---

