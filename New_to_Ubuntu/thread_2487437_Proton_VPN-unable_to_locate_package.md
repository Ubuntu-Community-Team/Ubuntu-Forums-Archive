---
title: "Proton VPN-unable to locate package"
date: 2023-06-05
forum: New to Ubuntu
---

### Post by dmacpeak2 on 2023-06-05
Hello-
I am trying to install Proton VPN. I recently installed Ubuntu and was happy I was able to flash the USB and get it installed. My pink cloud was short lived however in that I cant even install a VPN which should be a relatively easy task. Please see the below output. I have followed the directions several times and still I end up with the same bad result "unable to locate package". Any one who could assist many thnaks. I looked on the web and there is no real answer for this.....

buntu1@Linux-Laptop:~$ sudo apt update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease          
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease             
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.
ubuntu1@Linux-Laptop:~$ sudo apt-get install protonvpn
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package protonvpn
ubuntu1@Linux-Laptop:~$ install protonvpn
install: missing destination file operand after 'protonvpn'
Try 'install --help' for more information.
ubuntu1@Linux-Laptop:~$ instal --help
Command 'instal' not found, did you mean:
  command 'install' from deb coreutils (8.32-4.1ubuntu1)
Try: sudo apt install <deb name>
ubuntu1@Linux-Laptop:~$ sudo apt install protonvpn
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package protonvpn
ubuntu1@Linux-Laptop:~$ sudo apt-get autoremove protonvpn
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package protonvpn

---

### Post by dmacpeak2 on 2023-06-05
I have not been able to install Proton Mail Bridge so I can configure Mozzila Thunderbird.  I recieved error "unable to locate package: , which is the same error I am receiving when I tried to install the Proton Mail VPN. Please see the output below. I definatly downloaded the bridge.....

ubuntu1@Linux-Laptop:~$ sudo apt-get install ./protonmail-bridge_3.1.1-1_amd64.deb
Reading package lists... Done
E: Unsupported file ./protonmail-bridge_3.1.1-1_amd64.deb given on commandline
ubuntu1@Linux-Laptop:~$ sudo apt install protonmail-bridge
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
**E: Unable to locate package protonmail-bridge**
ubuntu1@Linux-Laptop:~$

---

### Post by QIII on 2023-06-05
Threads merged.

If you downloaded the .deb file, the typical process goes

```
sudo dpkg -i /path/to/package_file.deb
```

apt and apt-get search the repos for the package.  What you are seeing is an indication that the package does not exist in your active repos.  I'm not sure if it exists in the official repos.  Perhaps in Universe or Multiverse.

---

### Post by Holger_Gehrke on 2023-06-05
Did you try to follow the official installation procedure at [https://protonvpn.com/support/linux-ubuntu-vpn-setup/](https://protonvpn.com/support/linux-ubuntu-vpn-setup/) ? 'apt' and 'apt-get' can install local files, but for them to recognize local files you need to give a path to the file (basically the argument to the 'install' subcommand needs to contain at least one '/'; './' before the filename works just fine if the file is in the current working directory). Alternatively there's a manual configuration using OpenVPN found at [https://protonvpn.com/support/linux-openvpn/](https://protonvpn.com/support/linux-openvpn/) .

Holger

---

### Post by dmacpeak on 2023-06-07
Thanks! All I had to do was right click the .deb file and choose "open  with software installer". I had tried many times to "open with archive  manager" which was the pre selected option.  I just keep bouncing around  figuring out stuff. This is not for someone who does not want to learn  but its much better. 

I started practicing on a $40 chromebook to  get the feal for Ubuntu and then I bought a Lenovo laptop to install  Ubuntu on to make my everyday.... It came w windows 10 on it and I  almost had a panic attack in the windoes format. It is a really sad  state of affairs that everyone uses that stuff i.e. google,MSFT  Anyway,  thanks for the help!

---

### Post by idmbe on 2023-06-07
Open terminal and type:
```
cd Downloads
```

after that type:
```
sudo dpkg -i protonmail-bridge_3.1.1-1_amd64.deb
```

[COLOR=#b22222]Note[/COLOR]: make sure what name file is you are downloaded already, if [COLOR=#ff0000]protonmail-bridge_3.1.1-1_amd64.deb[/COLOR] or something else

---

