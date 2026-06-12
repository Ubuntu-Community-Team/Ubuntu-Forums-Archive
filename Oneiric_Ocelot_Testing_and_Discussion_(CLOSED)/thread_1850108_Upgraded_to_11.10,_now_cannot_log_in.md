---
title: "Upgraded to 11.10, now cannot log in"
date: 2011-09-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by burpootus on 2011-09-25
Just upgraded from 11.04 to 11.10 using Update Manager. After the post upgrade reboot, I can no longer log in with my normal user account in LightDM. I've tried all of the options, Unity, Unity 2D, Recovery, etc. and once I enter the password and hit enter the screen goes black for a few seconds and then it returns to the LightDM screen. I can log in to Ubuntu using either the Guest account or a second Administrator account I had made previously (for my wife, who's never used it), so there seems to be hope here. How can I troubleshoot my main user account from this other account I'm logged into?

************
Found that /home/user/.Xauthority had permissions set to root:root and corrected.

---

### Post by ventrical on 2011-09-26
> **burpootus said:**
> Just upgraded from 11.04 to 11.10 using Update Manager. After the post upgrade reboot, I can no longer log in with my normal user account in LightDM. I've tried all of the options, Unity, Unity 2D, Recovery, etc. and once I enter the password and hit enter the screen goes black for a few seconds and then it returns to the LightDM screen. I can log in to Ubuntu using either the Guest account or a second Administrator account I had made previously (for my wife, who's never used it), so there seems to be hope here. How can I troubleshoot my main user account from this other account I'm logged into?

************
Found that /home/user/.Xauthority had permissions set to root:root and corrected.

If the working account you have now is administrator then you can delete your original account and create a new one.

---

