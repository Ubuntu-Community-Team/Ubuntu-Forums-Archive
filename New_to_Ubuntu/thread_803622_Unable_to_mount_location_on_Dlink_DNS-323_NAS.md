---
title: "Unable to mount location on Dlink DNS-323 NAS"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by GNev on 2008-05-22
I have a Dlink DNS-323 NAS with 2 shares, 1 password protected and 1 unprotected. 

If I click Network on the Places menu the File Browser opens for network:/// and displays a "Windows Network" icon.

If I click the icon the address changes to smb:/// and an icon labeled with the Windows Workgroup WORKGROUP is displayed.

Clicking this icon the address changes to smb://workgroup/ and the window displays the other pcs on the network and the NAS DLINK-EEFFFAA.

Clicking the NAS icon switches the address to smb://dlink-eeffaa/ and shows icons for the shares on the drive: Protected and Unprotected.

If I click the Unprotected share it opens and I can see the files, modify them and write new files etc, however if I click the Protected share I am sked for the password, as I would expect. 

An Enter Password dialog box opens "Password required for share protected on dlink-eeffaa: Username: myusername, Domain: MSHOME, Password: blank.

I enter the share owner Username and password and click connect. This displays the messages: "Unable to mount location" "Failed to mount Windows share". I have tried changing the domain name to the Windows workgroup name "WORKGROUP",the NAS name DLINK-EEFFAA, deleting the name and get the same message no matter what. 

To access the share on Windows and on  MacOS I only have to enter the Username and Password.

What am I missing? Do I have to enter a mount command in terminal?

Regards

GNev

---

### Post by 2clicks on 2008-05-27
I am having the same problem.  It worked fine under 7.10, but after my upgrade to 8.04 I am seeing exactly what you describe.  I found in another forum (sorry I don't have a reference) that I could mount the share from the command line as follows:

smbmount //raid1nas/Dave /home/dave/DaveonNAS

This then asks for your password and mounts your 323 share in the folder specified in the second part of the phrase above (in this case DaveonNAS).

The unfortunate catch is that about a week ago, after a software update, this ceased to function as well.

Not sure which version your running, but I'm considering going back to 7.10.  It just worked.

Hope this helps.

---

### Post by frederic.tardif on 2009-01-14
Exactly the same problem with my freshly installed DNS-323. The file explorer mounts an unprotected partition like a charm, but it always fails when entering the credential for the protected version. Is there a way to let it work in command line?

I have tried:
sudo mount -t smbfs //192.168.2.26/Vault/Volume_1-1 /media/test -o username=frederic,password=mypassword

but it gives:
mount: wrong fs type, bad option, bad superblock on //192.168.2.26/Vault/Volume_1-1,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by frederic.tardif on 2009-01-14
just find out that it seems to be a known bug on ubuntu side:
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/209520](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/209520)

---

### Post by frederic.tardif on 2009-01-14
following of the suggestion in the bug report worked for me:

on the client, /etc/samba/smb.conf file, locate the global and add the lines below

[global]

# THE LANMAN FIX
  client lanman auth = yes
  client ntlmv2 auth = no

---

