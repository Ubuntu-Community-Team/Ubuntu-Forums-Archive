---
title: "Log in problem with Ubuntu 14.04 LTS"
date: 2015-06-08
forum: New to Ubuntu
---

### Post by kai-ahnig on 2015-06-08
Hi,

I am a newbie and have installed Ubuntu only recently.

System = Lenovo ThinkPad X300 [vintage [IMG]http://ubuntuforums.org/images/icons/icon11.png[/IMG]] with 2 HDD (1 x Samsung SDD 64GB with W7 [factory setup] + newly installed Hitachi 500GB [instead of DVD-writer]).

As the SSD was almost full, the Ubuntu installation procedure offered an installation on the Hitachi only.

I went through the whole process, adjusted the partition of the Hitachi to 350GB Windows & 150GB Ubuntu (all done and managed by the Ubuntu process) and eventually had to change the boot sequence in the BIOS as GRUB obviously has been installed on the Hitachi (and not as I have expected on the SSD) only.

When starting the system with boot sequence set to HDD 0 (SSD) no GRUB menu appears and the laptop starts with W7 (as usual)
Changing the BIOS so the Hitachi becomes the 1st drive, the GRUB menu pops up and let me choose between certain Ubuntu's and W7 [W7 works as ever]

When the Ubuntu welcome screen shows up and I try to log in, it first takes the password BUT returns to the welcome screen again. No message whatsoever. BUT entering a wrong password creates an error message. So it seems the password is correct but not accepted for what ever reason. I have changed the password successfully following a description on AskUbuntu but it does not make any difference.

The only message that found my interest appears (sometimes) during the startup phase saying that "a device could not be mounted and I should either wait, hit S (for skip?) or M (for manual mounting) and that's it. This message disappears after a few seconds.

Is there anybody out there who has a clue what's wrong?

Cheers

Kai

---

### Post by nerdtron on 2015-06-08
I'm not sure what is happening but are you hibernating windows? I so, you should not shutdown windows normally.

Another advise: IMPORTANT
If ever you re-install ubuntu (since you have installed it already). DO NOT choose "Replace Ubuntu" or "Replace Windows 7" or whatever along those line. These option will not only replace the OS you chosen but will also wipe all partitions on that hard drive. A lot of people post that problem here.

In case you' re-install Ubuntu your only option is the "Something Else" option which will allow you define which partitions to format and which partition to install Ubuntu.

---

### Post by kai-ahnig on 2015-06-09
Hi Nerdtron,

thanx for your reply. No I do not hibernate W7 and do not see any link between the W7 installation & Ubuntu as they are installed on 2 different drives.

btw, thanks for the hint with the new installation ....as this will probably the only solution for me.

take care

Kai

---

### Post by au10tic on 2015-06-11
at the login screen press ctrl+alt+f2 and see if you can log in to ubuntu via the terminal with the username and password you created during the installation. If you are able to login, type startx and see what happens. It should take you to the desktop, and we can probably further troubleshoot after confirming this.

You can then reconfigure lightdm. report back

---

### Post by kai-ahnig on 2015-06-11
Hi au10tic,

here we go. I followed your advice (Ctrl+Alt+F2) and that is the result after an obviously successful login

==================

Ubuntu 14.04.1 LTS knuth-ThinkPad-X300 tty2


knuth-ThinkPad-X300 login: knuth
password:
Last login: Thu Jun 11 12:28:56 CEST 2015 on tty2
Welcome to Ubuntu 14.04.1 LTS (GNU/LINUX 3.13.0-53-generic i686)


 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)


436 packages can be updated
189 updates are security updates


The programs included with the Ubuntu system are free software;
the exact etc., etc. etc....




knuth@knuth-ThinkPad-X300:~$


====================================


startx
xauth:  timeout in locking authority file /home/knuth/.Xauthority




REMARK: after approx. 2 minutes the following message shows up




..
No protocol specified


..
No protocol specified


etc.


xinit: giving up
xinit: unable to connect to X server: Resource temporarily unavailable


waiting for X server to shut down (EE) Server terminated successfully (0). Closing log file.


xinit: server error
xauth:  timeout in locking authority file /home/knuth/.Xauthority
knuth@knuth-ThinkPad-X300:~$
====================================

Does this help you any further?

Kai

---

### Post by au10tic on 2015-06-11
do the same steps above to login to the terminal, then type **sudo mv ~/.Xauthority ~/.Xauthority.backup** and then **sudo service lightdm restart **and try to log in again. If that doesnt work then try the below;

after login in;
[COLOR=#111111][FONT=Ubuntu]type [/FONT][/COLOR]**sudo apt-get install gdm** [COLOR=#111111][FONT=Ubuntu]Let it install and type [/FONT][/COLOR]**sudo dpkg-reconfigure gdm**[COLOR=#111111][FONT=Ubuntu] and follow the prompts to set it as your login manager, after confirming of setting gdm as your login manager press ctrl+alt+f7 to get back to the login screen and see if you can login. If you do, you can then go back to it run **sudo dpkg-reconfigure lightdm** and set that as your main login manager.[/FONT][/COLOR]

---

### Post by cariboo on 2015-06-11
Your problem looks more like a graphics driver problem. What graphics adapter does your system use?

---

### Post by kai-ahnig on 2015-06-12
Hi cariboo

the graphic card is a Mobile Intel 965 Express Chipset Family, 384MB Ram, card version 8.15.10.1867 08-06-2009

Cheers

Kai

---

### Post by kai-ahnig on 2015-06-12
Hi au10tic,

I did as you advised and got the following results:
after: sudo mv ~/.Xauthority ...... I get the message, that the call (start) of stat is not possible as the directory could not be found.

sudo apt-get install gdm worked flawless BUT did not change the behaviour of the log-in process. It is like an endless loop.

Any further idea?

REMARK: I answered also to cariboo's inquiry regarding the graphic card in place

Cheers

Kai

---

### Post by au10tic on 2015-06-13
im curious.. at the login prompt can you log in as guest or root? if not, are there any errors showing on your [COLOR=#111111][FONT=Ubuntu].xsession-errors file located in ~/ [home directory] while you are still able to login through the terminal type [/FONT][/COLOR]cat ~/.xsession-errors and post what you have there here.

---

### Post by kai-ahnig on 2015-06-13
Howdy,

I can log in as a GUEST. As I do not know how to log into ROOT, I pressed Alt+Ctrl+F2 and key-entered ROOT. I was told, that root is not installed BUT I can get it by using apt-get etc. So I did and ROOT was installed successfully. When I enter ROOT at the prompt I get the following message:
root: can't figure out DISPLAY, set in manually
In case you run a remote ssh session, restart your ssh session with:
ssh -Y

================
When logged in as a GUEST I do not have access to the HOME directory
================
When I enter "cat ~/.xsession-errors" after the prompt [knuth@knuth-ThinkPad-X300:~$] I get the message
file or directory not found

That's it - any further clue?

Cheers

Kai

---

### Post by cariboo on 2015-06-13
You can't login to a graphical desktop as root, and you don't need to be root for anything. The Ubuntu way is to use sudo to escalate a regular users privileges in order to do any administration tasks. What happens when you try to login with the user name you set when you did the installation?

---

### Post by kai-ahnig on 2015-06-14
After trying all kind of possible solutions I've found in different posts I finally reinstalled Ubuntu on my 2nd HDD (Hitachi). As already mentioned in a former post, allowing Ubuntu to erase & re-install itself on a HDD with a number of partitions means, that Ubuntu, without any information, declares the whole HDD as a Ubuntu partition and deletes ALL DATA - how strange is that?

Anyway, after the re-installation I had the exactly same behavior as before. Logging in "is a endless" loop, while logging in as Guest works fine.

Additional information:
My initial intention was to install Ubuntu on my first HDD (Samsung SSD). As the SSD was almost full, I moved all data etc. to the second HDD (Hitachi) to get sufficient space for the Ubuntu installation (approx. 15GB). When I started the installation process (via USB stick), Ubuntu offered me to REPLACE W7 instead of offering a parallel installation only. So I moved all data back and had Ubuntu installed on the second drive with the result mentioned above.

As the loop login problem seems to be well known would expect that someone has an enlightening idea;)

---

### Post by kai-ahnig on 2015-06-14
It is for sure not a satisfying solution, at least not for me, BUT after re-installing Ubuntu for a 3rd time AND this time without encryption & with automatic log-in, Ubuntu runs as expected.

So thanks to all the folks who tried to help me.

Cheers

Kai

---

### Post by cariboo on 2015-06-15
> **kai-ahnig said:**
> It is for sure not a satisfying solution, at least not for me, BUT after re-installing Ubuntu for a 3rd time AND this time without encryption & with automatic log-in, Ubuntu runs as expected.

So thanks to all the folks who tried to help me.

Cheers

Kai

It sure would have help if you had told us the above information from the very beginning.

---

### Post by danoc2 on 2015-07-01
Hi friends,

I am having the same problem as the OP. And in my case I must say I'm not into reinstalling without encryption and with automatic login, it partially deafeats the whole point of using ubuntu. So, can we re-open this discussion? I would really love to find the solution.

Thanks,
danoc

---

### Post by cariboo on 2015-07-01
> **danoc2 said:**
> Hi friends,

I am having the same problem as the OP. And in my case I must say I'm not into reinstalling without encryption and with automatic login, it partially deafeats the whole point of using ubuntu. So, can we re-open this discussion? I would really love to find the solution.

Thanks,
danoc

I would suggest starting a new thread, as your problem, even though it seems similar, may be something different from the op's. Go here:

[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

and click the Post New Thread button.

---

