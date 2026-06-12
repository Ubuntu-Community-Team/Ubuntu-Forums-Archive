---
title: "moving thunderbird to new ubuntu installation"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by ruud00000 on 2012-10-25
I just installed Ubuntu 12.04.1 32-bit instead of 12.04.1 64-bit. Made a  copy of the thunderbird and Frefox profile before doing so. Now when I  open Thunderbird a new defalut profile is created (named  m6rzzjis.default instead of the old name el0vempw.default). So I copy  the contents of the old default folder into the new one and overwrite  anything already there. This works fine for Firefox but doesn't work for  Thunderbird: the old mails / settings are not found. Even when I copy  the entire folder using the old name and change the reference to it in  the profile.ini the old mail and settings don't show.

What's wrong? How to solve?

Thanks.

---

### Post by newb85 on 2012-10-25
Have you read this thread?  (Specifically, posts #1 and #8)

[http://ubuntuforums.org/showthread.php?t=2074351&highlight=thunderbird]("http://ubuntuforums.org/showthread.php?t=2074351&highlight=thunderbird")

---

### Post by ruud00000 on 2012-10-25
I read that and tried that too, however without result. Now I set up the account from scratch. Just out of curiousity I removed Thunderbird and installed it again, but now referring to the just newly setup profile afterwards (renaming the path in profiles.ini just like I did before and now it does work. Apparently somehow the data as copied from the 64-bit version of Ubuntu / Thunderbird? cannot be read into the 32-bit version or in some other way the Thunderbird versions are incompatible in the way the data are stored?

---

### Post by oldfred on 2012-10-25
I have both Firefox & Thunderbird profiles in a NTFS partition so I could use XP and my Ubuntu installs. And I copy profiles to my laptop when travelling.

I do have to edit profile.ini with the correct profile and start Thunderbird once to create the default profile & profile.ini file.

Did you change user name. It could be ownership or permission issues?

What does  ls show.

f```
red@fred-Precise:~$ sudo ls .thun* -l
total 16
drwx------ 3 fred fred 4096 Oct 13 09:45 Crash Reports
-rw-rw-r-- 1 fred fred   94 Apr 18  2012 profiles1204.ini
-rw-r--r-- 1 fred fred  151 Nov 25  2009 profiles.ini
drwx------ 4 fred fred 4096 Apr 18  2012 qbugvibk.default

```I just noticed I copy my older profiles.ini and it has different permissions than my new one profiles1204.ini.

---

### Post by ruud00000 on 2012-10-25
Here's the directory contents of .thunderbird:
totaal 12
drwx------  2 ruud ruud 4096 okt 25 13:22 Crash Reports
drwxrwxr-x 14 ruud ruud 4096 okt 25 18:24 el0vempw.default
-rw-rw-r--  1 ruud ruud  104 okt 25 13:29 profiles.ini

user name the same (maybe I used a capital before, would that make a difference?)

---

### Post by oldfred on 2012-10-25
Yes, Capitals make a difference in Linux, not in Windows.

But usually usernames are lowercase?

---

