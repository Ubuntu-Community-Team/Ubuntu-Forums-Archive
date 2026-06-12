---
title: "/home folder renamed. no login possible"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by marcellux on 2012-05-01
Hi,

I did something extremely stupid: 

I went to system settings > user management and changed the path to the /home directory from my user.

Now, when I try to log in I first get: "Cannot enter home directory. Using /." And then:
 "Call to lnuser failed (temporary directories full?). check your installation".

I did not migrate the contents of my home folder before changing the path. 

Is there a way to set the /home folder path back to how it was? Is there any config file where to re-write the path back to where it was?

[kubuntu 11.10 3.0.0.19]

Thanks in advance!!

---

### Post by jtarin on 2012-05-01
[All things are possible.]("https://wiki.archlinux.org/index.php/Change_username")

---

### Post by marcellux on 2012-05-01
Thanks a lot Jtarin! The article is really instructive and it helps a lot to clear things out!

Problem is solved! 

I started in failsafe mode and typed: "usermod -d /my/new/home [username]" but it told me, [username] is already logged in...
So, I created a passwd for the root user and logged in as root. Then I typed "startx". I went to system settings (where all begun) account management and I typed the old path to /home to [username]! Now I can log in again as [username]!

---

### Post by jtarin on 2012-05-02
I'm glad it was helpful......it's easier to direct your somewhere than write it out and go through three pages or more here in the forum.

---

