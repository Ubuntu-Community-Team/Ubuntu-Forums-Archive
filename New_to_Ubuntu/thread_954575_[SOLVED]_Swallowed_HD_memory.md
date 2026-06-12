---
title: "[SOLVED] Swallowed HD memory"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by TheSixthPandava on 2008-10-21
I have problem with my HD.

My root partition is 72 GB and all data combined on it takes no more than 40 GB. But, it shows me that I have only 7.8 GB left. I am a begginer, installed Ubuntu only two months ago, and I don't know what to do about this problem.

Filesystems on my computer are:
[PHP]Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             72G   61G  7,8G  89% /
varrun                252M   88K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   68K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   34M  218M  14% /lib/modules/2.6.22-15-generic/volatile
/dev/hdc              698M  698M     0 100% /media/cdrom0
[/PHP]

Does anybody have any idea how can I resolve this problem?

---

### Post by fooman on 2008-10-21
if you run the "disk usage analyzer"...it will give you a complete breakdown of where your data is stored on your hard drive/partition.

look in applications > accessories > disk usage analyzer

run a scan of the suspect partition and see where the build up is.

---

### Post by taqkavar on 2008-10-21
Right there it is showing that 61GB is being used in that table. Do what the above user suggested.

---

### Post by lswb on 2008-10-21
Check the trash?

---

### Post by TheSixthPandava on 2008-10-21
THANK YOU VERY MUCH ON THIS!
It seems that I found the folder that gives me this problem.
in /home/marko/.cache/tracker folder I have exactly the same 27,3 GB of memory that is "missing". 

The files are:
> /home/marko/.cache/tracker/email-contents.db
/home/marko/.cache/tracker/email-index.db
/home/marko/.cache/tracker/email-meta.db
/home/marko/.cache/tracker/file-contents.db
/home/marko/.cache/tracker/file-contents.db-journal
/home/marko/.cache/tracker/file-index.db
/home/marko/.cache/tracker/file-index.tmp.1
/home/marko/.cache/tracker/file-index.tmp.2
/home/marko/.cache/tracker/file-index.tmp.3
/home/marko/.cache/tracker/file-index.tmp.4
/home/marko/.cache/tracker/file-index.tmp.5
/home/marko/.cache/tracker/file-index.tmp.6
/home/marko/.cache/tracker/file-index.tmp.7
/home/marko/.cache/tracker/file-meta.db
/home/marko/.cache/tracker/file-meta.db-journal
/home/marko/.cache/tracker/file-update-index.db

Among those files, most biggest file is file-contents.db. What are these files? Are they neccesery for Ubuntu?

---

### Post by TheSixthPandava on 2008-10-21
About the trash. I already emptied all of it, and there was some 7 GB of trash that wasn't shown in trash desktop ikon, but it didn't answered my problem. This Disk Usage Analyzer gave me an answer, but I am yet to see are these files are necessary.

---

### Post by Ctrl+Alt+Del on 2008-10-21
Tracker is search engine that is used to provide full text search, if you don't use it you can safely delete the directory and remove tracker indexing from sessions.

I myself keep it disabled on all my machines since i don't use it and i have run into quite a few bugs that resulted in wasted space and a lot of i/o.

---

### Post by hyper_ch on 2008-10-21
tracker is a file indexing program. With you the contents of file can be indexed and searched quickly. Sort of like Google Desktop...

However it using 20GB is big... it shouldn't be that much.

---

### Post by TheSixthPandava on 2008-10-21
So I can delete this folder without worry?
Ctrl+Alt+Del, how can I disable this Tracker?

---

### Post by hyper_ch on 2008-10-21
it should be started as service... but simplest way would be to remove it:
```

sudo apt-get purge tracker

```

---

### Post by TheSixthPandava on 2008-10-21
It seems that I made a mistake just hour ago, when trying to solve this problem. On another thread, someone suggested that I should empty /var/cache/apt/archives/ from deb files. I emptied it from everything, but in it was a file called partial and now it gives me an E: when I am trying to purge tracker.

---

### Post by tarps87 on 2008-10-21
Try ```
sudo aptitude -f install 
``` or ```
sudo aptitude install -f 
``` (can't remember which one)
you can also try ```
sudo apt-get -f install
``` but aptitude tends to work better for me

---

### Post by TheSixthPandava on 2008-10-21
It seems I really made big mistake when emptying this folder /var/cache/apt/archives/. I deleted partial without knowing what it is for, and don't know what to do know.

I led your suggestion and here what is says:
> Writing extended state information... Error!
E: Archive directory /var/cache/apt/archives/partial is missing.


---

### Post by hyper_ch on 2008-10-21
create that folder

---

### Post by tarps87 on 2008-10-21
Ok, try this ```
sudo mkdir /var/cache/apt/archives/partial
```
If I remember correctly partial is a folder so by recreating it and running aptitude again you may have so luck

---

### Post by TheSixthPandava on 2008-10-21
You guys are the best!!!
It worked! 
Thank you very much!

---

### Post by hyper_ch on 2008-10-21
to delete the downloaded packages run
```

sudo apt-get clean

```

---

### Post by TheSixthPandava on 2008-10-21
I did that also.
Well, I deleted those tracker files, purged tracker, and now I have my 34,6 GB free.
I want to thank you again for such valuable advices!

---

