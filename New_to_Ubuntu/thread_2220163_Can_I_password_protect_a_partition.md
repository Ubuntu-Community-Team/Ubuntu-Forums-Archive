---
title: "Can I password protect a partition?"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by WogBoy on 2014-04-26
Hi Guy's

Pc specs.  ** Kubuntu 14.04 LTS 64bit --****- Hp Pavilion G6, AMD A4-3305M With Radeon HD Graphics 1.90 Ghz 4GbRam 500 GB HDD**.
I have all the 3DCube plasma and assorted eye candy going, PC runs way better than it did with Winedows7. I do not own or have Winedows in my house anymore. Full convert here.
My set up now
1st partition 100 GB for Linux OS. Only software on this partition, Nothing else, I do not have or need a swap partition.
2nd Partition 400 GB Movie's music photo's etc.

My question is.
Would it be a good idea of making the second partition read only without a password?, Password needed to edit, write delete files. And How?

I do not care who in my family see's it, I just dont want them to be able to modify it. ( yes yes I should create a second account and all that but sometimes I log in as me not guest and leave the pc on ) In the past my daughter has cut/pasted stuff insetad of copy/paste. Also she sometimes boots my laptop from USB ( Puppy Linux) I want her to see the files but not modify in any way.

---

### Post by deadflowr on 2014-04-26
Change ownership and permissions on the directory(ies) on the 2nd partition.
Perhaps make root the owner(since you should have admin rights you can access that with sudo/password)
Then change the permission so that group and other have only read-only and execute allowed.
More on permissions here
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

thread lightly , though, and double check to make sure you change the permissions and ownerships on the right partition, or else trouble can ensue.

---

### Post by WogBoy on 2014-04-26
> thread lightly , though, and double check to make sure you change the  permissions and ownerships on the right partition, or else trouble can  ensue.
Thank's will do. I have a practice PC to do it all on first. I learned the hard way to check if its sda or sdb or whatever installing my first Ubuntu 12.04 to what was meant to be the USB stick. OOOP's.

---

### Post by WogBoy on 2014-04-27
It worked on a USB drive,  That is a screen shot of puppy linux looking at a pass protected usb drive, You can see the files copy them, But you can only unlock them from my laptop as root cool.

Now onto the next project since i can do that to a USB drive I plan on connecting a 3TB drive via usb to my WiFi router like this.
[http://techchannel.radioshack.com/connect-usb-external-hard-drive-wireless-router-1602.html](http://techchannel.radioshack.com/connect-usb-external-hard-drive-wireless-router-1602.html)
One of these.
[http://www.ebay.com.au/itm/Western-Digital-WD-3TB-Element-3-5-USB-External-Hard-Disk-Drive-Windows-Mac-/360572784133?pt=AU_HardDrives&hash=item53f3d00e05](http://www.ebay.com.au/itm/Western-Digital-WD-3TB-Element-3-5-USB-External-Hard-Disk-Drive-Windows-Mac-/360572784133?pt=AU_HardDrives&hash=item53f3d00e05)

That way the family has access to all the files without my pc being on. Also my TV has wifi I will try and connect that to. Movies on the big screen. Wheres the beer.

So far this linux stuff is easy.

---

### Post by Impavidus on 2014-04-27
> **WogBoy said:**
> It worked on a USB drive,  That is a screen shot of puppy linux looking at a pass protected usb drive, You can see the files copy them, But you can only unlock them from my laptop as root cool.
To keep things clear: the files can be unlocked as root from the laptop, both when running Kubuntu from the internal disk and when running puppy linux from the usb drive. Assuming your daughter has root access on her puppy system she can still delete the files. Even then, she cannot accidentally delete them and if your family is reasonable happy she won't delete them on purpose. And even if she would, you still have your backups. Right?

---

### Post by SeijiSensei on 2014-04-27
If you're concerned about your daughter deleting things, don't give her root access anywhere.  If her Puppy setup does what she needs, she doesn't need root privileges.  Give root a password on Puppy and remove your daughter from any administrative groups that can use sudo.  Read this for more details: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If she wants to install something on the Puppy installation, she'll need to ask you to do it.  If that's too much hassle or paternalism, then leave things as they are, but remember Impavidus's warning the next time something disappears on your system.

---

### Post by bgw99 on 2014-04-27
You can't give root a password on puppy linux. Puppy was designed as a single user client, not multi-user like most (all?) linux distros.

[http://puppylinux.com/technical/root.htm](http://puppylinux.com/technical/root.htm)

---

### Post by deadflowr on 2014-04-27
Puppy's design to be run as a live session, off a cd/usb.
But if you do install it, it's still malleable enough to turn into a multi-user system.

As well, if you ever have a file that you don't want to ever change, ever, maybe set an immutable attribute on it.
Even if someone had root, they'd have to also know how to change attributes as well, to do most anything to the file.(You can still copy an immutable file, but that's about it.)
Of course, if you need to keep rewriting to a file, then changing its attribute would be a hassle.

---

### Post by SeijiSensei on 2014-04-27
I skimmed the Puppy page you cited.  While they talk about some security implications of running as root, they don't address how it might be a problem on networks.

I'd have to see how Puppy is organized. Is spot also uid 0?  How about fido?  I'm guessing fido has a userland uid.  I might spin one up and take a look.  A user with uid 0 has pretty much the run of the place including any networked servers and devices.  Take a look at [this thread](http://fixunix.com/ubuntu/518267-mount-nfs-share-password.html) on why you cannot use a password with NFS.

You can force a password if you distribute the files with Samba.  Using SMB with Linux servers and Linux client is not the preferred choice; NFS is, but NFS has essentially no security beyond hostnames/IPs and the user IDs in /etc/passwd. 

So let's try this.  (I'm using Kubuntu 14.04.)  Install the "samba" package:
```
sudo apt-get install samba
```
Now use "sudo nano /etc/samba/smb.conf".  Scroll down the file until you see this line:
```
;[homes]
```
Remove the semi-colon at the beginning of that line and the two following.  That will make all the home directories on the machine visible using SMB.

Let's start the Samba server.
```
sudo service smbd restart
```
I used "restart" just in case the server, smbd, was already running on your machine.  "Restart" will start the service if it is not already running.

Next create an SMB password for yourself with the command:
```
smbpasswd -a your_Linux_username
```
and enter a password when prompted.  Now you will have the right to access your home directory using SMB networking. 

Time to give it a whirl.  Open Dolphin and type "smb://localhost/your_Linux_username" into the address bar.  You should be prompted for your username and the password you just created.  Your home directory will open in Dolphin.

This suggests one method to solve your problem, mounting the 400GB partition somewhere in the filesystem and exporting it with Samba.  In this case I'm going to use /srv/MrData/ as the "mount point" for the data partition.  Samba has a lot of security options, but here's one method that you might try.

1)  Are you so completely non-Windows that this partition has an ext4 filesystem?  That would be great.  If not, but you can backup the files and convert the filesystem to ext4 I'd do that.  If you don't have enough room to back up, let's talk about it another time.

2)  Create the MrData user in Linux and mount the partition, probably /dev/sda2, to /srv/MrData.  You'll want to do this via an entry in [/etc/fstab]("https://help.ubuntu.com/community/Fstab"). However, for now, let's just mount it from the command prompt:
```

sudo mkdir /srv/MrData
sudo mount /dev/sda2 /srv/MrData
```

3)  Now we're going to give MrData ownership of all the files on that filesystem.  He'll have read and write privileges as well. 
```

cd /srv
sudo chown -R MrData:MrData MrData
sudo chmod -R u+rwx,go+rx   MrData

```

4)  Use smbpasswd as before to create an SMB identity for MrData.  That will be your administrative login so you can have write privileges. Then create accounts for your daughter and anyone else who should have read-only privileges.  Since we gave you an SMB password before, you can also use your Linux username if you add it to the "write list" parameter below.

5)  Edit smb.conf again.  We are going to divide the users into a group with write privileges and one with read-only privileges.  Below the section you uncommented that defined "[homes]," add this stanza:
```

[MrData]
    path = /srv/MrData
    comment = Mr. Data's Riches
    write list = MrData, joanna
    read list  = stephanie, billy
    browseable = yes
    force user = MrData
    force group = MrData

```
This defines a share that only MrData can write to, but everyone else can read.  The "force user/group" directives tells Samba to conduct all its transactions with Linux as the MrData user.  That avoids problems with managing permissions at both the operating system and application level.  Restart samba with the "service" command as before.

Now MrData and joanna can write to /srv/MrData, but stephanie and billy cannot.

You can access the share like before, by pointing a file manager like Dolphin or Nautilus at the URL smb://server/MrData and logging in when prompted.

That's a start.  There's a [whole lot more you can read on Samba access controls](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html), but this might be enough.

By the way, Samba listens on all network interfaces by default.  You can connect from another networked machine using the same smb:// URL but with the name or IP address of the server rather than "localhost."

I would discourage you from letting your daughter use her Puppy installation on the machine with the data.  Have her use it on another computer and connect to the data over the network with SMB.  If Puppy doesn't have an SMB client, see if you can install cifs on it and [mount the MrData share in /etc/fstab]("https://wiki.ubuntu.com/MountWindowsSharesPermanently").

---

