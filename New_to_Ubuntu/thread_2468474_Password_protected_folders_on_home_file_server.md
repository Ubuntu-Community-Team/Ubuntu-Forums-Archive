---
title: "Password protected folders on home file server"
date: 2021-10-30
forum: New to Ubuntu
---

### Post by ajs2326 on 2021-10-30
I just recently set up a home file server running Ubuntu server 20.04. I made this server so every member of my family can use it, but I don't want each person to be able to look through everyone's specific folder. What I want to do is have each family member have their own password so only they can access their folder. This is how it is set up now when click on my home server in file manager from windows 10 (we all run that OS):

(network/10.x.x.xx/servername/)

Family Member 1
Family Member 2
Family Member 3
Family Member 4

How would I make it so if for example Family Member 3 wanted to go into their folder, a window would pop up asking for their credentials to access this folder after they clicked their name and they would have their own password to type in and that password would be different from everyone else's? 
I have been looking around and have not found a way to do this if it is possible so any help would be great. Thanks.

---

### Post by yancek on 2021-10-31
The standard Linux file server with windows clients is Samba which as been in existence for almost 30 years.  This requires installing Samba server as well as Samba client on each client machine.  The link below explains setting it up and includes setting a specific directory for a specific user to access.

 [https://www.process.st/checklist/linux-samba-file-server-setup-checklist/](https://www.process.st/checklist/linux-samba-file-server-setup-checklist/)

You can use encryption, discussed at the site at the link below.

[https://superuser.com/questions/1026431/how-to-password-protect-a-single-folder-on-ubuntu](https://superuser.com/questions/1026431/how-to-password-protect-a-single-folder-on-ubuntu)

You can use NFS which is the stadard Linux to Linux Server/Client which can also be use Linux to windows.

 [https://graspingtech.com/mount-nfs-share-windows-10/](https://graspingtech.com/mount-nfs-share-windows-10/)

---

### Post by ActionParsnip on 2021-10-31
Use SFTP and users will be jailed to their home. You can grant access as you do in Linux with groups.

---

### Post by TheFu on 2021-10-31
Storage encryption at the per-user level isn't part of current Ubuntu distributions and definitely not part of Samba.  Per-userid encryption only becomes decrypted with a normal Linux login, so samba doesn't count. That doesn't mean something couldn't be hacked together, but it would be non-standard.  

Samba is the most common method used from Windows clients ... the CIFS protocol is equivalent to "Windows Shares." With Win10+, be certain to set the samba protocol version to 3 or higher in the smb.conf file.  May want to enable encrypted network transfers too, for added security - but get the basic stuff working first, then you can add those 2 extra settings - smb3, encrypted networking.

So ... if you don't allow these users to login to the server using their Linux credentials - either on the console or through ssh, there is little use for file encryption on a per-userid level.  You can encrypt the entire OS at installation time. Or you can encrypt 1 partition/logical volume. Both options are up to you to choose.  Today, pretty much all the linux storage encryption methods have sufficient downsides/security problems EXCEPT LUKS via dm-crypt. If we assume you will be using LUKS encryption (cryptsetup is the tool), it will be very secure and support nearly automatic decryption.  LUKS containers typically are setup at the partition level, so we can put almost anything inside that container. 

You can setup separate partitions, each encrypted separately, but the hassles in doing that make it less than great and it wouldn't really help security.  After all, for users to access storage, the decrypted storage must be mounted. Then it is just storage and any local users to the system would be able to access it as the POSIX file permissions allow.  Encrypted storage really only matters when the computer is powered off.  When it is powered on and mounted, being encrypted doesn't matter.  Basically, encrypted storage means we can have a HDD fail and send it in for warranty reasons without fear any of the files will become known. LUKS encryption means there won't be any data leakage about the size or names of those encrypted files.

So, to use LUKS encryption, requires the passphrase or a USB flash drive with a keyfile or a yubikey 2FA device to be setup.  There are 8 slots in LUKS encryption, so 8 different methods can be used. These slots are part of the LUKS header. The data encryption is strong regardless of what happens in the header.  Android works the same way.  Initially, you'll probably want to use a passphrase. This can be changed.  On my laptop, I'm using 3 LUKS slots for access - 
[LIST]
[*]a really long passphrase that I probably cannot actually type,
[*]a static passphrase that is 50% what I type in and 50% what a yubikey will enter (which I setup),
[*]a challege/response passphrase tied to a different yubikey - I'm prompted to enter a passphrase, the yubikey does some crypto on it and sends the result like a keyboard typing into LUKS as the response.
[/LIST]
Any one of those 3 methods can be used to unlock the storage. This has to happen before the OS can be booted.
There are 5 slots left, which can be used by other people to use for unlock codes. Other people would get yubikeys with challenge/response devices.  Again, this is all pre-boot - sorta when just enough of the OS is loaded to read files, but not so much as to boot.

Since a file server probably needs to be on 24/7, you might want to go with a keyfile solution. This would put the keyfile on a flash drive that is connected to one of the internal or back ports of the *server*, so the other users don't know it exists.  Servers really need to be physically secured, if you care about security, right?  Anyway, you can setup LUKS to look in a specific place - usb flash drive - for a specific file - and to use that file for unlocking the LUKS storage.  The file can be almost anything.  Might be best to put 1000 family photos onto it, but only use 1 for the key. You could create a 4K key using almost any method you like.  sha1, whatever.  Then you can disconnect the flash storage, reboot, and throw that storage device into a pile with others. That would be sufficient for someone who doesn't know about the flash storage requirement to be locked out of the system completely.   I don't know about you, but I have about 20 flash devices near my server racks. Most are old 8GB SDHC or newer 32-64G microSD cards. There are a number of LUKS crypt how-to guides for flash storage.  You could put the boot files onto flash storage too, then just remove it except during boot updates or actual booting.  This is a viable mitigation to the "evil maid" attack that encryption doesn't completely solve - the extra step of keeping the boot files for an encrypted system on your person, always, means you'll know if the "evil maid" has taken the storage with the boot files, then you would assume those were compromised and the computer isn't safe.

Ok, so that gets the storage encrypted.

Basic Unix permissions can prevent users from accessing each other's HOME directories.  Just set the permissions on their HOME to be 700. That would result in :

$ ll /home/
total 48
drwxr-xr-x   5  root   root   4096 Jul 18 16:38 ./
drwxr-xr-x  26  root   root   4096 Oct 14 10:30 ../
[COLOR="#FF0000"]**drwx------**[/COLOR] 181 thefu  thefu  20480 Oct 31 09:52 thefu/

Just make each user's HOME like that. With those permissions, other users cannot access ~thefu, which is what you intend.  Root and unlimited sudo users would still have access, however.  Samba-only users *could* have access, since samba runs as root and misconfiguration could allow the access. We need to take correct steps to prevent that.

One stanza in the smb.conf file is needed to allow samba clients to access their individual HOME directory.  They won't be presented with any other directories and can't see each other's. Add this to the bottom of the smb.conf file, restart the smbd process.
```
[homes]
  comment = Home Directories
  hosts allow = 127.0.0.1 [COLOR="#A52A2A"]172.22.22.0/24[/COLOR]  
  hosts deny = 0.0.0.0/0
  browseable = yes
  guest ok = no
  writable = yes
  create mask = [COLOR="#A52A2A"]0600[/COLOR]
  directory mask = [COLOR="#A52A2A"]0700[/COLOR]
  valid users = %S

```
Change the allowed hosts to match your subnet.  Those create masks are very important to ensure the Linux-side of the access doesn't get broken.

It has been some time since I setup samba as a server. It may be necessary to use **smbpasswd -a** to set initial passwords for each user. Their userid needs to exist in the Linux password DB already.  You can prevent logins, but I'll assume that isn't really needed.  It might be nice to allow **sftp** access, which **WinSCP** supports from Windows.  We've already prevented users from seeing each other's files in their HOME directories with Unix permissions and by only using the "homes" stanza in the smb.conf file.

WinSCP can be used instead of samba on the Windows systems. We get it just by installing the openssh-server package on Ubuntu, which you'll want on the server anyways so you can remote in over ssh.  ssh is how Unix systems communicate. BTW, because we setup the HOME directories to have 700 permissions, NFS can also be used, if you like, without concern.

---

### Post by Morbius1 on 2021-10-31
It's not clear how you are set up but as an example let's say ....

I have a directory at /Data and under that directory I have a subfolder for a given client user like Mindy.

I would create a share definition at the end of **/etc/samba/smb.conf** that looks something like this:

```
[Mindy]
path = /Data/Mindy
read only = no
guest ok = no
valid users = mindy
```

*** You will have to create the local user - mindy - on the server.

*** You will need to make sure mindy owns the subfolder:
```
sudo chown mindy /Data/Mindy
```

*** And you will need to add her to the samba password database:
```
sudo smbpasswd -a mindy
```

*** And every time you edit smb.conf remember to restart smbd:
```
sudo service smbd restart
```

If client user mork tries to access the Mindy share he will get prompted for credentials but will fail since he is not mindy.

Note: You say you are using Ubuntu Server but if you are in fact Ubuntu Desktop as a server and you created shares using the file manager you aren't going to be able to pull this off. Actually you can but the syntax is not worth the effort. It's best to create shares in smb.conf directly.

---

