---
title: "E: Malformed entry 54 in list file /etc/apt/sources.list (Component)"
date: 2019-05-14
forum: New to Ubuntu
---

### Post by pquiros on 2019-05-14
Hello,

I'm new to Ubuntu and I have been trying to install some new programs but I get the following error "E: Malformed entry 54 in list file /etc/apt/sources.list (Component) "  I read a thread like this one, but in line 54 I see deb [http://dl.winehq.org/wine-builds/ubuntu/](http://dl.winehq.org/wine-builds/ubuntu/) xenial-mai , instead of [COLOR=#000000][FONT=&quot]54	deb [http://archive.canonical.com/](http://archive.canonical.com/) xenialpartner

[/FONT][/COLOR]Can someone help me resolve this issue ? :confused:



Here is the output of the steps I followed from the previous thread ([https://ubuntuforums.org/showthread.php?t=2347097](https://ubuntuforums.org/showthread.php?t=2347097)) 

Thanks in advance.

Ubuntumachine:~$ find /etc/apt/  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

```
     1	### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2	# You may comment out this entry, but any other modifications may be lost.
     3	deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
```


/etc/apt/sources.list.d/gns3-ubuntu-ppa-bionic.list


```
     1	deb [http://ppa.launchpad.net/gns3/ppa/ubuntu](http://ppa.launchpad.net/gns3/ppa/ubuntu) bionic main
     2	# deb-src [http://ppa.launchpad.net/gns3/ppa/ubuntu](http://ppa.launchpad.net/gns3/ppa/ubuntu) bionic main
     3	# deb-src [http://ppa.launchpad.net/gns3/ppa/ubuntu](http://ppa.launchpad.net/gns3/ppa/ubuntu) bionic main
```


/etc/apt/sources.list


     ```
1	# deb cdrom:[Ubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210)]/ bionic main restricted
     2	
     3	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4	# newer versions of the distribution.
     5	deb [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) bionic main restricted
     6	# deb-src [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) bionic main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) bionic-updates main restricted
    11	# deb-src [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) bionic-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) bionic universe
    17	# deb-src [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) bionic universe
    18	deb [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) bionic-updates universe
    19	# deb-src [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) bionic-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) bionic multiverse
    27	# deb-src [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) bionic multiverse
    28	deb [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) bionic-updates multiverse
    29	# deb-src [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) bionic-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse
    37	# deb-src [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse
    38	
    39	## Uncomment the following two lines to add software from Canonical's
    40	## 'partner' repository.
    41	## This software is not part of Ubuntu, but is offered by Canonical and the
    42	## respective vendors as a service to Ubuntu users.
    43	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
    44	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
    45	
    46	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
    47	# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
    48	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
    49	# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
    50	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
    51	# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
    52	deb [http://dl.winehq.org/wine-builds/ubuntu/](http://dl.winehq.org/wine-builds/ubuntu/) xenial main
    53	# deb-src [http://dl.winehq.org/wine-builds/ubuntu/](http://dl.winehq.org/wine-builds/ubuntu/) xenial main
[COLOR=#ff0000]    54	deb [http://dl.winehq.org/wine-builds/ubuntu/](http://dl.winehq.org/wine-builds/ubuntu/) xenial-mai[/COLOR]
    55	# deb-src [http://dl.winehq.org/wine-builds/ubuntu/](http://dl.winehq.org/wine-builds/ubuntu/) xenial-mai
    56	deb [http://dl.wine-builds/ubuntu/](http://dl.wine-builds/ubuntu/) xenial main
    57	# deb-src [http://dl.wine-builds/ubuntu/](http://dl.wine-builds/ubuntu/) xenial main
```

---

### Post by ajgreeny on 2019-05-14
> 54	deb [http://dl.winehq.org/wine-builds/ubuntu/](http://dl.winehq.org/wine-builds/ubuntu/) xenial-mai
55	# deb-src [http://dl.winehq.org/wine-builds/ubuntu/](http://dl.winehq.org/wine-builds/ubuntu/) xenial-mai
    Line 54 in that file you show us should read **xenial main** at the end , as should line 55 but as that is commented out (the # at the start) it will be ignored by the system and no error will show.

Edit the file manually (ask if you're not sure how) and then run ```
sudo apt update
sudo apt upgrade
```
Hopefully your error will now be gone.

---

### Post by yetimon_64 on 2019-05-14
ajgreeny's post should help you get rid of the error though one thing I've noted from your sources.list file is you appear to be a using a Bionic (18.04) install but for some reason are using the Xenial (16.04) repository for wine-builds.

According to [[COLOR=#0000ff]https://wiki.winehq.org/Ubuntu[/COLOR]]("https://wiki.winehq.org/Ubuntu") there is a Bionic repository as well. Normally you should be using their Bionic repository on a Bionic install. Is there any particular reason you have used the Xenial repository for wine-builds instead of the Bionic repository?

Regards, yeti.

---

### Post by ajgreeny on 2019-05-15
Well noticed yetimon_69!

I certainly missed that, but you're quite right, of course, and the discrepancy in versions should be dealt with.

---

### Post by pquiros on 2019-05-17
Hello guys,

Thanks for the quick reply, yes I am really new to ubuntu and honestly [COLOR=#000000]there's not a particular reason I have used the Xenial repository for wine-builds instead of the Bionic repository[/COLOR]
I simply installed it to give it a try, so far I like it but just getting use to it.

I read the information found in this forum [COLOR=#000000] [/COLOR][https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)[COLOR=#000000] but I was not successful trying to address the issue. Can you help me out here, to address the issue with the  [/COLOR][COLOR=#000000]discrepancy in versions ?

[/COLOR]Thanks in advance.

---

### Post by CatKiller on 2019-05-17
> **pquiros said:**
>  Can you help me out here, to address the issue with the  discrepancy in versions ?

First of all, that file is simply a text file. Your computer won't explode if you put the wrong thing in. As you've already found, if that file is wrong it just means that you can't update, and you might have trouble installing things.

You can see from the other entries that the right format is to have a URL, then a single-word description of which release it's for, and then a single-word description of which branch of the software you're interested in.

In your case, you're using 18.04, codenamed Bionic Beaver, so you're interested in the **bionic** release, rather than the xenial release. Xenial Xerus was the codename for 16.04.

For the last part, different projects have different branches for different purposes. There might be a branch called testing, or staging, or security, or whatever. It depends on the project, and the people that maintain the repository. In this case, you want to be using the **main** branch.

---

### Post by pquiros on 2019-05-17
Awesome guys, thanks a lot for the help, I finally got it fixed

---

### Post by Geoffrey_Arndt on 2019-05-17
In my view, the easiest way to edit the sources data (file) is to go through the graphical front end "Software & Updates" and click on the "Other Software" tab.   Then highlight the line in the source listing you need to update - - you'll see the "edit" button is now activated and available to change the source address.

---

