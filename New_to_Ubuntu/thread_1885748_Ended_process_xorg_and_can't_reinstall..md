---
title: "Ended process: xorg and can't reinstall."
date: 2011-11-23
forum: New to Ubuntu
---

### Post by Alexalad on 2011-11-23
I've had ubuntu for about almost a year, now. And lately, I've had some issues with the xorg process using 100% of my cpu. So I ended the processes (obviously, in hindsight, it was an incredibly stupid thing to do). As soon as I ended it, my screen went black and turned into a fullscreen terminal. I rebooted a few times, and only have a fullscreen terminal, now. I used the "apt-get remove xserver-xorg" then "apt-get install xserver-xorg".
This outputs "Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?"

I used the update command, which fails to fetch a long list of items followed by, "some index files failed to download, they have been ignored, or old ones used instead. 

I have a feeling, i'm just gonna have to start from scratch. But i'm really hoping not. If I do, is there a way to transfer my files on a usb drive by using the terminal? Although a magical fix would probably make my...week.

---

### Post by carverj on 2011-11-24
Run Ubuntu from live CD and backup your important files to USB external hard drive. 
Regarding the Xorg issue, what version of Ubuntu are you using? If the error you are getting when trying to apt-get is due to using older version, perhaps you could install latest Ubuntu over the top. Then restore the data from USB drive over that. You will then have to reinstall apps once again.

---

### Post by Alexalad on 2011-11-24
I'm using 10.04, lucid lynx, if that helps.

---

### Post by lolpenguin on 2011-11-24
Run
```
sudo dpkg --configure -a
```
and
```
sudo apt-get -f install
```
This will fix all broken packages, then
```
sudo apt-get update
sudo apt-get install xserver-common xserver-xorg-core xserver-xorg xserver-xorg-input-all xerver-xorg-video-all
``` (more packages may be required for your Xserver to run)
Then reboot and run
```
startx
```
And see if your GUI works.

---

### Post by Alexalad on 2011-11-24
The first command had no output.

The second ouput: 
"The following packages were automatically installed and are no longer required:
libvpx0 acroread-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 installed, 0 to remove and 0 not upgraded."

The third installed, but output a long list of 'failed to fetch *long link*' followed by: 
Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

And when I reboot and used the 4th command, I get:
xauth:  /home/*username*/.Xauthority not writable, changes will be ignored
xauth:  error in locking authority file /home/user/.Xauthority

exec: 3: /usr/bin/X: not found
giving up.
xinit: no such file or directory (errno 2): unable to connect to X server
xinit: no such process (errno 3): server error.
xauth: error in locking authority file /home/user/.Xauthority

Sudo startx gives the same output.

---

### Post by Alexalad on 2011-11-24
I also updated prior to my killing of xorg. Could that have any effect on my situation?

---

### Post by lolpenguin on 2011-11-25
Looks like you have a long string of non-existent files required by X (due to uninstall) and some broken sources. Don't worry about the output of the first two. You're using lucid lynx (10.04) right? If you aren't (eg 11.10 Oneiric Ocelot) replace all of "lucid" with the first word of the codename (eg oneiric)
```
nano /etc/apt/sources.list
```
Replace EVERYTHING with these:
```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ lucid main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://archive.ubuntu.com/ubuntu/ lucid universe

deb http://security.ubuntu.com/ubuntu/ lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ lucid-security main restricted
```
This will reset your sources list to the absolute defaults. Run
```
sudo apt-get update --fix-missing
sudo apt-get check
```
Then install all the X components as covered in my last post.
But if it all doesn't work you COULD BUT SHOULD NOT try this, as I have not confirmed that this will be safe or not.
```
sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop
```
If anybody knows if that removing ubuntu-desktop does not affect the console then please reply.

---

### Post by Alexalad on 2011-11-25
I replaced everything in that file, to find out, you have to be root to make the changes. So I did it again, and saved it. 

Then the 'fix-missing' command output another long line of 'failed to fetch link's, followed by a list of 'duplicate *long link*'

The check output 'done'.

But when I repeated the steps in your last post, I yielded the same results with the same output. 

Also, I went back and checked that sources file afterward to see if I had typed everything correctly. And I did, but there was a lot of other stuff added to it, too. Is this a result of the update command? Oh, and I'm uncertain of the last suggestion. I'll hold back a little before I try it.

---

### Post by MG&amp;TL on 2011-11-25
ubuntu-desktop is a meta-package, it can be safely removed without affecting other packages. See here: [http://ubuntuforums.org/showthread.php?t=1804431&page=2]("http://ubuntuforums.org/showthread.php?t=1804431&page=2")

---

### Post by Alexalad on 2011-11-25
When I removed ubuntu-desktop, it said it wasn't installed to begin with, and when I tried to install, it output a long list of 'failed to fetch link's' followed by:
Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by Alexalad on 2011-11-25
If everyone's out of ideas, I think i'm going to grab all my important files and transfer them to an external hardrive, then just reinstall ubuntu all over again. But before I do, I just wanna make sure that I am at a reasonable point to give up. If anyone has any suggestions at all, i'll try it. I have nothing else to lose at this point.

---

### Post by bryncoles on 2011-11-25
Hi Alexalad

I know nothing about anything, but I found this.  It might be helpful...?

[http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html)

Since you're having trouble fetching repositories, try just running ```
sudo dpkg-reconfigure xserver-xorg
``` first, before removing anything.  

*disclaimer* 

I don't know anything about anything!

---

### Post by bryncoles on 2011-11-25
Also, could you post the output of ```
lsb_release -a
```, just so we can all be sure of what version you're running?  Cheers!

And [this](http://askubuntu.com/questions/19170/ppa-causing-404-error) thread suggests that there might be files in /etc/apt/sources.list.d, so post the output of 

```
ls /etc/apt/sources.list.d
``` please, just so we can check!

---

### Post by Alexalad on 2011-11-25
--The reconfigure command output: 

/usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed.


--'lsb_release -a' command output:

No LSB modules are available.
Distributor ID: Ubuntu
Description:     Ubuntu 10.04.3 LTS
Release:            10.04
Codename:       lucid


--'ls /etc/apt/sources.list.d' output:
crebs-ppa-lucid.list
crebs-ppa-lucid.list.save
dropbox.list
lucid-partner.list
lucid-partner.list.save
pidgin-developers-ppa-lucid.list
pidgin-developers-ppa-lucid.list.save
pidgin-ppa.list
pidgin-ppa.list.save
tualatrix-ppa-lucid.list
tualatrix-ppa-lucid.list.save
ubuntu-audio-dev-ppa-lucid.list
ubuntu-wine-ppa-lucid.list
ubuntu-wine-ppa-lucid.list.save

For someone who claims to know little  you know a lot of tricky commands. Thanks for the help, though.

---

### Post by Alexalad on 2011-11-25
Oh, and I followed the steps in that link earlier, but when I install, it outputs a long list of archives that were unable to be fetched.

---

### Post by fdrake on 2011-11-25
can you try this please and post the results:
```

sudo aptitude install xorg
startx

```
also if you need a source file for lucid you can try mine;just run update/upgrade
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bk
sudo mv ~/source.list.txt /etc/apt/sources.list

```

note that xserver-xorg:
> 
Description: the X.Org X server
 This package [COLOR="Red"][U][B]depends on the full suite of the server and drivers for the X.Org X server.  It
 does not provide the actual server itself.[/B][/U][/COLOR]


---

### Post by Alexalad on 2011-11-25
--'sudo aptitude install install xorg' output a long list of lines, all starting with: 'Err [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) lucid/main x server-xorg...' 
and ended with 'could not resolve us.archive.ubuntu.com'.

After the list, it output:
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.7.6-2ubuntu7.10_i386.deb:](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.7.6-2ubuntu7.10_i386.deb:) Could not resolve 'security.ubuntu.com'

I'm sorry I can't copy/paste my output, but having no gui forces me to use the forums from my phone.

---

### Post by fdrake on 2011-11-25
are you sure you are online?
can you ping?

```

ping google.com -c 10

```

---

### Post by Alexalad on 2011-11-25
Honestly, I don't know. I don't even know what ping is. But that command output:

ping: unknown host google.com

---

### Post by fdrake on 2011-11-25
that means you are offline that's why you cannot download and install the packages . There should be nothing wrong with your source list. Do you use wifi to connect ? can you use an Ethernet cable for you connection?

---

### Post by Alexalad on 2011-11-25
I use wifi, but I have an ethernet cord  if I have to use it. How do I connect using the terminal, though?

---

### Post by fdrake on 2011-11-25
plug the Ethernet CAT-4 cord > reboot your pc > try the ping command;
if you see lines with numbers appearing it means you are connected. if  not you my have a DNS problem or DHCP issue to configure. In this case I suggest to use a live cd and back up your data and reinstall (it will probably take less than fixing the problem). If you are connected try to install the xorg package from my previous post.

Unfortunatelly I have to leave I hope you can solve your issue.
good luck. As I said before if you have few data to save just reinstall. It's not easy to communicate trough the phone in the forum.
Best of luck! 
Drake.

---

### Post by Alexalad on 2011-11-25
I can't find my ethernet cord. So I was trying to connect to my wifi through the terminal using the command:
'sudo iwconfig wlan0 essid Fishtank key s:XXXXXXXXXX'

I scanned beforehand, and I checked the spelling and capitalization twice, and I know everything is right. Unfortunately, it just output:

Error for wireless request "Set Encode" (8B2A) :
SET failed on device wlan0 ; Invalid argument.


I was hoping someone could tell me what this means, or where I messed up, or if its fixable. I haven't had a gui for 4 days, now and i'm kinda desperate. Thanks in advance.

---

### Post by lolpenguin on 2011-11-25
If you can't find the ethernet cord, buying one is feasible. The easiest way to connect to the internet is using (an ethernet cord).
If we don't come to an easy solution, back up important files/directories (eg. /home/user/, /usr/share/)

---

