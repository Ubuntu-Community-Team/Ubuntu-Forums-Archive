---
title: "Too many apps need to run as root to function"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by JoeEndUser on 2008-06-24
I'm hoping someone could help with a new approach to assist in usability.

Snowball:  I have to run thunderbird as root for some extensions to work, because of this Google Desktop needs root to access thunderbird, firefox needs to run root to be launched by google desktop, openoffice needs to be run in root in order to be launched by thunderbird, if openoffice runs as root than java does too etc etc.

I don't want to set a root user password if I can avoid it.  Any ideas to stop this would be most welcome!

---

### Post by billgoldberg on 2008-06-24
Use evolution instead would be one way to fix this, or file a bug report for thunderbird and hope they fix it soon.

---

### Post by markjensen on 2008-06-24
> **billgoldberg said:**
> Use evolution instead would be one way to fix this, or file a bug report for thunderbird and hope they fix it soon.
From reading the original post, it sounds like an **extension** is the problem.  Filing a bug report with the Thunderbird team will get nowhere.

What extension is it, specifically?  It sounds like _they_ are the ones that need to fix the problem (unless it is how it is installed or configured).

---

### Post by jpeddicord on 2008-06-24
> **markjensen said:**
> (unless it is how it is installed or configured).

If that's the case, running```
sudo chown -R user:user ~
```should fix the problem. (Replace user with your username, for example jacob:jacob.)

---

### Post by Greyed on 2008-06-24
Can you provide error messages?

---

### Post by JoeEndUser on 2008-06-24
Thank you all. I use the webmail extension with hotmail, which I think is the trouble. Looking around for a fix on the web as to why it wouldn't work, brought me to "it won't work without root access."  Turned out to be true.

It looks like I might be able to do the same thing with evolution, but I like thunderbird.

---

### Post by JoeEndUser on 2008-06-24
> **Greyed said:**
> Can you provide error messages?

None specifically, without root webmail just doesn't work.  Same with google desktop - just won't index thunderbird.  When trying to launch a program that should have root access it gives an - another instance of openoffice or firefox is running message.

Good to talk [post] through it, I see now my computer life is being hi-jacked by a hotmail extension!

---

### Post by JoeEndUser on 2008-06-25
As a follow-up, I got rid of the extension for hotmail.  I found that I didn't even need it as there is a direct way now: POP3.live.com, SSL, smtp.live.com, TLS.

I did have to completely reinstall Thunderbird from a back-up.  It either did not like having the webmail extension disabled, or did not like having the user/group changed.

Evolution looks good, but too much of a hassle to move right now, I have too many folders.

Cheers!

---

