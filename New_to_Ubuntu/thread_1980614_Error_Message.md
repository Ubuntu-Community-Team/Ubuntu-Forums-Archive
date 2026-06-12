---
title: "Error Message"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by wheelsmith on 2012-05-15
The 'Update Manager' wanted me to perform an update and required me to reboot the system to initiate this update.

When it went through the reboot process it stopped at a page that had 7 or 8 items  which all finished with (OK) except the last item in the list which, I'm paraphrasing here because I don't recall the exact wording, but in essence it said "Starting Crash Reporter" and where all the other items said  (OK) this one said (Failed) and things came to a halt and didn't progress any further.

Finally with the help of a tech friend of mine, he instructed me to turn off the computer and then turn it back on and enter the 'Safe Mode' and then click on "Recover Mode' and then click 'Repair Packages'. Essentially that was the chronology of events.

What exactly happened and was this the best progression to a solution?

William

---

### Post by grahammechanical on 2012-05-15
It would be nice to know what version of Ubuntu you are using. I am sure that the requirement to reboot was to complete the update. I have never needed to reboot to initiate an update.

Sometimes an update brings with it a new Linux kernel image and a reboot is required before the new kernel takes over. This need to reboot for the updated packages to take effect is sometimes needed for other stuff.

The question is, what was it that was updated? There have been some issues lately with Nvidia drivers. And so I would expect that there be updates to Nvidia drivers as the issues are fixed. Perhaps a newer Nvidia driver was installed that was not fixed or that caused another problem.

Do you have an Nvidia card?

I recently had a problem where I could not update because some package or other was missing a Header, whatever that means.

In another instance I was unable to boot up Ubuntu because the Nvidia driver failed to installed. But then again I am running 12.10 development branch so I expect this kind of stuff.

Regards.

---

