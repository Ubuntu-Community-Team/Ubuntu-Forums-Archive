---
title: "No icons after update to latest version of Ubuntu"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by Faudyen on 2011-10-18
Let me apologize I was following a thread last night and am not able to find it this morning.

My wife got an update from Ubuntu to upgrade to the latest version.  She did and after reboot the computer booted up to a white box with her user name and laptop model.  It is a Dell D430.

What I did...

ctrl alt f1 
logged in command line
sudo apt-get remove lightdm
sudo apt-get install lightdm

This brought a white pop up box to choose lightdm or gdm(I think, at work now)
I choose lightdm and then reboot
The computer did properly boot up this time and she was able to log in as normal but there are no icons on the desktop, no icons for wifi etc.

Should I try going back to the command line and then uninstalling lightdm again then re installing it and choosing the other option?
or is there something else that maybe I should try to get the icons back

Thank you in advance and best regards,

Faudyen

---

### Post by computerandu on 2011-10-18
Resetting Unity might help...

---

### Post by Faudyen on 2011-10-18
Hello,

I am not sure how to do that, even though Unity was in release we were using my wife switched it back to the old interface because she didnt like Unity so I have never used it.

If you could explain using shortcuts that would help since I have no icons.

Thank you for your help thus far.

---

### Post by computerandu on 2011-10-18
Here is how to reset Unity:

[http://www.computerandyou.net/2011/06/23/how-to-reset-unity-to-get-rid-of-messed-up-compiz-setting/](http://www.computerandyou.net/2011/06/23/how-to-reset-unity-to-get-rid-of-messed-up-compiz-setting/)

And if you do not like Unity you might want to switch to Gnome 3. Here is how to do that:

[http://www.computerandyou.net/2011/10/16/how-to-install-gnome-3-in-ubuntu-11-10/](http://www.computerandyou.net/2011/10/16/how-to-install-gnome-3-in-ubuntu-11-10/)

Hope that helps.

---

### Post by Faudyen on 2011-10-19
Well its seems that Unity is the problem since Gnome 3 works fine. I guess the suggestion here would be that if you have an older laptop to not upgrade to 11.10 and Unity will not support it.

---

### Post by computerandu on 2011-10-19
You might want to check whether your old computer support Unity...if not then you should settle for Unity 2D or Gnome 3...

---

