---
title: "Slow wireless internet upon installation 12.04LTS"
date: 2012-10-05
forum: New to Ubuntu
---

### Post by radamez85 on 2012-10-05
With the upgrade to ubuntu 12.04 LTS, my internet speed is way slowed then that of my windows 7. 
I have been poking around these forums looking at different threads on how to fix this issue, and have yet to find a resolution.

Please help, or can you please point me to a good thread on how to fix this issue?

---

### Post by Amplifox on 2012-10-05
Did you update ubuntu after the upgrade?

---

### Post by sahabcse on 2012-10-05
This thread may help

[http://ubuntuforums.org/showthread.php?t=1686641](http://ubuntuforums.org/showthread.php?t=1686641)

---

### Post by radamez85 on 2012-10-05
> **Amplifox said:**
> Did you update ubuntu after the upgrade?

I did the upgrades that ubuntu recommended.. Is there a download you can point me to?

---

### Post by varunendra on 2012-10-06
Hi radamez85,

Please download the 'wireless_script' linked in my signature, run it and post back the contents (within [noparse]```
 and 
```[/noparse] tags) of the 'netinfo.txt' file it creates. In addition to the script's results, please also post the output of:
```
ifconfig
```

This will provide us all the initial info required to figure out the cause of the problem and possibly troubleshoot it.

---

### Post by cway00 on 2012-10-06
[B] If internet is slow try to perform the following :
[/B]
Disable IPv6 If your internet is working Slow in Ubuntu 12.04 Precise Pangolin/Linux Mint 13/Any Ubuntu or Mint Version

Follow this to Disable IPv6, So we have to edit the **sysctl.conf **file.

To do this open Terminal (Press Ctrl+Alt+T) and copy the following commands in the Terminal:
```
sudo gedit /etc/sysctl.conf
```Now add these lines at the end of file:
```
# IPv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```Now Save** sysctl.conf** file and close.

Hope it helps

if it thus does not work.. then use a strong internet conection or a Lan to be sure that it is not from your service provider

---

### Post by HunkirDowne on 2012-10-06
> **varunendra said:**
> Hi radamez85,

Please download the 'wireless_script' linked in my signature, 

Nice script!  Had to learn what 'rfkill' was.  Gotz new toolz :-D

Thanks.

**Note to newbies:** Take a look at the script (this or any other) and if you don't know what it does, don't run it (this one is safe) before you know what it is going to do.  From the terminal type 'info [command]' where [command] is the program of interest.  For instance, I didn't know what 'rfkill' did so I did 'info rfkill' to find out that the 'list' command was safe (as in this script) but others were not necessarily safe and could put you in a worse (or possibly better?) state.

---

### Post by wildmanne39 on 2012-10-06
Hi, the easiest way to run this script that I wrote is to run this command.
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
then it creates netinfo text file in your home folder.
Thanks

---

