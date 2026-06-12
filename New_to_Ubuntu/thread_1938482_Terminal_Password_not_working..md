---
title: "Terminal Password not working."
date: 2012-03-09
forum: New to Ubuntu
---

### Post by acimi66 on 2012-03-09
Ubuntu 11.10
For software it takes the admin password fine but when I do "sudo" inside terminal
it says.
[sudo] password for acimi66: (i type it here)
sorry, try again:

I have removed terminal and reinstalled it. 
And I changed my admin password so as to have no special characters.

It's proving a little frustrating...

Any ideas??

---

### Post by acimi66 on 2012-03-09
Has no one ever come across this before?

---

### Post by Script Warlock on 2012-03-09
you possibly forgot the password.

---

### Post by acimi66 on 2012-03-10
Well the problem is that I when I install software through the repository it asks for admin password and I it works fine.

Is my terminal, Terminal?;)

---

### Post by disabled20191128 on 2012-03-10
caps lock or numlock activated / deactivated?

---

### Post by acimi66 on 2012-03-10
nice thought but no that doesn't seem to it.

---

### Post by acimi66 on 2012-03-10
I finally remembered the "man terminal" line...but terminal doesn't have a manual Ha!

Is re-installing the OS TOO extreme and idea? 

I have tried removing and re-installing multiple different terminals. It feels like its a deeper problem.

---

### Post by AnojiRox on 2012-03-10
restart your computer, then press [esc] when grub is loading. choose the latest 'recovery mode'. then, log in and type into terminal "passwd {username here}". this SHOULD work

---

### Post by winh8r on 2012-03-10
If you press ```
control + alt + F1
```

can you login to console using your normal login credentials?


use ```
control + alt + F7
``` to get back to desktop after trying

---

### Post by acimi66 on 2012-03-10
Hey thanks for the response's.
I went with CRTL+ALT+F1. I logged with my admin account  ( which worked with the admin password) and took a look at the MAN.

I needed to "adduser to admin group" so the SUDO command would work for my user to access ADMIN privileges.

Don't you just love working this **** out!?!:popcorn:

---

### Post by winh8r on 2012-03-10
This tutorial will help you to get it back on track.


[http://www.psychocats.net/ubuntu/fixsudo]("http://www.psychocats.net/ubuntu/fixsudo")

---

### Post by acimi66 on 2012-03-10
Yeah thanks Winh8r.
The one thing I didn't get, after setting up and ADMIN account and USER account was that I needed to add my USER to the ADMIN GROUP so SUDO would work.

Hope that helps someone...

---

### Post by winh8r on 2012-03-10
Glad to hear you got it working.

You can mark the thread as solved using the thread tools menu at the top of the this thread.

Good Luck

---

### Post by acimi66 on 2012-03-10
I was looking for that...Cheers

---

