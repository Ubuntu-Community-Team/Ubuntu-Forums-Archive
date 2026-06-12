---
title: "Cannot login to machine any more! systemd-logind service fails"
date: 2017-07-29
forum: New to Ubuntu
---

### Post by linengmiao on 2017-07-29
&#8203;Ive installed ubuntu 16.04 on my laptop a few months ago and suddenly I can t get past the splash screen.
[Where I m stuck][1]


  [1]: [https://i.stack.imgur.com/mJv7v.jpg](https://i.stack.imgur.com/mJv7v.jpg)


I went through all this: [https://www.reddit.com/r/linuxquestions/comments/6qa7fg/ubuntu_1604_grub_recovery_mode_etcresolvconf_no/](https://www.reddit.com/r/linuxquestions/comments/6qa7fg/ubuntu_1604_grub_recovery_mode_etcresolvconf_no/)  


and [https://www.reddit.com/r/techsupport/comments/6qa9bk/ubuntu_1604_grub_recovery_mode_etcresolvconf_no/?utm_content=title&utm_medium=user&utm_source=reddit&utm_name=frontpage](https://www.reddit.com/r/techsupport/comments/6qa9bk/ubuntu_1604_grub_recovery_mode_etcresolvconf_no/?utm_content=title&utm_medium=user&utm_source=reddit&utm_name=frontpage)


in order to be able to execute in chroot:


sudo apt update


sudo apt upgrade


sudo apt-get dist-upgrade


But that didn't solve the issue. What can I do in order to be able to login into my machine again?


When disabling quite splash, this is what I see:


[https://www.dropbox.com/s/q92t5iudlkxgp8f/IMAG4976.jpg?dl=0](https://www.dropbox.com/s/q92t5iudlkxgp8f/IMAG4976.jpg?dl=0) and  [https://www.dropbox.com/s/o70k7383xbmql1q/IMAG4977.jpg?dl=0](https://www.dropbox.com/s/o70k7383xbmql1q/IMAG4977.jpg?dl=0)


Finally after some time it just stays here: [https://www.dropbox.com/s/74mr1s0oiw33esq/IMAG4978.jpg?dl=0](https://www.dropbox.com/s/74mr1s0oiw33esq/IMAG4978.jpg?dl=0)


It just stays there. What do you think?

---

### Post by scoutchorton on 2017-07-29
If you notice on the one picture, it says "Failed to start Login service". That would probably explain why you can't get past the splash screen to, well, login. As for the Reddit threads and the last picture, it looks like your networking service is broken too, which would explain why you can't connect to the internet. Do you ever get past the last picture in order to get to a command line? I'm not sure if the tty would require the login service (which I assume it would), in which you might need to do some other stuff in root. I'd say do some research about those two issues (systemd-logind.service and NetworkManager.service not starting).

---

### Post by linengmiao on 2017-07-29
No I never get past the last picture to get a cmd line. I am able to get a terminal and internet if I use a live CD otherwise not. I tried everything I could find online and nothing worked! That's why I m posting smth here.

---

