---
title: "trying to transition from win10 -need software advice"
date: 2019-08-14
forum: New to Ubuntu
---

### Post by derek99 on 2019-08-14
Win 10 update forced me to switch to Linux.
I had some tools that I used constantly: FC (a Norton Commander style file manager), Notepad, and win-d to reveal the desktop.
Can somebody please advise on suitable Linux replacements?
I have also found software installation to be a nightmare. Is there a Ubuntu-for-beginners guide that does not assume some prior knowledge?

---

### Post by Autodave on 2019-08-14
You really need to install programs from either the Software Center or via *synaptic.*  Linux is quite different from Windows: so much different that you are better off forgetting everything you know about Windows.  I learned that lesson the hard way about 10 year ago when I moved to Linux.

Please tell us exactly what version of Linux you installed.

---

### Post by &amp;wP*!) on 2019-08-14
In addition to Autodave's comments, Ubuntu installation requires little understanding about your computer. Be aware that installing an operating system will wipe out the things on the harddisk where you install it with default settings. If you do a backup, just use the default settings of the installation procedure of Ubuntu.  
Take the LTS (long-term-support) of Ubuntu to install. [Download from here]("https://ubuntu.com/download/desktop") and burn it to a USB and boot your computer. Follow the instructions during the installation. I have been using Linux for at least 15 years - Ubuntu is so far the distribution, which installation is the easiest one!

---

### Post by TheFu on 2019-08-14
If you try to make Ubuntu work like Windows, you will be disappointed.  It is a very different OS with very different philosophies.
[http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) Linux for Windows People
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm) Linux is NOT Windows

Start with those two, then you can move onto the "Ubuntu Desktop Guide". [https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)

Whenever posting for help, please always include the Ubuntu version and which GUI (also called a "desktop"), so people don't have to guess. The 1st link above will explain a DE/Desktop. There are about 10 popular DEs.  Linux is loosely connected to the GUI.  It is just another program. The OS is not the GUI and more than notepad is the only editor on Windows.  Linux has lots and lots of different, crazy powerful, editors.  For a beginner, gedit, kate, or geany might be what you like.  I don't use any of those, though geany would be my preference as a programmer if my editor wasn't available.

You should use the current LTS release, 18.04, as a beginner.  No question about that.  Newer isn't better and 18.04 has free support until 2023.  Other releases have 9 months of support from their release date - so ... 19.04 support ends at the new year start.  No support, no patches, no upgrade path if you wait too long.  Basically, 19.04 users have 2.5 months to upgrade to 19.10 after it is released.
I'm an LTS-only person as are most server admins.  I won't install any non-LTS release on my servers.

If you google for answers, you'll need to learn to recognize reputable authors on reputable sites.  Staying with sites that have "ubuntu" in their domain name is usually safe.  There are many reputable websites that don't have ubuntu in their names, but it is best to learn about those from others. Look for references in these forums by posters with good reps.  Also, include the specific release in your search, since many important things have changed every 2 yrs to make instructions for 16.04 useless for 18.04 installations.

If you want more guides from more people, here's a list: [https://help.ubuntu.com/community/ExternalGuides](https://help.ubuntu.com/community/ExternalGuides)

---

### Post by oldfred on 2019-08-15
I prefer synaptic to install apps if not using command line. Program name may not be name used to install it.
sudo apt install synaptic

[https://en.wikipedia.org/wiki/Norton_Commander](https://en.wikipedia.org/wiki/Norton_Commander)
Midnight Commander is in repository
Search in synaptic gives me mc but also some other alternatives including krusader & gnome-commander
sudo apt install mc

[https://www.osalt.com/search?q=notepad](https://www.osalt.com/search?q=notepad)

Scroll down for many alternatives
[https://www.linuxalt.com/](https://www.linuxalt.com/)

If you go into help on the desktop menu, you can get to tips & tricks & then keyboard shortcuts.

---

### Post by him610 on 2019-08-15
You can substitute Midnight Commander for  FC (a Norton Commander style file manager) 
Any *buntu distribution has full screen text editors included, and can replace Notepad.
I use Xubuntu which includes Mousepad, nano, gedit, vi, and access (downloadable) to many others using synaptic or Software Center.

The Linux Command Line By William Shotts can be downloaded here,  [http://linuxcommand.org/tlcl.php]("http://linuxcommand.org/tlcl.php"). It is a very good book for those new to Linux; as well as, some of us who have been Linux users for a while.

---

