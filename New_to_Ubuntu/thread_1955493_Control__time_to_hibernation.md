---
title: "Control  time to hibernation?"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-09
[SIZE=3]I am using a desktop and [/SIZE][SIZE=3]I do not enjoy having to input my password after 11.10 periodically goes into hibernation.

Can I set the system to "always on"?[/SIZE]

---

### Post by ravinfy on 2012-04-09
Hello! 
I am sure so many others share the same opinion about systems going into Hibernation... however, on Ubuntu`s part, it is understandable that they give a default idle time before saving some power on your laptop. 

Theres help, however... how about going to "System Settings" -> "Power" and choosing not to Suspend the machine when it is inactive for sometime? 


See screenshot attached... If I wanted my machine to run continuously ONLY when its connected to a power source, I would choose "Dont Suspend" in place of the 1 hour. 
Ubuntu lets you choose different power profiles when on Battery and power - I find this very convenient to use. 

Hope this helps. 

Ravi

---

### Post by Boyntonstu on 2012-04-09
> **ravinfy said:**
> Hello! 
I am sure so many others share the same opinion about systems going into Hibernation... however, on Ubuntu`s part, it is understandable that they give a default idle time before saving some power on your laptop. 

Theres help, however... how about going to "System Settings" -> "Power" and choosing not to Suspend the machine when it is inactive for sometime? 


See screenshot attached... If I wanted my machine to run continuously ONLY when its connected to a power source, I would choose "Dont Suspend" in place of the 1 hour. 
Ubuntu lets you choose different power profiles when on Battery and power - I find this very convenient to use. 

Hope this helps. 

Ravi


My 11.10 is set at "don't Suspend".

Next suggestion please.

---

### Post by dylan07 on 2012-04-09
This worked for me:
  ```
gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true' 
```
  It disables the locking altogether

---

### Post by Boyntonstu on 2012-04-09
> **dylan07 said:**
> This worked for me:
  ```
gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true' 
```
  It disables the locking altogether

Thanks.

Fixed.

The screen goes dark but a mouse movement awakes it again.

No password required.

---

