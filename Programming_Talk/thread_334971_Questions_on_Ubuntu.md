---
title: "Questions on Ubuntu"
date: 2007-01-09
forum: Programming Talk
---

### Post by rayj00 on 2007-01-09
I am doing security testing on a product that is using Ubuntu 6.10.
It a hugely gutted in that most if not all of the normal linux commands
are not available. Logged in as admin, if I do an "ls" command, I only
see a few files. No directories. I cannot do a "cd /". It echos an error
message. What I'm looking for is the password file, but I can't get to
the /etc directory.....

My question is: Is there a backdoor or some kernel level commands
available? 

Thanks.

Ray

---

### Post by meng on 2007-01-09
Perhaps you should boot a LiveCD and use that to mount the partition so that you can examine it.

---

### Post by Tomosaur on 2007-01-09
strange, what's the product?

---

### Post by rayj00 on 2007-01-09
Actually, it's Extreme Networks XOS.......

---

### Post by pmasiar on 2007-01-09
> **rayj00 said:**
> I am doing security testing on a product ...Is there a backdoor or some kernel level commands available? 

is it just me who finds it funny? If you are doing security testing, *you* should be *answering* security questions, and not *asking* them? :evil: 

Nothing personal, I just found it funny.

---

### Post by rayj00 on 2007-01-10
> **pmasiar said:**
> is it just me who finds it funny? If you are doing security testing, *you* should be *answering* security questions, and not *asking* them? :evil: 

Nothing personal, I just found it funny.

You're absolutely right. However I have no experience with Ubuntu and just thought
I'd try to speed up my investigation a little as time is of the essence....

After all, that's what the web is all about!!! Seek and ye may find!!!

---

### Post by Tomosaur on 2007-01-10
Ubuntu is generally considered extremely secure. I'm not aware of any vulnerabilities that aren't down to user-error - the default Ubuntu install is virtually impossible to compromise unless you have direct access to the machine (ie, you're sitting down in front of it). If you manage to find a way of compromising an Ubuntu box, I'm sure people'd be very interested :)

---

