---
title: "Hibernating and switching between ubuntu and windows"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by Geoff16W on 2012-01-03
Now that I've made my Windows partition mount in Ubuntu as READ-ONLY does anyone see any problems with switching back and forth between operating systems after hibernating each system, rather than completely shutting down?

Thanks for your advice.

---

### Post by I_can_see_the_light on 2012-01-03
> **Geoff16W said:**
> Now that I've made my Windows partition mount in Ubuntu as READ-ONLY does anyone see any problems with switching back and forth between operating systems after hibernating each system, rather than completely shutting down?

Thanks for your advice.

Hibernating Ubuntu and then switching to windows shouldn't be any problem since Ubuntu will use your swap partition to store the active session. Every time you boot Ubuntu it will first check if it can restore a hibernated session. Windows will use hiberfile.sys or something like that to store your session but I have never tried to hibernate windows and boot something else.

---

### Post by Geoff16W on 2012-01-03
> **I_can_see_the_light said:**
> Hibernating Ubuntu and then switching to windows shouldn't be any problem since Ubuntu will use your swap partition to store the active session. Every time you boot Ubuntu it will first check if it can restore a hibernated session. Windows will use hiberfile.sys or something like that to store your session but I have never tried to hibernate windows and boot something else.

Well, I've done it and it appears to work. I'm under the impression I was only getting corrupted files because I was writing files to the Windows Partition from Ubuntu while Windows was in hibernation. Now that I've made the partition read-only, I feel like I will avoid that problem. 

Still maybe there is more going than I know.

Thanks for your response.
jw

---

### Post by I_can_see_the_light on 2012-01-03
> **Geoff16W said:**
> Well, I've done it and it appears to work. **I'm under the impression I was only getting corrupted files because I was writing files to the Windows Partition from Ubuntu while Windows was in hibernation.** Now that I've made the partition read-only, I feel like I will avoid that problem. 

Still maybe there is more going than I know.

Thanks for your response.
jw

I'll remember that if I ever find myself in your situation. Perhaps the best way to share files between Ubuntu and Windows is to either have a designated partition for that or to use Ubuntu One and Dropbox.

---

### Post by eGaTS on 2012-06-04
When I hibernate Vista, it boots immediately into a resume. Grub does not appear, nor can I access the Windows boot menu by pressing function keys. I would love to be able to do what you are describing in this thread, but I'm not sure where to start. What would be even better is if "Resume Windows from Hibernation" could be shown on the Grub boot menu as a separate option, along with the option to boot Windows normally, discarding the hibernation file. Oh, and hibernating Ubuntu and booting Windows works perfectly, of course.

---

### Post by inashdeen on 2012-06-04
First off, what is the difference between hibernate and shut down. secondly how do you switch between OS and yet still get the other on hibernate.


sorry , curious noob

---

