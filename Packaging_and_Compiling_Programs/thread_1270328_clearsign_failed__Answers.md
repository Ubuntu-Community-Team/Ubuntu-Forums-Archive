---
title: "clearsign failed : Answers"
date: 2009-09-19
forum: Packaging and Compiling Programs
---

### Post by tarundsk on 2009-09-19
All,

I was facing problems while signing package and while searching in forums I found out on this link - [http://ubuntuforums.org/showthread.php?t=641063&highlight=failed+secret+key](http://ubuntuforums.org/showthread.php?t=641063&highlight=failed+secret+key) but there was no answer.

So just for other users like me here is the solution - let me know if something is wrong here.

If you have GPG Keys than simply create the file ~/.devscripts & add the following :

DEBSIGN_KEYID="<Your KEY ID>"

To see the list of keys you can use : gpg --list-secret-keys.

-Tarun 
[http://www.tarunsadhana.com]("http://www.tarunsadhana.com/")

---

### Post by stanz on 2010-12-23
Thanks !!! This works!!
I've been searching for days trying to figure this signing error.

[SIZE=2][U]This info needs to be in more places!!

[/U]Question:: Does the .devscripts file delete/replace the .bashrc file?
     I just noticed mine is gone. ?!
[/SIZE]

---

