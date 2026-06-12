---
title: "Odd Folder Ownrship anomaly"
date: 2012-08-29
forum: New to Ubuntu
---

### Post by starz677 on 2012-08-29
I have one folder that for some reason adds a minus sign (-) to the owner name.

like this......
[B]
scooby -[/B]

instead of

**scooby**

I can't find any other file or folder that dos that other than one particular folder.

I can't remove the minus sign.

Anyone know what this is and what to do?

thx

---

### Post by NikTh on 2012-08-29
Hi , 
are you sure that is a minus sign ? or is this sign **~ **
provide more info with command ```
ls -ld <folder>
```Thanks

---

### Post by CharlesA on 2012-08-29
The command to show the permissions of a folder is actually:

```
ls -ld /path/to/folder
```

Running ls without -d would list whatever is in the folder.

---

### Post by starz677 on 2012-08-29
> **NikTh said:**
> Hi , 
are you sure that is a minus sign ? or is this sign **~ **
provide more info with command ```
ls -ld <folder>
```Thanks

Yes,  definitely a minus sign exactly as In the OP
When I run ls -l  (I cant access the Internet form the affected conmputer so unable to copy)

I get....

```
drwxrwxr-x 3 scooby root 4096 2012-08-29 10:25 scoobyfolder
```

So it appears correct in the ls command, but....when I try to access the folder via a browser it returns Permission Denied.

It seems that the minus sign is causing the interpretation of the folder owner to be wrong.

In other words...owner **scooby** <> owner **scooby -**

I have never seen this before and I've been working with Ubuntu for many years.

It is only that one folder.  All others have the same owner and do not have the minus sign after the owner.

Trying to change the owner name to scooby again does not remove the minus sign.

I couldn't find anything on this via Google so I assume this is indeed very strange?

BTW - the place whee I see the minus sign is graphical.  If I right click on the folder then choose Properties --> Permissions

.
.
.
.

---

### Post by NikTh on 2012-08-29
Hi , 
did you try to change the owner with chown command ? 
for example 
```
sudo chown scooby:scooby /path/to/folder
```
I really don't know what this minus sign could be.
Thanks

---

### Post by CharlesA on 2012-08-29
Is this folder being served via Apache? You said it gives you permission denied when you try to browse to it via web browser.

---

