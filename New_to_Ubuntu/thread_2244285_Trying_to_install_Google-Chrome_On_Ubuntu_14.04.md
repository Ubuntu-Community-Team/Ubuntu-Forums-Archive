---
title: "Trying to install Google-Chrome On Ubuntu 14.04"
date: 2014-09-15
forum: New to Ubuntu
---

### Post by khan3 on 2014-09-15
Hi,

I am trying to install google-chrome on ubuntu 14.04 however when i try running the program i am getting failed responses.

```
khan@ubuntu:~$ google-chrome
[0914/130243:ERROR:nss_util.cc(93)] Failed to create /home/khan/.pki/nssdb directory.
[0914/130243:ERROR:nss_util.cc(93)] Failed to create /home/khan/.pki/nssdb directory.
[7970:8007:0914/130243:ERROR:nss_util.cc(93)] Failed to create /home/khan/.pki/nssdb directory.
[7970:7970:0914/130243:ERROR:process_singleton_posix.cc(404)] readlink failed: Permission denied
[7970:7970:0914/130243:ERROR:process_singleton_posix.cc(240)] readlink(/home/khan/.config/google-chrome/SingletonLock) failed: Permission denied
[7970:7970:0914/130243:ERROR:process_singleton_posix.cc(240)] readlink(/home/khan/.config/google-chrome/SingletonLock) failed: Permission denied
[7970:7970:0914/130243:ERROR:process_singleton_posix.cc(264)] Failed to create /home/khan/.config/google-chrome/SingletonLock: Permission denied
[7970:7970:0914/130243:ERROR:process_singleton_posix.cc(404)] readlink failed: Permission denied
[7970:7970:0914/130243:ERROR:process_singleton_posix.cc(240)] readlink(/home/khan/.config/google-chrome/SingletonLock) failed: Permission denied
[7970:7970:0914/130243:ERROR:chrome_browser_main.cc(1155)] Failed to create a ProcessSingleton for your profile directory. This means that running multiple instances would start multiple browser processes rather than opening a new window in the existing process. Aborting now to avoid profile corruption.
khan@ubuntu:~$ 
```

I followed this tutorial:

[http://tecadmin.net/install-google-chrome-in-ubuntu/](http://tecadmin.net/install-google-chrome-in-ubuntu/)

Additionally, when i now run ```
sudo apt-get update
``` i am seeing this at the end:

```
Reading package lists... Done
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

Even after running apt-get update again the problems arent corrected.

---

### Post by SBMN7 on 2014-09-15
Try it, 
Open Terminal and Run the Commands
 1. Download key
 ***wget -q -O &#8211; [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -***
 2.  Add google chrome to sources.list
 ***sudo sh -c &#8216;echo &#8220;deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main&#8221; >> /etc/apt/sources.list.d/google.list&#8217;***
 3. Update list
 ***sudo apt-get update***
 4. install google chrome
***sudo apt-get install google-chrome-stable***
 5. Open google chrome
 6. Enjoy it [IMG]http://www.enqlu.com/wp-includes/images/smilies/icon_smile.gif[/IMG]

---

### Post by vasa1 on 2014-09-15
Try this tutorial (if you're using Ubuntu): [http://ubuntuforums.org/showthread.php?t=2243763](http://ubuntuforums.org/showthread.php?t=2243763)

It's made by one of our forum members. No need to mess with terminal commands :)

---

### Post by khan3 on 2014-09-16
> **vasa1 said:**
> Try this tutorial (if you're using Ubuntu): [http://ubuntuforums.org/showthread.php?t=2243763](http://ubuntuforums.org/showthread.php?t=2243763)

It's made by one of our forum members. No need to mess with terminal commands :)

I have tried it this way,but when i click the icon it doesent load. I am pretty sure its to do with the errors ive mentioned in my OP.

---

### Post by CantankRus on 2014-09-16
Seems to be a permissions issue.
How have you installed ubuntu?

Both Google-chrome and opera-developer won't run in my guest account while firefox will.
```
guest-huWTRH@Trusty:~$ **opera-developer **
Failed to move to new namespace: PID namespaces supported, Network namespace supported, but failed: errno = Operation not permitted

guest-huWTRH@Trusty:~$ **google-chrome**
Failed to move to new namespace: PID namespaces supported, Network namespace supported, but failed: errno = Operation not permitted
```

What happens when you run...
```
google-chrome --no-sandbox
```

---

### Post by khan3 on 2014-09-16
> **CantankRus said:**
> Seems to be a permissions issue.
How have you installed ubuntu?

Both Google-chrome and opera-developer won't run in my guest account while firefox will.
```
guest-huWTRH@Trusty:~$ **opera-developer **
Failed to move to new namespace: PID namespaces supported, Network namespace supported, but failed: errno = Operation not permitted

guest-huWTRH@Trusty:~$ **google-chrome**
Failed to move to new namespace: PID namespaces supported, Network namespace supported, but failed: errno = Operation not permitted
```

What happens when you run...
```
google-chrome --no-sandbox
```

I have innstalled google-chrome using the link to the tutorial in my OP.

When i try to run google-chrome no sandbox i get the same error messages.

```
[0914/150310:ERROR:nss_util.cc(93)] Failed to create /home/khan/.pki/nssdb directory.
[15004:15004:0914/150310:ERROR:browser_main_loop.cc(161)] Running without the SUID sandbox! See https://code.google.com/p/chromium/wiki/LinuxSUIDSandboxDevelopment for more information on developing with the sandbox on.
[0914/150310:ERROR:nss_util.cc(93)] Failed to create /home/khan/.pki/nssdb directory.
[15004:15031:0914/150310:ERROR:nss_util.cc(93)] Failed to create /home/khan/.pki/nssdb directory.
[15004:15004:0914/150310:ERROR:process_singleton_posix.cc(404)] readlink failed: Permission denied
[15004:15004:0914/150310:ERROR:process_singleton_posix.cc(240)] readlink(/home/khan/.config/google-chrome/SingletonLock) failed: Permission denied
[15004:15004:0914/150310:ERROR:process_singleton_posix.cc(240)] readlink(/home/khan/.config/google-chrome/SingletonLock) failed: Permission denied
[15004:15004:0914/150310:ERROR:process_singleton_posix.cc(264)] Failed to create /home/khan/.config/google-chrome/SingletonLock: Permission denied
[15004:15004:0914/150310:ERROR:process_singleton_posix.cc(404)] readlink failed: Permission denied
[15004:15004:0914/150310:ERROR:process_singleton_posix.cc(240)] readlink(/home/khan/.config/google-chrome/SingletonLock) failed: Permission denied
[15004:15004:0914/150310:ERROR:chrome_browser_main.cc(1155)] Failed to create a ProcessSingleton for your profile directory. This means that running multiple instances would start multiple browser processes rather than opening a new window in the existing process. Aborting now to avoid profile corruption.
[0914/150310:ERROR:nacl_helper_linux.cc(277)] NaCl helper process running without a sandbox!
Most likely you need to configure your SUID sandbox correctly


```

---

### Post by CantankRus on 2014-09-16
Are you running ubuntu in a virtual machine?

For the duplicate sources, run...
```
software-properties-gtk --open-tab 1
```
Look for 2 occurrences of **[http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/)** and remove one of them.

---

### Post by khan3 on 2014-09-16
> **CantankRus said:**
> Are you running ubuntu in a virtual machine?

For the duplicate sources, run...
```
software-properties-gtk --open-tab 1
```
Look for 2 occurrences of **[http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/)** and remove one of them.

Yes i am runnign it on a virtual machine.

Ty i got rid of the duplicate and when i run sudo apt-get update i dont get those reference errors now.

However when i go to run Google-chrome i still get these errors.

```
khan@ubuntu:~$ google-chrome
[0914/160314:ERROR:nss_util.cc(93)] Failed to create /home/khan/.pki/nssdb directory.
[0914/160314:ERROR:nss_util.cc(93)] Failed to create /home/khan/.pki/nssdb directory.
[16685:16722:0914/160314:ERROR:nss_util.cc(93)] Failed to create /home/khan/.pki/nssdb directory.
[16685:16685:0914/160314:ERROR:process_singleton_posix.cc(404)] readlink failed: Permission denied
[16685:16685:0914/160314:ERROR:process_singleton_posix.cc(240)] readlink(/home/khan/.config/google-chrome/SingletonLock) failed: Permission denied
[16685:16685:0914/160314:ERROR:process_singleton_posix.cc(240)] readlink(/home/khan/.config/google-chrome/SingletonLock) failed: Permission denied
[16685:16685:0914/160314:ERROR:process_singleton_posix.cc(264)] Failed to create /home/khan/.config/google-chrome/SingletonLock: Permission denied
[16685:16685:0914/160314:ERROR:process_singleton_posix.cc(404)] readlink failed: Permission denied
[16685:16685:0914/160314:ERROR:process_singleton_posix.cc(240)] readlink(/home/khan/.config/google-chrome/SingletonLock) failed: Permission denied
[16685:16685:0914/160314:ERROR:chrome_browser_main.cc(1155)] Failed to create a ProcessSingleton for your profile directory. This means that running multiple instances would start multiple browser processes rather than opening a new window in the existing process. Aborting now to avoid profile corruption.


```

---

### Post by khan3 on 2014-09-17
Bump

---

### Post by khan3 on 2014-09-17
> **khan3 said:**
> Bump

So i think i fixed it, it seems to be something to do with a corrupted config file.

if you remove the config folder

```
rm -r ~/.config/google-chrome
```

it will fix the issue as google-chrome will create a new config.

---

