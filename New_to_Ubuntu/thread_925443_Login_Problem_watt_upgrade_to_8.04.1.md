---
title: "Login Problem w/att upgrade to 8.04.1"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Rob Charles on 2008-09-20
I tried to complete the upgrade to HH and got hung up along the way where it did not look like it completed and my machine froze. When I tried to log in next I got the message saying my home directory did not exist. Looking at other posts I tried this: 

"boot into a single user mode: when you boot, GRUB should launch either showing you a list of installed kernels or a message asking you to press ESC to see the meny. Press ESC if needed, then e to edit the boot lines (you should not be asked for password, or if you are, you should know that password -- bootloader password). Edit the kernel line, and at the end of the last word in the line, put one space and type single. Press ENTER and b which should now make your Ubuntu boot into a single user mode, into a maintenance runlevel, and you should be logged in as root without any passwords (this is why you should set a bootloader password, to prevent this from happening if somebody gets to your machine). Now that you're in, and know the username who's home directory is missing (let's call it username in this example), first create that missing home directory:
Code:
mkdir /home/username
then set the owner to be username (it's root by default if you create it as root user):
Code:
chown username /home/username

I guess this did not solve things, because, when I now get to the initial login screens and enter username/PW I am sent to a plain orange screen where I can do nothing as nothing else on the page loads.  Next I hit Ctrl-Alt-F1 and it seems to show I running Ubuntu 8.04.1 ubuntu tty1 and let me login with my User/PW and I now have a terminal screen that ran checks and dumped me to the prompt [username]@ubuntu:[tilde]$

not sure what my next move should be here? In this terminal it sure seems to be recognizing my user/pw yet everytime I've gone through grub and recovery to check and fix/recover and get back to resume a boot when I enter the User/PW I get back to the blank orange screen. Thanks.

---

