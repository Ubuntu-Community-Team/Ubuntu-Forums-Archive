---
title: "plz help installing NAS on ubuntu desktop 16.04"
date: 2016-06-21
forum: New to Ubuntu
---

### Post by ame82 on 2016-06-21
i dont know from where to start, i installed ubuntu desktop 16.04, after readings , i found out i have to install samba which i did , but non of the posts i rade was useful to configer samba , even when i restart the system , the external hard disk i had it shared was not shared any more , 
some other people says i have to install ubuntu server, i prefere to use desktop and i am planing to create small nas drive to use it with ip cameras as net work storage
my question is 
1- where to start?
2- any good guide in details? 
3- i wish u guys fellow up and i will be able to update here my problems 
4- samba configration good guide, since every one uses different methods ,like system-config-samba which never worked with me , and edit samba with nano also didnt work fine, 
most important question, they create the share 1st then assign space , while i have an external hard disk which i want to share it as nas smb or cfs  any help

---

### Post by TheFu on 2016-06-21
There is no reason to install the "server" edition. Any desktop can perform as a "server" - just install the needed packages.  If you want network storage for Windows, you need Samba installed and configured.  If you want network storage for Unix, Linux, or OSX, you need NFS installed and configured. Simple.  The difference between "server" and "desktop" versions are just the base packages installed. Both can install other packages, as desired.  If you want storage available from anywhere in the world, in a secure way, use ssh/scp/sftp with key-based authentication. It really isn't too hard to setup, but there are a few moving parts.

The details change slightly with the different Linux releases.  For 16.04, there might not be many good guides yet, but those will come.  For a simple samba setup, the 14.04 guides should work fine, though I haven't used 16.04 with any of my samba servers, I don't recall seeing any major issues.  My samba setup has been working since the mid-1990s almost unchanged.

External disk?  What file system does it have?  Samba systems would prefer ext4.  You'll need to mount the storage through the /etc/fstab before trying to configure it for samba use too. If running NTFS, I think things are harder.

Lots of guides for samba setup ... "ubuntu samba setup" is the search term:
* [https://help.ubuntu.com/lts/serverguide/samba-fileserver.html](https://help.ubuntu.com/lts/serverguide/samba-fileserver.html)
* [https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)
* [https://www.howtoforge.com/tutorial/samba-server-ubuntu-16-04/](https://www.howtoforge.com/tutorial/samba-server-ubuntu-16-04/)
* [http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/](http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/)

The easiest are for simple setups. The ubuntu guides will handle more complicated needs, so they are probably harder to understand, but more complete. I have to admit that I haven't looked at any of these too closely - just know they are reputable sources.

Since samba is bridging file and directory permissions between 2 different OSes with different permissions models, that can mean that the person configuring it needs a strong understand of file and directory permissions for **BOTH** OSes.  There are tutorials to learn Linux file and directory permissions. This understanding is the cornerstone for all Unix-like systems and the security model on them. Learn it well, sooner than later to save yourself hours, days, weeks, of frustration.  These same permissions flow over into hardware access and process control too - so once you learn it, those become much easier to understand and control.  These permissions need to work as desired BEFORE samba can work.

Hope this makes sense.  You didn't really provide much information about the setup. Please tell us about the disk, file systems, how it is connected, how many users and groups are involved, and which client OSes need to be supported?

As far as running a NAS - that is a different thing, but samba can be part of that solution too.  Generally, it is best to only use samba for Windows clients and to use some other protocol for all other clients since they will speak native Unix file system permissions which are much more flexible than what Samba provides.  For access to your storage over the internet, sftp is by far the easiest to use for pretty much all OSes.  From Linux, I sometimes use sshfs, which is nice, simple, easy and secure.

---

### Post by mastablasta on 2016-06-22
i found it best and fastest to use sFTp with Windows clients, or when ease of use is needed a service such as owncloud or seafile Works well on local as well as internet level.

---

### Post by TheFu on 2016-06-22
sftp is handy.  WinSCP is a nice windows program for it, but there are others.

Just be certain to use a full VPN to your house if you go with owncloud or seafile.  HTTPS is **not** secure enough, IMHO.  Any security method dependent on DNS and public keys can be hacked. Sorry to say that, but it is the world we live in.

---

### Post by ame82 on 2016-06-22
samba system config doesnt work on ubuntu 16.04 and i guess i should to downgrade but i want to understand how to code the confg file better

---

### Post by mastablasta on 2016-06-23
are you using desktop version now or server? if desktop things could be done and setup in file manager via GUI i believe.

---

### Post by ame82 on 2016-06-24
i use disktop and i will look at ur link hope its helpful , do u guys know any page has tutorial  steps with no mistakes and no missing parts,

---

### Post by TheFu on 2016-06-25
> **ame82 said:**
> i use disktop and i will look at ur link hope its helpful , do u guys know any page has tutorial  steps with no mistakes and no missing parts,

Samba isn't a trival desktop program to be installed and run. It is a complex server with thousands of options depending on the needs. If you want to stick with just samba, then please post the output from **testparm** inside **code tags**. Also, please describe what you are looking to have - how many users. All separate files or shared?  Is this NAS for media, at home, backups, work, ... something else?  I ask since the setup is different for each and the complexity can very wildly between these.  Allowing 1 user to use samba is very different from allowing 500 people to have access. The type of file system the files being shared from matters as well.  Permissions under samba can be really easy or very hard, depends on the requirements.

To start, post what you have in the /etc/samba/smb.conf by running **testparm**. Explain what is and is not working. Please.

If the systems going to access the files aren't Windows, then a different file sharing method would be easier.

Everyone's knowledge is a little different. The "missing parts" are just things that the author thought were easy enough not to be mentioned. Plus every systems and network is a little different, so changing some little things (which might be big things to someone new) will always be required. That is the way of the world for any non-trivial skill and why apprenticeships and mentoring is required for many skills.  Learning Unix/Linux isn't any different.  The best way that I know to avoid those little mistakes which cause so many issues is to start from a reputable source and learn Linux from the basics up. When really new to Linux, it is best to avoid searching for answers and find a book to learn from in an organized way. If you plan to run servers like samba, it would be best to learn from a book for administrators, not end-users. Linux administration doesn't use GUIs. That is part of the power.

---

### Post by nerdtron on 2016-06-27
> **ame82 said:**
> i use disktop and i will look at ur link hope its helpful , do u guys know any page has tutorial  steps with no mistakes and no missing parts,

Here's a tutorial with screenshots: [http://www.technig.com/share-file-between-ubuntu-and-windows/](http://www.technig.com/share-file-between-ubuntu-and-windows/)

If that does not work, try to use the terminal: [http://tutorialforlinux.com/2016/02/15/easy-file-sharing-with-smb-quickstart-on-ubuntu-16-04-xenial-lts-linux/](http://tutorialforlinux.com/2016/02/15/easy-file-sharing-with-smb-quickstart-on-ubuntu-16-04-xenial-lts-linux/)

If you have any problems on it, post what have you done and the errors you are having on this thread.


Regards,
nerdtron

---

