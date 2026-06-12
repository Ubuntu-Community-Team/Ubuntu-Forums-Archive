---
title: "Sound error?"
date: 2012-10-02
forum: New to Ubuntu
---

### Post by Yezinki on 2012-10-02
After install & before reboot it displayed an error " Sound card mixer......Fail" what does that imply?

Thanks.

---

### Post by chkneater on 2012-10-02
Does ALSAmixer display a soundcard at all?

You can open a terminal and ' sudo alsamixer ' should open alsamixer and you can see a display of all soundcards available.

If that doesn't work, check in you applications menu under sound/video or maybe system settings depending on your system, or try right clicking on the speaker icon, One of those ways should open alsamixer for you.

What did you install btw, and is the soundcard onboard or not?  If you have an external soundcard, the notification may have just been because your onboard card is blacklisted, which is good because if it's not, there could be conflict betweent the onboard and external cards.

Oh, wait, now I see you're using 12.04!!  Just report back your system and soundcard.  Also, in you /etc/modprobe.d/alsa-base-blacklist.conf is there anything blacklisted?

Report back with your system/distribution/card info and you'll get better help quicker.

---

### Post by Yezinki on 2012-10-02
Thanks chkneater for your reply.

Correct ALSAmixer does display it after the reboot.

---

### Post by daslinkard on 2012-10-02
So this is now resolved?  If so, please mark it as such.

---

