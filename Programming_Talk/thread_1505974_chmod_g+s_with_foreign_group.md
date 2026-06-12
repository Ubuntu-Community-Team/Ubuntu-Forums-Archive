---
title: "chmod g+s with foreign group"
date: 2010-06-09
forum: Programming Talk
---

### Post by troy on 2010-06-09
I have an application that creates directories that are owned by me.  However, the group the directories belong to is not a group that I am a member of.  

I want to set the GUID on the directories.

It doesn't appear that I am able to unless I am a members of the group owner.  In fact if I set that GUID as root and then do it again under my id the GUID bit is removed.

It is a know requirement that 'chmod g+s othergroup  MyDir' will only work if the current user is a member of othergroup?

---

### Post by rnerwein on 2010-06-10
hi
i think you want get this:
mkdir blu
chmod 2777 blu --> drwxrw[COLOR=Red]s[/COLOR]rwx 2 richi richi 4096 2010-06-10 09:52 blu
su - surfer
cd /home/richi/tmp/blu
touch bla
ls -l bla --> -rw-r--r-- 1[COLOR=Red] surfer[/COLOR] [COLOR=Blue]richi[/COLOR] 0 2010-06-10 09:52 bla # ! surfer is not in the group "richi"
the owner now is surfer but the group is set to richi.
hope this help you
ciao

---

### Post by troy on 2010-06-11
That is not quite what I am asking.  Here is the example.  Notice the ssi directory doesn't have the GUID bit set.

```

bash-3.00$ id
uid=2714(tssadmin) gid=10(wheel) groups=10(wheel)

bash-3.00$ groups
wheel

bash-3.00$ ls -ld .
drwxrwxrwx  13 tssadmin iwglobal 512 Jun  9 17:17 .

bash-3.00$ ls -ld ssi xxx
drwxrwxrwx  2 tssadmin iwglobal 512 Jun  9 17:07 ssi
drwxrwxrwx  2 tssadmin wheel    512 Jun  9 17:17 xxx


bash-3.00$ chmod g+s xxx
bash-3.00$ chmod g+s ssi
bash-3.00$ ls -ld ssi xxx
drwxrwxrwx  2 tssadmin iwglobal 512 Jun  9 17:07 ssi
drwxrwsrwx  2 tssadmin wheel    512 Jun  9 17:17 xxx


bash-3.00$ chmod 2775 ssi
bash-3.00$ chmod 2775 xxx
bash-3.00$ ls -ld ssi xxx
drwxrwxrwx  2 tssadmin iwglobal 512 Jun  9 17:07 ssi
drwxrwsr-x  2 tssadmin wheel    512 Jun  9 17:17 xxx


```

---

### Post by rnerwein on 2010-06-12
hi
ok now i know what you mean.
you can't set the sbit for a group you aren't meber of. only super user can do that.
--> think about this. set a sbit of a group you aren't member of and the file is an executable uuuuuuuuuuuuups !!!!
ciao

---

