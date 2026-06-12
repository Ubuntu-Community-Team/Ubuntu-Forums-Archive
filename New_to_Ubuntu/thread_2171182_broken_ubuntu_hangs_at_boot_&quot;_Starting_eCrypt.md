---
title: "broken ubuntu hangs at boot &quot;* Starting eCryptfs [fail]&quot;"
date: 2013-08-29
forum: New to Ubuntu
---

### Post by Alfalfawar on 2013-08-29
When I turn on my computer I can choose from the following.
[COLOR=#800080]Ubuntu, with Linux 2.6.38-16 generic [/COLOR]<-- this one hangs[COLOR=#800080][/COLOR]
[COLOR=#800080]Ubuntu, with Linux 2.6.38-16 generic (recovery mode)[/COLOR]
[COLOR=#800080]Previous Linux Versions [/COLOR]<-- I have tried these with the same results[COLOR=#800080]
Memory test (memtest86+)
Memory test (memtest86+,  serial console 115200)[/COLOR]

After selecting the first one on the list some stuff happens before it hangs with a list including "* Starting eCryptfs [fail]" and all the rest that I can still see on my screen are "[ OK ]" or there is nothing on the right side of my screen for them but most of those are just empty lines.

Recovery Mode.
I can login when I select "resume" option and it says "Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-16-generic x86_64)" with some other stuff underneath that but it doesn't take me to Ubuntu and instead just waits for me to type something else. ](*,)
I have also done the "dpkg" option while following some of the many instructions I have found on the internet before coming here.
"failsafeX" works for some reason but I have to do it that way every time?

Online Resources.
[https://help.ubuntu.com/lts/installation-guide/i386/rescue.html](https://help.ubuntu.com/lts/installation-guide/i386/rescue.html) I couldn't follow this one, it makes no sense. :confused:
[http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/](http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/) I followed the first part of this but then gave up when I noticed the eCryptfs failure, I always thought it was timidity that was the culprit behind this problem because it is always at the end of the list when it hangs.
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode) I tried to follow this but didn't know what to do after step 9. :confused:

---

### Post by Jonathan Precise on 2013-08-29
At the Grub prompt, add [FONT=courier new]nomodeset[/FONT] after [FONT=courier new]kernel... [/FONT][FONT=courier new]quiet splash[/FONT]. That should fix the problem.

---

