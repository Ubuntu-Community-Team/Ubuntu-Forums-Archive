---
title: "Allow Shutdown at end of script (for Non-Root User) vs Sudo timestamp_timeout ?"
date: 2007-04-18
forum: Programming Talk
---

### Post by TomG on 2007-04-18
Hi

I have the following problem.

I want to shutdown automatically my PC at the end of a long script ("shutdown -h now"). So I :
 o added line in /etc/sudoers to avoid to enter password :  tom   ALL=(root) NOPASSWD: /sbin/shutdown 
 o created my shell script which works fine
 o put the line "sudo /sbin/shutdown -h now" at the end of my script

The drawback of this is of course if the script execution is longer than my sudo password timestamp_timeout (set to 60 in /etc/sudoers) then the shutdown will not occur as new identification will be needed.

Is there a way to workaround this except by increasing timestamp_timeout to a very high value ?

Thanks for any suggestion.
TomG

---

### Post by Ramses de Norre on 2007-04-18
* Don't use sudo inside the script but run the whole script as sudo... Using sudo inside scripts never turned out good to me.

* If it really must you can use **sudo -S *password* command** and set the read privileges of the file as restricted as possible (it contains your password in plain text...)

---

### Post by TomG on 2007-04-18
Thanks. A quick test on your 1st suggestion seems make the trick.
However I dont see need to put an entry inside /etc/sudoers as sooner or later a password is re-asked. I thought that it allowed to avoid password request.

---

### Post by bruenig on 2007-04-18
On my sudoers file, the syntax is different, I don't know if that is what is prompting you for a password or not but it looks like this.
username ALL=NOPASSWD: /sbin/shutdown

---

