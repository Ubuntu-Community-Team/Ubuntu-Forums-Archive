---
title: "Login password conundrum"
date: 2014-04-09
forum: New to Ubuntu
---

### Post by mlnease on 2014-04-09
Hello,

I'd like to use a really secure password for my xubuntu login.  Presently I'm using a very simple one--I could never remember the strong password I'd like to use, so how can I have that available to enter into the login window?  Can I do it somehow with a thumb drive or...?

Thanks in advance.

---

### Post by Coolgirl on 2014-04-09
dude I have like the same problem

---

### Post by mlnease on 2014-04-09
If I find a solution elsewhere I'll post it here, Coolgirl.

---

### Post by HermanAB on 2014-04-10
You could store a key on a USB stick and use that to log in.  Configuring PAM to do that is not easy, mainly because any mistake will leave you unable to log into your machine.  Some googling may find the answer though.

---

### Post by buzzingrobot on 2014-04-10
Basically, just create a strong password and memorize it.  Nonsense mnemonic phrases that mean something to you and no one else are good memory aids.  Lots of ideas out there.  Like here: [http://www.bbc.com/news/blogs-magazine-monitor-26969276](http://www.bbc.com/news/blogs-magazine-monitor-26969276).

For online passwords, some folks like password managers, which create and automate the use of strong passwords.  There is a long thread elsewhere on these forums about their pros and cons.

---

### Post by mlnease on 2014-04-10
Thanks, I'm aware of this (mnemonic) approach.  If possible, I'd like to use something stronger--ideally utilizing a usb stick.  It seems to me I've read about something like this somewhere but maybe it's propietary and not compatible with xubuntu.

p.s.  Thanks again, Buzzingrobot, I've had a look at the [thread]("http://ubuntuforums.org/showthread.php?t=1999228&highlight=password+manager") you started, 'Are Password Managers Really Necessary'.  It looks to me like KeePassx is what I was looking for (though I didn't know it).   According to their ['Features']("http://www.keepassx.org/features/") page, 

> 
[LIST]
[*]Database security
- access to the KeePassX database is granted either with a password, a key-file (e.g. a CD or a memory-stick) or even both. 
[/LIST]

So--even though I'm not sure yet that it really addresses my original question--how to protect my *machine* with a really strong login password--it is a step in the right direction and, since my original question doesn't seem to have an answer, I guess I'll mark this thread 'solved'.

Coolgirl, I hope this works for you too.

---

### Post by buzzingrobot on 2014-04-10
Not quite sure what you're looking for then, because either you or a piece of software need to create, and remember, the password in the first place.

---

### Post by mlnease on 2014-04-10
Yes, I understand that--I intended to use a strong password generator to generate a password I certainly wouldn't be able to remember--but once I have it, how do I enter it into the password field in the xubuntu login screen?  That's the question I'm trying to address but maybe I'm not expressing it clearly enough.  Thanks for your time and patience.

---

### Post by steeldriver on 2014-04-10
It sounds like you may be looking for how to set up and use **pam-usb** 

There appears to be some reasonably up-to-date information in this AskUbuntu answer --> [USB drive Login token system?]("http://askubuntu.com/a/10528/178692")

---

### Post by mlnease on 2014-04-10
Thanks, steeldriver--I'll have a look and get back to you.

---

### Post by mlnease on 2014-04-10
Yes, this is *exactly* what I was looking for.  I'll post here as soon as I've tried implementing it.  Thanks again.

---

### Post by ajgreeny on 2014-04-12
Just make sure you have more than one copy of the USB stick, if that's what you use, just in case one gets lost, or corrupt, or simply goes bad as usb sticks can.

---

### Post by mlnease on 2014-04-12
Thanks, I hope to implement this this afternoon and will post my results here.  After setting this up, will I still be able to use the usb stick for other purposes?  Add and remove files and so on?  The instructions don't make this clear (I don't think).

(EDIT--on hold till I get to town and pick up a couple more thumb drives).

---

