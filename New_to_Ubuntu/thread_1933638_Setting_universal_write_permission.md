---
title: "Setting universal write permission"
date: 2012-02-29
forum: New to Ubuntu
---

### Post by AllanLindh on 2012-02-29
Just installed latest version of Ubuntu, on an old dual core PC, just need for running linux programs.
How do I set universal write permission?
I know, I know, it's a bad idea.
This is a single user system, one task, do not have time to learn the gastly details of linux write permission
please just tell me how to end the problem
I'm running a lot of other peoples make files, it will take forever to track down everywhere they need to write to
I tried su, didn't work, apparently disabled.
Can I log in as something powerful, and get away from this problem?
Administrator??
thanks
Allan Lindh

---

### Post by josephmills on 2012-02-29
> **AllanLindh said:**
> Just installed latest version of Ubuntu, on an old dual core PC, just need for running linux programs.
How do I set universal write permission?
I know, I know, it's a bad idea.
This is a single user system, one task, do not have time to learn the gastly details of linux write permission
please just tell me how to end the problem
I'm running a lot of other peoples make files, it will take forever to track down everywhere they need to write to
I tried su, didn't work, apparently disabled.
Can I log in as something powerful, and get away from this problem?
Administrator??
thanks
Allan Lindh

?? ```
sudo -i 
```  ??
exit ^^ to well..
you can also learn about permissions here 
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

hope that you get it sorted out

---

### Post by AllanLindh on 2012-02-29
Thanks very much
typed in sudo -i
now I'm in some new place,
as superuser
have no idea what to do
all I really want to do is set /local to be have write permission for everyone
thanks
Allan

---

### Post by chipbuster on 2012-02-29
Saying that changing all files to writable a bad idea is a bit like saying the Titanic hit a small piece of ice, but was otherwise okay.

Changing everything to writeable will allow you to do whatever you want, yes. It will also allow you to accidentally change critical system files, which will break your system irreparably.

You say your computer is a single-user system, but if its connected to the internet (which I presume it is), it's really not single-user anymore.

> 
I'm running a lot of other peoples make filesNot quite sure what that means.....but it seems to imply that your system is not, in fact, single-user

If you need a root terminal login, you can use sudo -i for Ubuntu.

EDIT: Pertaining to your new question, I haven't been able to locate any /local folder in Ubuntu. What exactly are you talking about?

---

### Post by AllanLindh on 2012-02-29
Slight progress
typed sugo -
got in as su
went to /usr
typed      chmod a+w local
this changed all the permission characters for /usr/local
then logged out as su
but now when I run my makefiles
it cannot write into the directories downstream from /usr/local
Sorry to be so dumb, I'd blame it on age
  but was just as dumb when I was first trying to UNIX 40 years ago
Would changing the ownership of the makefile to mine help??
thanks again

---

### Post by Dubslow on 2012-02-29
If you're absolutely sure you know the risks, then using 
```
sudo chown -R $USER:$USER /
``` and/or ```
sudo chmod -R ugo+w /
``` will do the trick. The former sets every file and directory to be owned by whatever your username is, as opposed to being owned by root. The latter adds write permissions to every user for every file, though obviously this isn't the only way the get what you want here. DO NOT DO THIS ON ANY COMPUTER WHERE YOU'RE NOT THE ONLY USER. People can exploit this to, among more creative things, wipe the entire drive in one command.

The alternative is to just to do```
sudo -i
``` whenever you use command line. That will give you a command line with root privileges, allowing any access you want.


Edit: After seeing your post right above this, in general the '-R' option will cause 'chown' and 'chmod' to recurse through each subdirectory, as you're looking for.

---

### Post by AllanLindh on 2012-02-29
You sir, are a prince
Got by with less drastic action
just created universal write permission for everything in /usr/local
chmod a+w *
And that did trick

Thank you one thousand times
Allan

---

### Post by HeroOfCanton on 2012-02-29
Glad to hear you managed to figure it out. Make sure you mark the thread solved in "Thread Tools" at the top so we don't continue to wander in to check it out.

---

