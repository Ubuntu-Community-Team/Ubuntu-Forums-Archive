---
title: "Grub boot menu configuration"
date: 2016-04-26
forum: New to Ubuntu
---

### Post by mike_m22 on 2016-04-26
Hello!

I am using Ubuntu 14.04 LTS with Grub 2.02. I would like to configure my boot screen, so that I have two options to select from (that will enable booting on different runlevels):

[LIST]
[*]runlevel 3
[*]runlevel 4
[/LIST]
At the moment I have two boot menu items to select from:

[LIST]
[*]*Ubuntu
[*]Advanced options for Ubuntu
[/LIST]
How to configure this list, so that I can select one of the two specified runlevels?

Thank you in advance.

---

### Post by ajgreeny on 2016-04-26
Welcome to the forums mike_m22.
I assume you must have copied your query from some typed source which has given it a strange tabulated format which I have removed.
Please type direct into the text entry box that is available for this in future, and please use the default formatting for text.

The following askubuntu page may help you with your query, though I have no experience of this, and I wonder why you want to boot to run level 3 and 4; is this a server?
Ask again if this does not make sense to you
[http://askubuntu.com/questions/228402/boot-to-runlevel-3](http://askubuntu.com/questions/228402/boot-to-runlevel-3)

---

### Post by mike_m22 on 2016-04-26
ajgreeny, thank you for your answer.
Sorry for formatting, I don't know what caused the issue as I was typing my post from the scratch.
I'd just like to figure out if it is possible to customize these boot options. However, the link you provided did not help me.

Maybe someone else has an idea?

---

### Post by grahammechanical on 2016-04-26
There is a Grub manual. It available as a downloadable PDF. I have not studied the Grub manual to the extent that I could pass an examination on the subject but I do not think the Grub can give you want you want. You may have to look elsewhere such as systemd.

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

[http://landoflinux.com/linux_runlevels_systemd.html](http://landoflinux.com/linux_runlevels_systemd.html)

Regards

---

### Post by mike_m22 on 2016-04-27
Finally I have figured out how to solve this issue.

There's a file /etc/grub.d/40_custom. In this file additional boot menu entries can be added. I copied the main menu entry ('Ubuntu' - responsible for running OS normally) from the /etc/default/grub.cfg file and pasted it to the 40_custom file. Then I added the runlevel numer 3 at the end of the line starting with 'linux...'. I also changed the name of this menu entry. Afterwards I copied this code piece one more time and I changed the data, so that numer 4 (4th runlevel) and the corresponding name were set.
When 40_common file was ready, I updated the grub.cfg by running the following command:
grub-mkconfig -o /boot/grub/grub.cfg
And that was it - after rebooting in my boot menu I could find two new entries reponsible for running OS on two specified runlevels.

See the link:
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

Thanks for hints!

---

### Post by oldrocker99 on 2016-04-27
Excellent. You solved your problem and posted how you solved it. It's forum etiquette to use the thread tools at the top to mark this thread [SOLVED]. Do that and all will be jake.

---

