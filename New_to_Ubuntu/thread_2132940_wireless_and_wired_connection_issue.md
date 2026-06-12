---
title: "wireless and wired connection issue"
date: 2013-04-06
forum: New to Ubuntu
---

### Post by vadertater on 2013-04-06
The issue is I have to constantly switch between the two wireless networks on campus - very annoying. The connection will still be there, but it will stop connecting to the servers. This is better than before, when I couldn't even connect to the internet. I also cannot connect via ethernet now and the option 'Auto Ethernet' is not available in the network menu. 

I am running 12.10 on a Toshiba satellite C855. I already installed the correct driver for my realtek card, but this particular issue started when I updated my kernel to get rid of the apport error. The kernel is 3.8.1-030801-generic (which is not an ubuntu kernel... even though the link I got it from was an ubuntu website). Here are the instructions I followed: [http://www.liberiangeek.net/2013/03/linux-kernel-3-8-1-releasedhow-to-install-upgrade-in-ubuntu-12-10/](http://www.liberiangeek.net/2013/03/linux-kernel-3-8-1-releasedhow-to-install-upgrade-in-ubuntu-12-10/)

Everything else is working fine. As far as I can tell it's only the wirelss/wired issue that is effecting my usage. Would this issue be solved by changing kernel to an ubuntu kernel? And if so, how would I do that?

---

### Post by wildmanne39 on 2013-04-06
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.

That looks like an ubuntu kernel to me on that site.

Thanks

---

### Post by vadertater on 2013-04-06
I have the wireless script. It's not not in the correct file format though. What type does it need to be to upload? and how do I convert it?

---

### Post by wildmanne39 on 2013-04-06
Please copy and paste the information using code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by vadertater on 2013-04-06
```
#!/bin/bash
#Script created by anewguy, tested by chili555 and edited by krytarik, llua and wildmanne39
exec > netinfo.txt 2> /dev/null
echo -e "\n*************** info trace ****************\n"
echo -e "\n\n**** uname -a ****\n\n"
uname -a
echo -e "\n\n**** lsb-release ****\n\n"
cat /etc/lsb-release
echo -e "\n\n**** lspci ****\n\n"
lspci -nnk | grep -iA2 net
echo -e "\n\n**** lsusb ****\n\n"
lsusb
echo -e "\n\n**** iwconfig ****\n\n"
iwconfig
echo -e "\n\n**** rfkill ****\n\n"
rfkill list all
echo -e "\n\n**** lsmod ****\n\n"
lsmod
echo -e "\n\n**** nm-tool ****\n\n"
nm-tool
echo -e "\n\n**** NetworkManager.state ****\n\n"
cat /var/lib/NetworkManager/NetworkManager.state
echo -e "\n\n**** NetworkManager.conf ****\n\n"
cat /etc/NetworkManager/NetworkManager.conf
echo -e "\n\n**** NetworkManager.conf-10.04 ****\n\n"
cat /etc/NetworkManager/nm-system-settings.conf
echo -e "\n\n**** interfaces ****\n\n"
cat /etc/network/interfaces | sed 's/wpa-psk [[:graph:]:]\+/wpa-psk <WPA key removed>/'
echo -e "\n\n**** iwlist ****\n\n"
[ -t 0 ] && sudo iwlist scan
[ ! -t 0 ] && gksudo iwlist scan
echo -e "\n\n**** resolv ****\n\n"
cat /etc/resolv.conf
echo -e "\n\n**** blacklist.conf ****\n\n"
cat /etc/modprobe.d/blacklist.conf
echo -e "\n\n**** dmesg ****\n\n"
dmesg | egrep 'air|ath|carl|at7|iwl|ipw|rtl8|rt2|rt3|rt6|rt7|r818|r871|rtl8|tg3|ssb|wl|b43|bcma|brcm|b44|eth1|ndis|wmi|wlan0'
echo -e "\n\n**************** done ********************\n\n"
sed -i 's/\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]/<MAC address removed>/' netinfo.txt
```

---

### Post by wildmanne39 on 2013-04-06
Hi go into your home folder and post the file named netinfo.text you actually posted the script.
Thanks

---

### Post by vadertater on 2013-04-07
I actually typed in the command wrong the first time and it just gave me that script. Now I have netinfo.txt but it is too big to attached. 

Can I do something with pastebinit?? I'm not sure what the commands are to use the program, but I know it can save a lot of space and still get you the info you want...

---

### Post by vadertater on 2013-04-07
Hopefully this works!

[http://paste.ubuntu.com/5685145/](http://paste.ubuntu.com/5685145/)

---

### Post by wildmanne39 on 2013-04-07
According to the information you posted there is a bug in that kernel, so you would be better off trying another kernel.

Also please note that your driver is very problematic in ubuntu, did you compile the driver you have now or is it the one that come with ubuntu?
If you want we can try a patch for that driver that I found it will be quite a process but it may work if it does we will have learned a lot.
Thanks

---

### Post by vadertater on 2013-04-07
Ok, so how would I go about getting a different kernel? I used that link in my first post before, so would I just find a differentl url to a different kernel, but follow the general format of that initial article??

I compiled it myself from the realtek site. Ubuntu didn't have a driver for my wireless card. I am willing to try and fix it, but I am a beginner. I've done a few things, like install the kernel, driver, etc and I'm starting to get the hang of some stuff, but I am by no means advanced - I'd say I'm definitely still a beginner.

---

### Post by wildmanne39 on 2013-04-07
Here is good directions for insalling a new kernel with a link to the files you will need.
[http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade](http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade)
Use link for directions, you choose which version of the kernel you want to install.
Thanks

---

### Post by vadertater on 2013-05-13
Wild Man,

I'm really sorry I disappeared for a while... school got a bit hectic as the semester wrapped up. So I am back now. If you're still willing to work with me, I'll let you know this:

I followed your instructions you posted. I went to [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") and copied the i386.deb and all.deb files for this kernel [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/). I then changed my directory to where I saved them. I installed, using:

```
sudo dpkg -i name.deb
```

I started with the all.deb file and got: 
```
Selecting previously unselected package linux-headers-3.6.3-030603.
(Reading database ... 213689 files and directories currently installed.)
Unpacking linux-headers-3.6.3-030603 (from linux-headers-3.6.3-030603_3.6.3-030603.201210211349_all.deb) ...
Setting up linux-headers-3.6.3-030603 (3.6.3-030603.201210211349) ...
```

Then I moved on to the next one:

```
nate@nate-Satellite-C855:~/Downloads/kernelppamainlinev3_6_3quantal$ sudo dpkg -i linux-headers-3.6.3-030603-generic_3.6.3-030603.201210211349_i386.deb
Selecting previously unselected package linux-headers-3.6.3-030603-generic.
(Reading database ... 227978 files and directories currently installed.)
Unpacking linux-headers-3.6.3-030603-generic (from linux-headers-3.6.3-030603-generic_3.6.3-030603.201210211349_i386.deb) ...
dpkg: dependency problems prevent configuration of linux-headers-3.6.3-030603-generic:
 linux-headers-3.6.3-030603-generic depends on linux-headers-3.6.3-030603.

dpkg: error processing linux-headers-3.6.3-030603-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-3.6.3-030603-generic
```

I then went back into the correct directory and realized I had downloaded two of the same file: linux-headers-3.6.3-030603-generic_3.6.3-030603.201210211349_i386.deb so I deleted one. And tried installing it again, but I got the same issue. Is this something on my end? Do I need to do something to uninstall my current kernel?

Is there a place where I can check to find the most recent and bug free or minimal bug kernel for quantal?

---

### Post by vadertater on 2013-05-13
I also got an error... it showed up in my right top corner and it says: Error: BrokenCount>0 which means I have installed packages with unmet dependencies. 

So I got the below:
```
nate@nate-Satellite-C855:~$ sudo apt-get -f
apt 0.9.7.5ubuntu5.1 for amd64 compiled on Mar 13 2013 21:25:25
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]
```

I've had this issue for a while (that is about when I installed the new kernel) according to that date. Just thought you should know.

---

### Post by vadertater on 2013-05-13
I started reading ubuntu for non-geeks 2nd edition... and I realized I should have chosen the amd64 files. Especially since I'm running 12.10 64-bit... I'll let you know if it fixes the problem

---

### Post by vadertater on 2013-05-13
```
sudo apt-get install -f
```

Used that guy and removed the all.deb file. Now gonna try it again with the amd64.deb files

I also reread the names of the .deb file and I realized I have 4 different files - one is not repeated. So I'm keeping them both, but paying closer attention to the order I am installing them.

It looks like it worked so far... I am rebooting now.

---

