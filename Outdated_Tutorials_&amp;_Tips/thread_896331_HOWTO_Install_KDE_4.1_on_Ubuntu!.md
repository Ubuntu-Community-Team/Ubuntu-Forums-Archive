---
title: "HOWTO: Install KDE 4.1 on Ubuntu!"
date: 2008-08-21
forum: Outdated Tutorials &amp; Tips
---

### Post by irrdev on 2008-08-21
This simple Howto will get KDE 4.1 STABLE up and running alongside Gnome and Ubuntu. Depending upon the speed of your internet connection, it will take between 20 minutes to 3 hours to complete the download/install.

**Preparation:** It is always a good idea to do a backup before you ever plan to install many packages all at once. You don't have to necessarily backup your home directory, but it would probably be advisable to at least backup /etc/. 

**Repositories:** We'll be taking advantage of a set of KDE 4.1 packages released by Kubuntu members on launchpad. _Go to System->Administration->Software Sources_. At this point you will be asked for your administrative password. After authentication, a small window will appear in the middle of the screen. _Open the "Third-Party Software" tab_. At the bottom of the window, _click the "Add..." button, and type in_: > *[COLOR="Blue"]deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main[/COLOR]* in the prompt that appears. Close the prompt by clicking the "Add Source" button. Finally, click the "Close" button at the bottom-left of the window. A progress update dialog will appear, as Ubuntu will take a few minutes to update your repositories, so be patient. That's it for the first step! Now we can install the packages...

**Installation:** Open a terminal window by clicking _Applications->Accessories->Terminal_. At the terminal prompt, type:
> sudo aptitude update && sudo aptitude install kubuntu-kde4-desktop
Click enter, and you will be prompted for your administrative password. Authenticate, click enter, and aptitude should take care of the rest. As I said before it can take anywhere from 20 minutes to 3 hours to complete the package downloads, all depending upon your internet connection. When the download is complete, KDE 4.1 will be automatically installed on your computer.

**Post-Installation:** I assume that if you plan to use KDE 4.1, then you will probably want to use the KDE 4.1 Desktop Manager (kdm). This step isn't strictly necessary, but it is rather nice nonetheless. After the KDE 4.1 packages are downloaded and installed, type the following command at the prompt:
> sudo dpkg-reconfigure kdm-kde4
Enter your password, and use the arrow and enter keys to navigate the terminal-based wizard. When you are prompted to choose a Desktop Manger, select "kdm-kde4" with the arrow keys and click enter. 

**Up and Running!** It's now time to try out KDE 4.1! You'll probably need to restart your computer first, however, so that kdm-kde4 will replace gdm. After restart, you'll be presented with a new slick-looking login screen. First of all, _click "Session" ( or Options->Session) and select "KDE 4" in the dialog that appears. Click OK to confirm your choice_. Now you can enter your username and password before clicking enter. You will prompted with a dialog asking "Do you want to make KDE 4 your default Desktop?". This choice is really totally up to you. You might want to get used to running KDE 4.1 before you make it the default, however. Should you ever want to login to Gnome again, click the Session button at login and select "Gnome" instead. It's that simple!


**That's it!** You now have both Gnome and KDE 4.1 installed on your computer. Have fun experimenting with your new kde desktop, and if you want, you can install extra *plasmoids* by typing this command in the terminal or konsole:
> sudo apt-get install kdeplasma-addons

Should you ever want to remove KDE 4.1 from your computer *completely*, the job is quite simple. Simply type in this command at the terminal:
> sudo aptitude remove kubuntu-kde4-desktop

Thanks for reading this small howto/tutorial! Hope it helps! If you have any problems, just post them below. :)

---

### Post by killingtime on 2008-08-26
great share...working fine in my ubuntu :D

---

### Post by N1ko on 2008-08-30
Hi, I tried to remove the metapackage (kubuntu-kde4-desktop) and it did remove itself just fine but it also left all the kde-packages. How I can remove kde4.1 totally?

---

### Post by gjoellee on 2008-08-30
on the link below you can download and install KDE4.1 with a one click install =)
[http://kshoster.net/?c=downloads_apturl](http://kshoster.net/?c=downloads_apturl)

just find "KDE4":)

I like to keep it easy

---

### Post by irrdev on 2008-09-03
> **N1ko said:**
> Hi, I tried to remove the metapackage (kubuntu-kde4-desktop) and it did remove itself just fine but it also left all the kde-packages. How I can remove kde4.1 totally?
If you used aptitude instead of apt-get to originally install kubuntu-kde4-desktop, removing this metapackage with aptitude will remove all of the kde4 packages. Apt-get will not do this for you. That is why I instructed to use aptitude for the installation. 

If you **did** use apt-get instead of aptitude for installation, and wish to fully remove the kde4 packages, there is still a foolproof way to get rid of them. Open Synaptic Package Manager, make sure the "Origin" filter is selected in the left-hand pane, and then select the [COLOR="Blue"]ppa.launchpad.net/main[/COLOR] repository. Synaptic will list all the installed and available packages for kde4. Simply go through the list, and deselect all the installed ones. Now select the [COLOR="Blue"]ppa.launchpad.net/universe[/COLOR] repository, and repeat the entire process. When you are finished, click "Apply" in the toolbar, and all the kde4 packages will be completely uninstalled!

---

### Post by bayvista on 2009-02-25
Thanks for a great Howto. I now have KDE up and running. BUT: I am trying to use Kaffeine. When I click on 'Help', it says:

Could not launch HELP. Could not find khelpcenter

Any ideas?

---

### Post by bayvista on 2009-03-02
*sudo aptitude remove kubuntu-kde4-desktop *

This can be a very dangerous command as I found out. It also removed Gnome and I ended up with an unusable system. After much stuffing around, I reinstalled KDE, found the Synaptic equivalent and eventually found Gnome (the applications are not sorted by name!!). I reinstalled Gnome and now all I have to do is get rid of KDE properly. I think I'll stick to Symantic.

Not very amusing

---

