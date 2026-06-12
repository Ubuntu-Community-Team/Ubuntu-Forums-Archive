---
title: "Upgrading 12.04 LTS to 14.04 LTS"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by tb75252 on 2014-04-18
I am using Ubuntu 12.04 LTS, 64-bit.

Now that 14.04 LTS is available I was expecting Update Manager to ask me if I wanted to upgrade to the new version.  That does not seem to be happening.

So I downloaded and burned the .iso file and booted up with it.  But the menu choices presented to me do not include the option to upgrade from 12.04 LTS to 14.04 LTS.  I am surely doing/interpreting something wrong, so I am turning to the experts for some help.

Thanks.

---

### Post by Danger_Monkey on 2014-04-18
The easiest way to do this is to use the built in tools.  I just did this on two of my test servers:

```


[COLOR=#111111][FONT=Consolas]$ sudo apt-get update[/FONT][/COLOR]
[COLOR=#111111][FONT=Consolas]$ sudo apt-get install update-manager-core
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]$ sudo do-release-upgrade


```


[/FONT][/COLOR]

---

### Post by tb75252 on 2014-04-19
> **Danger_Monkey said:**
> The easiest way to do this is to use the built in tools.  I just did this on two of my test servers:

```


[COLOR=#111111][FONT=Consolas]$ sudo apt-get update[/FONT][/COLOR]
[COLOR=#111111][FONT=Consolas]$ sudo apt-get install update-manager-core
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]$ sudo do-release-upgrade

[/FONT][/COLOR]
```[COLOR=#111111][FONT=Consolas]


[/FONT][/COLOR]
Does not seem to work for me:
```
$ sudo do-release-upgrade
[sudo] password for tb: 
Checking for a new Ubuntu release
No new release found
```
PS:  I am sure that I still have 12.04 LTS installed because:
```
$ cat /etc/issue
Ubuntu 12.04.4 LTS \n \l

```

---

### Post by plucky on 2014-04-19
See [http://askubuntu.com/questions/125392/why-is-no-new-release-found-when-upgrading-from-a-lts-to-the-next](http://askubuntu.com/questions/125392/why-is-no-new-release-found-when-upgrading-from-a-lts-to-the-next)

Update Manager will offer the upgrade after the first point release in July.You can still get the upgrade by using ```
sudo do-release-upgrade -d
```

Please be aware that as 14.04 has just been released,the repositories might be very busy and cause upgrades to fail.

Good Luck

---

### Post by 3rdalbum on 2014-04-19
> **tb75252 said:**
> I am using Ubuntu 12.04 LTS, 64-bit.

Now that 14.04 LTS is available I was expecting Update Manager to ask me if I wanted to upgrade to the new version.  That does not seem to be happening.

As mentioned above, the upgrade won't be offered until 14.04.1 or unless you specially request it.

> So I downloaded and burned the .iso file and booted up with it.  But the menu choices presented to me do not include the option to upgrade from 12.04 LTS to 14.04 LTS.  I am surely doing/interpreting something wrong, so I am turning to the experts for some help.

To upgrade using the normal Ubuntu CD, you need to run the installer. Choose the "Something Else" option, select your Ubuntu partition and click Edit Partition. Set the mount point to "/". If you have any other partitions, for instance /home or /boot, then set those up too. Click Next and you'll be asked a question that is really a very complicated way of saying "Linux is already installed on /, this will erase your existing system files only", answer in the affirmative.

Your /home folder will be preserved, even if it is in the same partition as /. Your package list will be remembered, and newer versions from 14.04 will be installed into the new system as a courtesy. For this reason I recommend you remove all programs and packages that you won't really want anymore (for instance, things you tried out once but don't want to keep using).

---

