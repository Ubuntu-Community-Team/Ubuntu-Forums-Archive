---
title: "Is my flash drive failing?"
date: 2012-07-31
forum: New to Ubuntu
---

### Post by venom104 on 2012-07-31
Okay I'm having an annoying problem with my flash drive. Whenever I eject it or use the option to "safely remove it", it remounts itself. I am unable to mount it after this because it gives me an error message.

Is my flash drive failing? It did not used to do this.

---

### Post by miegiel on 2012-07-31
> **venom104 said:**
> ...
 it gives me an error message.
...

And the error message is?

---

### Post by BBQdave on 2012-07-31
> **venom104 said:**
> Okay I'm having an annoying problem with my flash drive. Whenever I eject it or use the option to "safely remove it", it remounts itself. I am unable to mount it after this because it gives me an error message.

Is my flash drive failing? It did not used to do this.

If you are getting odd performance with the flash drive on other machines, time to move on and not trust the flash drive.

You could try a basic format such as FAT 16 or FAT 32 on your flash drive, see if the performance improves. Though as inexpensive as flash drives are, do not risk important data on it - might be time for a new flash drive :)

---

### Post by vexorian on 2012-07-31
> **venom104 said:**
> Okay I'm having an annoying problem with my flash drive. Whenever I eject it or use the option to "safely remove it", it remounts itself. I am unable to mount it after this because it gives me an error message.

Is my flash drive failing? It did not used to do this.
Does it unmount itself or does it stay mounted? (Do you notice a change in the interface between unmounting and it appearing again, or is everything the same?)

---

### Post by venom104 on 2012-08-01
> **miegiel said:**
> And the error message is?


The error message states...

"Could not display "computer:///",

Error: location is already mounted, please select another viewer and try again.

It seems to dismount fine, but then it's automatically remounted!

I think I'm going to bite the bullet and just order a new 16 GB one and save this 8GB one for emergencies or a USB based linux distro (like DSL).

---

### Post by venom104 on 2012-08-01
> **vexorian said:**
> Does it unmount itself or does it stay mounted? (Do you notice a change in the interface between unmounting and it appearing again, or is everything the same?)


Yes, the drive disappears from the "explorer" window, then reappears after half a second.

---

### Post by NikTh on 2012-08-01
Hi , 
what dmesg says ? 

plug in flash drive , open a terminal (fullscreen)and watch the messages . 

```
watch -n 1 "dmesg|tail -n 30"
```Thanks

---

### Post by venom104 on 2012-08-14
My new flash drive came in the mail. It does not do the same thing that my old flash drive did.


I'm guessing it was failing.

Marked as solved.

---

