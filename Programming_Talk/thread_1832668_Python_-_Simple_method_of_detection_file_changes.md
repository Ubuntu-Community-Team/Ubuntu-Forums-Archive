---
title: "Python - Simple method of detection file changes"
date: 2011-08-25
forum: Programming Talk
---

### Post by Tony Flury on 2011-08-25
I am looking for recommendations for the simplest way of getting a python application to detect or be notified of changes to (i.e. creating, deletion, modifying or renaming of a file) within a file system (or a sub set of directories).

I would rather not do full recursive search looking for new files and changes and running that every few minutes, i would prefer an (more or less) real time notification of changes.

Is there anything like that available in a library that i can build an application on ?

---

### Post by dazman19 on 2011-08-25
I don't know if this is what you want. But I would track the time you edited the file and possibly the size and save the files last edited time and store it in a database or another file or something.

Then every so often check that they match up. 
If they don't then, compare them line by line, until you find a change. 

I know this is not really what you asked for.. because that was probably the solution you originally had in mind.
And if you have lots of tiny files in many sub-directorys it could be a lot of processing overhead, waste of hard disk seek time and could take quite a while. 

I actually have created a database and stored all my files in it as blobs. their file size, name, location, last modified, user who modified etc. and I log the INSERT, UPDATE & DELETES to a history table which is managed by triggers. So this would serve me fine for that purpose. However this will not work with the traditional filesystem.

---

### Post by kurum! on 2011-08-25
> **Tony Flury said:**
> I am looking for recommendations for the simplest way of getting a python application to detect or be notified of changes to (i.e. creating, deletion, modifying or renaming of a file) within a file system (or a sub set of directories).

I would rather not do full recursive search looking for new files and changes and running that every few minutes, i would prefer an (more or less) real time notification of changes.

Is there anything like that available in a library that i can build an application on ?
Search google for AIDE (intrusion detection). Or pyInotify

---

### Post by Tony Flury on 2011-08-25
Thanks Kurum - excellent.

I have in mind a on-fly backup program, which will keep timed snapshots of individual files, and eventually will have a GUI that allows you to browse through the various time stamped versions of a file, and restore them - i.e. think Nautilus but with a time dimension derived from the backup.

After the first (admittedly time consuming back up build), a service will sit and monitor the file system, and take a snapshot of the files as they are changed, and queue them for storage. 
If I shutdown before all the queued files are stored - the queue will be retained - and storage will be re-attempted next time.

My intention is to be able to backup my data to a NAS device but without having to leave my laptop on as it churns away across the folders building massive zip files (which by the time they get to my NAS device they are generally unreadable).

Eventually I may offer it as an application suite for people to play with, enhance etc.

---

### Post by kunal00731 on 2011-08-25
Hi,
I know this post was created a long time ago, but still it has very recently helped me to get out of a similar deadlock. Hence thank you, guys.

---

### Post by Smart Viking on 2011-08-25
> **kunal00731 said:**
> Hi,
I know this post was created a long time ago, but still it has very recently helped me to get out of a similar deadlock. Hence thank you, guys.
AFAIK, it was created one hour ago. :)

---

### Post by kunal00731 on 2011-08-29
Sorry, My bad. Anyway it was really good.

---

### Post by kunal00731 on 2011-08-29
Sorry, My bad. Anyway it was really good.:P

---

