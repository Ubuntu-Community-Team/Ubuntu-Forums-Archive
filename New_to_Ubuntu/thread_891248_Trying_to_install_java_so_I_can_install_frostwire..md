---
title: "Trying to install java so I can install frostwire. I type su in terminal typing..."
date: 2008-08-15
forum: New to Ubuntu
---

### Post by Pascal11110 on 2008-08-15
I type su into the terminal and it asks for my password, but when I try to type it no letters show up and if I press enter it says authentication failure, any ideas?

---

### Post by picpak on 2008-08-15
That's how sudo works: just type in your password, hit enter and it will work.

You mean sudo, not su, right? Just wondering. :)

---

### Post by nicedude on 2008-08-15
su is not the way to go root

try sudo -i

or better yet just sudo before any command that requires root privileges.

---

### Post by starcannon on 2008-08-15
Password field is blind in terminal, they keystrokes are going in, just not showing in terminal; don't worry, its working as designed.

The easiest way to install java is through synaptic, search for "ubuntu-restricted-extras" without quotes and install those, you'll get java, and a bunch of other necessary extras.

If you want to do the same thing in the command line then:
```
sudo apt-get install ubuntu-restricted-extras
```

GL

---

### Post by iaskedalice09 on 2008-08-15
You're not downloading it, right? 'Cause it's in the repos

sudo apt-get install sun-java6-jre

When it pops up the licence, hit the right arrow key and hit enter to hit OK. Good luck!

*ETA by that first sentence I mean you CAN download it, but its just more efficient to do what's already in the repos. No disrespect intended sorry. :-)

---

### Post by Pascal11110 on 2008-08-15
thank you so much star cannon, works great

---

### Post by Pascal11110 on 2008-08-15
now it is stuck in the terminal on the license for java and won't let me press okay even when I press enter.

---

### Post by picpak on 2008-08-15
Try pressing space...

---

### Post by Pascal11110 on 2008-08-15
still didn't do anything

---

### Post by iaskedalice09 on 2008-08-15
Push the right arrow (looks like >) then hit Enter.

---

### Post by Pascal11110 on 2008-08-15
thank you that worked

---

### Post by crjackson on 2008-08-15
> **Pascal11110 said:**
> I type su into the terminal and it asks for my password, but when I try to type it no letters show up and if I press enter it says authentication failure, any ideas?

Were you able to grab frostwire from the link I posted?

---

### Post by Pascal11110 on 2008-08-15
I didn't try it, I just wen tot frostwire.com like someone else suggested.

---

