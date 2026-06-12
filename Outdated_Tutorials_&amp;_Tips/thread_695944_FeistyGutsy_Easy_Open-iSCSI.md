---
title: "Feisty/Gutsy Easy Open-iSCSI"
date: 2008-02-13
forum: Outdated Tutorials &amp; Tips
---

### Post by epyon_avenger on 2008-02-13
I keep reading about random troubles setting up Open-iSCSI initiators, or random configuration issues, so I figured I'd browse the web and compile the guides I've seen into an easy to follow guide, and here it is! This is the setup we use in my production environment and it works fine on our Feisty and Gutsy servers. Below or above that is iffy, but it's pretty general so I don't see why it wouldn't work.

This guide assumes your storage devices have 2 controllers per array each with their own IP address. If you have a single "head" address, just use that instead and ignore the second storage IP lines. It also assumes that you have presented the iSCSI shares to your server from the storage. Doing so usually requires copy/pasting the IQN for the server (found in the /etc/iscsi/initiatorname.iscsi file) into a hosts field on the iSCSI storage array.

[INDENT]**Install open-iscsi**
[INDENT]sudo aptitude install open-iscsi[/INDENT]
**Set All Discoveries to Auto-Login at Boot**
[INDENT]sudo nano -w /etc/iscsi/iscsid.conf
[INDENT]Change node.startup to: node.startup = Automatic[/INDENT][/INDENT]
**Restart open-iscsi**
[INDENT]sudo /etc/init.d/open-iscsi restart[/INDENT]
**Discover Targets**
[INDENT]sudo iscsiadm -m discovery -t st -p <Storage IP 1>
*sudo iscsiadm -m discovery -t st -p <Storage IP 2>*[/INDENT]
**Auto Login to Storage**
[INDENT]sudo iscsiadm -m node -T <Storage IQN 1> -p <Storage IP 1> -o update -n node.conn[0].startup -v automatic
*sudo iscsiadm -m node -T <Storage IQN 2> -p <Storage IP 2> -o update -n node.conn[0].startup -v automatic*[/INDENT]
**Check if Sessions Started**
[INDENT]sudo iscsiadm -m session
[/INDENT]
**Create Directories for iSCSI Mounting**
[INDENT]sudo mkdir /<Mount Point>[/INDENT]
**fdisk iSCSI Storage**
[INDENT](self explanitory)[/INDENT]
**mk2efs iSCSI Storage**
[INDENT](self explanitory)[/INDENT]
**Note UUID for iSCSI Storage**
[INDENT]sudo vol_id -uuid /dev/<device>[/INDENT]
**Use UUIDs in fstab**
[INDENT]sudo nano -w /etc/fstab
[INDENT]*UUID=<Big Long String>	<Mount Point>	<FileSystem>	_netdev	0	0*[/INDENT][/INDENT]
**Modify /etc/rc.local to Mount iSCSI Storage**
[INDENT]sudo nano -w /etc/rc.local
[INDENT]*mount -a*[/INDENT][/INDENT]
**Correct Shutdown Order**
[INDENT]sudo mv K20open-iscsi S50open-iscsi[/INDENT]
**Reboot to Check if Sessions are Loaded, Mounts Mounted, etc.**[/INDENT]

---

### Post by tmagner on 2009-02-24
Thanks for the procedures.  Question, is <Server Name> in the Change IQN in /etc/iscsi/initiatorname.iscsi the same as Storage IQN 1 in the Auto Login to Storage step?

---

### Post by epyon_avenger on 2009-02-24
> **tmagner said:**
> Thanks for the procedures.  Question, is <Server Name> in the Change IQN in /etc/iscsi/initiatorname.iscsi the same as Storage IQN 1 in the Auto Login to Storage step?

Actually, I should change that step. Things are a bit easier now and I understand them better.

Where I work, we changed the auto-generated IQN to something more memorable so we wouldn't have any trouble typing it in to our storage arrays. However, now I find that some storage arrays -must- have a properly formatted IQN, so you can ignore that step and keep the default IQN and just copy/paste it into the storage you're having present to the server.

---

### Post by tmagner on 2009-02-25
I've tried the procedures and can't get past the error below.  I pasted in some of my results from the procedure steps but I can't figure out what I'm doing wrong.  Can you see anything that you can help me out with?


administrator@LinuxServer:~$ sudo iscsiadm -m discovery -t st -p 10.1.100.10:3260
10.1.100.10:3260,1 iqn.2001-05.com.equallogic:0-8a0906-91fdc1202-f393d150cf846f70-abwoosteruserdata
10.1.100.10:3260,1 iqn.2001-05.com.equallogic:0-8a0906-ae9dc1202-b16407d1f22499ab-linuxserver1
10.1.100.10:3260,1 iqn.2001-05.com.equallogic:6-8a0900-7e5dc1202-07858ea61564638d-vss-control



InitiatorName=iqn.2001-05.com.equallogic:0-8a0906-ae9dc1202-b16407d1f22499ab

administrator@LinuxServer:~$ sudo /etc/init.d/open-iscsi restart
 * Disconnecting iSCSI targets                                           [ OK ] 
 * Stopping iSCSI initiator service                                      [ OK ] 
 * Starting iSCSI initiator service iscsid                               [ OK ] 
 * Setting up iSCSI targets                                                     
iscsiadm: No records found!

---

### Post by epyon_avenger on 2009-02-25
So, for you the setup should be something like this...

sudo iscsiadm -m discovery -t st -p 10.1.100.10
sudo iscsiadm -m node -T iqn.2001-05.com.equallogic:0-8a0906-91fdc1202-f393d150cf846f70-abwoosteruserdata -p 10.1.100.10 -o update -n node.conn[0].startup -v automatic
sudo iscsiadm -m node -T iqn.2001-05.com.equallogic:0-8a0906-ae9dc1202-b16407d1f22499ab-linuxserver1 -p 10.1.100.10 -o update -n node.conn[0].startup -v automatic
sudo iscsiadm -m node -T iqn.2001-05.com.equallogic:6-8a0900-7e5dc1202-07858ea61564638d-vss-control -p 10.1.100.10 -o update -n node.conn[0].startup -v automatic

sudo /etc/init.d/open-iscsi restart

sudo iscsiadm -m session

Assuming that you've changed the iscsid.conf to automatic, then the session command should show the three sessions started. If not, can you tell me what kind of storage arrays you're using? I gathered equallogic from the iqns but I could look it up specifically to make sure there's no caveats for that one in particular.

---

### Post by tmagner on 2009-02-25
I did a re-install and got past the error with your new instructions.  Here's where I'm at now:

administrator@LinuxServer:/$ sudo /etc/init.d/open-iscsi restart * Disconnecting iSCSI targets                                                  iscsiadm: Could not get host for sid 1.
iscsiadm: could not get host_no for session 6.
iscsiadm: could not find session info for session1
                                                                         [ OK ]
 * Stopping iSCSI initiator service                                      [ OK ] 
 * Starting iSCSI initiator service iscsid                               [ OK ] 
 * Setting up iSCSI targets                                                     
Login session [iface: default, target: iqn.2001-05.com.equallogic:0-8a0906-ae9dc1202-b16407d1f22499ab-linuxserver1, portal: 10.1.100.10,3260]
Login session [iface: default, target: iqn.2001-05.com.equallogic:6-8a0900-7e5dc1202-07858ea61564638d-vss-control, portal: 10.1.100.10,3260]
Login session [iface: default, target: iqn.2001-05.com.equallogic:0-8a0906-91fdc1202-f393d150cf846f70-abwoosteruserdata, portal: 10.1.100.10,3260]
                                                                         [ OK ]
administrator@LinuxServer:/$ sudo iscsiadm -m sessioniscsiadm: Could not get host for sid 1.
iscsiadm: could not get host_no for session 6.
iscsiadm: could not find session info for session1
iscsiadm: Can not get list of active sessions (6)

I'm using a Dell/Equallogic PS5000 SAN.  Thanks.

---

### Post by epyon_avenger on 2009-02-25
> **tmagner said:**
> I did a re-install and got past the error with your new instructions.

It looks like you might be suffering from the bug listed here: [https://bugs.launchpad.net/ubuntu/+source/open-iscsi/+bug/289470](https://bugs.launchpad.net/ubuntu/+source/open-iscsi/+bug/289470)

Apparently it is fixed in Jaunty, but Intrepid is still affected till they backport the fix. However, after reading through their comments, it appears that iSCSI should still be working, it's just that the session listing doesn't work.

Thus! I would see if the iSCSI disk shows up with fdisk and if it does, then congrats, you're now using iSCSI! If not, let me know and we can try to troubleshoot sans the session listing.

---

