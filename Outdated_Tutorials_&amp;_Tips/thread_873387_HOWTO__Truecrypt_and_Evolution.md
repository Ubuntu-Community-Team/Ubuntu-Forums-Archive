---
title: "HOWTO:  Truecrypt and Evolution"
date: 2008-07-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Capa Pinbacker on 2008-07-28
For anyone who likes to store their email in encrypted containers (for security and portability reasons), here is way to link evolution to files stored on an encrypted drive.

First, install Truecrypt (see [http://ubuntuforums.org/showpost.php?p=5478994&postcount=55](http://ubuntuforums.org/showpost.php?p=5478994&postcount=55)).  Make sure to format the container using a Linux file system (e.g., ext2 or ext3) since evolution's lock files won't work otherwise.

Then, create the link to the encrypted container as follows:

1. For a new Ubuntu installation, start Evolution normally and go through the configuration questions.  Then close Evolution
2. Mount the encrypted drive (in my case it is mounted at /media/truecrypt1) and create a directory in which to store the evolution-data (in my case it is at /media/truecrypt1/Datafile/evolution):
3. Navigate to the /home/user directory and type the following:
   sudo rm -f -r .evolution (you will want to copy the .evolution directory before removing it if you already have valuable files there)
   ln -s /media/truecrypt1/Datafile/evolution .evolution
4. Verify that the link brings you to the mounted drive location.
5. Start Evolution and, voila, it should be storing data into the encrypted drive.

Not only is your evolution data encrypted, but it is in a container you can easily backup, etc.

---

### Post by Alex James on 2009-09-20
Thanks for that Capa.

In Hardy and in Jaunty, there may be an issue with dismounting the Evolution container: On AAO, it will dismount correctly if Evolution hasn't yet been started. It will also dismount correctly even if Evolution has been started *as long as you haven't exited TrueCrypt*. Once you exit TrueCrypt with Evolution running from a container, you cannot unmount the container. A forced unmount will not allow further remounts of the Evolution container until Ubuntu is rebooted, in my experience.

---

