---
title: "Not Enought Free Disk Space (13.10)"
date: 2014-04-20
forum: New to Ubuntu
---

### Post by richramik on 2014-04-20
Had this problem for the past week or so.  Figured it would go away when I went to install 14.04.  However, I couldn't do the install of 14.04 becaue of this.  I am not a techy type at all, but I have gathered the following information from the screen.

"Not enough free disk space".   I received another message stating that I needed 58.7MB in /boot.  I'm assuming the additional space is needed in order to continue.

Somewhere along the line, I got a message to run "sudo apt-get clean".  Ran the command as shown, tried to install 14.04 again, but still no success.

I then checked properties for /boot and found that I have 270 items  240.9MB.  

Not sure what all of this means, but I have figured that if the /boot space (?) problem isn't solved, I will not be able to install 14.04.  Now that I think about it, the last time I ran synaptic, it wouldn't do the install of the updates.

What do I need to do to move forward?  Guessing, that I must first fix 13.10, then install 14.04.

Thanks in advance, Rich Ramik

---

### Post by 23dornot23d on 2014-04-20
Hi  				 				 					 						 	[**[COLOR=#000000]richramik[/COLOR]**]("http://ubuntuforums.org/member.php?u=659993")

If you can give us some more information by typing df -a into a terminal

**df -a**

It will give us some information about the disk space you have available at the moment.

as an example it should return something similar to this below .........

```

K53SV:~$ df -a
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda12      53783672 36763704  14264864  73% /
proc                   0        0         0    - /proc
sysfs                  0        0         0    - /sys
none                   4        0         4   0% /sys/fs/cgroup
none                   0        0         0    - /sys/fs/fuse/connections
none                   0        0         0    - /sys/kernel/debug
none                   0        0         0    - /sys/kernel/security
udev             1967348       12   1967336   1% /dev
devpts                 0        0         0    - /dev/pts
tmpfs             395620     1212    394408   1% /run
none                5120        0      5120   0% /run/lock
none             1978092       84   1978008   1% /run/shm
none              102400       12    102388   1% /run/user
none                   0        0         0    - /sys/fs/pstore
binfmt_misc            0        0         0    - /proc/sys/fs/binfmt_misc
systemd                0        0         0    - /sys/fs/cgroup/systemd
gvfsd-fuse             0        0         0    - /run/user/1000/gvfs
/dev/sdb1         975552   132928    842624  14% /media/keith/E0FD-1813

```

---

### Post by Bashing-om on 2014-04-20
richramik; ! Let's look at what is:


Post back the outputs - between code tags - of terminal commands:
```

df -h
df -i

```
"df -h" to check  "you are out of space" ;
"df -i" to check that there are 'inodes' available to assign to new files .
Then ;
Let's look at where your space hogs are . Yout think /boot, OK ->
```

cd /
sudo du -sx * | sort -n
cd

```
If you need to drill down further, use cd to move to a directory of interest then repeat the "du" command.
The results are in megabytes.

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]a tale will be told
[/INDENT][/INDENT]

---

### Post by ibjsb4 on 2014-04-20
To clean boot and other things

```
sudo apt-get autoremove
```

---

### Post by Bashing-om on 2014-04-20
richramik;

+1 ibjsb4' as this is release 13.10 !

[INDENT][INDENT]should workie great
[INDENT][INDENT][INDENT]last long time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by richramik on 2014-04-21
Sorry for the late response, but I just got home from work.

I hope I have provided the information you were looking for.  I sort of kinda understand what you are trying to see; that is in a galaxy far, far, far, far, far, far - well you get the idea.

Thanks,
Rich



rich@rich-500-164:~$ df -a
Filesystem                   1K-blocks     Used  Available Use% Mounted on
/dev/mapper/ubuntu--vg-root 1914570108 43123196 1774169372   3% /
proc                                 0        0          0    - /proc
sysfs                                0        0          0    - /sys
none                                 4        0          4   0% /sys/fs/cgroup
none                                 0        0          0    - /sys/fs/fuse/connections
none                                 0        0          0    - /sys/kernel/debug
none                                 0        0          0    - /sys/kernel/security
none                                 0        0          0    - /sys/firmware/efi/efivars
udev                           3628516        4    3628512   1% /dev
devpts                               0        0          0    - /dev/pts
tmpfs                           727804     1164     726640   1% /run
none                              5120        0       5120   0% /run/lock
none                           3639000       76    3638924   1% /run/shm
none                            102400       32     102368   1% /run/user
none                                 0        0          0    - /sys/fs/pstore
/dev/sda2                       241965   238429          0 100% /boot
/dev/sda1                       497696     3376     494320   1% /boot/efi
systemd                              0        0          0    - /sys/fs/cgroup/systemd
gvfsd-fuse                           0        0          0    - /run/user/1000/gvfs
rich@rich-500-164:~$ 

========================================================

rich@rich-500-164:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  1.8T   42G  1.7T   3% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         3.5G  4.0K  3.5G   1% /dev
tmpfs                        711M  1.2M  710M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         3.5G   76K  3.5G   1% /run/shm
none                         100M   32K  100M   1% /run/user
/dev/sda2                    237M  233M     0 100% /boot
/dev/sda1                    487M  3.3M  483M   1% /boot/efi


rich@rich-500-164:~$ df -i
Filesystem                     Inodes  IUsed     IFree IUse% Mounted on
/dev/mapper/ubuntu--vg-root 121577472 407923 121169549    1% /
none                           909750      2    909748    1% /sys/fs/cgroup
udev                           907129    523    906606    1% /dev
tmpfs                          909750    540    909210    1% /run
none                           909750      4    909746    1% /run/lock
none                           909750      4    909746    1% /run/shm
none                           909750     24    909726    1% /run/user
/dev/sda2                       62496    280     62216    1% /boot
/dev/sda1                           0      0         0     - /boot/efi
rich@rich-500-164:~$ 

========================================================

rich@rich-500-164:~$ cd /
rich@rich-500-164:/$ sudo du -sx * | sort -n
[sudo] password for rich: 
Sorry, try again.
[sudo] password for rich: 
du: cannot access &#8216;proc/2795/task/2795/fd/4&#8217;: No such file or directory
du: cannot access &#8216;proc/2795/task/2795/fdinfo/4&#8217;: No such file or directory
du: cannot access &#8216;proc/2795/fd/4&#8217;: No such file or directory
du: cannot access &#8216;proc/2795/fdinfo/4&#8217;: No such file or directory
0	initrd.img
0	initrd.img.old
0	proc
0	sys
0	vmlinuz
0	vmlinuz.old
4	cdrom
4	dev
4	lib64
4	mnt
4	opt
4	srv
8	media
16	lost+found
72	tmp
228	root
1164	run
9852	bin
12180	sbin
14400	etc
236379	boot
479644	var
1343440	lib
4000148	usr
37172008	home
rich@rich-500-164:/$

---

### Post by 23dornot23d on 2014-04-22
/dev/sda2                       241965   238429          0 100% /boot

/dev/sda2                    237M  233M     0 100% /boot

/dev/sda2                       62496    280     62216    1% /boot

236379	boot

_______________________

I never use a separate boot partition ..... but it seems some people do - but only assign it a very
small space ......

I would look at gparted ...... but I know other people can take you through this from the command
line .......... so I will leave it for them to talk you through it ............

probably due to a lot of old kernels ...... but who knows .......... ?

237 meg for the boot area .... is that enough and how do people decide what to make it
are there some rules for this ..........

[http://askubuntu.com/questions/89710/how-do-i-free-up-more-space-in-boot](http://askubuntu.com/questions/89710/how-do-i-free-up-more-space-in-boot)

---

### Post by Impavidus on 2014-04-22
That /boot partitions was probably created and made too small automatically. The installer creates a /boot partition when you opt for an encrypted hard drive.

Run```
sudo apt-get autoremove
```to get rid of old kernel images. If it complains that it can't, because you have to fix the package manager first, run these two commands```
uname -r
dpkg --list | grep linux-image
```They should give you the presently running kernel and a list of installed kernel packages. Uninstall the kernel packages older than your running kernel with```
dpkg -P linux-image-<version>
```

You write you can't install 14.04 because of this problem. But you can surely do a clean install, you just can't upgrade. If you do a clean install, keep all files backed up on an external drive. It is possible to keep your home directory during reinstallation, but don't count on it, especially not on encrypted systems.

---

### Post by richramik on 2014-05-05
Impavidus

Just getting back to the computer after shoulder surgery.

I ran the comands and no more message about "Not Enough Free Disk Space".

I've burned a ISO DVD with 14.04.

Tried inserting the DVD and restarting the system, but I believe it was doing an upgrade.  So I stopped the install.  Knowing that an upgrade is a no-no, what should I do next?

Thanks
Rich Ramik

---

