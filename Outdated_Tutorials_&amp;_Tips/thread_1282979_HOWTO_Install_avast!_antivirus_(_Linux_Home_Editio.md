---
title: "HOWTO: Install avast! antivirus ( Linux Home Edition )"
date: 2009-10-05
forum: Outdated Tutorials &amp; Tips
---

### Post by credobyte on 2009-10-05
[CENTER][[IMG]http://i37.tinypic.com/25gts47_th.png[/IMG]]("http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb")[SIZE=5][B][COLOR=Green]
a[/COLOR][/B][/SIZE][SIZE=5]**[COLOR=Green]vast![/COLOR] Linux Home Edition**[/SIZE]
[SIZE=2][COLOR=DimGray]Ubuntu 9.04 ( Jaunty Jackalope )[/COLOR][/SIZE]
[/CENTER]
 [CENTER]



[/CENTER]
 [CENTER]
[LEFT][COLOR=Red]**All-in-One ( command for those who don't have the time to follow the guide )**[/COLOR]
```
cd $HOME && wget http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb && sudo dpkg -i avast4workstation_1.3.0-2_i386.deb && rm avast4workstation_1.3.0-2_i386.deb
```
[LIST=1]
[*]Download Avast anti-virus .deb by clicking on the Download button at the top of this guide
[*] Move the file ( [COLOR=Green]avast4workstation_1.3.0-2_i386.deb[/COLOR] ) to your home directory ( example: /home/ubuntu )
[*] Open Terminal ( [COLOR=RoyalBlue]Applications -> Accessories -> Terminal[/COLOR] ) and execute the following commands
[/LIST]
  ```
cd ~/
sudo dpkg -i avast4workstation_1.3.0-2_i386.deb
```[COLOR=Green][B]
Congratulations![/B][/COLOR] Avast anti-virus have been successfully installed and you can access it by using it's launcher under [COLOR=RoyalBlue]Applications -> Accessories[/COLOR].

[/LEFT]
 [LEFT][COLOR=Gray]** To get your registration key, go to [http://www.avast.com/eng/home-registration.php#registration](http://www.avast.com/eng/home-registration.php#registration) and fill the form.[/COLOR][/LEFT]
 
[/CENTER]

---

### Post by adeypoop on 2009-10-18
I use Avaast on windows, had't realised there is a linux version. I can't help wondering if this is needed though? I understood Linux to be quite safe from virus without requiring anti-virus software due to the fact apps don't run as root. Anyone know if we really need anti-virus software in our linux os?

---

### Post by sigurnjak on 2009-10-18
Can it be set up to scan email in thuderbird ?

---

### Post by Meanderer on 2009-11-07
> **adeypoop said:**
> I use Avaast on windows, had't realised there is a linux version. I can't help wondering if this is needed though? I understood Linux to be quite safe from virus without requiring anti-virus software due to the fact apps don't run as root. Anyone know if we really need anti-virus software in our linux os?

I'm new to all this BUT I did read a thread the other day that warned of "sharing" files between Ubuntu and Windows. It said that if you download a file via Ubuntu you are virtually safe from viruses etc unless you use a contaminated file via your windows system. It suggested that you have to virus check it be using in windows.
I've just learnt how to share a Thunderbird files between Ubuntu or WinXP on separate drives. So that's why I'm now looking to use Avast with Ubuntu as I do with WinXP.

---

### Post by PhantomPholly on 2010-08-27
Odd issue:  Fresh install - the Applications/Accessories menu option for Avast disappeared after running once.

Ubuntu 10.04.1, full install default choices full disk (format first).
Installed ok, ran update manager ok, re-boot.
Install Avast! - menu option appeared under Applications/Accessories as expected.
Run Avast, select "update database" - abend.  Now the menu option is gone!  Grrr.

Run the instructions above to add menu option - no luck.  Search for abend; Google is your friend.
Execute the fix described (sysctl -w kernel.shmmax=128000000).  That doesn't fix the missing menu.  Remove using Synaptic Package Manager; re-install.  No joy.

Start over (full Ubuntu re-install), this time adding the sysctl -w kernel.shmmax=128000000 fix before installing Avast.  Again the menu option appears.  Being more cautious, re-boot before trying it (Windows habit, sorry but I'm still a NooB!).  After re-boot, menu option is gone again!

Still the "add the menu command" does not work.  Synaptic Package Manager says it is installed, but I don't know how to make it execute or add the menu option.

Help?

---

### Post by jkonrad on 2011-03-05
This post seems to be referring to another thread with longer instructions.

I just downloaded and installed Avast for Linux. I then updated the engine, and experienced the problem that others have mentioned here

[http://ubuntuforums.org/showthread.php?p=9101637](http://ubuntuforums.org/showthread.php?p=9101637)

I followed the instructions for the fix and rebooted. Now I do not have the icon for Avast. I'm not sure what the executable is, nor where to find it. If I did and it's still on the system, making an icon is not hard.

Any thoughts on why this happens. Oh ... I'm loading this on my linux laptop so I can go fix my sisters Windows machine. It's sick with a virus so I thought I'd just plug in her HD to this sweet Ubuntu box and clean it up. Anyone with some helpful thoughts for me?

---

### Post by frankduffey on 2011-03-28
> **jkonrad said:**
> This post seems to be referring to another thread with longer instructions.

I just downloaded and installed Avast for Linux. I then updated the engine, and experienced the problem that others have mentioned here

[http://ubuntuforums.org/showthread.php?p=9101637](http://ubuntuforums.org/showthread.php?p=9101637)

I followed the instructions for the fix and rebooted. Now I do not have the icon for Avast. I'm not sure what the executable is, nor where to find it. If I did and it's still on the system, making an icon is not hard.

Any thoughts on why this happens. Oh ... I'm loading this on my linux laptop so I can go fix my sisters Windows machine. It's sick with a virus so I thought I'd just plug in her HD to this sweet Ubuntu box and clean it up. Anyone with some helpful thoughts for me?
:)
Why not use a Ubuntu CD ton clean the windows machine look up clean windows virus with Ubuntu cd on how to geek there are instructions on how to clen her machine with a ISO boot cd or use a linux boot cd with antivirus tools. there are several ones available.:guitar:

---

