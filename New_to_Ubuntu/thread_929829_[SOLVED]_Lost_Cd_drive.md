---
title: "[SOLVED] Lost Cd drive"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by keefy777 on 2008-09-25
After the latest update it seems that i have lost my cd drive to the point that it wont even open up, no lights on etc
any ideas

---

### Post by keefy777 on 2008-09-25
anyone please

---

### Post by kansasnoob on 2008-09-25
Hmmm, I'm clueless, but could you at least tell us what version of Ubuntu you're using? Is it Hardy Heron 8.04?

If it happened right after an update that indicates a problem with the OS rather than hardware ............. maybe:confused:

---

### Post by keefy777 on 2008-09-25
yes it is hardy heron 8.04 and i too believe that something has changed but haven't the know how to fix it  
Any ideas

---

### Post by Technoviking on 2008-09-25
Hmmm... even with a misconfiguration in Ubuntu you CD drive should still open if you press the button. 

1. Can you open the drive during the bios screen.
2. If you can't, have you checked the power and IDE(??) connections to the CD drive.

---

### Post by kansasnoob on 2008-09-25
Well, let's try some simple stuff.

Go to System > Administration > Software Sources and see what's ticked. Click on the updates tab and make sure that only Important Security Updates and Recommended Updates are "ticked".

Then go to Terminal (Applications > Accessories > Terminal) and copy-n-paste the following commands:

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

```
sudo apt-get -f install
```

Wait between each command until the "prompt" (like: lance@lance-desktop:~$) shows up again and post any errors that show up.

---

### Post by kansasnoob on 2008-09-25
> **Mike said:**
> Hmmm... even with a misconfiguration in Ubuntu you CD drive should still open if you press the button. 

1. Can you open the drive during the bios screen.
2. If you can't, have you checked the power and IDE(??) connections to the CD drive.

I appreciate the help! It seems like an odd coincidence:confused:

---

### Post by keefy777 on 2008-09-26
Ok hi all 
I have tried that to no avail nothing changed.
Is there a command i can put in to show any errors that have occoured

---

### Post by keefy777 on 2008-09-28
Just a quick update after a few resets it seems to have healed itself, which clarifies to me that my pc is a living entity that is prone to severe mood swings, and through gentile manipulation i have appeased the beast.

So thanks from me and Melissa the PC, to all who have mediated between me and her we are back on talking terms.

---

