---
title: "Startup Manager not saving"
date: 2011-12-28
forum: New to Ubuntu
---

### Post by PumaMania on 2011-12-28
Hello; I am running Ubuntu 11.10 on a Dell Inspiron N4110. I'm dualbooting Ubuntu and Windows 7, and I am trying to use Startup Manager to make Windows the default OS (but give the bootloader a 5 second wait for me to switch to Ubuntu when I want to. [oh hey that rhymed]) The 5 second wait period has changed, but Ubuntu is till the default OS, even though I have chosen Windows. Startup Manager even says Windows is the default but when I power on Ubuntu remains the default. Can anyone help me to fix this? Thanks :)

---

### Post by benpack101 on 2011-12-28
I would use the terminal.

Type in "sudo gedit /etc/default/grub" (now if you use a different text editor than gedit use that instead)

Then a text document will open up.

Go to the line GRUB_DEFAULT=

'0' represents the first displayed OS, '1' the second, and so on. Go ahead and make the change and then save. 

Then go back to the terminal and update the grub menu, "sudo update-grub" Upon your next restart your new default OS should be set.

Best regards!

---

### Post by drs305 on 2011-12-28
You can also give 'Grub Customizer' a try. It was designed for Grub 2 and in most cases works a lot better than Startup Manager, which was initially written for Grub Legacy. 

You can learn more about it by clicking the link in my signature line.

---

### Post by PumaMania on 2011-12-28
Thanks @drs305, the Grub Customizer worked perfectly! Thanks to @benpack101 as well. I didn't know how to do that before anyways so now I know :P

---

