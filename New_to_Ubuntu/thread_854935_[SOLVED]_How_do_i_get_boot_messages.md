---
title: "[SOLVED] How do i get boot messages"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Pierrot Lafouine on 2008-07-10
Hi all
I noticed this afternoon, when I reboot, error messages from drivers.
Now I want to fix that, I'm not able to get messages when Ubuuntu boot.

How do I enable message display when Ubuntu boot ?

---

### Post by bhadotia on 2008-07-10
Press ctrl+alt+f1.. And press ctrl+alt+f7 to get back to splash screen (I think- haven't tried it - my boot splash does not work at all :))

---

### Post by llamakc on 2008-07-10
OP: do you want the scrolling info underneath the progress bar, or do you want to return to a more traditional and informative console boot (sans grub's splash) method?

---

### Post by tjwoosta on 2008-07-10
this isnt my thread but i would like to know how to get the scroling info under the progress bar

---

### Post by Pierrot Lafouine on 2008-07-10
Thanks,
It worked

---

### Post by Pierrot Lafouine on 2008-07-10
> **llamakc said:**
> OP: do you want the scrolling info underneath the progress bar, or do you want to return to a more traditional and informative console boot (sans grub's splash) method?

Hummm, not sure I understand the question.
What are the others messages I can enable will Ubuntu boot ?
Thanks

---

### Post by bhadotia on 2008-07-10
@> this isnt my thread but i would like to know how to get the scroling info under the progress bar 	  	
Use the  startup manager to enable text during the boot.

---

### Post by llamakc on 2008-07-10
```
sudo apt-get install startupmanager
```

---

### Post by tjwoosta on 2008-07-10
thanks guys

---

### Post by tjwoosta on 2008-07-10
ok i got one problem


this has been going for about 10 minutes now

---

### Post by Pierrot Lafouine on 2008-07-10
> **tjwoosta said:**
> ok i got one problem


this has been going for about 10 minutes now

Hummm with a problem like this, I think it would worth for you to start a new thread.

Thanks

---

### Post by iaculallad on 2008-07-10
> **tjwoosta said:**
> ok i got one problem


this has been going for about 10 minutes now

On a regular SUM post-configuration task, it would only take about 3-5 seconds to save changes. In you're case, if you observe that it did not create the changes you had set up on SUM's configuration, you could still revert back to your old menu.lst settings.

*When you first execute SUM, it saves a copy of your current menu.lst file as /boot/grub/menu.lst.backup*

To revert changes:

```
sudo mv /boot/grub/menu.lst.backup /boot/grub/menu.lst
```

---

### Post by tjwoosta on 2008-07-10
> Hummm with a problem like this, I think it would worth for you to start a new thread.

Thanks 

not necessary, 

it seems it only happens when i try to enable the text at boot, so i just wont have text at boot (not a big deal)

---

### Post by bhadotia on 2008-07-10
It takes some time sometimes :)

---

