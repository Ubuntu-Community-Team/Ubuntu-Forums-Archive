---
title: "Ubuntu fails to start"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by Falc7 on 2008-10-22
Hi
Recently ubuntu won't load up the desktop, it after GRUB and the short loading screen the computer goes blank and stays that way, any ideas on what i can do?
I think it might have been after an update, but i am not sure

---

### Post by mlentink on 2008-10-22
In your grub menu, you can choose either the recovery mode, or even a prior kernel. I would try that first.

---

### Post by didac on 2008-10-23
Or in the GRUB menu choose the normal entry, press 'e' to edit it, delete the words 'quiet' and 'splash' if they're there, press ESC, then 'b' to boot and watch the screen for messages.

---

### Post by Falc7 on 2008-10-24
The word quiet was there and i deleted it, but there was no change.

I will give a more detailed description of the problem:
I select ubuntu, i get the logo screen and the orange bar goes across, then it appears as if the computer goes into hibernation. The screen displays no signal, the little LED changes from green to orange (standby mode). And nothing else happens.

---

### Post by porchrat on 2008-10-24
could be an acpi issue.  Do what didac suggested, but instead add "noacpi" (without the "") after the word splash.

---

### Post by Falc7 on 2008-10-24
Just to clarify, the line i am editing is the kernal line right?

I tried the noacpi, but it didn't change anything as far as i can tell. It is strange, if i edit the kernal line, and i hit the reset button once the screen goes blank later, any changes i made to the line are not there again when i check in GRUB.

---

### Post by taseedorf on 2008-10-24
try this


delete the "quiet" line AND delete the "splash" line

---

### Post by Falc7 on 2008-10-25
I deleted that from the kernal line, but i didn't notice any changes to the load up, there were no messages on screen

---

### Post by Duck2006 on 2008-10-25
Did you try booting into recovery mode?

---

### Post by Falc7 on 2008-10-25
When i choose recovery mode, it gives me several options to repair dkpg and something else. I tried all 3 of those options and nothing seemed to help.

---

### Post by porchrat on 2008-10-25
> **Falc7 said:**
> Just to clarify, the line i am editing is the kernal line right?

I tried the noacpi, but it didn't change anything as far as i can tell. It is strange, if i edit the kernal line, and i hit the reset button once the screen goes blank later, any changes i made to the line are not there again when i check in GRUB.

The reason the changes don't stick is because you are editing the settings for this boot session only.  When the computer is reset it won't remember any changes.  It is best to mess around with it like that just in case it causes a serious problem, then all you need to do is reset and everything is fine again.

---

### Post by Falc7 on 2008-10-25
ah i see, thanks for telling me

I have checked those lines and i do not seem to get any errors before the computer goes into hibernation. If i have to reinstall ubuntu, what is a good program i can use to take the files of the ubuntu side of the computer onto the XP side while i reinstall ubuntu?

---

### Post by didac on 2008-10-27
If you can boot with the LiveCD, just mount your XP partition and your Linux partition, and start copying files. Usually you would copy those in your home folder. If file permissions are important, compressed them into a tar.gz ball which will keep permissions intact.

---

