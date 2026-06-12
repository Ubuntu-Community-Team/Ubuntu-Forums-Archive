---
title: "HOWTO: Integrate Ubuntu Studio with your existing Ubuntu installation."
date: 2007-05-21
forum: Outdated Tutorials &amp; Tips
---

### Post by scottpledger on 2007-05-21
This is my first how-to, so if I make any mistakes here or if it is not easy enough to understand, let me know and I will fix them as soon as I can.

Below are the steps that I took to integrate the new Ubuntu Studio into my existing Ubuntu install.  I have no guarantees that it will work with anything other than Ubuntu 7.04.  It may/may not apply to (X/Ed/K)ubuntu.[LIST=1]
[*]From a terminal, run the following two commands:
```
sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
```This one will add the Ubuntu Studio repository to your apt-get sources list.

```
 wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update
```And this one will add the gpg key to your apt-get keys.
[*]Now, if you prefer to use the command line to install your packages, run the following:

```
sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-gdm-theme ubuntustudio-graphics ubuntustudio-icon-theme ubuntustudiolauncher ubuntustudio-look ubuntustudio-screensaver ubuntustudio-session-splashes ubuntustudio-theme ubuntustudio-video ubuntustudio-wallpapers
```Otherwise, go into Synaptic and select the following packages for installation.
```

ubuntustudio-audio
ubuntustudio-audio-plugins
ubuntustudio-gdm-theme
ubuntustudio-graphics
ubuntustudio-icon-theme
ubuntustudiolauncher
ubuntustudio-look
ubuntustudio-screensaver
ubuntustudio-session-splashes
ubuntustudio-theme
ubuntustudio-video
ubuntustudio-wallpapers

```Click 'Apply'.

NOTE: I did *_**not**_* include ubuntustudio-sounds, ubuntustudio-desktop, ubuntustudio-artwork, and ubuntustudio-default-settings.  When I selected these, synaptic wanted to remove ubuntu-desktop and ubuntu-sounds, which I didn't want.  You can select these if you wish, but I have not tried them, and thus I can't say if they will work or not.  Let me know if they do/do not work for you and I will modify this to reflect that.
WARNING:  ilheu has told me that the ubuntustudio-gdm-theme is no longer in the repo (Not completely confirmed, but suspicions exist).  If you have found this to be accurate, I have attached the necessary .deb file to this thread.
[*]Restart your computer.
[*]Once it has restarted, your gdm theme should be different.  If it is not, don't worry -- just log in as usual.
[*]If you would like your system to have the same appearance as Ubuntu Studio, continue following this guide.  Otherwise, you're done!
[*]If you want to change the theme to the Ubuntu Studio theme, follow these steps:[LIST=1]
[*]Go to System -> Preferences -> Theme.
[*]Scroll down and select the 'UbuntuStudio' theme.
[*]If you don't mind having a different background and it says that it suggests a desktop background, click that button (otherwise you will have the original Ubuntu background, which looks kind of awkward).
[*]Click 'Close'.[/LIST] 
[*]If you still had the old Ubuntu GDM theme and want to change it, follow these steps:[LIST=1]
[*]Go to System -> Administration -> Login Window.
[*]Click the 'Local' tab at the top of the window.
[*]Under the theme list, select 'Ubuntu-Studio'.
[*]Click 'Close'.[/LIST] 
[*]If you want to change the splash screen for when you log in, follow these steps:[LIST=1]
[*]Go to System -> Administration -> Synaptic Package Manager.
[*]Search for "gnome-splashscreen-manager".
[*]Select 'gnome-splashscreen-manager' for installation.
[*]Click 'Apply'.
[*]Once it has finished installing the packages, close Synaptic.
[*]Now, go to System -> Preferences -> Splash Screen.
[*]Click 'Install'.
[*]When the 'Open' dialog appears, navigate to '/usr/share/pixmaps/splash/' and install each individual .png file under that directory.  This way, you won't have to do this again in the future, if you want to go back to the original Ubuntu splash screen.
[*]Select 'splash_US.png' and click 'Activate'.
[*]Close the Splashscreen Manager window.[/LIST] 
[*]If you want to change your Screensaver to the Ubuntu Studio screensaver, follow these steps:[LIST=1]
[*]Go to System -> Preferences -> Screensaver.
[*]Select 'Floating Ubuntu Studio'.
Note: The 'Flurry' Screensaver is cooler.
[*]Make sure that you have 'Activate screensaver when computer is idle' checked, otherwise, it simply won't use the Screensaver.
[*]Click 'Close'.[/LIST] 
[*]Now, you're finally done integrating Ubuntu Studio into your existing Ubuntu installation.[/LIST]

---

### Post by dmfield on 2007-05-26
doesn't work with AMD64, i know you didn't say it would , just letting you know.

---

### Post by mikemn84 on 2007-06-30
Thanks for that, I couldn't track down where the splash screens were installed to till I ran across this.

Cheers

---

### Post by Nolroz on 2007-07-23
What about the low latency Kernel?  Does that get upgraded as well, or is replacing the Kernal digital brain surgery?

---

### Post by AlexenderReez on 2007-07-23
i have installed few of ubuntu studio meta packages and i think there is no meta package that required to install kernel latency :)

---

### Post by kavani on 2007-07-24
I also have an AMD64, but I installed the 32-bit Feisty on my laptop.  It's working fine!  Thanks!  :guitar:

---

### Post by -Vampyre- on 2007-07-26
I installed all the studio meta packages to my fiesty install. I had no issues. One of the ones you left out includes the lowlatency kernel. I had tried the studio cd and it wouldn't run with the kernel, but upgrading from a regular fiesty worked fine. The only thing i had to go back and get was the restricted manager for the low latency kernel.

---

### Post by PPBoy828 on 2007-08-11
Beautiful!!! Thank You!

I used your method for installation and have had no issues but, I also found this and thought it might be helpful to others who want to install Ubuntustudio alternatively: [How to Install Ubuntu Studio.]("http://news.softpedia.com/news/How-to-Install-Ubuntu-Studio-54514.shtml")

---

### Post by boob11 on 2007-08-13
Thank You!

---

### Post by tomash_cz on 2007-09-06
Hello, thanks for all the guides, i have successfully installed the ubuntu studio theme, but one thing i am missing... I have checked the official screenshots from ubuntustudio and found out that my panel and window borders does not have the nice eyecandy 3D look. can you please advise what shall I do to succeed? I really like the window border and main gnome panel (bottom and top) to be in 3D. not its just 2D black line.. thanks very much for advise or help. ubuntu rocks! (and ubuntu studio is the right punk;)

---

### Post by iheartubuntu on 2007-09-29
Hi all. I was looking through the archives about installing Ubuntu Studio and  since I am still fairly new to Ubuntu, what if I dont like Ubuntu Studio and want to go BACK to regular Ubuntu? Any tips? Thanks :)

---

### Post by LT1Caprice57L on 2007-10-11
OK.  I just installed the icon GTK and Metacity themes on Feisty because that's all I wanted.  They all worked fine.  I upgraded to Gutsy and now the metacity/GTK themes don't work right - panels and title bars lost the glossy appearance and are now simply flat black.  Any ideas?  This was the only theme I've noticed this on - all my other custom installed GTK and Metacity themes still work fine.  What gives?

---

