---
title: "Object Storage won't automount?"
date: 2024-04-22
forum: New to Ubuntu
---

### Post by rsaz904 on 2024-04-22
Hello all,

I am new to linux / ubuntu / servers / everything.  I've recently dabbled into setting up my own cloud drive service using nextcloud.  I have ubuntu 22.04 running on an Oracle Cloud Instance and I have created an Object storage bucket on Oracle as well.  I am able to get the storage bucket mounted and I have verified files that are uploaded in the oracle web portal are viewable in the mounted folder and vice versa.

command used to mount: sudo s3fs nextcloudbucket [COLOR=#0000ff]/ncbucket -o endpoint=us-ashburn-1 -o passwd_file=.passwd-s3fs -o url=https://xxxxxxxxx.compat.objectstorage.us-ashburn-1.oraclecloud.com/ -o nomultipart -o use_path_request_style -o allow_other[/COLOR]

The problem I am having is as soon as I reboot the drive becomes unmounted again.

bucket name in oracle : nextcloudbucket
folder name: /ncbucket
actual instance name is included in place of xxxxxxxxx

I have tried placing the following command into /etc/fstab:  [COLOR=#0000ff]s3fs#nextcloudbucket /ncbucket fuse _netdev,allow_other, use_path_request_style, passwd_file=${HOME}/.passwd-s3fs, url=https://xxxxxxxx.compat.objectstorage.us-ashburn-1.oraclecloud.com/ 0 0[/COLOR]

It appears to save correctly but does not remount the drive on reboot.  
I also added the following while troubleshooting but Im not sure its really needed. [COLOR=#0000ff]systemctl enable NetworkManager-wait-online.service[/COLOR]
  
Thanks for any help you can lend!  See below for inputs / outputs:
[COLOR=#0000ff]
ubuntu@hcp:~$ ls -al[/COLOR]
total 144
drwxr-x--- 6 ubuntu ubuntu  4096 Apr 22 16:50 .
drwxr-xr-x 6 root   root    4096 Apr 20 01:59 ..
-rw------- 1 ubuntu ubuntu  7904 Apr 22 16:51 .bash_history
-rw-r--r-- 1 ubuntu ubuntu   220 Jan  6  2022 .bash_logout
-rw-r--r-- 1 ubuntu ubuntu  3771 Jan  6  2022 .bashrc
drwx------ 2 ubuntu ubuntu  4096 Apr 20 01:37 .cache
drwxrwxr-x 3 ubuntu ubuntu  4096 Apr 22 14:27 .local
-rw------- 1 ubuntu ubuntu    86 Apr 22 14:30 .passwd-s3fs
-rw-r--r-- 1 ubuntu ubuntu   807 Jan  6  2022 .profile
drwx------ 2 ubuntu ubuntu  4096 Apr 20 01:27 .ssh
-rw-r--r-- 1 ubuntu ubuntu     0 Apr 20 01:39 .sudo_as_admin_successful
-rw-r--r-- 1 root   root   82228 Apr 20 01:50 hst-install-ubuntu.sh
-rw-r--r-- 1 root   root    4497 Apr 20 01:49 hst-install.sh
drwxr-xr-x 2 root   root    4096 Apr 22 16:41 ncbucket
-rw-rw-r-- 1 ubuntu ubuntu     6 Apr 22 16:40 test2.txt
[COLOR=#0000ff]ubuntu@hcp:~$ df -h[/COLOR]
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           2.4G  1.5M  2.4G   1% /run
efivarfs        256K   15K  242K   6% /sys/firmware/efi/efivars
/dev/sda1        73G  9.4G   64G  13% /
tmpfs            12G  1.2M   12G   1% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
/dev/sda15       98M  6.3M   92M   7% /boot/efi
tmpfs           2.4G  4.0K  2.4G   1% /run/user/1001
[COLOR=#0000ff]s3fs             16E     0   16E   0% /ncbucket[/COLOR]
ubuntu@hcp:~$ ^C
ubuntu@hcp:~$

[COLOR=#0000ff]ubuntu@hcp:~$ cd /ncbucket
ubuntu@hcp:/ncbucket$ ls -a[/COLOR]l
total 18
drwxrwxrwx  1 root root     0 Jan  1  1970 .
drwxr-xr-x 21 root root  4096 Apr 22 17:00 ..
-rw-r-----  1 root root 12697 Apr 22 16:40 [COLOR=#0000ff]Untitled.jpeg[/COLOR]
-rw-r--r--  1 root root     6 Apr 22 16:42 [COLOR=#0000ff]test2.txt[/COLOR]
ubuntu@hcp:/ncbucket$



**sudo nano /etc/fstab**

LABEL=cloudimg-rootfs   /        ext4   discard,errors=remount-ro       0 1
LABEL=UEFI      /boot/efi       vfat    umask=0077      0 1
[COLOR=#0000ff]systemctl enable NetworkManager-wait-online.service[/COLOR]
[COLOR=#0000ff]s3fs#nextcloudbucket /home/ubuntu/ncbucket fuse _netdev,allow_other, use_path_request_style, passwd_file=/.passwd-s3>[/COLOR]

# CLOUD_IMG: This file was created/modified by the Cloud Image build process
######################################
## ORACLE CLOUD INFRASTRUCTURE CUSTOMERS
##
## If you are adding an iSCSI remote block volume to this file you MUST
## include the '_netdev' mount option or your instance will become
## unavailable after the next reboot.
## SCSI device names are not stable across reboots; please use the device UUID
## instead of /dev path.
##
## Example:
## UUID="94c5aade-8bb1-4d55-ad0c-388bb8aa716a" /data1 ext4 defaults,noatime,_netdev 0 2
##
## More information:
## [https://docs.us-phoenix-1.oraclecloud.com/Content/Block/Tasks/connectingtoavolume.htm](https://docs.us-phoenix-1.oraclecloud.com/Content/Block/Tasks/connectingtoavolume.htm)
##

---

### Post by TheFu on 2024-04-22
[https://askubuntu.com/questions/1363974/adding-object-storage-to-etc-fstab-getting-parse-error](https://askubuntu.com/questions/1363974/adding-object-storage-to-etc-fstab-getting-parse-error) has an example:

```
WTX-Cotton-bucket /home/ubuntu/wtx_cotton_storage fuse.s3fs allow_other,use_path_request_style,passwd_file=/home/ubuntu/.passwd-s3fs,url=https://axrpuscetkut.compat.objectstorage.us-ashburn-1.oraclecloud.com,endpoint=us-ashburn-1,kernel_cache,multipart_size=128,parallel_count=50,multireq_max=100,max_background=1000,_netdev

```

Based on this manual mount command, 
```
sudo s3fs nextcloudbucket /ncbucket -o endpoint=us-ashburn-1 -o passwd_file=$HOME/.passwd-s3fs -o url=https://xxxxxxxxx.compat.objectstorage.us-ashburn-1.oraclecloud.com/ -o nomultipart -o use_path_request_style -o allow_other
```

I'd first point out that in the fstab, you cannot use $HOME variables, so you'll need to reference the passwd credentials exactly.

```
nextcloudbucket       /ncbucket     fuse.s3fs       allow_other,use_path_request_style,passwd_file=/etc/.passwd-s3fs,url=https://xxxxxxxxx.compat.objectstorage.us-ashburn-1.oraclecloud.com,endpoint=us-ashburn-1,kernel_cache,multipart_size=128,parallel_count=50,multireq_max=100,max_background=1000,_netdev     0       0
```
That's my guess. IDK.  I know nothing about s3fs or Oracle's offers.

Be certain to lock down the permissions and owner for the credential files   600 and root:root. Don't want those to leak, right?

---

