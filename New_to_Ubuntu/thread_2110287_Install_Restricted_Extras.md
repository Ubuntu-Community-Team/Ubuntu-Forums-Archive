---
title: "Install Restricted Extras"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by Dyronne on 2013-01-29
I was trying to install the restricted extras and at the end when the agreement came up I could not press the ok at the bottom. So i exited out of the terminal. Now when I try to redo the install I get this error: 

"E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

how do i finish the install????

---

### Post by monkeybrain2012 on 2013-01-29
> **Dyronne said:**
> I was trying to install the restricted extras and at the end when the agreement came up I could not press the ok at the bottom. So i exited out of the terminal. Now when I try to redo the install I get this error: 

"E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

how do i finish the install????

Just means that some other instances of the package manager or apt-get is running. Just wait a bit a try again.

---

### Post by ntzrmtthihu777 on 2013-01-29
I ran into this once before, if I remember correctly you need to run some dpkg command because it stopped in the middle of the install/update and its "stuck"

I forget the exact command, lemme have a look see.

---

### Post by deadflowr on 2013-01-29
When you get to the agreement again, use the tab and/or the arrow keys to navigate the yes and no and click it on the yes.

---

### Post by ntzrmtthihu777 on 2013-01-29
> **deadflowr said:**
> When you get to the agreement again, use the tab and/or the arrow keys to navigate the yes and no and click it on the yes.
Quite true, I did not understand that once when I was new to buntu, lol. Live and learn, that's what ya gotta do at times, learn from your mistakes.

---

### Post by oldos2er on 2013-01-29
> **Dyronne said:**
> how do i finish the install????

```
sudo dpkg --configure -a
``` then follow deadflowr's advice.

---

### Post by Dyronne on 2013-01-30
Ok thanks guys imma try that now......

---

### Post by CK000 on 2013-02-08
If you can not click the ok button due to the size of your screen: hold down the left [alt] key and move the mouse around until you can see the ok button to click it.

---

