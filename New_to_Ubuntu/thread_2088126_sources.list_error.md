---
title: "sources.list error"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by pokemondawg2 on 2012-11-25
I can't sudo apt-get update or install anymore because of this error:

```
E: Malformed line 51 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

```

Help would be much appreciated on how to fix, thank you. :)

---

### Post by ibjsb4 on 2012-11-25
Hi [pokemondawg2]("http://ubuntuforums.org/member.php?u=1759369"), welcome to the forum  :)

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

cat -n /etc/apt/sources.list

and please post

---

### Post by pokemondawg2 on 2012-11-25
Got this:

```
 1
     2  # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     3  # newer versions of the distribution.
     4  deb http://us.archive.ubuntu.com/ubuntu/ quantal main restricted
     5  deb-src http://us.archive.ubuntu.com/ubuntu/ quantal restricted main multiverse universe #Added by software-properties
     6
     7  ## Major bug fix updates produced after the final release of the
     8  ## distribution.
     9  deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
    10  deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-updates restricted main multiverse universe #Added by software-properties
    11
    12  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    13  ## team. Also, please note that software in universe WILL NOT receive any
    14  ## review or updates from the Ubuntu security team.
    15  deb http://us.archive.ubuntu.com/ubuntu/ quantal universe
    16  deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates universe
    17
    18  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    19  ## team, and may not be under a free licence. Please satisfy yourself as to 
    20  ## your rights to use the software. Also, please note that software in 
    21  ## multiverse WILL NOT receive any review or updates from the Ubuntu
    22  ## security team.
    23  deb http://us.archive.ubuntu.com/ubuntu/ quantal multiverse
    24  deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
    25
    26  ## N.B. software from this repository may not have been tested as
    27  ## extensively as that contained in the main release, although it includes
    28  ## newer versions of some applications which may provide useful features.
    29  ## Also, please note that software in backports WILL NOT receive any review
    30  ## or updates from the Ubuntu security team.
    31  deb http://us.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
    32  deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse #Added by software-properties
    33
    34  deb http://security.ubuntu.com/ubuntu quantal-security main restricted
    35  deb-src http://security.ubuntu.com/ubuntu quantal-security restricted main multiverse universe #Added by software-properties
    36  deb http://security.ubuntu.com/ubuntu quantal-security universe
    37  deb http://security.ubuntu.com/ubuntu quantal-security multiverse
    38
    39  ## Uncomment the following two lines to add software from Canonical's
    40  ## 'partner' repository.
    41  ## This software is not part of Ubuntu, but is offered by Canonical and the
    42  ## respective vendors as a service to Ubuntu users.
    43  deb http://archive.canonical.com/ubuntu quantal partner
    44  deb-src http://archive.canonical.com/ubuntu quantal partner
    45
    46  ## This software is not part of Ubuntu, but is offered by third-party
    47  ## developers who want to ship their latest software.
    48  deb http://extras.ubuntu.com/ubuntu quantal main
    49  deb http://us.archive.ubuntu.com/ubuntu/ quantal-proposed restricted main multiverse universe
    50  deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-proposed restricted main multiverse universe #Added by software-properties
    51  deb http://launchpad.net pithos
    52  deb-src http://launchpad.net pithos
    53  deb-src http://extras.ubuntu.com/ubuntu quantal main

```

---

### Post by pokemondawg2 on 2012-11-25
I know I need to delete 51-52 but I'm not sure how...:(

---

### Post by monkeybrain2012 on 2012-11-25
> **pokemondawg2 said:**
> I know I need to delete 51-52 but I'm not sure how...:(

In the terminal type
```

gksudo gedit /etc/apt/sources.list

```

Delete the offending lines and save, close the editor.

Then in the terminal again

```
sudo apt-get update
```

Edited: Opps, you are using kubuntu so the editor is not gedit, I think it is kate but not sure, so replace gedit with kate in the above and see if it works.

---

### Post by pokemondawg2 on 2012-11-25
Error:

```
Failed to run gedit '/etc/apt/sources.list' as user root.

Unable to copy the user's Xauthorization file.
```

---

### Post by ibjsb4 on 2012-11-25
If your not using that PPA, yes then delete or just comment (#) out.

If you are using that ppa then change those lines to read

deb [http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu](http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu) quantal main 
 deb-src [http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu](http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu) quantal main

 [https://launchpad.net/~kevin-mehall/+archive/pithos-daily](https://launchpad.net/~kevin-mehall/+archive/pithos-daily)

---

### Post by El Tito on 2012-11-25
Hi. Pandora player?, I found this page in which it is correctly written the ppa:

[https://launchpad.net/~kevin-mehall/+archive/pithos-daily](https://launchpad.net/~kevin-mehall/+archive/pithos-daily)

click on technical details about this ppa, and correct the lines, (if this is what you were looking for).

Good luck!!

---

### Post by newb85 on 2012-11-25
Follow monkeybrain's advice.

As an aside, it looks like you tried to add a PPA for pithos.  You can add the developer's PPA as follows:

```
sudo add-apt-repository ppa:kevin-mehall/pithos-daily
```

Edit: sorry, didn't mean to duplicate.

---

### Post by El Tito on 2012-11-25
I would use nano to edit sources.list. It is very simple and it should not return any errors.
In the console type:

sudo nano /etc/apt/sources.list

---

### Post by ibjsb4 on 2012-11-25
> **pokemondawg2 said:**
> Error:

```
Failed to run gedit '/etc/apt/sources.list' as user root.

Unable to copy the user's Xauthorization file.
```

Don't know whats up with that, but just use your software sources.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab)

---

### Post by monkeybrain2012 on 2012-11-25
> **pokemondawg2 said:**
> Error:

```
Failed to run gedit '/etc/apt/sources.list' as user root.

Unable to copy the user's Xauthorization file.
```



See my edited post above, gedit is NOT the text editor for kubuntu, you need to change gedit to kate (I think)

---

### Post by ibjsb4 on 2012-11-25
> **monkeybrain2012 said:**
> See my edited post above, gedit is NOT the text editor for kubuntu, you need to change gedit to kate (I think)

kubuntu; duh  :)

Probably no software sources either

---

### Post by ibjsb4 on 2012-11-25
Well [pokemondawg2]("http://ubuntuforums.org/member.php?u=1759369"), if your not totally confused by the onslaught of post, lets add one more.

kdesudo kate /etc/apt/sources.list

should be correct for kubuntu

Edit: #!**!!

---

### Post by oldos2er on 2012-11-25
```

gksudo gedit /etc/apt/sources.list

```

Should be ```
kdesudo kate /etc/apt/sources.list
```

> Probably no software sources either

In Kubuntu it's ```
kdesudo software-properties-kde
```

---

### Post by pokemondawg2 on 2012-11-25
Ok well the only thing working for me here at the moment is: 
```
sudo nano /etc/apt/sources.list
```
Thing is, I'm not sure how to save my progress upon finishing. :confused:
P.S. I'm running Kubuntu 12.10 (Quantal Quetzal)

---

### Post by monkeybrain2012 on 2012-11-25
USe kdesudo and kate as posted by oldos2er and ibjsb4. nano is for geeks to show off or people without a graphic desktop . :) (I am surprised no one tells you to use vi yet)

Here you get the basic commands.
[http://mintaka.sdsu.edu/reu/nano.html](http://mintaka.sdsu.edu/reu/nano.html)

---

### Post by pokemondawg2 on 2012-11-25
Great, got rid of the Pithos error, but now this for OpenOffice:

```
W:Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/quantal/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

It's not coming up in sudo nano /etc/apt/sources.list now. :(

---

### Post by pokemondawg2 on 2012-11-25
I need to get access to '/etc/sources.list.d' to edit this but I'm not sure how to grant myself access to it. :confused: I added a screenshot of the directory.

---

### Post by monkeybrain2012 on 2012-11-25
Well it looks like you have added the OpenOffice ppa for some reasons, but it doesn't work for 12.10  [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa) Check the "published in" tab to see that it only works for old versions of Ubuntu.

It is not in /etc/apt/sources.list because there are files for them in /etc/apt/sources.list.d which is a directory, you can cd into the this directory and delete them 

find the two files in /etc/apt/sources.list.d

then 

```
sudo rm /etc/apt/sources.list.d/filename

```


or (recommended)

open the Software Centre, go to Edit > Software Sources > Other Software and remove the lines for the OpenOffice ppa (right click and choose remove) then  reload the Software Centre (This is in general the easiest way to manipulate sources list without having to manually edit it) 

I am not sure whether the Software Centre is in Kubuntu, if not maybe synaptic is installed? In that case go to Edited > Repositories > Other Software.

---

### Post by arpanaut on 2012-11-25
[http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/)

it would appear that that ppa is no longer maintained for anything after Maverick
see what you have in /etc/apt/sources.list.d  if they are in there remove or comment (#) at beginning of the offending lines.

EDIT: You would edit that file the same way you edited the other one.

---

### Post by pokemondawg2 on 2012-11-25
:grin: Finally, everything is back to normal, thank you to all of the people who took their time to help me. I appreciate it.

---

