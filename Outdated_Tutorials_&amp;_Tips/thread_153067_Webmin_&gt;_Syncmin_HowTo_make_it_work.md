---
title: "Webmin &gt; Syncmin HowTo make it work"
date: 2006-03-31
forum: Outdated Tutorials &amp; Tips
---

### Post by lindsay_keir on 2006-03-31
Webmin > Syncmin HowTo make it work

Syncmin "out-of-the-box" does not work. 
* Syncmin creates an rsync command that uses ssh as the security shell.
* ssh does NOT recognize the --password-file= parameter.
The result is that hidden behind the scenes you are being asked for a password - which fails!

Basically you want to tell the target system's root account to automatically trust the source system's root account.

A generated Syncmin command looks like this...
[FONT="System"]/usr/bin/rsync -av --rsh=ssh --temp-dir=/tmp --port=55555 --rsync-path=/usr/bin/rsync  /home/lindsay/storage root@testy:/MyBackup/images --password-file=/etc/webmin/syncmin/data/106221326.sec[/FONT]

The following assumes that...
(1) You are using root for Webmin and have given your Webmin(s) the root password (XXXXXX) using 
     [FONT="System"]sudo /usr/share/webmin/changepass.pl /etc/webmin root XXXXXX[/FONT]
(2) ssh is OpenSSH Version 2, available on both systems, and rsa is the recommended method to use (2006-March) 

There are only two commands; both are run on the SOURCE system - portal

Ubuntu Kubuntu systems - Permission denied, please try again.
RootSudo systems have a slight complication. You need root access while running the commands. This is simple; but, you need console access to the target system. How you get console access is your concern.

(1) Generate the trusted keypair - only done 1st time

[FONT="System"]root@portal:~#
root@portal:~# ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/root/.ssh/id_rsa):
Created directory '/root/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /root/.ssh/id_rsa.
Your public key has been saved in /root/.ssh/id_rsa.pub.
The key fingerprint is:
29:f1:18:d8:1d:87:53:e4:ff:1a:af:f1:c6:ca:ec:89 root@portal
root@portal:~# [/FONT]

(2) RootSudo systems - switch to root access.

[FONT="System"]root@testy:
root@testy:~# sudo passwd -l root
Password changed.
root@testy:~# sudo passwd root
Enter new UNIX password: XXXXXX
Retype new UNIX password: XXXXXX
passwd: password updated successfully
root@testy:~#  [/FONT]

(3) Tell the TARGET SYSTEM (root@testy) to trust the SOURCE SYSTEM (portal)

[FONT="System"]root@portal:~#
root@portal:~# ssh-copy-id -i ~/.ssh/id_rsa.pub root@testy
21
The authenticity of host 'testy (192.168.1.140)' can't be established.
RSA key fingerprint is fe:17:c2:6c:85:9c:25:ee:f4:19:3b:5a:ac:89:27:bc.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'testy,192.168.1.140' (RSA) to the list of known hosts.
root@testy's password: XXXXXX[/FONT]
Now try logging into the machine, with "ssh 'root@testy'", and check in: .ssh/authorized_keys to make sure we haven't added extra keys that you weren't expecting.
root@portal:~#

(2) RootSudo systems - switch to sudo access.

[FONT="System"]root@testy:~#
root@testy:~# sudo passwd -l root
Password changed.
root@testy:~#[/FONT]

Give it a try using ssh root@testy - see no password required. And now your Syncmin job will also work. Give it a try by doing a [Run Now] from the Scheduled Cron Jobs function.

NOTES:

After wading for days through multiple pages on Webmin, OpenSSL, etc. I came across these excellent notes at [http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)
A big tip of the hat to Steve Kemp - the site's webmaster. All I did was paraphrase this into a Webmin and Ubuntu viewpoint. And of course the fantastic work done by the (K)Ubuntu group; and never, ever forgetting Jamie Cameron of Webmin fame and function - maybe someday there will be a distro that incorporates Webmin.

The SOURCE files created/updated are:
[FONT="System"]  -rw-------  1 root root 887 2006-03-28 15:41 id_rsa
  -rw-r--r--  1 root root 221 2006-03-28 15:41 id_rsa.pub
  -rw-r--r--  1 root root 540 2006-03-28 15:42 known_hosts[/FONT]
The TARGET file created/updated is:
[FONT="System"]  -rw-------  1 root root 221 2006-03-28 15:43 authorized_keys[/FONT]
See how clean everything is - nice and simple.

When defining the Syncmin job, the Target User must be root; but, the password can be anything and I suggest it NOT be the actual passord; there's no sense in leaving rsync's --password-file around with the real password.

To recap... by including a system named "backup"
[FONT="System"]root@backup:~# sudo passwd root
root@portal:~# ssh-copy-id -i ~/.ssh/id_rsa.pub root@backup
root@backup:~# sudo passwd -l root[/FONT]


My actual wish was to control Syncmin from portal, but actually pass files from anywhere to anywhere. Unfortunatly the created rsysnc command doesn't pass on the source host information, and the ssh shell doesn't accept some of the formatting. Ah well!

---

### Post by 4o66 on 2008-08-25
I have taken over the syncmin project.

In order to address the issues listed, I have been updating the code in [webmin and usermin]("http://www.webmin.com").

As soon as the new version is released (1.440 Webmin and 1.370 Usermin) you will be able to perform all the key management functions from there.

I will be updating the syncmin interface as well, to support more options with radio or checkbox inputs, and hopefully add an error reporting option.

Check the [syncmin page]("http://sourceforge.net/projects/syncmin") for updates.

---

### Post by jesuspresley on 2009-06-22
Is there any progress on the project?
I am configuring a daily backup of our fileserver to a NAS - Rsync would dramatically reduce the traffic in our LAN.

---

