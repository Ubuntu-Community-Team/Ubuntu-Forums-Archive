---
title: "Noob question but not sure how to explain in a title ( Help )"
date: 2018-07-04
forum: New to Ubuntu
---

### Post by scrubby18 on 2018-07-04
Hello fellow Linux users, sorry if I posted in the wrong forums, this is my first time using the ubuntu forms.


    I have been having an issue with Lubuntu 18, the issue being an boot issue and it will not allow me to get into the OS because it freezes after the grub menu but after some research, I think I have found what may have been causing the issue, there are a few people with the same laptop model, citation below but here is what may be causing the issue "*It appears to be a bug with the laptop driver, system tries to turn  on a keyboard backlight which doesn't exist, which freezes the system on  any boot after the first.  Apparently, this was introduced in kernel  4.1.3, and hasn't really even been acknowledged by the kernel devs.   There is a workaround listed that I have yet to try, and I'll post when I  get a chance.*" 

    So, in this thread, the guy talks about how this command or code (don't really know, I'm very new to Linux) apparently fixed it, here it is,*** sudo systemctl mask [EMAIL="systemd-backlight@leds\:dell\:\:kbd_backlight.servic"]systemd-backlight@leds\:dell\:\:kbd_backlight.servic[/EMAIL]e***  
Now, my question is how do I insert this, do I go into the grub menu, press e then insert the line or what? Any help will be appreciated. 

[https://ubuntuforums.org/showthread.php?t=2332063](https://ubuntuforums.org/showthread.php?t=2332063)

---

### Post by bodhin2 on 2018-07-04
sorry i am not a heavy - but - don't mess with stuff yet.  try rebooting and hold down the shift key! or else keep hitting the shift key.  this may the kernel bug i am dealing with as well as others.  it sucks.  last time i held the key from startup it took me to the bios/boot weird area or some such - hit enter and then hold down the shift.  this may vary.  but the shift trigger the continuation of the bootup.  one laptop is like this the other normal  i have not updated my wife's yet - will see what that brings later today.  welcome and hope this works - this is a new glitch and major as far as i am concerned and i have used linus since the start of ubuntu or even a bit before that.

---

### Post by scrubby18 on 2018-07-05
I managed to bypass the error by going into the grub menu by spamming  shift, once in, I pressed E onto Lubuntu, then added "  systemd.restore_state=0 " to the boot parameters and it bypassed the  issue, because with my laptop, it seems as it looks for something that  doesn't exist and doesn't know what to do so it hangs the system, but this fix has to be done every time I load up the OS lol

---

