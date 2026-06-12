---
title: "shutdown screen"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by rburkartjo on 2011-10-15
stupid little question but when i shut down the screen that comes up think it is call xspalsh or usplash or whatever only takes up about 1/4 of my desktop the rest is blank. works fine but wonder why. been this way for awhile and how can i correct

---

### Post by rburkartjo on 2011-10-16
any ideas?

---

### Post by jtarin on 2011-10-16
Can you describe what you see as a splash picture?

---

### Post by rburkartjo on 2011-10-16
jt it is the same as my splash screen the one that comes on before the login screen comes on. the one you get after you hit restart or shutdown (think it is called the usplash screen) before that command is carried out. except it is always about 1/4 the size of my monitor. the splash screen is always full sized.

---

### Post by jtarin on 2011-10-16
If you have Nvidia or ATI graphic card you might try [this fix.]("http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/") BTW it's called Plymouth.

---

### Post by rburkartjo on 2011-10-17
jt i need to fine tune the script it might work however how do i disable this script. somehow the program startup manager affects this and it and disabled that program. i need to disable your script re install startup manger and play with it. tks will let you know

---

### Post by rburkartjo on 2011-10-17
only get text now when i startup and shutdown(no splash screen or shutdown screen at all) but at least everything else is working and i can log in

---

### Post by rburkartjo on 2011-10-17
get this error when i try to run startup manager from terminal
does load just get this error report

```

ray@ray-GC660AA-ABA-SR5123WM:~$ su-to-root -X -c /usr/sbin/startupmanager
Grub2 detected
Usplash not detected
Splashy not detected
Found background image: good.jpg
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Linux Mint Xfce Edition (1) on /dev/sda6
done
Traceback (most recent call last):
  File "/usr/sbin/startupmanager", line 54, in <module>
    main()
  File "/usr/sbin/startupmanager", line 51, in main
    SumGui()
  File "/usr/share/startupmanager/gtk_frontend.py", line 193, in __init__
    self.setup_widgets()
  File "/usr/share/startupmanager/gtk_frontend.py", line 202, in setup_widgets
    self.set_shared_grub_widgets()
  File "/usr/share/startupmanager/gtk_frontend.py", line 223, in set_shared_grub_widgets
    self.timeout_spinner.set_value(self.grub.get_timeout())
  File "/usr/lib/pymodules/python2.7/bootconfig/grub.py", line 91, in get_timeout
    timeout = utils.extract_number(line)
  File "/usr/lib/pymodules/python2.7/bootconfig/utils.py", line 64, in extract_number
    match = number_filter.search(line)
TypeError: expected string or buffer
ray@ray-GC660AA-ABA-SR5123WM:~$

```

---

### Post by rburkartjo on 2011-10-17
i had made the following excuteable.
so just messing around tried to uninstall by running

sudo rm /home/ray/Desktop/fixplymouth-natty.txt
however even though i removed it from the desktop it is not uninstalled
just messing around there is no big hurry

---

### Post by rburkartjo on 2011-10-17
okay since i really never deleted the script just put it back on my desktop

---

### Post by rburkartjo on 2011-10-19
still wondering if anyone know how to disable this script. just cant seem to figure out. it is running as a startup bin/bash script somewhere.

---

### Post by rburkartjo on 2011-10-19
here is the script output
#!/bin/bash
# ----------------------------------
# Author: D0rkye
# Homepage: [http://d0rkye.zsenialis.com/](http://d0rkye.zsenialis.com/)
# Most code probably by kyleabaker: [http://kyleabaker.com/2010/07/11/how-to-fix-your-ubuntu-boot-screen/](http://kyleabaker.com/2010/07/11/how-to-fix-your-ubuntu-boot-screen/)
#
# Fix for Ubuntu 11.04, for BURG, and some extra bloat by Paolo Bernardi ([http://paolobernardi.wordpress.com/](http://paolobernardi.wordpress.com/))
# ----------------------------------

# Usage: install_if_not_installed package_name
function install_if_not_installed
{
	PACKAGE="$1"
	INSTALLED=$(dpkg -L "$PACKAGE" > /dev/null 2>&1 && echo OK || echo KO)
	if [ "$INSTALLED" == "KO" ]
	then
		sudo apt-get install "$PACKAGE" -y
	fi
}

# Usage: contains regexp file
function contains
{
	REGEXP="$1"
	FILE="$2"

	grep "$REGEXP" "$FILE" > /dev/null && echo OK || echo KO
}

install_if_not_installed v86d
install_if_not_installed hwinfo

sudo hwinfo --framebuffer
echo "---------------------------------------------------------------"
echo "Please enter the best resolution from the list above"
echo "It usualy looks like this >>Mode 0x0323: 1024x768 (+4096), 24 bits<<"
echo "And you have to enter it like this >>1024x768-24<<"
echo "---------------------------------------------------------------"
read resolution

sed 's/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"quiet\ splash\"/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"quiet\ splash\ nomodeset\ video\=uvesafb\:mode\_option\='$resolution'\,mtrr\=3\,scroll\=ywrap\"/g' /etc/default/grub > ./newgrub
sudo cp -f ./newgrub /etc/default/grub
rm ./newgrub

sed 's/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"quiet\ splash\"/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"quiet\ splash\ nomodeset\ video\=uvesafb\:mode\_option\='$resolution'\,mtrr\=3\,scroll\=ywrap\"/g' /etc/default/burg > ./newburg
sudo cp -f ./newburg /etc/default/burg
rm ./newburg

sed 's/\#GRUB\_GFXMODE\=640x480/GRUB\_GFXMODE\='$resolution'/g' /etc/default/grub > ./newgrub
sudo cp -f ./newgrub /etc/default/grub
rm ./newgrub

if [ "$(contains uvesafb /etc/initramfs-tools/modules)" == 'KO' ]
then
	sudo echo "uvesafb mode_option=$resolution mtrr=3 scroll=ywrap" | sudo tee -a /etc/initramfs-tools/modules
fi

if [ "$(contains FRAMEBUFFER=y /etc/initramfs-tools/conf.d/splash)" == 'KO' ]
then
	echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
fi

sed 's/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"\(.*\)vt\.handoff\=7\(.*\)\"/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"\1\2\"/g' /etc/grub.d/10_linux > ./new10linux
sudo cp -f ./new10linux /etc/grub.d/10_linux
rm ./new10linux
sudo chmod +x /etc/grub.d/10_linux

sudo update-grub2
which update-burg > /dev/null 2>&1 && sudo update-burg
sudo update-initramfs -u
echo "The resolution should be fixed after a reboot"

---

### Post by jtarin on 2011-10-19
From the link I have given you there are instructions for reverting the script.....here is what is written but I suggest you read the "comments" section on that page yourself.

> Anyway, for now, to revert by hand the script changes you should:

1) edit /etc/default/grub (and /etc/default/burg if you use it) to restore the
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash” line (the script adds some other options involving uvesafb); if you still have some problems you could try adding “nomodeset” to the options list

2) remove the text “uvesafb mode_option=1024×768-24 mtrr=3 scroll=ywrap” from /etc/initramfs-tools/modules

3) remove the text “FRAMEBUFFER=y” from /etc/initramfs-tools/conf.d/splash

4) run update-grub and update-initramfs -u

---

### Post by rburkartjo on 2011-10-19
tks jt will mark solved when i get a chance to fix. really appreciate your help in trying to fix

---

### Post by jtarin on 2011-10-19
Your welcome. I hope things work out for you.:P

---

### Post by rburkartjo on 2011-10-19
jt just noticed that there is no default grub(that file is blank). however i made a copy before i installed and ran the script you referenced. if i just placed the backup copy in the default grub with is now blank and then ran sudo update-grub would that work. tks

---

### Post by jtarin on 2011-10-20
> **rburkartjo said:**
> jt just noticed that there is no default grub(that file is blank). however i made a copy before i installed and ran the script you referenced. if i just placed the backup copy in the default grub with is now blank and then ran sudo update-grub would that work. tksTry deleting the script then....[Just reinstall Grub.]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2")Then run update. This should repair your Grub install as it should be. Simply copying files for an application such as Grub is not a good idea.

---

### Post by rburkartjo on 2011-10-20
okay tks

---

