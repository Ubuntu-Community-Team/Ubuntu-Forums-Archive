---
title: "Sudo su vs. sudo su - in Ubuntu 14.04"
date: 2016-02-15
forum: New to Ubuntu
---

### Post by Grigoriy on 2016-02-15
Hello!

I've always been using either sudo or sudo su. And today I found out  that there's also a sudo su - option. That it changes the pwd and sets  the root's environment too. In regards to the latter, would it make any  difference if I'm trying to do under root:
a) delete files;
b) change attributes of files;
c) install and uninstall applications;
d) edit config files;
e) delete root's trash
OR... no matter what, I should always add a hyphen after "su" and not adding it is just a bad habit (as some say)?

---

### Post by blueridgedog on 2016-02-15
In my opinion, if you are going to use sudo su, you pretty much have embarked on a path where you need to know what you are doing and the two are functionally the same as far as risk.  If you have a root user environment that you have tweaked with special aliases and other items, then it may have merit.

---

### Post by Tadaen_Sylvermane on 2016-02-15
isn't sudo -i the preffered way? is what I've been doing for awhile now. I was advised that sudo su was a bad way to go.

---

### Post by grahammechanical on 2016-02-15
In discussions like this one we need to keep in mind that the thread will be seen by many new users who will not be aware of the risks involved in working as root/administrator and they may do severe damage to the OS in which only a re-install will fix. With this issue in mind there are 2 documents that we can review

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Regards.

---

### Post by Grigoriy on 2016-02-15
So... I still haven't got an answer...

---

### Post by sandyd on 2016-02-15
The difference is that su does not load load your shell profile or change you to your home directory as if you had logged in as the user through the login prompt. It changes the user. That's it. It does not matter whether you are root, amy, bob, or some other user, the effect is the same

To test that out...

Create a new user
```

sudo adduser testmeout

```

```

sudo -u testmeout bash -c "echo 'export THISISAROOTVAR=1' >> /home/*testmeout*/.profile"
```

This will add a command to set the value of THISISAROOTVAR to ~/.profile of the user, which is sourced on a default login.

If you want to do it unsafely....
```

sudo bash -c "echo 'export THISISAROOTVAR=1'  >> /root/.profile" 
```

Now, try both commands, and run
```

env | grep THISISAROOTVAR
```
on each.

You will also notice that using su without the dash will not change the current directory that you are in, su with the dash will change your directory to the user's current home folder.

---

### Post by QIII on 2016-02-15
To answer your questions:

> In regards to the latter, would it make any difference if I'm trying to do under root:
a) delete files;
b) change attributes of files;
c) install and uninstall applications;
d) edit config files;
e) delete root's trash

Generally, "No" .

> OR... no matter what, I should always add a hyphen after "su" and not adding it is just a bad habit (as some say)?
This is a little vague.  But to answer:  What reason would you ever need to use anything but "sudo"?  I have found very few reasons to use "su" at all and what to do expect to gain with the hypen?

Here is my take:

Almost always, "sudo" is sufficient for what you will need to do.  I avoid "sudo -i" -- I consider the extra cost of typing four extra characters before each command to be a very good reminder that I'm not in Kansas anymore and that I need to be very aware of what I am doing.  "sudo su" gains you very little.  In fact, after all these years, I have exactly *one* command for which I find the need for "su".

---

### Post by lisati on 2016-02-15
> **QIII said:**
> 
Almost always, "sudo" is sufficient for what you will need to do.
Likewise for me. I simply don't need the elevated privileges and associated risks of damage very often in day-to-day use, let alone having to think about the subtleties of the different options available.

---

### Post by Grigoriy on 2016-02-15
Thank you **all** for detailed and interesting answers, especially **QIII** who's actually given me a direct answer to my question from the original post.

---

### Post by mc4man on 2016-02-15
I'd only use sudo su when sudo gets a permission denied.

As far as sudo su vs. sudo su - , seems pretty simple here, at least the difference.
sudo su gives you a root prompt at your home dir. (ck. ls -la). You exit it when done.
sudo su -i gives you a root shell login at root's dir. You logout when done.

So they are different, whether it matters for this or for that actions  I don't  have any pressing need there as usage is rare.
(- though would be interesting to know

---

### Post by Grigoriy on 2016-02-16
Okay, thanks for your input!

---

