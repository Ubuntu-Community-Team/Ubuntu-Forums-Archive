---
title: "Connecting 2 ubuntu pcs using crossover cable for data transfer"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by ask_ on 2011-12-23
Hello,

My goal is to transfer a few files from one computer to another.
One is running Lubuntu 11.10 other is running Ubuntu 11.10.

I have a ethernet crossover cable to connect the two.

I followed the tips given here [http://www.ehow.com/how_8363411_connect-two-linux-pcs.html](http://www.ehow.com/how_8363411_connect-two-linux-pcs.html) 
.
The two PCs are pinging to each other but I don't know how to copy files from one to another. How to do so?

Thanks.

---

### Post by CharlesA on 2011-12-23
nfs is dead easy to set up.

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

I use ssh and rsync myself, but that can get complicated if you are sharing files between machines.

---

### Post by ask_ on 2011-12-23
> **CharlesA said:**
> nfs is dead easy to set up.

.

I wish I could say the same. :) . Since I am a beginner, I am finding it daunting. Still I will give it a shot.
One quick question though, will it do if I only follow the steps given in the quick start section? (I mean are they a short cut guide for simple setup,without security?)

Also , I have a doubt in following instruction
> Let's say we want to export our users' home directories in /home/users. First we create the export filesystem:
# mkdir -p /export/users 

Is 'users' a placeholder for the username whose files I wish to share ? Or should I use the 'users' as it is ?

---

### Post by ChimeraMica on 2011-12-23
If you're looking for something extremely simple, Giver is a decent application.

---

### Post by CharlesA on 2011-12-23
> **ask_ said:**
> I wish I could say the same. :) . Since I am a beginner, I am finding it daunting. Still I will give it a shot.
One quick question though, will it do if I only follow the steps given in the quick start section? (I mean are they a short cut guide for simple setup,without security?)

Also , I have a doubt in following instruction


Is 'users' a placeholder for the username whose files I wish to share ? Or should I use the 'users' as it is ?
I am not sure. I haven't used nfs on my machines, since I use ssh a lot.

Personally, I would just use a thumb drive if it's just a few files. Otherwise just install openssh-server and copy them via sftp.

---

### Post by oldfred on 2011-12-23
I use nfs and have scripts to recreate it on a new install, mount folders & then rsync from Desktop or Laptop. I even get confused with my scripts as the folders are identical in both systems but I mount one or the other with a LT or DT to try to keep them apart.

On a new install I include this in my new install script, earlier in script I created the folders and added the mounts to fstab :

```
#NFS setup
fname_exp=/etc/exports
nfs1="/mnt/data 192.168.1.0/24(rw,no_root_squash,async)"
nfs2="/mnt/shared    192.168.1.0/24(rw,no_root_squash,async)"
echo $nfs1 >> $fname_exp
echo $nfs2 >> $fname_exp

```

You have to install the nfs files:

```
# For NFS /etc/exports already edited
apt-get install nfs-kernel-server nfs-common portmap
#
dpkg-reconfigure portmap
exportfs -a
service portmap restart


```
Then on either laptop or Desktop I have a file like this - one has LT the other DT.
This mounts laptops folder into Desktop, My desktop has fixed IP, but sometimes I have to edit the IP of the laptop script:

```

#!/bin/bash
# check that exports has been updated and path is correct
#/etc/exports
#/mnt/data 192.168.1.0/24(rw,no_root_squash,async)
#/mnt/shared    192.168.1.0/24(rw,no_root_squash,async)

sudo mkdir /mnt/data_LT
sudo mkdir /mnt/shared_LT
sudo mount 192.168.1.120:/mnt/data /mnt/data_LT
sudo mount 192.168.1.120:/mnt/shared /mnt/shared_LT

```then I run this to copy files from LapTop to DeskTop:

```
#!/bin/bash
# run Mount_NFS.sh first
# a - archive, retain file settings
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
echo "starting..."

rsync -aruvP /mnt/data_LT/Documents /mnt/data
rsync -aruvP /mnt/data_LT/Projects //mnt/data
rsync -aruvP /mnt/data_LT/PDF /mnt/data
rsync -aruvP /mnt/data_LT/kmymoney /mnt/data
#
rsync -aruvP /mnt/shared_LT/OfficeFiles /mnt/shared
rsync -aruvP /mnt/shared_LT/mozilla /mnt/shared
#rsync -aruvP /mnt/shared_LT/Photos/All2010 /mnt/shared
rsync -aruvP /mnt/shared_LT/Photos/All2011 /mnt/shared
```

HOWTO: NFS Server/Client if no windows 
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)

---

### Post by ask_ on 2011-12-24
Thanks for the help people.

Actually what I wanted to do would be easily done if I use a thumb drive as pointed out by CharlesA.

I hadn't imagined this thing to be as detailed as outlined.
But now that I have seen the docs,it seems fun to try it out this way rather than using thumb drive. 

The newer links provided seem to be more easier to understand for a person of a beginner level such as me,than the community help page. This one in particular -
[http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)

Just one doubt though, I should use the 'ifconfig' command to configure my ip,right ?

And once configured how long does the ip remain that way? Does the LAN ip address remain the same till I change it next time by ifconfig ?

---

### Post by HermanAB on 2011-12-24
Well, the easiest servers to set up are FTP and SSH.  Proftpd, vsftpd and sshserver all work out of the box.  People only run into problems with those if they change the configuration.

---

### Post by CharlesA on 2011-12-24
> **ask_ said:**
> 
Just one doubt though, I should use the 'ifconfig' command to configure my ip,right ?

And once configured how long does the ip remain that way? Does the LAN ip address remain the same till I change it next time by ifconfig ?

I've never used ifconfig to set the ip address, but once you configure it, it should stay until reboot if /etc/network/interfaces tells it something different. That is where I usually change the ip of a network card.

> **HermanAB said:**
> Well, the easiest servers to set up are FTP and SSH.  Proftpd, vsftpd and sshserver all work out of the box.  People only run into problems with those if they change the configuration.

+1 to ssh. That would probably be the easiest way to do it, almost no config and you can use sftp from a terminal or something like Filezilla to connect.

---

### Post by ask_ on 2011-12-24
> **CharlesA said:**
> I've never used ifconfig to set the ip address, but once you configure it, it should stay until reboot if /etc/network/interfaces tells it something different. That is where I usually change the ip of a network card.



+1 to ssh. That would probably be the easiest way to do it, almost no config and you can use sftp from a terminal or something like Filezilla to connect.

I am unable to understand the instructions given for nfs.(I have done the work by flash drive by the way,but just wanted to try this for fun, no pressure)

I will try out ssh too. Could you provide links for ssh ?
And does ssh need active internet connection ? Or the data can be transferred via crossover cable directly ? I am able to ping the computer via terminal.


Thanks.

---

### Post by jerome1232 on 2011-12-24
I don't understand what's wrong with right clicking the folder, clicking sharing options and tada, shared. (I believe that will use samba but it will setup things for you)

Alternatively install openssh-server on both machines and use nautilus's built in sftp browser.

edit: I missed the Lobuntu part, since I doubt it uses nautilus that kinda scraps my whole point :{

---

### Post by zero2xiii on 2011-12-24
Wow,

Sooooo complicated for something soooo very simple? Why not just install samba, and share the folder and use the network to transfer? Dead easy, and ZERO setup... Unless you call "Right click > Sharing options > Share + allow guest access" as setup...

What SSH concerns, it also has the minimum setup:
[http://www.jonathanmoeller.com/screed/?p=1585](http://www.jonathanmoeller.com/screed/?p=1585)
just ssh into the computer as a user already on the computer eg:
Computer A ssh into computer B, Computer B has an account called Bob:

```
ssh bob@192.168.1.2 #IP adress is only an example adress
```

then cd to the folder you want the files from and copy it from there to the local machine...

Googling this have me confused, seemed like you have to pipe and redirect outputs, you cant simply do it step by step:
[http://stackoverflow.com/questions/343711/transferring-files-over-ssh](http://stackoverflow.com/questions/343711/transferring-files-over-ssh)

Last link:
[http://polishlinux.org/apps/ssh-tricks/](http://polishlinux.org/apps/ssh-tricks/)

Might work best if you HAVE to use ssh... Dead simple, I just setup and coppied several files from my 2 computers with this... Seems simple enough. Just setup ssh-server (or just install and use an already existing account) and then use that SCP command. Pretty straight forward...
Although the syntax is pretty simple...

Still, stick to samba is my suggestion..

Cherz

---

### Post by Paqman on 2011-12-24
> **ask_ said:**
> 
I have a ethernet crossover cable to connect the two.


Just a small point: on any computer made in the last few years you don't need a crossover cable. You can use any cable, and the network card detects that it's connected directly to another computer and sorts the pins out. You only need a crossover on really old hardware.

Personally I would just pop open the case, take the hard drive out and plug it into a spare SATA/IDE header on the other machine. Boot up and transfer away at tiptop speed.

---

