---
title: "Explore &quot;My documents&quot; from Vista in Ubuntu"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by eliaspoveda on 2008-04-25
Hi everybody!

I have Vista and Hardy Heron in the same disk.

Now I'm in Ubuntu and I'm trying to explore the files that are at the Vista partition, but when I open, for example, My Documents folder, i can't.

I think it's becouse i use a password to start Vista but Ubuntu doesnt give the option to introduce the password.

I don't want to use shared folders, i want to explore all the folders.

Any idea?

Thanks!

---

### Post by swoll1980 on 2008-04-25
what error message to you get?

---

### Post by eliaspoveda on 2008-04-25
I don't get any error message, i just can't see the files inside the folders.

Thanks!

---

### Post by swoll1980 on 2008-04-25
how are you getting to the folder? what path? /media/sda1/documents and settings/user_name/my documents?

---

### Post by eliaspoveda on 2008-04-25
Exactly. :)

---

### Post by orethrius on 2008-04-25
What's the result in ~/test.log if you do a Run Program (Alt+F2), followed by
```
xterm -e 'mount | grep /media/sda1 > ~/test.log'
```

---

### Post by silverglade00 on 2008-04-25
> **swoll1980 said:**
> how are you getting to the folder? what path? /media/sda1/documents and settings/user_name/my documents?

That should be "/media/sda1/Users/user_name/Documents" in Vista.

---

### Post by orethrius on 2008-04-25
> **silverglade00 said:**
> That should be "/media/sda1/Users/user_name/Documents" in Vista.

I'm just curious whether the right filesystem driver is loading or not.
It's still NTFS for Vista, right?

---

### Post by stchman on 2008-04-25
> **eliaspoveda said:**
> Hi everybody!

I have Vista and Hardy Heron in the same disk.

Now I'm in Ubuntu and I'm trying to explore the files that are at the Vista partition, but when I open, for example, My Documents folder, i can't.

I think it's becouse i use a password to start Vista but Ubuntu doesnt give the option to introduce the password.

I don't want to use shared folders, i want to explore all the folders.

Any idea?

Thanks!

You need to properly mount your Vista partition in fstab.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

You can choose ntfs or ntfs-3g(read/write).  I recommend you dont write to the system partition of Vista as you can mess it up.

---

### Post by eliaspoveda on 2008-04-25
yes, you're right that's the path, sorry and about the ~/test.log... it says "permission denied" :oops:

Im spanish, sorry for my english

---

### Post by orethrius on 2008-04-25
> **stchman said:**
> You need to properly mount your Vista partition in fstab.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

You can choose ntfs or ntfs-3g(read/write).  I recommend you dont write to the system partition of Vista as you can mess it up.

What, do you search for NTFS and answer EVERY POST that comes up?  :D
Nah, just kidding, this'll get solved sooner just by your involvement! ;)

> **eliaspoveda said:**
> yes, you're right that's the path, sorry and about the ~/test.log... it says "permission denied" :oops:

Im spanish, sorry for my english

That's okay, you speak English better than many people I know.  ;)

When you say "permission denied", this is in the log file (see stchman's reply above) or as a reply to trying to read the logfile (something else is wrong)?

---

### Post by eliaspoveda on 2008-04-25
So many people helping! i'm shy its hard to follow the instructions. xD

Yes, I haven't change the Vista partition, but in my desktop everything was ok without touching nothing.

If I don't use password in vista the problem is solved?

---

### Post by orethrius on 2008-04-25
> **eliaspoveda said:**
> So many people helping! i'm shy its hard to follow the instructions. xD

Yes, I haven't change the Vista partition, but in my desktop everything was ok without touching nothing.

If I don't use password in vista the problem is solved?

Unless Vista uses some password-keyed encryption I haven't heard about, the password's existence itself is irrelevant.

If I may, what part of stchman's directions is giving you trouble?

As an aside, do you want the Vista drive to be read-only (recommended) or read-write (possibly unstable and NOT recommended)?

---

### Post by rajaram_s on 2008-04-25
if it says access denie, open the same file with the sudo command....

---

### Post by orethrius on 2008-04-25
> **rajaram_s said:**
> if it says access denie, open the same file with the sudo command....

The only problem with that being, of course, that opening the file with **sudo** doesn't fix his home partition not being readable.  I believe you meant to say
```
sudo chmod -R +r ~
```
;)

---

