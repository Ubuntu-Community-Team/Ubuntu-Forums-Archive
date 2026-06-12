---
title: "Synaptic is stuck after failing to install fancontrol(Ubuntu 16.04 LTS)"
date: 2016-04-27
forum: New to Ubuntu
---

### Post by matti123456 on 2016-04-27
This is my first time using Synaptic. I tried to install fancontrol and something went wrong, it is still trying to install fancontrol(i think), but it is stuck.

I took a screenshot of the situation, it has been stuck like this for some time.
[ATTACH=CONFIG]268672[/ATTACH]

---

### Post by Bucky Ball on 2016-04-27
Welcome. There is a very distinct message window right on top saying you have pressed control+c and that has stopped the operation. Are you sure you want to do that? Answer yes or no, the system is waiting for your input.

---

### Post by matti123456 on 2016-04-27
> **Bucky Ball said:**
> Welcome. There is a very distinct message window right on top saying you have pressed control+c and that has stopped the operation. Are you sure you want to do that? Answer yes or no, the system is waiting for your input.

I closed the installation window, everything seems to be fine and Synaptic indicates that fancontrol is now installed. That is bit confusing since the installation window said that ''Not all changes and updates succeeded''.

The message window you meantioned is there, because i copied the text and it popped up. I though it meant that the installation is still not finished and that is why i wanted to show it in the screenshot.

Still not sure, if i disrupted the installation and which parts were not updated/installed properly.

Edit:I tried sudo pwmconfig and it worked. So i guess there is no problem?

---

### Post by Bucky Ball on 2016-04-27
> **matti123456 said:**
> The message window you meantioned is there, because i copied the text and it popped up.

Ah, that must be it.

> **matti123456 said:**
> Edit:I tried sudo pwmconfig and it worked. So i guess there is no problem?

Looks that way. Do:
```

sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

... and see if it spits out any errors. If not, mark the thread as solved and sail on. ;)

Some apps can take a while to install before you're plopped back at the cursor. Perhaps the app itself needs a while to set up before then.

---

### Post by matti123456 on 2016-04-27
> **Bucky Ball said:**
> Ah, that must be it.



Looks that way. Do:
```

sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

... and see if it spits out any errors. If not, mark the thread as solved and sail on. ;)

Some apps can take a while to install before you're plopped back at the cursor. Perhaps the app itself needs a while to set up before then.

Thanks! Everything seems to be in order. :P

---

