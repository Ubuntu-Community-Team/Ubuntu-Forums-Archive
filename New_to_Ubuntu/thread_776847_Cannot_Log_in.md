---
title: "Cannot Log in"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Jeenyus on 2008-05-01
So the other day I go to log into ubuntu and receive the following error message,
"GDM could not write to you authorization file.  This could mean that you are out of disk space or that you home directory could not be opened for writing.  In any case, it is not possible to log in.  Please contact you system administrator."

I run a dual boot of XP and ubuntu with a third shared partition.  The only thing I can think of happening is when I download torrents, I copy the files to the shared partition then delete them from the Deluge folder on the ubuntu partition.  If for some reason the deleting from the ubuntu partition doesn't work as I think it does, or something along those lines, then I could see my ubuntu partition being full, otherwise I have no idea what is wrong.

Any advice is appreciated, I'm not all too savvy with ubuntu yet so please try and be as thorough as possible, thank you very much in advance.

---

### Post by Monicker on 2008-05-01
Try logging in as root using the Recovery Mode boot menu option.  Normally linux always sets aside some free space for the root user, so you should be able to get in with that account.

---

### Post by Jeenyus on 2008-05-01
I was able to log in using the recovery mode, but what can I do from the terminal to make it so I am able to log in using the normal ubuntu log in?

---

### Post by Monicker on 2008-05-01
> **Jeenyus said:**
> I was able to log in using the recovery mode, but what can I do from the terminal to make it so I am able to log in using the normal ubuntu log in?


Find out where all the space is being consumed


df -h
sudo du -ch --max-depth=1 /


Or you can proceed straight to where Deluge is storing files, if you think that is the problem.

---

