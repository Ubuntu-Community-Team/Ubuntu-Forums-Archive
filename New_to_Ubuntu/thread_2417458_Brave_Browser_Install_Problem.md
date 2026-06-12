---
title: "Brave Browser Install Problem"
date: 2019-04-23
forum: New to Ubuntu
---

### Post by anthony10053 on 2019-04-23
Hi All, I am trying to install the Brave Web Browser using Ubuntu 18.04. The Brave site give the following install instructions for Ubuntu 16.04+ and Mint 18+.


curl -s [https://brave-browser-apt-release.s3.brave.com/brave-core.asc](https://brave-browser-apt-release.s3.brave.com/brave-core.asc) | sudo apt-key --keyring /etc/apt/trusted.gpg.d/brave-browser-release.gpg add -

source /etc/os-release

echo "deb [arch=amd64] [https://brave-browser-apt-release.s3.brave.com/](https://brave-browser-apt-release.s3.brave.com/) $UBUNTU_CODENAME main" | sudo tee /etc/apt/sources.list.d/brave-browser-release-${UBUNTU_CODENAME}.list

sudo apt update

sudo apt install brave-keyring brave-browser


Everything seemed to be going fine until I entered sudo apt update. This is the result - 

"E: Malformed entry 1 in list file /etc/apt/sources.list.d/brave-browser-release-bonic.list(Component)
E: The list of sources could not be read."

What do I need to do now?

Thanks!

---

### Post by cruzer001 on 2019-04-23
Looks like that ***UBUNTU_CODENAME*** in your command needs to be changed to ***bionic***.  The instructions on their homepage are not very clear on this.

The Ubuntu Handbook makes more sense to me.

[http://ubuntuhandbook.org/index.php/2018/12/how-to-install-brave-web-browser-in-ubuntu-linux-mint/](http://ubuntuhandbook.org/index.php/2018/12/how-to-install-brave-web-browser-in-ubuntu-linux-mint/)

---

### Post by Holger_Gehrke on 2019-04-23
UBUNTU_CODENAME is defined in /etc/os-release. Since the instructions say to source that file, it should be all right. In the manual page for sources.list ('man 5 sources.list') there's always a space between the brackets and the options in a deb-line, so the line in the file /etc/apt/sources.list.d/brave-browser-release-bionic.list should probably read
```

deb [ arch=amd64 ] [https://brave-browser-apt-release.s3.brave.com/](https://brave-browser-apt-release.s3.brave.com/) bionic main

```
with spaces between '[' and 'arch=amd64' and ']'. Doing it that way, 'sudo apt update' works as it should on my system.

Holger

---

### Post by anthony10053 on 2019-04-24
Thanks for the information and links. I followed the directions from in the Ubuntu Handbook as far as the instructions to refresh the system cache. I don't know how to do that.

There is a red circle with a white line through it at the top right of my screen. The message says to run the package manager. I closes after displaying the following message.
  
E: Malformed entry 1 in list file /etc/apt/sources.list.d/brave-browser-release-bionic.list (Component)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by anthony10053 on 2019-04-25
Okay! Apparently I need some sleep to help me see clearly. I am new to using the terminal  and didn't know how to use some of the Linux editors like vi which is the only one that comes to mind right now. Happily I discovered **gedit** which I used to edit the line in /etc/apt/sources.list.d/brave-browser-release-bionic.list which Holger provided. I then continued with the instructions in the Ubuntuhandbook and everything is working fine so far.
Thanks!

---

### Post by cruzer001 on 2019-04-25
Excellent :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by simon d w on 2019-05-19
Just worked out i have a 32bit machine and it only runs on 64bit.

---

