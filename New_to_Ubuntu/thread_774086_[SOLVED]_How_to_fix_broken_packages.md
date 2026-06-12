---
title: "[SOLVED] How to fix broken packages?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by bhadotia on 2008-04-29
I am trying to install updates through the update manager , but when I click "install updates" the following message shoes up:

Could not apply changes!
Fix broken packages first.

Now I went into synaptics package manager to see what I could do . I selected edit>fix broken packages, and then again tried to install the updates through update manager after closing synaptics. But again the same message is showing up, what should I do?

Many thanks in advance.

---

### Post by Oldsoldier2003 on 2008-04-29
> **bhadotia said:**
> I am trying to install updates through the update manager , but when I click "install updates" the following message shoes up:

Could not apply changes!
Fix broken packages first.

Now I went into synaptics package manager to see what I could do . I selected edit>fix broken packages, and then again tried to install the updates through update manager after closing synaptics. But again the same message is showing up, what should I do?

Many thanks in advance.

```
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

Please post any error messages you receive.

---

### Post by bhadotia on 2008-04-29
Thanks, everything went fine.

---

### Post by bhadotia on 2008-04-29
Although everything went fine in the terminal there are still some updates that the update manager is showing and when I click "install updates " the same message shows up.  

Help please.

---

### Post by bigken on 2008-04-29
system/administration/synaptic use the custom filter to look for broken packages and remove them

---

### Post by bhadotia on 2008-04-29
There are no packages there. I reloaded but still it was empty.

---

### Post by bigken on 2008-04-29
sorry I cant be of more help have tried google :confused:

---

### Post by Oldsoldier2003 on 2008-04-29
could you post the output of ```
sudo apt-get check
```

---

### Post by pedro_orange on 2008-04-29
> **bhadotia said:**
> Although everything went fine in the terminal there are still some updates that the update manager is showing and when I click "install updates " the same message shows up.  

Help please.

```
sudo apt-get upgrade 
```

Should update all your packages.
Does the error only occur when you open Update Manager GUI? Or does the error appear in Synaptic?

---

### Post by bigken on 2008-04-29
try this in a terminal 
sudo dpkg --configure -a

---

### Post by bhadotia on 2008-04-30
Sorry for the late reply. After the restart everything seems to be alright now. Am downloading the updates at present.

---

