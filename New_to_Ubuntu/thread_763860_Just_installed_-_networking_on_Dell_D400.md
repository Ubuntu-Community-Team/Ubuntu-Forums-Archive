---
title: "Just installed - networking on Dell D400"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by evadwolrab on 2008-04-23
As the title says, just installed on a Dell Latitude D400. Ubuntu 7.10.

I remember from having Xubuntu on it a few months ago that it needs to go and get the broadcom drivers or some such. I've had a look in the restricted drivers dialog, and it tells me the software source for bcm43xx-fwcutter is restricted (or words to that effect).

I installed the .deb from [here]("http://packages.ubuntu.com/gutsy/utils/bcm43xx-fwcutter"), but is still doesn't seem to be doing anything on the wireless front after a restart.

I've tried plugging into my router with an ethernet cable, it says it's requesting an address from the router for about a minute, then nothing.

Is this a common thing? I'm pretty sure when I first put Xubuntu on the same laptop, it had no problem going online through the ethernet cable and from there I could get the stuff I needed to get the wireless going.

**See update in post #4 - now using Hardy Heron.**

---

### Post by Het Irv on 2008-04-23
did you install the file: wl_apsta.o?
That file is the actuall firmware.

---

### Post by Michael.Godawski on 2008-04-24
When you have installed the fwcutter download the wl_apsta.o file.
Then open the Restricte Driver manager and check the box next to the broadcom entry. Now navigate to the wl_apsta.o file. The firmware should be installed now and active.

---

### Post by evadwolrab on 2008-04-24
Got it working last night on 7.10.

Ran the update to Hardy today and now when I select 'Enable' on the Broadcom driver, it tries to go online to get the firmware and fails, but doesn't give me the option to find the file locally.

Plus, wired internet still doesn't work on my Belkin router. Very annoying, but it has worked before on Xubuntu with an older router.

---

### Post by evadwolrab on 2008-04-24
Can a mod change the title of this thread to "Networking on Dell D400: No internet at all and can't install Broadcom" please?

Might get me some help and will be easier to find for other people in future IMO. Cheers. :)

---

### Post by evadwolrab on 2008-04-24
Pretty please? :p

---

