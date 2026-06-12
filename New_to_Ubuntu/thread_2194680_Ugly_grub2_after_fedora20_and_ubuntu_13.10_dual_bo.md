---
title: "Ugly grub2 after fedora20 and ubuntu 13.10 dual boot"
date: 2013-12-19
forum: New to Ubuntu
---

### Post by ChandanIN on 2013-12-19
Hello,


Today I have installed fedora 20 with ubuntu 13.10 , But the boot screen looking ugly.
How can I customize grub2 after this.

Please help me .

Thank You

---

### Post by deadflowr on 2013-12-20
Did you customize grub before?

I'm guessing when you installed fedora, it install it's own version of grub.
customizing grub2 is basically the same, across distros.
(Of course there are a few key differences; such as, I wouldn't expect the debian theme to be installed on fedora)

You could look over [grub manual]("http://www.gnu.org/software/grub/manual/grub.html")


and of course this
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

### Post by alankon on 2013-12-20
Hi,

I recently found a great tool called "Grub Customiser" that provides a user-friendly way of making changes to grub.

sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer

---

### Post by deadflowr on 2013-12-20
> **alankon said:**
> Hi,

I recently found a great tool called "Grub Customiser" that provides a user-friendly way of making changes to grub.

sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer

ppa's don't work on Fedora.
That said, hopefully if the op wishes, the op can reinstall the grub version on Ubuntu and then add the ppa for Ubuntu.
How to do that(reinstall grub) is in one or the other of the links I posted.

---

### Post by fantab on 2013-12-20
> **ChandanIN said:**
> Hello,


Today I have installed fedora 20 with ubuntu 13.10 , But the boot screen looking ugly.
How can I customize grub2 after this.

Please help me .

Thank You

Fedora uses 'GRUB_THEME=' in /etc/default/grub, you can comment out the line with '#' and uncomment 'GRUB_BACKGROUND=' (see code below)
After which you have to update grub.

```


**#GRUB_THEME=**/boot/grub2/themes/demo/theme.txt
**GRUB_BACKGROUND**=/boot/grub2/themes/demo/terminal-background-workaround.png
```

OR....

Boot into Ubuntu and get back the control of grub.

```

sudo grub-install /dev/sd**X**
```
Replace '**X**' with appropriate HDD, like, /dev/sd**a** or /dev/sd**b**

---

