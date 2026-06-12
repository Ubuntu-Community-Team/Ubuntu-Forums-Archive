---
title: "Deja Dup Restore fails: Error &quot;No backups to restore&quot;"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by RayArdia on 2012-02-18
Using Ubuntu Oneiric, decided because of complicated sound problems to backup my Home Folder and re-install 11.10.
Backed up to an external Phillips HDD, checked that the Full Backup files were there - they are, a Manifest file and some 1102 volumes each of 52.4MB. After re-installing Oneiric I tried to restore the backup but Deja Dup gives this error:-
"Restore Failed
No backups to restore"
Where the blazes do I go from here? Can someone help me please!
Ray

---

### Post by RayArdia on 2012-02-19
Following the previous failure I tried copying backup files from the Phillips HDD to local Tmp folder. 
All seemed OK but when I tried again to restore I got the following error message:-
Traceback (most recent call last): 
  File "/usr/bin/duplicity", line 1359, in <module> 
    with_tempdir(main) 
  File "/usr/bin/duplicity", line 1342, in with_tempdir 
    fn() 
  File "/usr/bin/duplicity", line 1276, in main 
    restore(col_stats) 
  File "/usr/bin/duplicity", line 591, in restore 
    restore_get_patched_rop_iter(col_stats)): 
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 521, in Write_ROPaths 
    for ropath in rop_iter: 
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 493, in integrate_patch_iters 
    for patch_seq in collated: 
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 378, in yield_tuples 
    setrorps( overflow, elems ) 
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 367, in setrorps 
    elems[i] = iter_list[i].next() 
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 112, in difftar2path_iter 
    tarinfo_list = [tar_iter.next()] 
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 328, in next 
    self.set_tarfile() 
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 322, in set_tarfile 
    self.current_fp = self.fileobj_iter.next() 
  File "/usr/bin/duplicity", line 627, in get_fileobj_iter 
    backup_set.volume_name_dict[vol_num], 
KeyError: 1

I foolishly thought that by using Oneiric's default backup program I would be making things easier, not more complex!

As I have no idea where to go from here can anyone help please?

---

### Post by kazztan0325 on 2012-02-19
Hi RayArdia,

I don't understand why would you like to restore your Home Folder to "local Tmp folder".

Why don't you restore your backup files to "original place"?

---

### Post by RayArdia on 2012-02-19
> **kazztan0325 said:**
> Hi RayArdia,

I don't understand why would you like to restore your Home Folder to "local Tmp folder".

Why don't you restore your backup files to "original place"?

Just to clarify, I first tried to restore from my external HDD direct to the original locations, and got the error "No backups to restore" (see my first post)
In order to try another way I copied the backup files to Tmp and then tried to restore (to original locations) from there. At least I got a response which SEEMS a little more helpful - at least Duplicty recognised that there are some backup files!

That having been said, I'm still not really any farther up the road to getting my files back and still need some assistance please.

---

### Post by kazztan0325 on 2012-02-19
> **RayArdia said:**
> Just to clarify, I first tried to restore from my external HDD direct to the original locations, and got the error "No backups to restore" (see my first post)
In order to try another way I copied the backup files to Tmp and then tried to restore (to original locations) from there. At least I got a response which SEEMS a little more helpful - at least Duplicty recognised that there are some backup files!

That having been said, I'm still not really any farther up the road to getting my files back and still need some assistance please.

Sorry, I misunderstood your situation.

By the way, I found a web page in Launchpad:
**Déjà Dup Bugs Bug #601243 "No backups to restore" message when trying to restore**
[https://bugs.launchpad.net/deja-dup/+bug/601243]("https://bugs.launchpad.net/deja-dup/+bug/601243")

I'm sorry but I'm not sure the thread of comments on the bug report would be helpful for you...

---

### Post by RayArdia on 2012-02-20
> **kazztan0325 said:**
> Sorry, I misunderstood your situation.

By the way, I found a web page in Launchpad:
**Déjà Dup Bugs Bug #601243 "No backups to restore" message when trying to restore**
[https://bugs.launchpad.net/deja-dup/+bug/601243]("https://bugs.launchpad.net/deja-dup/+bug/601243")

I'm sorry but I'm not sure the thread of comments on the bug report would be helpful for you...

Thanks a lot, very interesting stuff ...... but as I don't really understand it doesn't help me a lot! However it's nice to know that I'm not alone in getting the "No backups.." message.
The problem outlined seems in many ways more complicated than mine for I haven't changed storage mediums or reformatted or anything like that.

---

### Post by RayArdia on 2012-02-23
This morning, just out of curiosity I tried to restore my files again (from the copy of the backup that I made in /Tmp.
You're ahead of me aren't you? I WORKED PERFECTLY!
All files now restored to their original places - I haven't a clue what went right this time when it failed on so many other tries. NOTHING was changed in any way.

---

