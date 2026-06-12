---
title: "[SOLVED] trouble with administration tools"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by fr.theo on 2008-06-16
I am having trouble with two functions under the menu "systems" in Ubuntu which worked previously.

1. Software sources

2. synaptic pakage manager


they worked previously, but now they won't load, any help on this matter would be much appreciated

FR. T.

---

### Post by iaculallad on 2008-06-16
Try to post the errors prompted to your when accessing your Synaptics/Software Sources if any.

---

### Post by fr.theo on 2008-06-16
there are no error messages, when I try to select "software sources" from the "system/administration" menu it begins to run but nothing happens after that.


it use to work, I have searched the web for any previous problems of this kind and so far I have found nothing.

do you have any advice.

---

### Post by iaculallad on 2008-06-16
What about trying it on your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

Or try opening it using:

```
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
```

---

### Post by rraj.be on 2008-06-16
Can you install any thing using terminal.

Try this at terminal and post the output.

```
sudo synaptic.

```

---

### Post by fr.theo on 2008-06-17
I have tried, but to no avail, system still idle?

---

### Post by rraj.be on 2008-06-17
ok.

whats the output of ```
sudo synaptic
``` in terminal.

---

### Post by fr.theo on 2008-06-17
it worked, the synaptic pakage manager popped up? I am not sure what I did.

how do I download the updates which Ubuntu displays on the top of the screen "the big red arrow pointing down with an exclamation mark in it"?

it has updates that I need, or so it tells me, what do I do.

once again thanks for you help really appreciate it.

---

### Post by fr.theo on 2008-06-17
rraj.be and Iaculallad thanks the update works it is currently doing it now, thank you both for your help.

---

### Post by rraj.be on 2008-06-17
> **fr.theo said:**
> it worked, the synaptic pakage manager popped up? I am not sure what I did.

how do I download the updates which Ubuntu displays on the top of the screen "the big red arrow pointing down with an exclamation mark in it"?

it has updates that I need, or so it tells me, what do I do.


Just double click that red button and it will open update manager.

Just click install updates.
> 
it has updates that I need, or so it tells me, what do I do.

once again thanks for you help really appreciate it.

We are glad to help you.

---

