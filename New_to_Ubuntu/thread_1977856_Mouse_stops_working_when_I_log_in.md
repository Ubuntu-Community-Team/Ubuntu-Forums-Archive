---
title: "Mouse stops working when I log in"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by lynx5 on 2012-05-10
Once I type my password and log in the mouse freezes in place and I cannot move it

What can I do to fix this?

I'm on 12.04

Thanks for any help

---

### Post by PhantomTurtle on 2012-05-10
> **lynx5 said:**
> Once I type my password and log in the mouse freezes in place and I cannot move it

What can I do to fix this?

I'm on 12.04

Thanks for any help

Does it actually login or is the whole system frozen(can you still use your keyboard to navigate and use Ubuntu). Try installing updates, maybe it is already fixed.

---

### Post by lynx5 on 2012-05-10
Its only the mouse. I installed updates, but the problem remained

---

### Post by hansdown on 2012-05-10
Welcome to the forum, lynx5.

Is this a wireless mouse?

Could you please give details of make and model?

---

### Post by lynx5 on 2012-05-10
No, I am on a laptop. It was working usually fine before this, but the pointer did rarely freeze

---

### Post by hansdown on 2012-05-10
> **lynx5 said:**
> No, I am on a laptop. It was working usually fine before this, but the pointer did rarely freeze

O.K.

Which laptop are you using?

---

### Post by lynx5 on 2012-05-10
MSI, what other specs do you need?

---

### Post by hansdown on 2012-05-10
> **lynx5 said:**
> MSI, what other specs do you need?

Sorry. I should have asked for more info.

eg; u100, etc.

---

### Post by papibe on 2012-05-10
Hi lynx5.

I know it's a long shot, but I think you're suffering [this]("https://bugs.launchpad.net/ubuntu/oneiric/+source/gnome-settings-daemon/+bug/868400") bug.

Try opening a terminal (Ctrl+Alt+T), and try this:
```
synclient Touchpadoff=0
```
The mouse movement should return immediately. If that doesn't work, this is the other recommended solution:
```
sudo killall -u lightdm syndaemon
synclient Touchpadoff=0

```
I hope that helps, and tell us how it goes.
Regards.

---

### Post by HunterDX77M on 2012-05-10
I had the exact same problem and it fed me up. Here is a link to a thread I had about.

[http://ubuntuforums.org/showthread.php?t=1915057]("http://ubuntuforums.org/showthread.php?t=1915057")

There's not that much here, but one of the things that at least made it a little easier was knowing that I didn't have to completely restart my computer every time that it happened (see the thread for more details). Also, when I didn't feel like restarting, I usually took out my wireless mouse to get things done.

---

### Post by lynx5 on 2012-05-10
Sorry I don't know what my make and model is...  

I tried synclient Touchpadoff=0  

there was no response in terminal.

sudo killall -u lightdm syndaemon 

gave me syndaemon: no process found

by the way 

sudo restart lightdm brings me back to the login page and thus fixes the problem, but once I log back in the pointer freezes again.

---

### Post by lynx5 on 2012-05-10
I fixed the problem somehow, But i think its only temporary.  there is a button that disables the trackpad, it shows whether it is on or not on the screen when I press it too. I realized it had inversed somehow, so I pretty much pressed it over and over until the pointer unfroze  the strange thing is that it is in the on position, as in it say the trackpad is disabled, but it is working now..

---

