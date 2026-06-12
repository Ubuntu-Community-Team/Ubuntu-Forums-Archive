---
title: "Security Question: Can anyone log in as ROOT"
date: 2009-08-02
forum: Recurring Discussions
---

### Post by joydeep_jra on 2009-08-02
I had a problem ([http://ubuntuforums.org/showthread.php?t=1229327](http://ubuntuforums.org/showthread.php?t=1229327)) That has been solved by [[COLOR=#d40000]**aysiu**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941"). However the solution ([http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)) left me thinking.
 
Anyone can interupt the boot, go to recovery mode & log in as ROOT. Is this not a big security hole. Am I missing something - did I have a easy time as I did not have ROOT password set.

---

### Post by aysiu on 2009-08-02
Physical access is root access.

This is true for all Linux distributions. It's also true for Windows and Mac OS X.

For more details, read this thread:
[http://ubuntuforums.org/showthread.php?t=989517](http://ubuntuforums.org/showthread.php?t=989517)

---

### Post by lisati on 2009-08-02
Some interesting reading:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://ubuntuforums.org/showthread.php?t=989517](http://ubuntuforums.org/showthread.php?t=989517)
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Edit: aysiu beat me to posting one of the links! :)

---

### Post by lswb on 2009-08-03
> **aysiu said:**
> Physical access is root access.

This is true for all Linux distributions. It's also true for Windows and Mac OS X.


Sort of. It's a lot easier to get root/admin through physical access on a ubuntu system than with windows, though there are things you can do to make the ubuntu system equally or even more difficult to access.

---

### Post by Bigtime_Scrub on 2009-08-03
Logging in as root is the old Linux way of doing things and is secure as long as you know what you are doing. FYI, most distros use su and not sudo which some argue makes Ubuntu *less* secure, because in general on Ubuntu the user password is the same as the super user password. In distros that allow root log in the two passwords are different and thus, more secure.

---

### Post by aysiu on 2009-08-03
> **Bigtime_Scrub said:**
> Logging in as root is the old Linux way of doing things and is secure as long as you know what you are doing. FYI, most distros use su and not sudo which some argue makes Ubuntu *less* secure, because in general on Ubuntu the user password is the same as the super user password. In distros that allow root log in the two passwords are different and thus, more secure.
Not quite.

Check this link for the real pros and cons of sudo v. su
[https://help.ubuntu.com/community/RootSudo#Advantages%20and%20Disadvantages](https://help.ubuntu.com/community/RootSudo#Advantages%20and%20Disadvantages)

---

### Post by aesis05401 on 2009-08-03
I would just like to point out that from '95 to XP every Windows OS could be pwned at power-up with virtually no effort.  Hint: they were loading accessibility options before the user had to login.

For all I know the exact same vector still works on Vista and 7, I'm no longer into MS like that though ;)

I think a lot of new users have not thought about security in depth during their MS years, so now this physical access thing scares them.. Crazy how often this question comes up.

---

### Post by lswb on 2009-08-03
> **Bigtime_Scrub said:**
> Logging in as root is the old Linux way of doing things and is secure as long as you know what you are doing. FYI, most distros use su and not sudo which some argue makes Ubuntu *less* secure...

The OP was referring to booting into single user/recovery mode, no login required. sudo vs su doesn't apply.

---

