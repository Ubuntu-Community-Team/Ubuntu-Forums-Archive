---
title: "XXcopy in Linux"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by wportre on 2008-05-27
I know the answer is always "better/faster/cheaper in Linux" so please help me out. I have used <a href="http://www.xxcopy.com">xxcopy</a> for years as a backup/disk replication/file manipulation godsend in Windows. For those not familiar, it is a DOS-shell utility based on xcopy with a bewildering array of switches and macros that let you do pretty well anything, such as copy all pictures above 50k dating from 2005 into a single directory with the files named according to their original location. So incremental backup (my main aim)is a breeze. <b>dump</b> seems to go some of the way there, and Amanda looks pretty powerful, but can someone point me at the "Linuxxxcopy" (TM) that I am missing? Thanks. wp

---

### Post by 505 on 2008-05-27
I don't think there is such a tool. However, all operations that you describe above can be done in Linux: it's called piping. You can feed the results of one command onto another by joining them with the | sing.
So by combinging the find command and the cp command you can copy things, e.g.

find . -size 50k | xargs cp ~

Will copy all files that are 50 kb in size to the home directory. Sometimes you need the extra xargs command, sometimes you don't, e.g.

cat /etc/file | grep "X"

cat will print the file /etc/file, but grep will make sure only those lines with an X are displayed.

I'd advice you to take a good look at the find command and piping, it's very powerful, in fact possible more powerful that xxcopy can every be.

---

### Post by bumanie on 2008-05-27
Possibly look up dd commands. Not sure if it's what you're looking for, but it is used for data retrieval etc and can copy large amounts of data from one drive/partition to another. The output can also be gzipped.

---

### Post by hyper_ch on 2008-05-27
for incremental backups you might want to use rsync

---

### Post by sdennie on 2008-05-27
I regularly use sbackup.  It's simple if you want it to be but fairly powerful if you want to dive in:

```

sudo apt-get install sbackup

```

You'll then find it in System->Administration.

---

### Post by wportre on 2008-05-27
Thanks all: I'll let you know how I get on. Ubuntu [Linux] rocks, btw: all the surprises have been positive, from ssh with public/private keys (rapidly ported to Windows via Openssh) to playing different-region DVDs unexpectedly. Great project.

---

