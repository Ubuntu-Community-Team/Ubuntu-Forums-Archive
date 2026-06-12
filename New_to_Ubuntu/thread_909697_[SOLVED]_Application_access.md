---
title: "[SOLVED] Application access"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by mrwilson on 2008-09-03
Hello
I cannot access the folowing applications:
Hardware manager

I cannot access Synaptic Package Manager

When trying to install software than makes it own directory I get a permission denied and the install will not occur

When using sudo or other commands I get the following error on terminal "Unable to resolve hot brad-desktop" (a frequent message when trying to do most anything)for instance I tried to type in "sudo apt-get install ubuntu-restricted-extras" and it would not resolve my desktop, asked for my password and then just went back to the brad@brad-desktop~

I cannot configure the devices in network tools(eth0 etc)

Whenever I try to run an administrative application such as the ones noted above it trys to open the app for around 7-10 seconds then quits completely.

there are apps I can open such as Network, although I have given up trying to get wireless access on that computer.

Do I possibly have a bad install?  Lack of permissions?  I am using the latest download of Ubuntu (one week ago) and am dual booting with XP.XP works pefectly and booting into ubuntu also works perfectly

Thanks for your considerations

I did check ID, it said 114(admin) 4(adm)

---

### Post by cwsnyder on 2008-09-03
Can you sign in on Terminal as 'su'?  This should ask you for your user password, and if valid, sign you in as root, sort of a semi-permanent sudo.  **_Do this with extreme care and exit the 'su' as soon as possible._**  IF you can get to a root terminal as 'su', try getting into System >> Administration >> Users and Groups.  Check if your user name is listed as part of 'sudoers' group.  If not, unlock the listing and add your user name to 'sudoers', along with root, if root is not already on the list.

You might also try using the 'live disk' option of your install disk.  This is acting as if the root account has not been created, or your password has been changed.  After booting from the 'live' disk, try chroot to get into the installation and changing your password using the 'passwd' command.

---

### Post by mrwilson on 2008-09-03
Thank you.  I will try that.  I am reinstalling it now as i didnt think i would get an answer, so I will get back as soon as that is completed.  I have a feeling that this install will be the same so chances are good I will need this advice.  I have read many of the similar problems here and tried many of the solutions.  None seemed to work

I am not sure what Live Disk is

---

### Post by mrwilson on 2008-09-03
After the re-install I can access all that I should.  I am not sure what happened becuase originally when I first installed ubuntu I could access the hardware managers etc.  Then it jsut quit.

Thank you very much for your response, very much appreciated

---

### Post by free10 on 2008-11-17
> **cwsnyder said:**
> Can you sign in on Terminal as 'su'?  This should ask you for your user password, and if valid, sign you in as root, sort of a semi-permanent sudo.  **_Do this with extreme care and exit the 'su' as soon as possible._**  IF you can get to a root terminal as 'su', try getting into System >> Administration >> Users and Groups.  Check if your user name is listed as part of 'sudoers' group.  If not, unlock the listing and add your user name to 'sudoers', along with root, if root is not already on the list.

You might also try using the 'live disk' option of your install disk.  This is acting as if the root account has not been created, or your password has been changed.  After booting from the 'live' disk, try chroot to get into the installation and changing your password using the 'passwd' command.

I have the same thing happening after upgrading to 8.04, with synaptic not running from system>>Administration though I can get into terminal and bring up synaptic with sudo synaptic. but also system>>Administration>>hardware testing OR drivers fails. I also have a problem with the update manager when there are updates and I click on the notification icon. The update window opens showing them but then fails to function if I click on anything even trying to close it. I have been getting the updates by using the terminal since the icon update fails to work right.

I tried typing just SU into terminal and then my password and got back "su: Authentication failure", so SU fails though it doesn't fail using sudo synaptic, after saying  unable to resolve host dwight2-desktop and then asks for password which it then recognizes as correct. 

If I just type sudo then I get back this..
dwight2@dwight2-desktop:~$ sudo
sudo: unable to resolve host dwight2-desktop
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

Whatever all that means. Got any ideas?? Thanks Dwight

---

