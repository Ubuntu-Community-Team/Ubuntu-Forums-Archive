---
title: "Change Desktop Environment"
date: 2024-06-19
forum: New to Ubuntu
---

### Post by emmanuelkatto on 2024-06-19
Hi everyone, I am Emmanuel Katto and I'm new to Ubuntu. I'm having some trouble figuring out how to change my desktop environment. I've heard of GNOME, KDE, and XFCE, but I'm not sure how to switch between them. I currently have the default GNOME desktop environment, but I'd like to try something else.


 Can someone please guide me on how to switch to a different desktop environment? 

Thanks!
Emmanuel Katto

---

### Post by Rubi1200 on 2024-06-19
You could add another user or multiple users (Linux is designed for multi-user scenarios) and then download and install each desktop environment you want to try. Then when you login in to, say, user2 you would access that particular environment.

However, there is a much simpler and in my opinion fun way which is to either use liveUSB versions or better still install a virtual machine client and install different flavours,

If you are on Gnome take a look at Gnome Boxes (which can be installed from the repositories). It does not offer all the fine-tuning options that some other clients have but it does offer an easy way to install and use virtual machines.
[https://help.gnome.org/users/gnome-boxes/stable/](https://help.gnome.org/users/gnome-boxes/stable/)

---

### Post by guiverc on 2024-06-19
I'm a lover of many desktops on my system...

I'm using Ubuntu *oracular* currently, and the desktop I'm signed in with is a Lubuntu session, ie. I'm using the LXQt desktop as packaged by the Lubuntu team (*I'm a Lubuntu team member*), but my install media was actually an Xubuntu ISO.  When I boot the system, it gets to the DM (*Display Manager*) which can also be called *greeter*, where I select my username & enter password... There is a area there where I can click & get a dropdown of options which let me choose the session I wish to use; which is where I can select Ubuntu Desktop (Xorg), Ubuntu Desktop (Wayland), Xubuntu Desktop... Lubuntu Desktop.. & many more.  I usually just enter the password though & it logs in with whatever I used last.

There are complications when using a multi-desktop system like I'm using, so be warned it's not really for newbies, further you can't keep adding desktops on a Ubuntu system and not expect strange *quirks* or *issues* (I've written about that [here]("https://askubuntu.com/questions/1295149/installing-several-different-flavours-of-ubuntu-20-04")).  Key complications can be

- more packages installed; so larger footprint (ie. more disk space required for your system)
- more packages to update; thus more & larger updates (bandwidth used)
- more programs appearing in windows.. eg. if I search for text editor I'll see *featherpad* (Lubuntu LXQt), *mousepad* (Xubuntu Xfce), *text *(Ubuntu Desktop GNOME), *pluma *(Ubuntu MATE) etc... and using the wrong one for your desktop can use excess RAM (*this won't be an issue if you have >5 GB of RAM*)


I still love it....


(   I've used multiple desktops for decades.. but originally it was because I could download Ubuntu Desktop ISOs bandwidth free from home, install them & switch to a local mirror (*making package upgrades/downloads bandwidth free*) then remove the ubuntu-desktop package and all GUI that was installed, and install with the *flavor*-desktop I wanted to use still bandwidth/quota free... I accidentally didn't erase the ubuntu-desktop meta-package that was originally installed & discovered I could have multiple.. which is where I am now  )

Summary

- you can have multiple desktops installed  (*what I do now*)
- you can even remove what you had (*do this at text terminal*) then install the new desktop you want to try  (*what I originally did*)
- there are costs to multi-desktop installs (*bandwidth, disk space, complexity*), and if you *bloat* your system down too heavily additional quirks/problems can occur.

---

### Post by KenUBF on 2024-08-01
I would second what the other replies say. I'd test out other desktop environments in a Virtual machine first to see which you like best, and then move to install the one you like best. I wouldn't recommend installing anymore than one other environment because of the glitches that can occur. That happened to me when I tried to install KDE with Gnome (which I'm using now) and I just didn't like it as much as I thought I would so I went to uninstall it and my system began to glitch out and UI elements didn't match, as if parts of KDE didn't get properly uninstalled and I wasn't able to fix it and had to reinstall my system.

Having been given this warning and you choose one after trying them out in a virtual machine and still want to try out a new desktop environment on your main system follow these steps. First, update your system. Then you can install KDE for example by opening the command line, also called the Terminal and typing: sudo apt install kde-plasma-desktop When you log out and then see your log in screen you should see a drop down menu with an option for your new KDE environment along with your original one. The steps are pretty much the same for every other desktop environment. 

Here is a YouTube video that looks to be a good tutorial for extra help. [https://www.youtube.com/watch?v=ifyu2mcze4M](https://www.youtube.com/watch?v=ifyu2mcze4M)

---

### Post by guiverc on 2024-08-01
I'll add another alternative, which can effect a change of desktop environment via re-install; ie. *non-destructive re-install*.

I've written about this [here on another support site]("https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533").

I'll walk though a *Quality Assurance* test I've run for many releases, and whilst problems were discovered with it during *noble* or 24.04 testing (*thus its more limited for 24.04 where ubuntu-desktop-installer is being used*), it still works... alas issues I discovered lead to *forced format* I talk about [here]("https://askubuntu.com/questions/1515275/cant-uncheck-format-checkbox-on-manual-partitioning-screen-when-trying-to-r") (24.04 ISOs using *ubuntu-desktop-installer*).

I start with a Lubuntu system, ie. desktop configured with additional apps installed, my data files, altered wallpaper & themes selected.  My starting point being Lubuntu/LXQt is only because I'm that team, but it could be any system (ie. start with Xubuntu, Kubuntu, Ubuntu-MATE, Ubuntu Desktop etc)

- *non-destructively *install Ubuntu Desktop over the Lubuntu system.  The install requires internet, so it can download the *manually installed* apps you added to the system, but the expectation here (*if done correctly*) is you've replaced the LXQt desktop used by Lubuntu, with a GNOME system used by Ubuntu Desktop....  In QA I use a non-standard music player so I can re-start that player & have it continue my playlist/songs (*that app re-installing being a check I was going to perform anyway*).

-* non-destructively *install Xubuntu over what was a Ubuntu (GNOME) system.. ie. the GNOME desktop will be replaced by a Xfce desktop, with core apps changed to Xfce apps, but my additional or *manually installed* apps re-installing...  Again I expect my datafiles to be there, so I continue listening to my music playlist as I check this out...

- (I'll do same with Ubuntu-MATE, Kubuntu and others if I have time..)

- *non-destructive* install of Lubuntu, where I expect this final install to return me to where I was, whilst it won't be a *new* or *clean* install, as I expect to be returned to my changed wallpaper, my altered themes etc I made after my initial install, as this was not the addition of a desktop I'd not used before, but a re-install of LXQt thus it won't appear as clean... Again I expect my additional or *manually installed* apps & datafiles to be present....

This can be a *cleaner* approach, for one its easier; however as it involves an install, it's easy to make a mistake & accidentally erase data should you forget to uncheck a format box etc... thus always have good backups before you attempt this...

Note: Issues


As KenUBF does indicate, whilst each desktop does keep its own configurations, there is overlap in that many desktops are GTK based & thus changes to one theme will impact other GTK based desktops, likewise the Qt based desktops can influence particularly other Qt configs... plus most desktops change GTK/Qt themes at each change (as most users will expect a Qt app to theme correctly when they change a GTK desktop)... I'm somewhat (*acutely*) aware of this thru experience, thus tend to be careful when I make any theming change.


Changing desktops can be done via package changes; but I've found slight differences between releases, which is why I've now just change via *meta-packages*, esp. the Ubuntu *flavor* team packages as upstream *debian meta packages* can have differences for releases (*esp. where re-installs are used which is something I do*).

---

