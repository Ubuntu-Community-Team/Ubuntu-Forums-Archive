---
title: "Re-installing method."
date: 2008-06-27
forum: New to Ubuntu
---

### Post by pudding on 2008-06-27
Hi,

I installed Kubuntu, and want to switch to Ubuntu. I installed Kubuntu on an empty second hard disk, with WinXP on the primary, and would like to remove that and put Ubuntu on the secondary instead. Do I need to uninstall Kubuntu, or can I simply put the Ubuntu CD in and format and install and the GRUB loaded will change from offering Kubuntu to Ubuntu? Dont want to just reinstall then mess up the GRUB menu etc..

Thanks for any help.

---

### Post by iaculallad on 2008-06-27
On your terminal:
```

sudo apt-get install ubuntu-desktop
```

---

### Post by nothingspecial on 2008-06-27
```
sudo apt-get install ubuntu-desktop
```

will give you the option of logging into Ubuntu or Kubuntu:)

---

### Post by mcduck on 2008-06-27
> **pudding said:**
> Hi,

I installed Kubuntu, and want to switch to Ubuntu. I installed Kubuntu on an empty second hard disk, with WinXP on the primary, and would like to remove that and put Ubuntu on the secondary instead. Do I need to uninstall Kubuntu, or can I simply put the Ubuntu CD in and format and install and the GRUB loaded will change from offering Kubuntu to Ubuntu? Dont want to just reinstall then mess up the GRUB menu etc..

Thanks for any help.

You do not need to make a new install at all. Ubuntu and Kubuntu are the same operating system, the only difference is the desktop environment and default applications included on the install disk.

To get Uubuntu desktop just install theb "kubuntu-desktop"-package with Synaptic, or run the following command:

```
sudo apt-get install ubuntu-desktop
```

Youc an select which desktop environment you want to use at the login screen, and later on you can uninstall ubuntu-desktop & it's programs if you feel like that.

---

### Post by Elfy on 2008-06-27
> will give you the option of logging into Ubuntu or Kubuntuand an extremely full menu once you have both installed :)

If you do want to just go for the ubuntu install - do as before and use the manual partition method, then choose the existing partition to install to.

---

### Post by pudding on 2008-06-27
Ok thanks for the replies. Im not connected to the net as I didnt get my wireless card to work in Kubuntu. Will that command from the terminal work?

---

### Post by mcduck on 2008-06-27
No, sorry, it wont. You need to be connected to internet, otherwise the package management will have quite a hard time trying to download the packages from Ubuntu's servers.. ;)

In that case you have no othe roptions than to do a full new install with the other disk.

---

### Post by Archmage on 2008-06-27
As far as I know you could use the alternate Ubuntu-CD as an additional source for packages and this way install ubuntu on your kubuntu.

---

