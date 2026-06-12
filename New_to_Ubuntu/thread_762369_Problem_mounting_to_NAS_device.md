---
title: "Problem mounting to NAS device"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by sp00ner on 2008-04-22
I have mounted my NAS device and can read files OK, and can even create new folders and delete existing folders on the NAS. So you would figure I have read and write access, but when I try to copy and paste a file from my local disk to the NAS I get an error that says not enough space on the disk. This is in the file explorer in the GNOME desktop for 7.10. I know there is plenty of space left on the NAS.:confused:

Anyone have any thoughts? I'd appreciate them.

---

### Post by brettg on 2008-04-22
Check the amount of space available on the root partition (and /home if different). It might be a problem with your temp folder.

---

### Post by sp00ner on 2008-04-24
Wasnt sure how to do this. A search on these forums lead me to this command. Here is the output

df -h

user@PLUTO:~$ df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              53G  2.8G   48G   6% /
varrun                506M  220K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   84K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm

If I read it correctly, there is 48GB available on the root partition????

---

### Post by sp00ner on 2008-04-25
Bump....still looking for a solution.

---

### Post by sp00ner on 2008-04-26
Another bump...

Anybody....Anybody....

Bueller....Bueller.......

---

### Post by gug@fnal.gov on 2008-04-26
Hi,
   Did you check at the commandline whether you can copy a file to the area? I could not tell from you post whether you were attempting to copy the file to the directory you created on the NAS or elsewhere. It is generally useful to go back to a simpler case first and verify that things work there. It would be helpful to know the following information:
* username and groups
* directory permissions on area you are trying to write to and parent directory
* if you can copy a file at the command line or not

I have a NAS and am running 7.10, and I was able to create a directory at the command line and then use the GUI windows to drag and drop a file to that new area on the NAS. I did not try create the directory graphically, and while this does not sound like a permissions problem it still may be worth you sanity to recheck them.

---

### Post by sp00ner on 2008-04-26
Hi gug, thanks for the reply. You may be on to something. I used all termanal commands to create a folder on the NAS called test. I then copied a small txt file from my home directory to the test folder on the NAS. It worked. Then I used the GUI file explorer to delete the text file from test on the NAS and attempted to copy the same text file from my home directory to the test folder on the NAS. Error...not enough space. BTW, I was using sudo when I was using the command line.

So here is what I am trying to do. I am ripping my CD collection to mp3's. I have a folder in my home directory called Music. The mount point to my NAS is also in my home directory called nas. So lets say I have a folder in /home/Music called Queensryche and I need to copy it to nas/Music. I try navigating to /home/Music and I try the command sudo cp Queensryche /home/user/nas/Music. i get error cp: omitting directory `Queensryche/'

I must be using the cp command incorectly?

---

### Post by sp00ner on 2008-04-27
Last bump for the night.

---

