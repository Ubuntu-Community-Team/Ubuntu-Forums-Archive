---
title: "Nvidia Xconf file"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by jpba on 2011-11-08
Hello. I was a Windows XP user, and i install the Ubuntu 11.10.
Everytinhk is nice, but i just cant configure my monitor. I receive this message...
"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

Can someone help me, please, and tell me the commands to fix this? 
Just put it here and i copy and paste in the terminal.

Another thing, Ubuntu doesn't recognize my monitor.
The monitor is a "HP D2837A" and my Nvidia Card is a G-Force MX440SE AGP8X"

Thank you

João
Lisbon

---

### Post by beew on 2011-11-08
Like the message says, run 'nvidia-xconfig' as root and reboot.

To do this, open a terminal and type
```
sudo nvidia-xconfig
```, submit your password when prompted. When it is done restart the computer.

---

### Post by jpba on 2011-11-08
Thanks, i will try it...

I receive this message:

"jpba@Ubuntu-Wireless:~$ sudo nvidia-xconfig
[sudo] password for jpba: 

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

jpba@Ubuntu-Wireless:~$

---

### Post by beew on 2011-11-08
> **jpba said:**
> Thanks, i will try it...

I receive this message:

"jpba@Ubuntu-Wireless:~$ sudo nvidia-xconfig
[sudo] password for jpba: 

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

jpba@Ubuntu-Wireless:~$

That's fine. It is the standard message, the error message says that the default xorg.conf was not complete so  it was renamed as a back up and a new one was created with the Nvidia info. Just reboot now.

---

### Post by jpba on 2011-11-08
Its works, but the Ubuntu doesn't recognize my monitor.
When i use the Windows XP, i could put the "inf" file, how do i do it in Ubunt?
The "inf" file is in this link: [http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=pt&prodTypeId=382087&prodSeriesId=298743&prodNameId=30495&swEnvOID=20&swLang=13&mode=2&taskId=135&swItem=vc-10499-1](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=pt&prodTypeId=382087&prodSeriesId=298743&prodNameId=30495&swEnvOID=20&swLang=13&mode=2&taskId=135&swItem=vc-10499-1)

Can i install it?

---

