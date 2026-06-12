---
title: "Windows doesn't have permissions to view USB stick on Ubuntu in network"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by AJP123 on 2011-11-05
Hi everyone,

I'm a complete newbie to Ubuntu, although I love the fact that it's a FREE operating system. Bear that in mind when you answer my question.

Basically, I'm attempting to create a headless server out of a netbook I picked up for free using Ubuntu 11.04 (would rather not upgrade). This arose from considering buying a NAS drive for all my server requirements (file sharing, printer sharing, iTunes server, remote access, etc), but then realising, because of the free netbook I acquired, I could potentially do the same thing using Ubuntu.

So I decided to test the simplest thing a server should be capable of doing - file sharing. It was working a breeze until I tried to view files on my USB stick plugged into the server on my Windows Vista computer. According to Windows Vista, it doesn't have the necessary permissions to use the USB stick. 

I've googled the topic a few times and have come across the following links [here]("http://www.tomshardware.com/forum/237494-50-windows-drive-ubuntu-ubuntu-windows"), [here]("http://nixliving.blogspot.com/2009/12/permissions-samba-sharing-external-ntfs.html") and [here]("http://www.pendrivelinux.com/sharing-files-between-ubuntu-flash-drive-and-windows/"). Trouble is, I don't really understand them. The second link involves installing pysdm, which wasn't hard using the command line, but then messing around with the FSTAB system configuration file, something I don't really want to do. 

Thus, what is the simplest and/or risk-free way of changing the permissions of the USB stick on Ubuntu so I can share it with Windows, with full permissions? I'd rather not mess with configuration files, if possible, and would prefer using a GUI to the terminal (coming from Windows, not very proficient with using the terminal at this stage), if at all possible.

Thankyou,
God bless,
Andy =)

---

### Post by HalfEmptyHero on 2011-11-06
Unfortunately you are going to have to edit the fstab. It's nothing scary, and it shouldn't break anything unless you modify what is already in there. That guide with pysdm was pretty detailed, I suggest following it. If you have any trouble with it, feel free to ask and I'll try and help you out.

If you are scared about editing the fstab, back it up first:

sudo cp /etc/fstab /etc/fstab_backup

That way if you mess something up you will be able to restore it using

sudo cp /etc/fstab_backup /etc/fstab

---

### Post by AJP123 on 2011-11-06
I'll give it another shot, thanks for the backup tip. I basically understand what those terminal commands do =D.

I remember trying to follow the guide you mentioned, but it didn't work for some reason. To clarify, when you manually change the FSTAB, that's just to tell Ubuntu to change the permissions of the actual device (identified by the UUID) as opposed to the mount point /dev/sdb1 or similar? How do you actually go about changing the permissions themselves for the actual device then? Do you need to use the GUI pysdm and check/uncheck specific boxes?

Thanks heaps for your help =)

---

### Post by HalfEmptyHero on 2011-11-07
> **AJP123 said:**
> I'll give it another shot, thanks for the backup tip. I basically understand what those terminal commands do =D.

I remember trying to follow the guide you mentioned, but it didn't work for some reason. To clarify, when you manually change the FSTAB, that's just to tell Ubuntu to change the permissions of the actual device (identified by the UUID) as opposed to the mount point /dev/sdb1 or similar? How do you actually go about changing the permissions themselves for the actual device then? Do you need to use the GUI pysdm and check/uncheck specific boxes?

Thanks heaps for your help =)

I've never used pysdm, and I personally think it's easier just to edit it by hand. There is a good guide on fstab [here]("http://www.tuxfiles.org/linuxhelp/fstab.html"), but I would recommend adding the following line to your fstab:

UUID=[your_disk_uuid] /media/flashdrive auto rw,auto,user,sync 0 0

Obviously you would subsitute [your_disk_uuid] with the uuid you get from issuing the blkid command from the terminal, and you can change /media/flashdrive to whatever you want the mount point to be. What this line does is, whenever your flash drive is mounted, it will be mounted to /media/flashdrive, the filesystem type will be automatically detected, it will have read and write permissions, it will be automatically mounted, you don't have to be root to read/write to it, and files will be copied to it right away.

There are a few ways to get this line into /etc/fstab. You can use a text editor like gedit to view it in a gui and paste the line

gksudo gedit /etc/fstab

You could also automatically append the line to it:

sudo su

echo "UUID=[your_disk_uuid] /media/flashdrive auto rw,auto,user,sync 0 0" >> /etc/fstab

exit

echo is the terminal command for printing text, and >> is a feature that allows you to pipe the output of a command to the end of a file. One > would replace the file completely, so make sure you use both.

---

### Post by AJP123 on 2011-11-12
So, I did what you said =)

However, upon ejecting and re-inserting my USB Stick into the Ubuntu 11.04 server, I get the following error message:

"Error

Unable to mount 8GB

Error mounting: mount exited with exit code 1: helper failed with:
mount: mount point /media/flashdrive1 does not exist".

Here, '8GB' is the name of the flash drive, and I used '/media/flashdrive1' as the mount point.

What are the causes of this? Is it that I can't name the mount point 'flashdrive1'? What restrictions are there on the names of mount points?

Thankyou,
Andrew.

P.S: My apologies for taking so long to do this. Uni has beckoned with exams.

Update: I also tried using the mount point 'fd1', with the same error. Any help?

---

### Post by AJP123 on 2011-11-18
> **AJP123 said:**
> So, I did what you said =)

However, upon ejecting and re-inserting my USB Stick into the Ubuntu 11.04 server, I get the following error message:

"Error

Unable to mount 8GB

Error mounting: mount exited with exit code 1: helper failed with:
mount: mount point /media/flashdrive1 does not exist".

Here, '8GB' is the name of the flash drive, and I used '/media/flashdrive1' as the mount point.

What are the causes of this? Is it that I can't name the mount point 'flashdrive1'? What restrictions are there on the names of mount points?

Thankyou,
Andrew.

P.S: My apologies for taking so long to do this. Uni has beckoned with exams.

Update: I also tried using the mount point 'fd1', with the same error. Any help?

Update: Apparently I have to make the mount point directory with "sudo mkdir /media/flash1". Makes perfect sense :D. So far, this is what I need to do:

```

sudo su
blkid
mkdir /media/[mount_point]
echo "UUID=[your_disk_uuid] /media/[mount_point] auto rw,auto,user,sync 0 0" >> /etc/fstab
exit

```

Then go into the USB drive properties, share tab, and allow folder sharing. 

**However, they are only read-only on my Windows machine - I can't edit the files.** This is verified by the fact that when I go into the properties of the USB drive, I only have "Create and delete files" permission on the Ubuntu Machine. I only have "Access files" permissions for the root group and others (meaning, other network users). Does this have something to do with the fstab entry I had to add?

---

