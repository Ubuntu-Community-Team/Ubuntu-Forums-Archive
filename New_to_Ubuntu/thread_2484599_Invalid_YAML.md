---
title: "Invalid YAML"
date: 2023-03-03
forum: New to Ubuntu
---

### Post by luca310 on 2023-03-03
Hello,

I'm very new to Ubuntu and I'm trying to set up an ubuntu server for the first time now. I'm struggling with connecting to my wifi though.
When trying to apply the netplan I get the following error:


Invalid YAML: inconsistent indentation:
password: "..."
^

I'm aware that YAML files are very strict in terms of indentations, but I followed an instruction online so I don't really get why it doesn't work for me. Can somebody help me?

I attached my config as a Picture.

---

### Post by MAFoElffen on 2023-03-03
it would help 'better' to copy it to a usb drive, then post the text of the contents of the file within code tags.... That way we could check for tabs or inconsistent spacing... Which that error is all about.

The NetPlan example given for wifi RE: [https://netplan.io/examples](https://netplan.io/examples)
```

network:
  version: 2
  renderer: networkd
  wifis:
    wlp2s0b1:
      dhcp4: no
      dhcp6: no
      addresses: [192.168.0.21/24]
      nameservers:
        addresses: [192.168.0.1, 8.8.8.8]
      access-points:
        "network_ssid_name":
            password: "**********"
      routes:
        - to: default
          via: 192.168.0.1

```
Translating that to yours , and keeping track of consistent spacing and indentation (I see yours varies). (note that I typically use 4-space indentation). Do not use tabs...
```

network:
    version: 2
    renderer: networkd
    ethernets:
        enp1s0:
            dhcp4: true
    wifis:
        wlp2s0b1:
            optional: true
            dhcp4: true
            access-points:
                "network_ssid_name":
                    password: "**********"

```
You could just copy/paste that into a file on a USB, then copy it to your .yaml file.

Recommendation after you get that working, is to make a copy of it somewhere, then change the IP's to static. The reason for a 'server' is that you can find it on your network, know where it is always, and use the server services. Hard to do that if the IP address changes by being dynamic, instead of being static. Make sense?

---

### Post by luca310 on 2023-03-04
How do I open the USB-Stick and copy the pasted text on there?

---

### Post by MAFoElffen on 2023-03-04
For Desktop to a file: Select text. Copy selection. Open your favorite editor. Paste the text to it. Save file onto your USB Drive.

To mount the USB to a server:
ID the USB thumb drive
```

$ sudo fdisk -l | grep '^/dev/' | grep -v 'loop'

/dev/sda1        2048    1128447    1126400   550M EFI System
/dev/sda2     1128448    1390591     262144   128M Microsoft reserved
/dev/sda3     1390592 1888827391 1887436800   900G Microsoft basic data
/dev/sda4  3842101248 3844114431    2013184   983M Windows recovery environment
/dev/sda5  3844114432 3907028991   62914560    30G Windows recovery environment
/dev/sda6  1888827392 3842101247 1953273856 931.4G Linux filesystem
/dev/sdb1        2048 1953515519 1953513472 931.5G Microsoft basic data
/dev/sdb2  1953515520 3907028991 1953513472 931.5G Linux filesystem
/dev/sdc1   2048 1953523711 1953521664 931.5G Linux filesystem
[COLOR=#ff0000]/dev/sdd1  8192 15523839 15515648  7.4G  b W95 FAT32[/COLOR]

```
Look at the size and filetype to ID the device as your USB drive.

Create a place to mount the drive on your server
```

sudo mkdir /media/usb-drive

```

Mount the drive to your server
```

sudo mount /dev/sdd1 /media/usb-drive

```

Check if the mount was successful
```

mount | grep /media/usb-drive

```

If so, then 
```

cd /media/usb-drive

```

...That's about as basic of instructions as I can get... Then do what you want. Afterwards, to unmount the drive
```

sudo umount /media/usb-drive

```

---

### Post by luca310 on 2023-03-04
So I did all this and now it says root@server:/media/usb-drive#: 

But how do I copy the pasted command in the text file now and paste it into the netplan, so the indentations are correct?

Also why does this all has to be so complicated lol

---

### Post by MAFoElffen on 2023-03-04
Find the name of the NetPlan file (that name varies)...
```

ls /etc/netpan/*.yaml

```
Copy the name down...

Then it would be similar to (bacause you saved the name as something in that file on the USB drive).
```

sudo cp /media/usb-drive/pasted_file_name.yaml /etc/netplan/original_file_name.yaml

```
Changing that to the appropriate file names...

That will overwrite the file...

Then 
```

sudo netplan generate
sudo netplan apply

```

---

### Post by luca310 on 2023-03-04
Thank you for your help so far. Did everything above, when I enter netplan apply it does nothing for a few seconds and then says "A dependency job for netplan-wpa-wlp2s0b1.Service failed. See 'journalctl -xe' for details. 
When I enter journalctl -xe it says "Timed out waiting for device /sys/subsystem/net/devices/wlp2s0b1."

Do you have any idea how to fix that?

---

### Post by MAFoElffen on 2023-03-04
Do:
```

ip addr

```
to get a list of the network devices and their status.

Dang. That should work, but may be affected by this current bug: [https://bugs.launchpad.net/ubuntu/+source/netplan.io/+bug/1906646](https://bugs.launchpad.net/ubuntu/+source/netplan.io/+bug/1906646)

---

