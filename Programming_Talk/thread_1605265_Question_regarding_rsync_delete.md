---
title: "Question regarding rsync delete"
date: 2010-10-25
forum: Programming Talk
---

### Post by aliahsan81 on 2010-10-25
Hi All

I am making a script that will take files (note only files not dirs).And copy to remote server with rsync.Problem is that when any  is deleted from source its should be deleted from destination.rsync do this very well with directories but not with files.I am using below command can any one guide me to crack this problem.

```

rsync -var --progress -e ssh someuser@somehost.com:/root/test/some_name*  --delete /back-up-2010-10-25/

```


Above command will copy all thing from root/test/some_name* to  backup dir.

Now i want if any file is deleted from source with name of some_name.xyz it should be deleted from destination.Is that possible with rsync.

---

