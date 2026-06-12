---
title: "Can not run update-manager"
date: 2013-08-17
forum: New to Ubuntu
---

### Post by wogga2 on 2013-08-17
I'm running 12.10
I've been away from home a lot for work lately and have missed a lot of updates, including the new distro. Since i've been back to my machine, i have a system error in my header notifying me that the system is unable to run package manager. When i try to check for updates, this is the error message i receive:
"
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:
E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_quantal-updates_universe_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.
"

I've opted to report the error when update manager/software center crash, but i'm not sure how to report the bug with an error message attached.

can anyone help me get update manager back up and running? i'd like to get up to the current distro.

thanks.

---

### Post by GwL3eNC on 2013-08-17
Hello

can you try

sudo rm /var/lib/apt/lists/* -rf
sudo apt-get update

---

### Post by ibjsb4 on 2013-08-17
If that way will not work, you can [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter these commands one line at a time.

```
sudo rm -r /var/lib/apt/lists
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get update
```

If you wish to know more about the error your getting, [look here]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened&sa=Search&cof=FORID:9").

And welcome to the forums :)

---

### Post by wogga2 on 2013-08-18
Thank you, [**[COLOR=#000000]ibjsb4[/COLOR]**]("http://ubuntuforums.org/member.php?u=1729120"). That got update manager (and software center) to run without crashing.

Now, unfortunatey, when i run update i receive this error message:
"
Not enough free disk space

The upgrade needs a total of 33.2 M free space on disk '/boot'. Please free at least an additional 5,328 k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.
"

I have many GB of free space on my drive. Why would this message appear?

Thanks for the welcome.

---

### Post by ibjsb4 on 2013-08-18
> I have many GB of free space on my drive. Why would this message appear?

Lets have a look, in terminal:

```
df -h
```

And did you do what it said?

```
sudo apt-get clean
```

And it mentions /boot.  Whats going on there?

```
ls /boot
```

---

### Post by wogga2 on 2013-08-19
> **ibjsb4 said:**
> Lets have a look, in terminal:

```
df -h
```

c@HAL-9000:~$ df -h
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu-root  139G   60G   72G  46% /
udev                     3.8G  4.0K  3.8G   1% /dev
tmpfs                    1.6G  900K  1.6G   1% /run
none                     5.0M     0  5.0M   0% /run/lock
none                     3.9G  448K  3.8G   1% /run/shm
none                     100M   40K  100M   1% /run/user
/dev/sda1                228M  189M   27M  88% /boot
/home/c/.Private         139G   60G   72G  46% /home/c

> And did you do what it said?

```
sudo apt-get clean
```

c@HAL-9000:~$ sudo apt-get clean
c@HAL-9000:~$ 

Nothing.

> And it mentions /boot.  Whats going on there?

```
ls /boot
```

c@HAL-9000:~$ ls /boot
abi-3.5.0-17-generic         initrd.img-3.5.0-26-generic
abi-3.5.0-21-generic         initrd.img-3.5.0-27-generic
abi-3.5.0-23-generic         [COLOR=#0000cd]lost+found[/COLOR]
abi-3.5.0-25-generic         memtest86+.bin
abi-3.5.0-26-generic         memtest86+_multiboot.bin
abi-3.5.0-27-generic         System.map-3.5.0-17-generic
config-3.5.0-17-generic      System.map-3.5.0-21-generic
config-3.5.0-21-generic      System.map-3.5.0-23-generic
config-3.5.0-23-generic      System.map-3.5.0-25-generic
config-3.5.0-25-generic      System.map-3.5.0-26-generic
config-3.5.0-26-generic      System.map-3.5.0-27-generic
config-3.5.0-27-generic      vmlinuz-3.5.0-17-generic
[COLOR=#0000cd]grub   [/COLOR]                      vmlinuz-3.5.0-21-generic
initrd.img-3.5.0-17-generic  vmlinuz-3.5.0-23-generic
initrd.img-3.5.0-21-generic  vmlinuz-3.5.0-25-generic
initrd.img-3.5.0-23-generic  vmlinuz-3.5.0-26-generic
initrd.img-3.5.0-25-generic  vmlinuz-3.5.0-27-generic
c@HAL-9000:~$ 

lost+found and grub were highlighted in blue in my terminal window.

---

### Post by ibjsb4 on 2013-08-19
Ok, your /boot is full of old kernels.  You need to remove all but the two latest and that will fix the problem.

There are several ways to do this.  Everyone has their pet way :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9)

An easy (GUI) way is with ubuntu-tweak.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

My pet way is with synaptic package manager.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels+synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels+synaptic+package+manager&sa=Search&cof=FORID:9)

Which has many other uses.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en&siteurl=](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en&siteurl=)

If you want to try it:

```
sudo apt-get install synaptic
```

---

### Post by wogga2 on 2013-08-19
Thanks. I'm up to date.

---

### Post by ibjsb4 on 2013-08-19
Congradulations :)  Don't forget

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by wogga2 on 2013-08-19
as an aside question - why have i never had this issue (old kernel excess) before?
i'm not actually new to the forums. i re-registered after that glitch.
 i've actually been running ubuntu (as a light user) since 7. i skipped 11 and went straight to 12 with this most recent machine. i thought it was strange that synaptic wasn't the main repository interface anymore since the switch to unity. this is the third machine i've run ubuntu on with a string of versions and i've never seen that before. seems so strange. i assume the original update issue was resultant of me neglecting updates for too long.

---

