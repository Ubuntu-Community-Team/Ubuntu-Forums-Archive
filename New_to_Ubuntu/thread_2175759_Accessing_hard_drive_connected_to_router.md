---
title: "Accessing hard drive connected to router"
date: 2013-09-20
forum: New to Ubuntu
---

### Post by palmgrower on 2013-09-20
I got a hard drive connected to router usb. Went on 192.168.1.1 and installed the hard drive. Opened Files, CTRL-L, entered smb://192.168.1.1. The hard drive icon pops up. Opened the hard drive. avi files are listed. Double click on an avi file. vlc opens but video doesn't play. What is missing? Thanks.

---

### Post by tgalati4 on 2013-09-20
There is an error console in vlc under Tools-->Messages.  Post anything that might be helpful.

You can also run vlc in a terminal and post those messages.

---

### Post by palmgrower on 2013-09-20
No messages. Zero errors.

one thing I noticed. It takes a long time to open drive, change view to list, open a folder. Every action takes a good minute. Thanks.

EDIT: I take it back. After 2 miinutes of waiting, finally I got something 
"filesystem error: failed to read (invalid argumument)"

---

### Post by nerdtron on 2013-09-21
How about try other paths such as sftp://192.x.x.x or cifs://192.x.x.x or maybe it is a nas share?

What is the model of your router? Does it have a Web GUI on where you configure the shared hard drive? Or is there anything on the router manual about accessing the hard drive?

---

### Post by DuckHook on 2013-09-21
Most router-based HDD couplings require you to activate the proper protocols. Then you must configure the HDD with proper users/groups/permissions. If improperly configured, you can see the HDD and even the files, but won't be permitted to access and/or change them.

1. Follow the instructions on your router's documentation to have the proper protocols activated: NFS and/or Windows CIFS.
2. Follow instructions to set proper users/groups/permissions to permit access for the desired user(s) or groups(s), including passwords.
3. Make sure that your client computers have the proper corresponding protocols. Example: I use NFS, so must have *nfs-common* installed. I don't use CIFS so can't help you there, but understand that all CIFS components are already installed by default in a standard Ubuntu install.

If the foregoing are installed and configured properly, only then can you access files. Steps 1 and 2 are usually done through the router's web interface. Step 3 must be done using the standard tools on your specific distro.

---

### Post by palmgrower on 2013-09-22
Thanks for the replies. The drive was not nas. Some of the replies are above my head. I followed this instruction:
[http://www.lancebledsoe.com/external-network-drive-ubuntu/](http://www.lancebledsoe.com/external-network-drive-ubuntu/)

Specifically,
sudo aptitude install smbfs
sudo mkdir /media/public
gksudo gedit /etc/fstab

add these two lines to fstab and save the file:

# Mount my network drive using these parameters
//192.168.1.1/Plugable_USB3_SATA_U3_92 /media/public smbfs guest 0 0

Plugable_...... was the name on the router setting screen from 192.168.1.1. There is a space after the name.

sudo mount -a

Now the hard drive appears as PUBLIC in media.
If anyone knows an easier way, please let me know.

Router: WD My Net N900
All my PC's are wired to the router. I haven't read the manual. My bad.

---

### Post by nerdtron on 2013-09-22
Those steps are "one time setup" only. You'll only go to those steps the first time you set it up on your computer. If you have already successfully mounted it using mount -a and the fstab entry is correct. There's no more work to do. This drive will be automatically mounted when you reboot your computer.

---

