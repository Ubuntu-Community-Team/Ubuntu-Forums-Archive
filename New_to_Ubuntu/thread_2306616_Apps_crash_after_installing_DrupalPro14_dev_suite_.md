---
title: "Apps crash after installing DrupalPro14 dev suite on fresh Ubuntu 14.04"
date: 2015-12-17
forum: New to Ubuntu
---

### Post by UTAN_dev on 2015-12-17
I'm trying to set up a Drupal development environment inside a Ubuntu 14.04.3 guest on a Win7 host. I'm running the latest VBox (5.0.10 r104061) and have installed ubuntu-14.04.3-desktop-amd64.iso on the VM. Everything seemed fine until I ran the install scripts for DrupalPro14, which removes a bunch of software (e.g. LibreOffice) and installs LAMP, Netbeans, and other software used for Drupal development.


The VM ran fine until after I installed DrupalPro14. Now, apps crash all the time. Here's an example:


[IMG]http://i.imgur.com/WFCWLaL.jpg[/img[/IMG]


Being inexperienced at debugging Ubuntu issues, I don't know the first place to look. I also posted in the DP14 issue queue, but does this sound familiar to any of you? Thanks for your help.

---

### Post by deepakdeshp on 2015-12-17
One way of testing is uninstall Drupal and test again for any crashes,  Also install stable version of Drupal . Does it have any error log file? Please check.

---

### Post by scoutchorton on 2015-12-18
> **UTAN_dev said:**
> inside a Ubuntu 14.04.3 guest

Could be lack of permissions for installing it. Try uninstalling it, and go into terminal and type
```
sudo apt-get install *program name*
```
The 'sudo' part means 'super user do', and if you have permission to do it as super user, well, there shouldn't be problems.
Report back with results! Good luck! :D

---

### Post by UTAN_dev on 2015-12-18
Please let me clarify. "DrupalPro14" is not Drupal; it's a set of shell scripts that transforms a fresh Linux install into a development environment for Drupal devs. It installs a bunch of software (LAMP, Netbeans, drush…) you need to develop in Drupal — and uninstalls a bunch more (Libre Office, games, Shotwell…) that just take up room in a dev environment.

So there's nothing for me to easily revert. It's not as if I was installing Drupal itself and could simply remove it. I can, however, take a VirtualBox snapshot of the VM after installing Ubuntu and installing updates, before running the DP14 scripts.

At this point, I learned from the maintainer of DP14 that he runs it flawlessly on Linux Mint, so I'm going to move my efforts in that direction. Thanks for the replies and enjoy your day!

---

### Post by brian-mccumber on 2015-12-18
Did you install the Virtualbox guest additions as per the install Ubuntu instructions at the DrupalPro14 git page?

> 
[COLOR=#333333][FONT=Helvetica Neue]Note: At this point if you are installing Ubuntu in a VirtualBox machine you may want to install also the VirtualBox guest additions. Instructions at [/FONT][/COLOR][https://www.virtualbox.org/manual/ch04.html](https://www.virtualbox.org/manual/ch04.html)[COLOR=#333333][FONT=Helvetica Neue] (look under "Installing the Linux Guest Additions"). If you are installing in a physical machine ignore this note.[/FONT][/COLOR]


---

### Post by UTAN_dev on 2015-12-18
Yes, I did. Thanks.

---

### Post by brian-mccumber on 2015-12-18
Ok just checking. 

I run Ubuntu 14.04 as my only operating system and I installed a Lamp server on my laptop so I can develop websites using php, wordpress, drupal, opencart ect. The only problem I had was gaining permissions for the web root folder, but since I set permissions for it and the server is offline development only, all I have to do is extract the cms I want to use and place it in the webroot directory and when I navigate to localhost in the browser it just works. 

I have also figured out how easy it is to use Nautilus file manager to connect to webhosts via the file manager so it is really easy to work on sites using native Linux text editing software like Gedit or Geany on the web hosts. This is my preferred way to build websites that include a cms. It saves all the hassle of setting up a dev server, I just install the cms on the host and connect to the host via Nautilus and I can edit any and all files in the cms installation and see the results in real time when the page is refreshed in the browser.

You are dual booting with Ubuntu as the guest, so I don't know if any of these suggestions would help, when I was on Windows I had a Wamp server set up but it was a pain in the ass to configure it and get it running correctly and I used notepad++ and filezilla to work on remote sites via ftp. When I switched to Ubuntu I found that with Ubuntu it was much much easier to set up a Lamp server for local dev and work on remote sites from the file manager than it was to use 4 different programs to do the same things in Windows. Good luck.

---

