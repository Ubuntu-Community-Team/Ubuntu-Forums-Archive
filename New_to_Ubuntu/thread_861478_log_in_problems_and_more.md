---
title: "log in problems and more"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by FSten on 2008-07-16
I have been using Ubuntu for quite a while and everything has been working fine until just recently.

When I tried to log in with my usual user name, I got some error messages which I did not have time to read, and then I was returned to the log in screen again. When trying to log in again, the computer just freezes and I had to restart.

I have been able to log in user another user account on the computer. When I tried to access the home directory of my usual user name, I was not able to open that filer, using either "places" or the command line.

Another thing is that I am only able to access the other user's home directory using the command line.

I also have windows installed, and noticed that I am not able to access my linux partitions anymore. That has worked previously.

I cannot recall do anything in particular before this problem occured, but it did happen after I had to use windows. But that has not caused any problems before.

Ok, I guess it sounds a bit confusing, but I have no idea on how to try to fix this, and any hints would be appreciated.

---

### Post by jimmy the saint on 2008-07-16
if you can replicate that error message it sure would make it a lot easier to isolate the problem.

---

### Post by carandraug on 2008-07-16
You can probably acess your user home folder using the LiveCD. Just pop in the ubuntu CD you used to install Ubuntu (or any other liveCD) and you should have no problems. Just don't erase anything that may be important when using it.

---

### Post by FSten on 2008-07-16
The problem is that after trying to log in, there's some text that I don't have time to read, and then I am returned to the log in screen again.

---

### Post by FSten on 2008-07-16
> **carandraug said:**
> You can probably acess your user home folder using the LiveCD. Just pop in the ubuntu CD you used to install Ubuntu (or any other liveCD) and you should have no problems. Just don't erase anything that may be important when using it.

Thanks. I will try this and copy the files I need and then just make a clean install.

---

### Post by carandraug on 2008-07-16
> **FSten said:**
> Thanks. I will try this and copy the files I need and then just make a clean install.
If you want to make a backup of everything you have in your home folder (instead of copying the files that you think you'll need just to find out later that maybe, that .conf file, now erased, is actually quite useful) use the following command ```
rsync -acvSHx --exclude lost+found /home/ /where_you _want_to_backup
``` since you'll be doing it with a live CD, switch "/home/" for "/media/whatever_the_name_is/home/"

---

