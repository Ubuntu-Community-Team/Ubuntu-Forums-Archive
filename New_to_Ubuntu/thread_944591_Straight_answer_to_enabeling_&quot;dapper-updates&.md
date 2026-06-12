---
title: "Straight answer to enabeling &quot;dapper-updates&quot; channel"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by NoJobyDesert on 2008-10-11
Trying to upgrade from 6.06 to 8.04. I understand that the "dapper-updates" software channel needs to be enabeled. I have searched around and am unable to find a stright forward answer to do this. Something about "/etc/apt/sources.list" maybe?

---

### Post by louieb on 2008-10-12
Its been awhile since I've used Dapper. Tools have been added since to  manage software sources with a GUI. 

If you have been getting security updates  the channel is enabled.

Are you follow the upgrade guide [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)? 

If you have more questions post /etc/apt/sources.list

Might want to backup your current install before you begin.  [Howto: Backup with Partimage - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=287522")

---

### Post by Kevbert on 2008-10-12
If you can, it may be easier to back up all your important data and perform a clean install of Hardy Heron. You can get a list of all installed packages with
```
sudo dpkg --get-selections > filename
```
Save the file to a floppy for safekeeping
Next you can then re-install these packages on 8.04 by copying the file to your home directory and running
```
sudo dpkg --clear-selections
sudo dpkg --set-selections < filename
sudo aptitude install dselect-upgrade

```

---

### Post by iponeverything on 2008-10-12
I think that you might have a much better chance of success by going from

dapper -> feisty -> hardy 

instead of trying to go direct from:  dapper -> hardy

---

### Post by NoJobyDesert on 2008-10-12
Yes, I am using this guide: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

I went into the update manager, and it offered me 8.04. I clicked "upgrade".
Good so far, this is what I get: [IMG]http://acsusa.fileave.com/sample/upg1.jpg[/IMG]

Then I get this:
[IMG]http://acsusa.fileave.com/sample/upg2.jpg[/IMG]
Is the site "archive.ubuntu.com" and "security.ubuntu.com" just unavailable. Or is there a bigger problem?

---

### Post by louieb on 2008-10-12
I just ping'ed both. No problem. 

```
ping archive.ubuntu.com
```
press <cntl+c>  to stop
Try it and see what you get. 
   
Please post /etc/apt/sources.list  

Just want to check to see if anything looks out of place.

---

### Post by NoJobyDesert on 2008-10-12
Here is my /etc/apt/sources.list:
> 
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe



---

### Post by louieb on 2008-10-12
looks like it should work.
but one odd thing you have a mix of the US mirror and the main archive 

mix of //us.archive.ubuntu.com/ and //archive.ubuntu.com/

If your in the US I'd edit the source.list file so that all the deb urls point to   //us.archive.ubuntu.com/   otherwise use     //archive.ubuntu.com/

To edit Press Alt+F2 to open the run dialog and enter
```
gksudo gedit /etc/apt/sources.list
```Or open System>Adminstration>Synaptic  Package Manager 

In Hardy under the **settings** menu there is a** repositories **option. Can't remember if Dapper had that too but you could try it and see. 

Btw the security urls look fine you should leave them as is.

---

