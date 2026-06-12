---
title: "CD burning and usb problems"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by shudders on 2008-07-24
Hey all,

This is my first time using ubuntu as desktop and I've managed to get most things working thanks to all of you here on the forum. :) I still feel like a complete beginner though.

However, there are two things I just can't figure out. 

1) USB-mounting. I'm running ubuntu hardy with a vmware windows guest. In order to get USB support in the guest I googled and found a solution. 
```

change /etc/init.d/mountdevsubfs.sh
remove comment from the following 4 lines starting with mkdir -p /dev/bus/usb/.usbfs

        #
        # Magic to make /proc/bus/usb work
        #
        mkdir -p /dev/bus/usb/.usbfs
        domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
        ln -s .usbfs/devices /dev/bus/usb/devices
        mount --rbind /dev/bus/usb /proc/bus/usb

```
After doing this USB worked in vmware. But now the USB stick doesn't mount in ubuntu. Is there a way to get USB support in both ubuntu and the vmware guest?

2) CD burning. I can burn fine through Nautilus, no problems at all. But when I try k3b or Brasero they get (what I assume) are permission problems. I have checked "access to cd burning" in user permissions for my account. I couldn't find any other solutions using google. Do I need to disable automounting of CDs? But if I do that, will I not get a problem with dvd playback later? (I'm using this box as a htpc with mythtv too.)

Any help is greatly appreciated. And if any more information is needed I will try my best to supply it. 

Thanks in advance.

---

### Post by unutbu on 2008-07-24
Regarding CD burning:
Go to System>Preferences>Removable Drives and Media.
Under the Storage tab edit the command used for Audio and/or Data CDs. Or you can disable it and launch you CD burning app manually.

This I believe is correct for Gutsy systems. I have a vague impression that things might have changed for Hardy, but I just can't recall. If it has changed, check in System>Preferences for a similar menu item.

PS. If k3b or Brasero do not work, here is a down-and-dirty solution which may get them working. When nautilus notices a blank CD, it launches a process called nautilus-cd-burner. If you kill these processes, then other CD burner apps should work.

To find the process ID (PID) numbers, type:

```
ps axuw | grep cd-burn
```

If you see something like this:
```

user   **15734**  6.6  1.7  39128 18072 ?        S    07:25   0:04 /usr/bin/nautilus-cd-burner
```

then type:
```

kill **15734**
```
The second column is the PID.

---

### Post by shudders on 2008-07-25
The layout is a bit different in hardy (Removable devices noly show cameras and handhelds), but now that I know what I'm looking for I*ll try and find it. 

I'll try your dirty solution asap though. :) 

Thanks!

Edit: I tried disabling the auto-burn in Nautilus --> Edit --> Settings and then burn with Brasero. But now I get a different error. :(

```

BraseroWodim stderr: Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 5

```

---

