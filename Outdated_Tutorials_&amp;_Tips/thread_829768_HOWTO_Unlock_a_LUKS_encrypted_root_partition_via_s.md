---
title: "HOWTO: Unlock a LUKS encrypted root partition via ssh"
date: 2008-06-15
forum: Outdated Tutorials &amp; Tips
---

### Post by hyper_ch on 2008-06-15
[SIZE="6"]HOWTO: Unlock a LUKS encrypted root partition via ssh[/SIZE]

[SIZE="5"]Introduction[/SIZE]

Fully encrypted systems prevent others from getting your data from physical access. The rationale behind the encryption of a complete system is that you don't have worry about what you encrypt and what not, because everything (except for the /boot) partition will be encrypted.

However the problem I have encountered so far is, how could I reboot my computer from afar? I would be required to be in front of the computer and enter the password. I have wondered this far how I could reboot the computer remotely.

On Debian Administrator I found then an [article]("http://www.debian-administration.org/articles/579") written by Wulf (Wolfram Coulmann) in which he creates an initrd with dropbear as lightweight ssh server and an unlock script. However that script has still a few bugs and is not suited for Ubuntu. In the comments however, there are a few modifications (especially comment #31 and #29) which will make it also work on ubuntu.

[SIZE="5"]The Script[/SIZE]

Well, here's the script: dropbear
```

#!/bin/bash

# We add dropbear to the initrd to be able
# mount crypted partitions from remote

# copyright Wulf Coulmann
# GNU GPL
# http://www.gnu.org/licenses/gpl.html
#
# Download me here: http://gpl.coulmann.de/dropbear
# get infos about this script here:
# http://gpl.coulmann.de/ssh_luks_unlock.html

# Modified by Anonymous 2008
# Modified By Geoffroy RABOUIN 26/05/2008
# Modified by hyper_ch 15/06/2008

### INSTRUCTIONS FOR UBUNTU ###
# 0. Enable root login
# 1. Install killall, busybox and dropbear:
#    ~# sudo apt-get install psmisc busybox dropbear
# 2. Edit network configuration below and copy contents
#    of this file to /etc/initramfs-tools/hooks/dropbear
# 3. Save the script and make it executable:
#    ~# sudo chmod +x /etc/initramfs-tools/hooks/dropbear
# 4. Create new initrd:
#    ~# sudo mkinitramfs -o /boot/netboot
# 5. Edit /boot/grub/menu.lst and add your new initrd as the first entry
# 6. Delete the dropbear script the hooks folder
#    ~# sudo rm /etc/initramfs-tools/hooks/dropbear
# 7. Profit!

PREREQ=""
prereqs()
{
echo "$PREREQ"
}

case $1 in
prereqs)
prereqs
exit 0
;;
esac

# Begin real processing below this line

# load the prepared functions of debians initramfs enviroment
source /usr/share/initramfs-tools/hook-functions

# build the directories
DIRS='/lib /bin /usr/bin /usr/sbin/ /proc/ /root/.ssh/ /var/ /var/run/ /etc/dropbear/'
for now in $DIRS ; do
if [ ! -e ${DESTDIR}$now ]
then
mkdir -p ${DESTDIR}$now
fi
done

# copy the ssh-daemon and librarys
copy_exec /usr/sbin/dropbear /usr/sbin/
copy_exec /usr/bin/passwd /usr/bin/
copy_exec /bin/login /bin/
copy_exec /usr/bin/killall /usr/bin/
copy_exec /sbin/route /sbin/
copy_exec /usr/bin/awk /usr/bin/
#copy_exec /usr/bin/strace /usr/bin/
#copy_exec /bin/nc /bin/
copy_exec /usr/bin/wc /usr/bin/

# some librarys are not autoincluded by copy_exec
copy_exec /lib/libnss_compat.so.2 /lib/
copy_exec /usr/lib/libz.so.1 /usr/lib/
copy_exec /etc/ld.so.cache /etc/
copy_exec /lib/libutil.so.1 /lib/

# we copy config and key files
cp -pr /etc/dropbear/dropbear_dss_host_key ${DESTDIR}/etc/dropbear/
cp -pr /etc/dropbear/dropbear_rsa_host_key ${DESTDIR}/etc/dropbear/
cp -pr /etc/passwd ${DESTDIR}/etc/
cp -pr /etc/shadow ${DESTDIR}/etc/
cp -pr /etc/group ${DESTDIR}/etc/
if [ -e /root/.ssh/authorized_keys ]
then
cp -pr /root/.ssh/authorized_keys ${DESTDIR}/root/.ssh/
fi
cp -pr /etc/nsswitch.conf ${DESTDIR}/etc/
cp -pr /etc/localtime ${DESTDIR}/etc/
cp -pr /lib/tls ${DESTDIR}/lib/

# we don't have bash in our initrd
# also we only add the root account
cat /etc/passwd | grep root | sed s/\\/bash/\\/sh/ > ${DESTDIR}/etc/passwd
cat /etc/shadow | grep root > ${DESTDIR}/etc/shadow
cat /etc/group | grep root > ${DESTDIR}/etc/group

cat >${DESTDIR}/scripts/local-top/network_ssh << 'EOF'
#!/bin/sh

# we start the network and ssh-server

PREREQ=""
prereqs()
{
echo "$PREREQ"
}

case $1 in
prereqs)

prereqs
exit 0
;;
esac

# Begin real processing below this line

# build up helpful environment
[ -d /dev ] || mkdir -m 0755 /dev
[ -d /root ] || mkdir --mode=0700 /root
[ -d /tmp ] || mkdir /tmp
[ -d /sys ] || {
mkdir /sys
mount -t sysfs -o nodev,noexec,nosuid none /sys
}
[ -d /proc ] || {
mkdir /proc
mount -t proc -o nodev,noexec,nosuid none /proc

}

mkdir -p /var/lock
mkdir -p /var/log
touch /var/log/lastlog
mkdir /dev/pts
mount -t devpts -o gid=5,mode=620 /dev/pts /dev/pts

/bin/sleep 5

################# CHANGE THE LINES BELOW #################
# The network setup: edit ip address and gateway to match your needs
ifconfig eth0 172.16.2.128 netmask 255.255.255.0
route add default gw 172.16.2.2
################# CHANGE THE LINES ABOVE #################

# display the network settings for double check
ifconfig

# If you like to use dhcp make sure you include dhclient or pump in
# /etc/initramfs-tools/hooks/dropbear via
# copy_exec /sbin/dhclient


# for debugging ssh-server you may run it in forgound
# /usr/sbin/dropbear -E -F
# for more debugging you may run it with strace
# therfor you have to include strace and nc at top of
# /etc/initramfs-tools/hooks/dropbear via
# copy_exec /usr/bin/strace
# copy_exec /usr/bin/nc
# then start nc on an other host and run
# /usr/sbin/dropbear -E -F 2>&1 | /bin/nc -vv <ip of other host> <nc port of other host>
# e.g.:
# /usr/sbin/dropbear -E -F 2>&1 | /bin/nc -vv 192.168.1.2 8888

# We will use /dev/urandom because /dev/random gets easily blocked
mv /dev/random /dev/random.old
ln -s /dev/urandom /dev/random
# /usr/sbin/dropbear -E -F -b /etc/dropbear/banner -d /etc/dropbear/dropbear_dss_host_key -r /etc/dropbear/dropbear_rsa_host_key -p 22
/usr/sbin/dropbear -b /etc/dropbear/banner -d /etc/dropbear/dropbear_dss_host_key -r /etc/dropbear/dropbear_rsa_host_key -p 22
#ls -al
rm -f /dev/random
mv /dev/random.old /dev/random
EOF
chmod 700 ${DESTDIR}/scripts/local-top/network_ssh

cat >${DESTDIR}/etc/dropbear/banner << 'EOF'

To unlock root-partition run
unlock


EOF

# script to unlock luks via ssh
# dirty but effektive
cat >${DESTDIR}/usr/bin/unlock << 'EOF'
#!/bin/sh

/bin/sh /scripts/local-top/cryptroot

# Kill processes locking boot process
[ `ls /dev/mapper/ | grep -v control| wc -l | awk '{print $1}'` -gt 0 ] && {
for i in `ps | grep -E "cryptroot|cryptsetup" | awk '{ print $1 }'`
do
kill $i
done
}
/bin/sh /scripts/local-bottom/rm_dropbear
EOF

chmod 700 ${DESTDIR}/usr/bin/unlock

# make sure we exit dropbear at the end of the startup process
cat >${DESTDIR}/scripts/local-bottom/rm_dropbear << 'EOF'
#!/bin/sh
PREREQ=""

prereqs()
{
echo ""
}

case $1 in
prereqs)

prereqs
exit 0
;;
esac

# Begin real processing below this line
# we kill dropbear ssh-server

/usr/bin/killall dropbear

EOF
chmod 700 ${DESTDIR}/scripts/local-bottom/rm_dropbear

```

[SIZE="5"]Step 0: Enable root login[/SIZE]

Well, forum policies say, that no root login tutorials must be given (see [here]("http://ubuntuforums.org/showthread.php?t=765414")). However there's plenty or resources out there on the net on how to do that.

The reason why I say that root must be enabled is, because I couldn't work out how to get the whole sudo permission stuff into the initrd. I'm sure there must be a way and if someone is willing to take up the challenge, please go ahead. However you can enable root login only during the creation of the initrd. Once it's created then the according stuff is saved in there and you can remove root login from the actual installation again. The root login is only required to log into dropbear and then run the unlock script. It's not used for anything else.

[SIZE="5"]Step 1: Install required packages[/SIZE]

Install those packages:
```

sudo apt-get install psmisc busybox dropbear

```

[SIZE="5"]Step 2: Configure network[/SIZE]

In the script change the network configuration to your needs. I have sofar only used static ips. The script itself provides also option for dhcp - however I did not try those.
```

################# CHANGE THE LINES BELOW #################
# The network setup: edit ip address and gateway to match your needs
ifconfig eth0 172.16.2.128 netmask 255.255.255.0
route add default gw 172.16.2.2
################# CHANGE THE LINES ABOVE #################

```
The above settings are just the values from my vmware machine on where I tested it.

[SIZE="5"]Step 3: Save the script and make it executable:[/SIZE]

Save the altered script to */etc/initramfs-tools/hooks/dropbear* and make it then executable:
```

sudo chmod +x /etc/initramfs-tools/hooks/dropbear

```

[SIZE="5"]Step 4: Create new initrd[/SIZE]

Run this command to create a new initrd with the name of "netboot". Of course you can rename "netboot" to anything you like.
```

sudo mkinitramfs -o /boot/netboot

```

[SIZE="5"]Step 5: Edit /boot/grub/menu.lst and add your new initrd as the first entry[/SIZE]

Now you have to edit grub's menu list to add the new init.rd.
Run:
```

sudo nano /boot/grub/menu.lst

```
to edit the menu.lst in nano.
Go to the end (or almost) and copy an existing kernel entry e.g.
```

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,1)
kernel          /vmlinuz-2.6.24-19-generic root=/dev/mapper/sda4_crypt ro quiet splash
initrd          /initrd.img-2.6.24-19-generic

```
Change it to something like:
```

title           Netboot
root            (hd0,1)
kernel          /vmlinuz-2.6.24-19-generic root=/dev/mapper/sda4_crypt ro quiet splash
initrd          /netboot

```
Don't copy my example directly but use yours. That way the root hd entry and the mapper name are correct.

Finally, at the top of the menu.lst also change the default boot entry accordingly. If you have 7 kernel entries, then you will put a "6" there because it starts with 0 and you add the netboot one at the bottom.

[SIZE="5"]Step 6: Delete the dropbear script the hooks folder[/SIZE]

When I tried it on my machine, after a kernel upgrade there were some problems (which may have resulted from my earlier tries with a buggy script). Just to make sure, delete the dropbear script from the folder.
```

sudo rm /etc/initramfs-tools/hooks/dropbear

```

[SIZE="5"]Step 7: Profit![/SIZE]

That's it... it should be working now.

[SIZE="5"]A few things to mention[/SIZE]

- Well, in the script I currently call a *ifconfig* after the network configuration. I did that for bugtracing. You can of course delete that from the script.

- After you have now created the netboot initrd you can either change the root password again or disable root login. As the initrd is not encrypted it is possible to get the hash of the root password and so you want to use a different one from remote unlocking the crypto drives. I highly recommend changing the password or disabling root login in the actual machine.

- Although the system is fully encrypted, there are still two possible attacks left to gain access to the data:
(1) ColdBoot Attack by reading the crypto password from the ram blocks (not much you can't do against that without special hardware, see [here]("http://citp.princeton.edu/memory"))
(2) The created initrd can be manipulated so that it logs the crypto password somewhere. As /boot is not encrypted an attacker may gain this way the password for the LUKS-devices. You could, to prevent that, make a bootable cd with the according kernels and initrds and implement some kind of hash check... maybe there are other methods... feedback is welcomed here.

- Most of this tutorial is not from me, just a few adapations and explanations. So thanks goes to Wolfram Coulmann and the others who modified the original script.

---

### Post by kevdog on 2008-06-15
I will try this out this weekend, however, is networking services up, prior to booting into the encrypted partition -- this could potentially be a problem for me -- particularly if a wireless connection isnt up and running.

---

### Post by hyper_ch on 2008-06-15
yes, networking will be up priot to booting into the encrypted partition. You'll have to set this up in the initrd.... good luck with it :)

---

### Post by say2sky on 2008-06-15
> **hyper_ch said:**
> [SIZE="6"]HOWTO: Unlock a LUKS encrypted root partition via ssh[/SIZE]



Thanks a lot for your howto. I hope to ask if it is possible for adsl user.
What files which is related with pppoe should be put into initrd.img and how send the IP to remote user. I think these are two questions, is there a ready resolution to them.

BTW, where you get the ubuntu 8.04.1 version? I haven't find it is out.

---

### Post by hyper_ch on 2008-06-16
I have no clue about pppoe....

But for the ip, you can use dynamic ip client such as dyndns or no-ip... however you'd have to integrate that also into your initrd image. dyndns and no-ip shouldn't be to hard... that's one binary and a config file (or something like that) that you can easily copy to the according dirs and have it run in the script after the network is setup...

---

### Post by say2sky on 2008-06-18
> **hyper_ch said:**
> I have no clue about pppoe....

But for the ip, you can use dynamic ip client such as dyndns or no-ip... however you'd have to integrate that also into your initrd image. dyndns and no-ip shouldn't be to hard... that's one binary and a config file (or something like that) that you can easily copy to the according dirs and have it run in the script after the network is setup...

thanks a lot for help. I will do it and will also try to setup pppoe for adsl so I can access all my files from anywhere through security connection at any time.

---

### Post by hyper_ch on 2008-06-18
well, last time I used a dial-up modem was like 8 years ago... and using modems was bad in w2k also... no clue about linux.

---

### Post by EuleLL on 2008-06-21
Thanks! This works like a charm...

But I got one problem:

After mounting the root partition early crypto disks are mounted (I have a 2nd HDD that is mounted before sshd starts)

is there a way to load sshd before the mounting or keeping beardrop alive until the 2nd password for the 2nd harddrive has been entered?

Cheers,

Eule

---

### Post by hyper_ch on 2008-06-21
well, there is the unlock script you can modify that... but why not auto-mounting the other partitions with a key that is on the root partition?

---

### Post by EuleLL on 2008-06-22
hi there,

to tell you the truth, i would love to do that - but i actually have no clue how to do that - they have the same password anyway...

my setup is as following:

i have on lvm partition on hdd1 that includes the encrypted root, home and swap partitions
and i have one second hdd that has only one encrypted ext3 partition.
ubuntu server (hardy) is running and the system...

I really thankful for any help,

thanks

EuleLL

---

### Post by hyper_ch on 2008-06-22
(1) create a random keyfile
```

sudo dd if=/dev/urandom of=/root/keyfile bs=1024 count=4

```

(2) chmod keyfile to root-read only
```

sudo chmod 0400 /root/keyfile

```

(3) add the key as new possible authorization
```

sudo cryptsetup luksAddKey /dev/sdX /root/keyfile

```

You should first be prompted to authorize yourself with an existing keyfile or password and the should get an output like that:
> 
Enter any LUKS passphrase:
key slot 0 unlocked.
Command successful.


(4) Open /etc/crypttab
```

sudo nano /etc/crypttab

```
and add the new harddisk there (you may already have it added, if so then just alter the existing one)
```

sdX_crypt      /dev/sdX  /root/keyfile  luks

```

(5) Open /etc/fstab
```

sudo nano /etc/fstab

```
and add the new harddisk there (you may already have it added, if so then just alter the existing one)
```

/dev/mapper/sdX_crypt  /media/sdX     ext3    defaults        0       2

```
That would mount it at /media/sdX

That's it, the second harddisk will get unlocked automatically upon booting normally.

---

### Post by EuleLL on 2008-06-22
It works!!! I can't tell you how thankful I am!

You should get a golden medal...


now i can finally put the server away from the desk and completly restart it remotley.

Thanks again,

EuleLL

---

### Post by hyper_ch on 2008-06-22
;) good

---

### Post by pixelbrei on 2008-07-01
Wow, exactly what i need, nice tutorial! Could not test it so far though, because i need to encrypt root on the target machine first...

There still are a few things that i have to say :)

1) about your coldboot / encryption password attacks:
i spend some time thinking about "security" when it comes to remote machines, 
and i do not believe you can protect this password by other means than physically
securing your machine against access from unauthorized persons.
Think about an attacker stealing the dropbear host keys, emulating your machine,
and capturing the password... You can try to get some "security by obscurity", but that's it, i believe.

2) about those many-disk encryption with all the same password:
i used to build my own initrd-init-script which asks for a password, and echoes it 
to the cryptsetup commands... sadly it was unportable like hell, so i'll rather use
the "key file on encrypted root" variant. if an attacker gets into the system far 
enough to read this file, he could also use other variants of getting the key, like 
changing initrd, reading the RAM content, etc. so having the key in a file is no
further security impact i think.

3) i have a difficult situation here, which i'll try to solve, but hints from your side
are welcome, too :)
i have a multi-boot machine, with a root-encrypted winxp (truecrypt) on it. the 
truecrypt bootloader is required to come up _before_ grub gets control. so i need some
way to make the truecrypt bootloader pass on to grub after some timeout, or such.
i did not yet investigate this problem, but i'll post if i find a solution.

so, thanks for this thread!
greets
pixelbrei

---

### Post by hyper_ch on 2008-07-01
> **pixelbrei said:**
> 1) about your coldboot / encryption password attacks:
i spend some time thinking about "security" when it comes to remote machines, and i do not believe you can protect this password by other means than physically securing your machine against access from unauthorized persons. Think about an attacker stealing the dropbear host keys, emulating your machine, and capturing the password... You can try to get some "security by obscurity", but that's it, i believe.

Well, you could put that initrd onto a cd-rom and make that bootable... then you could first check if it's a cd-rom, you could even generate then a md5 check of that cd... in that case, in order to capture, someone would have to boot alternatively and then have a differen md5 checksum... but even that could be fooled somehow... there is no true security but I think it's protected enough and by standard method a cd-rom boot with dropbear should be sufficient to calm everyone but the most paranoid ones (they wouldn't probably go online anyway).

> **pixelbrei said:**
> 2) about those many-disk encryption with all the same password:
i used to build my own initrd-init-script which asks for a password, and echoes it to the cryptsetup commands... sadly it was unportable like hell, so i'll rather use the "key file on encrypted root" variant. if an attacker gets into the system far enough to read this file, he could also use other variants of getting the key, like changing initrd, reading the RAM content, etc. so having the key in a file is no
further security impact i think.
same here... if one can access somehow to root partition and alter it then you are not safe anway... so you only need to care about how secure the root partition...

> **pixelbrei said:**
> 3) i have a difficult situation here, which i'll try to solve, but hints from your side are welcome, too :)
i have a multi-boot machine, with a root-encrypted winxp (truecrypt) on it. the truecrypt bootloader is required to come up _before_ grub gets control. so i need some way to make the truecrypt bootloader pass on to grub after some timeout, or such. i did not yet investigate this problem, but i'll post if i find a solution.
if I understand correctly, then truecypt will put its own bootloader and then goes directly to boot the ms bootloader... I'm not sure if you can change that... however it should be possible to alter the windows bootloader in a way, that it can load linux instead...
A quick google serach returned this: [http://www.linuxquestions.org/questions/linux-software-2/grub-redhat-7.2-enigma-and-win2k-dual-boot-8294/](http://www.linuxquestions.org/questions/linux-software-2/grub-redhat-7.2-enigma-and-win2k-dual-boot-8294/)
I did not read it completely but it seems to be a howto on how to boot linux from a windows boot loader. Let me know of the results.

---

### Post by pixelbrei on 2008-07-01
> **hyper_ch said:**
> 
if I understand correctly, then truecypt will put its own bootloader and then goes directly to boot the ms bootloader... I'm not sure if you can change that... however it should be possible to alter the windows bootloader in a way, that it can load linux instead...
A quick google serach returned this: [http://www.linuxquestions.org/questions/linux-software-2/grub-redhat-7.2-enigma-and-win2k-dual-boot-8294/](http://www.linuxquestions.org/questions/linux-software-2/grub-redhat-7.2-enigma-and-win2k-dual-boot-8294/)
I did not read it completely but it seems to be a howto on how to boot linux from a windows boot loader. Let me know of the results.

wow, that was a quick response :)
i didn't look into your link, because i searched the truecrypt forum and 
found a way of inverting the order of grub and truecrypt.
just tested it, and it worked fine. here is the link:
[http://forums.truecrypt.org/viewtopic.php?p=41943#41943](http://forums.truecrypt.org/viewtopic.php?p=41943#41943)
so, i will now set up my machine to encrypted root fs :)

---

### Post by hyper_ch on 2008-07-01
nice, will have a look at the TC forum also ;)

---

### Post by pixelbrei on 2008-07-01
Ok, now i tried this script, and there are two things that should be mentioned:

1) it is (or may be) necessary to add your nic driver module to /etc/initramfs-tools/modules. i had to do so.
2) the script does not work with splash screen enabled (at least not for me).

but apart from that, it works like a charme :) really cool!

---

### Post by say2sky on 2008-07-22
> **hyper_ch said:**
> (1) create a random keyfile
```

sudo dd if=/dev/urandom of=/root/keyfile bs=1024 count=4

```

(2) chmod keyfile to root-read only
```

sudo chmod 0400 /root/keyfile

```

(3) add the key as new possible authorization
```

sudo cryptsetup luksAddKey /dev/sdX /root/keyfile

```

You should first be prompted to authorize yourself with an existing keyfile or password and the should get an output like that:


(4) Open /etc/crypttab
```

sudo nano /etc/crypttab

```
and add the new harddisk there (you may already have it added, if so then just alter the existing one)
```

sdX_crypt      /dev/sdX  /root/keyfile  luks

```

(5) Open /etc/fstab
```

sudo nano /etc/fstab

```
and add the new harddisk there (you may already have it added, if so then just alter the existing one)
```

/dev/mapper/sdX_crypt  /media/sdX     ext3    defaults        0       2

```
That would mount it at /media/sdX

That's it, the second harddisk will get unlocked automatically upon booting normally.

following command
```
cryptsetup luksOpen /dev/sdb1 sdb1 --key-file /etc/keys/keyfile
```
can be used when needed to map the encrypted partition

my question is 
is it possible to map encrypted root partition of remote system which have dropbear running from user's desktop by using a keyfile stored in user's desktop system?

use something similar 
```

ssh username@192.168.0.100 cryptsetup luksOpen /dev/sdb1 sdb1 --key-file remote system's keyfile

```

---

### Post by hyper_ch on 2008-07-22
in one of my old howtos (rsyncing) I have a command to issue a command over ssh. Have a look here: [http://www.howtoforge.com/rsync_incremental_snapshot_backups](http://www.howtoforge.com/rsync_incremental_snapshot_backups)

Search especially for the command above this line: This will run a the mysql backup scrip on the production server.

With that you can execute a shell script (or run a command) on the other server. However I'm not sure how you would send to local stored key over the ssh command to the "exec" part on the remote server. You'll have to try that yourself.

---

### Post by say2sky on 2008-07-22
> **hyper_ch said:**
> in one of my old howtos (rsyncing) I have a command to issue a command over ssh. Have a look here: [http://www.howtoforge.com/rsync_incremental_snapshot_backups](http://www.howtoforge.com/rsync_incremental_snapshot_backups)

Search especially for the command above this line: This will run a the mysql backup scrip on the production server.

With that you can execute a shell script (or run a command) on the other server. However I'm not sure how you would send to local stored key over the ssh command to the "exec" part on the remote server. You'll have to try that yourself.

Thanks a lot for your info. 
I know ssh and rsync both can run command on remote system. 
I hope not to store keyfile on a unencrypted partition, so I want to use keyfile on desktop system to open the root partition on server. This is good security solution and also can achieve the automatically copy/rsync file between server and desktop with encrypted partition. 
I will try it.

---

### Post by say2sky on 2008-07-23
to hyper_ch:

I tried but not work. I hope to ask do you think it is possible to use local keyfile to mapping remote encrypted partition through ssh server like your suggested one. 

I think you are an expert about ssh, LUKS and related thing and have deep understanding about all these. 

Thanks a lot for your help.

---

### Post by hyper_ch on 2008-07-24
is there a reason you want to use a keyfile?

You could try to include sshfs or nsf into the initramfs and then mount your local partition/folder into the remote system and then use the keyfile... that way the keyfile won't be written onto the server's unencrypted space.

---

### Post by say2sky on 2008-07-24
> **hyper_ch said:**
> is there a reason you want to use a keyfile?

You could try to include sshfs or nsf into the initramfs and then mount your local partition/folder into the remote system and then use the keyfile... that way the keyfile won't be written onto the server's unencrypted space.

My reason is:
use  your howto about LUKS encrypted root partition to run my system at home but keep root partition security  and when I am outside at any place I can automatically sync my data into home server by regular interval, if no keyfile can be used I cannot set an automatically cron.

---

### Post by moep on 2008-07-28
Thanks a lot for this tutorial, it’s extremely helpful.


Setting up the script on 8.04.1 was a breeze but I can’t seem to get DHCP working.
I've added 

```
copy_exec /sbin/dhclient /sbin/
```

to the top of the script and commented out the ifconfig/route commands without much luck.
Is there a step I'm missing here?

Also, I would like to customize dropbear by changing the port it’s listening to and removing the banner. How would I do this?

---

### Post by hastala on 2008-08-10
hi,

what do i have to do to add a second encrypted volume to the dropbear script? i saw the tutorial for storing the second key on the encrypted root volume, but that doesn't feel like an option for me.

---

### Post by hyper_ch on 2008-08-10
> **moep said:**
> setting up the script on 8.04.1 was a breeze but I can’t seem to get DHCP working.
Why do you want to use DHCP?

> **moep said:**
> Also, I would like to customize dropbear by changing the port it’s listening to and removing the banner. How would I do this?
Well, have a look at dropbear config.

> **hastala said:**
> what do i have to do to add a second encrypted volume to the dropbear script? i saw the tutorial for storing the second key on the encrypted root volume, but that doesn't feel like an option for me.

What's wrong with using a key to make the other volumes transparent?

---

### Post by hastala on 2008-08-10
> What's wrong with using a key to make the other volumes transparent? 

well, if my root volume goes bazonk for some reason, i'd be lost. i know i could have the keyfile stored in some other place as a backup, but i'd have to have this other place encrypted too...

do you know how to make the cryptroot script see my other volume? 

or could i put sth. like
```
cryptsetup luksOpen /dev/md0 md0_crypt
mount /dev/mapper/md0_crypt /mountpoint
```
in some place in the initrd?
if yes, where would that be?

---

### Post by hyper_ch on 2008-08-10
> **hastala said:**
> well, if my root volume goes bazonk for some reason, i'd be lost. i know i could have the keyfile stored in some other place as a backup, but i'd have to have this other place encrypted too...
you can have up to 10 passwords/keys stored in an encrypted volume for uncrypting it.

---

### Post by hastala on 2008-08-10
> **hyper_ch said:**
> you can have up to 10 passwords/keys stored in an encrypted volume for uncrypting it.

i knew you were gonna say this ;)

still, there's some downsides to that, e.g. if somebody has access to my root volume (which is not THAT critical to me, i basically just encrypted it because the alternate installer for 8.04 allowed me to do it and i knew about the hassle of doing it later on).

do you know where sth. like unencrypting and mounting another partition should be in the initrd? or how to add / alter the cryptroot file?

---

### Post by hal2100 on 2008-12-02
Hello,

is there a way to add the "unlock via ssh" funtion permanently to the boot images? Everytime my ubuntu fetches a kernel update I have to recreate the procedure. Sometimes I have to start the new kernel by the "old" way to create an updated netboot image, otherwise the disks are not found.

---

### Post by hyper_ch on 2008-12-02
you can still use the old initramfs and alter the grub entry to direct it then at the new real kernel... works for me.

---

### Post by raouf.d on 2008-12-29
Hi everybody,

I have the same issue as hal2100, on a test server running 8.04 with 2.6.24-16 and the custom boot image for unlocking luks, what I'm trying right now is build a new kernel (2.6.28 with ext4 support) so the kernel build and install successfully but at reboot, I can't unlock luks even with the console.

Dropbear shows itself, but when I put enter unlock command nothing happens excepts he kick me off.

When I try the new kernel with the old netboot image as you say hyper_ch I got some error messages about missing modules.

Does anyone of you have done something similar?

---

### Post by hyper_ch on 2008-12-29
hmmm, strange :(

---

### Post by raouf.d on 2008-12-29
I tried on a new server, freshly installed. I installed the new kernel

> raouf@hades:~$ sudo dpkg -i linux-image-2.6.28-nct-optimized_i386.deb 
Selecting previously deselected package linux-image-2.6.28-nct-optimized.
(Reading database ... 24973 files and directories currently installed.)
Unpacking linux-image-2.6.28-nct-optimized (from linux-image-2.6.28-nct-optimized_i386.deb) ...
Done.
Setting up linux-image-2.6.28-nct-optimized (2.6.28-nct-optimized-10.00.Custom) ...

 Hmm. There is a symbolic link /lib/modules/2.6.28-nct-optimized/build
 However, I can not read it: No such file or directory
 Therefore, I am deleting /lib/modules/2.6.28-nct-optimized/build


 Hmm. The package shipped with a symbolic link /lib/modules/2.6.28-nct-optimized/source
 However, I can not read the target: No such file or directory
 Therefore, I am deleting /lib/modules/2.6.28-nct-optimized/source

Running depmod.



On reboot I got this time the prompt for uncrypting the partition, helpless.

How is it possible to generate a new initrd for 2.6.28 with the 2.6.24, or am I missing something.

r@

---

### Post by deadball on 2009-01-17
It works fantastic.

But i have used the script from [http://debian.mandel.name/template/etc/initramfs-tools/hooks/dropbear](http://debian.mandel.name/template/etc/initramfs-tools/hooks/dropbear) which appears to be newer

But there are some warnings:
```

/scripts/local-top/cryptroot: line 338: modprobe: not found
Enter passphrase to unlock the disk /dev/disk/.....:
key slot 0 unlocked.
Command successful.
/scripts/local-top/cryptroot: line 1: lvm: not found

```

AND ssh always give me security alert, cuz of ssh keys. Didn't take dropbear over my openssh keys? That was said during the installation.
Can i manually add the keys?

But i wonder how safe the whole thing is. E.g. someone cracks my root pw (its different of my "real" root pw), can he do something in busybox?

Could he delete/corrupt my partition or sth even worse?

Or should i just give the root acc a strong pw and thats it? Same danger as the "normal" ssh?

Is the script itself "secure", that means it doesn't save the password anywhere or sth?

Best regards,
db

---

### Post by hyper_ch on 2009-01-17
he could potentially then alter the initrd for the remote unlocking... besides that I wouldn't know what he could do.... once you created that initrd you should disable root again...

Well, if you have LVM and need it, then you need to load the according drivers and stuff also into the intitrd that is created...

---

### Post by deadball on 2009-01-17
And then i give him my key :D

Is there an other way to alter the initrd except getting root or local access?

So i think it's okay for me. Mb i add hashes or so. 

Could u give me a tip regarding the ssh keys (see edit above:))

Thanks!

Best regards,
db

---

### Post by hyper_ch on 2009-01-17
the initrd is just there to create a "preboot" starting that allows different services to be started... if you have a look it's only about 11 mb in size ;)

While the initrd is started, the drive still remains encrypted. So that means even if someone gets access to your initrd they still have no access to the data. However it that person is skilled, he could alter the initrd and implement a keylogger or something.

The initrd does not store the key to unlocking the partition anywhere. All it does is implement the necessary tools to start networking, a light ssh server and the necessary things to unlock the encrypted partition(s).

The safest would be to have a different root password for the initrd than you use for anything else and disable root after creating the initrd...

If you're worried about someone messing with your initrd, you could even burn it onto a cd and then alter the grub entry to use the one on the cd...

---

### Post by hyper_ch on 2009-01-17
to modify just that initrd you could do this

(1) make a directory somewhere and go there
```

mkdir ~/Desktop/netboot
cd ~/Desktop/netboot

```

(2) extract the initrd
```

gunzip < /boot/netboot | cpio -i --make-directories

```

Now you have all the stuff available. This means you could now manually modify the /etc/passwd file and group files and alter passwords there...

(3) re-create the initrd with the altered info (in the ~/Desktop/netboot folder)
```

find ./ | cpio -H newc -o > netboot.cpio
gzip netboot.cpio
cp netboot.cpio.gz /boot/netboot2

```
--> I copied it to a new name so the working one will be preserved and you can just test the altered one ;)

---

### Post by deadball on 2009-01-24
Is anybody working on this script?

Will it be included in the Kernel at some time?

---

### Post by hyper_ch on 2009-01-25
I don't think it will be included in the kernel... and yes, I use it on three boxes ;)

---

### Post by whin on 2009-01-25
ow thanks for the help, this what im looking

---

### Post by deadball on 2009-01-25
Do you use exactly this Version?

What's with this version: 
[http://debian.mandel.name/template/etc/initramfs-tools/hooks/dropbear](http://debian.mandel.name/template/etc/initramfs-tools/hooks/dropbear)

---

### Post by hyper_ch on 2009-01-25
I use this version and a different one for etch. no clue about that other one.

But if you look at the modified history of that one, my version is included there also ;)

---

### Post by deadball on 2009-01-25
:D yep.

I see. I'll try this script (i needed to reinstall, because of a forgotten password.. - a good advice: NEVER change your luks pws at 4:00 when you go to sleep after that :D)

Schöne Grüße nach Switzerland ;)

---

### Post by hyper_ch on 2009-01-25
you can't just "change" a luks password... you can only add a new one and then delete the old one ;) good luck with the script. I'd also be interested to hear how that modified version works.

---

### Post by deadball on 2009-01-25
Actually i added a new improved one and killed the old slot.

good idea :D

I'll report how its goin

---

### Post by deadball on 2009-01-30
Cool:

[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002590.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002590.html)

> 
 * Document how to enable remote device unlocking via dropbear ssh server
    in the initramfs during boot process. Thanks to Chris <debian at x.ray.net>
    for the great work. (closes: #465902)


---

### Post by hyper_ch on 2009-01-30
nice finding :)

---

### Post by deadball on 2009-01-30
Was luck. But maybe this script will really be included some time :D:D

---

### Post by hyper_ch on 2009-01-30
would be nice... the only thing that would be great in addition would be to have a seperate user/password list for those that can login in dropbear.

I did enable root, setup the remote login, disabled root again... I didn't want to have anybody else login - i mean I don't want to have the same login credentials :)

---

### Post by deadball on 2009-01-30
You can create your own.. The hook script only copies /etc/shadow and /etc/password .. mb you can adjust the path in the hook.

Yesterday I realised via ps ax that a process "askpass" (or somtheing like that, i'll look later) is still running when the system is up. Where does it come from? :D

---

### Post by hyper_ch on 2009-01-30
I know I can :) there just needs to be a "confortable" way to make sure of that ;)

---

### Post by junxx on 2009-01-30
> **hyper_ch said:**
> [SIZE="6"]
- Although the system is fully encrypted, there are still two possible attacks left to gain access to the data:
(1) ColdBoot Attack by reading the crypto password from the ram blocks (not much you can't do against that without special hardware, see [here]("http://citp.princeton.edu/memory"))
(2) The created initrd can be manipulated so that it logs the crypto password somewhere. As /boot is not encrypted an attacker may gain this way the password for the LUKS-devices. You could, to prevent that, make a bootable cd with the according kernels and initrds and implement some kind of hash check... maybe there are other methods... feedback is welcomed here.

- Most of this tutorial is not from me, just a few adapations and explanations. So thanks goes to Wolfram Coulmann and the others who modified the original script.

Greetings!

I am also looking since quite some time for a way that supports remote prebooth authentification for whole disc encryption. This solution comes quite close, however as you wrote the /boot partition can be altered with e.g. a keylogger or so. Since a month or so I am toying around with a yubikey([http://www.yubico.com/home/index/](http://www.yubico.com/home/index/)) which is basically a OTP token. The neat thing is that its realisation is kinda a 1 button usb keyboard, so no drivers etc. are needed and validation is done via a webservice (at yubico, however you can also setup your own server for validation as all tools they provide are open source). 

There are already pam modules that support yubikey, but that does not solve the problem how to securely mount an encrypted disc on a remote server. I think if the authors of LUKS/dm-crypt would integrate yubikey authentification as an optional feature we solved our problem. If the /boot is altered in some way to log passwords it wont matter since we are using OTP. 

What do you think about the idea? Could that work? At the moment I see 2 problems:

1.) If we add yubikey OTP auth. as another layer like i.e. first provide yubikey, after that provie the password -> same problem as before, password can be logged. One might say that they cannot get to the password login without yubikey, but if they can install a keylogger they might as well try to directly mount the volume or change the sourcecode of dm-crypt to ignore yubikey since the key itself is not used for the encryption. 

2.) If we use the yubikey password to encrypt the device then we have the problem that the drive is encrypted with password A and on next login the key will generate a password B...


Any discussions or ideas are welcome.

---

### Post by sampei7777 on 2009-02-09
> **hyper_ch said:**
> 
The safest would be to have a different root password for the initrd than you use for anything else and disable root after creating the initrd...


Thank You, it worked very well for me.

But now I have a problem: when I disable the root account the cron jobs do not run as root.

In the syslog I have:
CRON[]: Authentication failure

If I enable the root account, it works.
So is it possible to do a cron job as root having the root account disabled?

Thank You

PS: ubuntu Server 8.10 64 bit, kernel: 2.6.27-11-server, x86_64

---

### Post by hyper_ch on 2009-02-09
How did you disable root?

```

sudo passwd -l root

```?

---

### Post by sampei7777 on 2009-02-09
> **hyper_ch said:**
> How did you disable root?

```

sudo passwd -l root

```?

Yes. I did

```
sudo passwd -l root
```

and cron does not work as root.

Then, if I do

```
sudo passwd -u root
```

it works.

---

### Post by hyper_ch on 2009-02-09
then just set a very, very, very complex password for it.

---

### Post by DWGS on 2009-08-06
has anyone got this working on ubuntu 9.04? I would like to be able to use it but I can't seem to get it work. It seems my networking is not brought up early enough.

---

### Post by timc3 on 2009-09-02
I was also thinking about looking into it for Ubuntu 9.04? Any luck trying?

---

### Post by __phil__ on 2009-10-26
installation worked fine except those these 2 message:
"ln: .... "/tmp/mkinit..//lib//libnss_compat.so.2": file exists <- don't know what's the problem here
libz.so.1 not found <- i edited the script to use libz.so instead
furthermore I had to copy crypt* from /usr/share/initramfs-tools/scripts/local-top/ to etc/initramfs-tools/scripts/local-top/


basically it's working as i can login from remote to this busybox, but seems modprobe is not installed and I don't know how to fix it. :(
# unlock
/scripts/local-top/cryptroot: line 341: modprobe: not found

---

### Post by __phil__ on 2009-10-26
the error msgs disappeared after replacing modprobe with /sbin/modprobe but when i try "unlock MYPASSWORD" the call doesn't come back and it stucks on ssh I can cancel with ctrl+ c and retry, but no chance for remote login :(

---

### Post by YarekT on 2009-11-01
Hi everyone
im new to the forums, I have a server at work which got lots of my code there so i would like to protect it against any theft and the like. But the inconvenience is that I cannot reboot it remotely. My idea was to store a keyfile which unlocks the root partition in the boot partition for the period of the reboot, ie. copy keyfile, reboot, delete keyfile.
Ive been messing about with it but ended up bricking the box (i was trying it remotely). Now its probably sitting waiting for the password or some other error. But no matter, ill fix it when im back at work.
Do you guys think this is a workable solution? i tried copying the keyfile to boot but it didnt work, probably because theres something to do with the configuration, since /etc/crypttab is not accessible during boot.

---

### Post by hal2100 on 2010-05-02
Hello,

this solution doesn't seem to work on Lucid anymore. But there seems to be a prepared solution already. As far as I understand the old workaround blocks the new solution or I cannot find a way to enable the new solution.
Dropbear seems to be running, but I am unable to log in.

Thanks for any infos on this topic.

---

### Post by chris2407 on 2010-05-14
hi guys,

im using Ubuntu 10.04 LTS Lucid encrypted by Luks. I followed all instructions and executed all comands all seemed to be fine but i dont know what to do at this step:

> [SIZE=5]Step 5: Edit /boot/grub/menu.lst and add your new initrd  as the first entry[/SIZE]
cause the file menu.lst does not exist in this folder and i dont know what to type into this file... what could i do about it?

i think grub is replaced by grub 2 now and the menu.lst file is replaced by [B][I]grub.cfg in the wiki it clearly says that i should not edit this file... what do you guys think?

thanks
[/I][/B]

---

### Post by chris2407 on 2010-05-14
i tried to edit the [B][I]grub.cfg but was not sure about it what to edit... im also not sure about other parts of this tutorial... could someone please help me with this? I have teamviewer running on the Ubuntu machine maybe somebody could configure this for me? I would highly appreciate it.

My msn is: [email]chris2407@hotmail.com[/email]

many thanks
[/I][/B]

---

### Post by m3w2 on 2010-05-15
> **chris2407 said:**
> i tried to edit the [B][I]grub.cfg but was not sure about it what to edit... im also not sure about other parts of this tutorial... could someone please help me with this? I have teamviewer running on the Ubuntu machine maybe somebody could configure this for me? I would highly appreciate it.

My msn is: [EMAIL="chris2407@hotmail.com"]chris2407@hotmail.com[/EMAIL]

many thanks
[/I][/B]

If you get it working, please post the solution. I'm having the same problem.

---

### Post by koba101 on 2010-05-26
ok this is weird ....what worked for me was keeping the exact same boot configurations as the rest including quiet and splash and when the screen freezes on boot i enter the passphrase 

>  linux ($sgd_linux_kernel)$sgd_vmlinuz_path root=UUID=$sgd_root_uuid
 quiet splash


not the best of solutions but works for now

---

### Post by johnt0000 on 2010-07-19
For those of you have problems editing the grub menu.

Ubuntu 10.04 uses Grub2, it doesn't like the grub.cfg edited manually.

My (temporary (will break with kernel updates and the like)) solution:
open /boot/grub/grub.cfg and copy the default menuentry

create a new script in /etc/grub.d/41_netboot

#########contents##########

echo "Adding netboot" >&2
cat << EOF
    menuentry "netboot" {
        ***insert contents from copied default menuentry here, replacing the initrd line with the one below**
        initrd  /netboot
    }

EOF

###########################
make this executable
then run update-grub

to set as default edit /etc/defaults/grub
and change
GRUB_DEFAULT=0
to
GRUB_DEFAULT="netboot"

I got that far, and the server has got to the stage where the ssh opens, but any user/pass gets denied.

any idea?

John

---

### Post by Dedas on 2010-12-12
I'm trying to do this with 10.10 but no luck. For instance, I do not have a /etc/initramfs-tools/root folder. Anyone in the same boat?

---

### Post by DarkBabar on 2010-12-14
> **Dedas said:**
> I'm trying to do this with 10.10 but no luck. For instance, I do not have a /etc/initramfs-tools/root folder. Anyone in the same boat?

This tutorial is badly outdated. Take a look at this instead:
/usr/share/doc/cryptsetup/README.remote.gz

---

### Post by DarkBabar on 2010-12-22
I'm having trouble getting this to work. I've described my problem here: [http://ubuntuforums.org/showthread.php?p=10269823](http://ubuntuforums.org/showthread.php?p=10269823)
Has anyone gotten this to work with 10.10?

---

