---
title: "Ubuntu on WSL2 for Drupal website development"
date: 2020-06-07
forum: New to Ubuntu
---

### Post by manarak on 2020-06-07
Hello all, this is my first post here.

I am interested in installing ubuntu on Windows WSL2 to use it for Drupal website development and website maintenance.

Currently I am using WAMPserver on Windows, I'm very happy with it, but Drupal requires Drush and Composer for website maintenance and updates, all the literature is written for linux.

So I am looking into using WSL2 with ubuntu - and I am looking for a tool similar to WAMPserver for ubuntu.

What I particularly appreciate in WAMPserver is that everything comes pre-installed and pre-configured, and the program takes care of creating new vhosts, etc. as needed, no need to do anything in the Windows hosts file, etc. It just works directly out of the box. Also, changing PHP or MySQL versions takes just a mouseclick, for example I can click database->mysql5 and then PHP version->5.56, services-> restart and it's done. Or activating and deactivating Apache modules, setting PHP parameters, etc.
I was using XAMPP for Windows before and ditched it for WAMPserver because XAMPP for Windows was too unflexible.

So what tool would you recommend I use on ubuntu ?

---

### Post by SeijiSensei on 2020-06-07
I suggest running [VirtualBox]("https://www.virtualbox.org/") in Windows ([download]("https://download.virtualbox.org/virtualbox/6.1.10/VirtualBox-6.1.10-138449-Win.exe")) and installing an ordinary Ubuntu distribution rather than futz with WSL. 

Make sure to install the [Extension Pack]("https://download.virtualbox.org/virtualbox/6.1.10/Oracle_VM_VirtualBox_Extension_Pack-6.1.10.vbox-extpack") after creating the Ubuntu VM. Double-clicking the downloaded Pack will install it.

I often use the "Seamless" display mode to have both OSs display their application windows on the common screen.  I run Windows VMs on Linux, and configure my Windows desktop to have the panel at the top of the screen and hide itself automatically. To run a Windows app, I just move the mouse to the top of the screen so the panel appears. You can set up Ubuntu to do the same.  Or you can use multiple monitors.

One other advantage of using virtual machines is you can try out different flavors of Ubuntu ([download]("http://cdimage.ubuntu.com/focal/daily-live/current/")) and different distributions of Linux. I've used the [K Desktop Environment]("https://kde.org/") for years so I install [Kubuntu]("http://cdimage.ubuntu.com/kubuntu/focal/daily-live/current/"). Other people prefer more "light-weight" flavors like Lubuntu ([download]("http://cdimage.ubuntu.com/lubuntu/focal/daily-live/current/")), using the [LX Desktop Environment]("https://wiki.lxde.org/en/Main_Page"), or Xubuntu ([download]("http://cdimage.ubuntu.com/xubuntu/focal/daily-live/current/")) which uses yet-another desktop, [XFCE]("https://www.xfce.org/").

Ubuntu has a package called "lamp-server" that will install Apache, PHP, and MySQL together plus any interstitial connectors they require like the "php-mysql" package.  After you've installed Ubuntu, open a Terminal window and type the command:
```
sudo apt install lamp-server^
```
The tilde ("^") is required. Preceding the command with "sudo" means it runs with administrative privileges so you'll be prompted for your password. (You get admin privileges for 15 minutes by default, then you'll be asked your password again.)  The command apt runs the basic program that manages software installation from the Ubuntu "repositories" where all the freely-available software resides.

There's no graphical app I know of that will manage the tasks you describe. [Webmin]("http://www.webmin.com/") might be a possibility. I haven't used it in years because I prefer the command line, and I don't like the idea of installing a web application with admin privileges across my server.  That security issue is less critical while you're experimenting with running Linux in a virtual machine. If you decide to try webmin, use the "[Debian package]("https://prdownloads.sourceforge.net/webadmin/webmin_1.941_all.deb")" listed in the menu.

Changing PHP versions won't be as easy as you describe either. The current Ubuntu release with long-term support, 20.04 or "Focal Fossa," includes PHP 7.4.  I could probably code a method to have a second instance of Apache that runs 5.6 listening on a separate port.  But clicking a button to change versions?  Don't know of anything like that.

Activating or deactivating Apache modules can be done from the command line with the a2enmod and a2dismod commands. You'll always need to restart Apache after any such change with the command
```
sudo systemctl restart apache2
```

You don't need to use the "server version" of Ubuntu to run any of this.  You can just install the needed packages onto any desktop distribution. Besides, the server version has no GUI.

---

### Post by keenbuliag12 on 2020-06-21
Wow, I'm curious about web development and Ubuntu. :) [https://keenbuliag2020.wixsite.com/davaohenyo](https://keenbuliag2020.wixsite.com/davaohenyo)

---

### Post by mastablasta on 2020-06-22
or you can just download Drupal virtual machine from bitnami stack, load it up in virtualbox, select user name and password and you are good to go (you can start developing):  [https://bitnami.com/stack/drupal](https://bitnami.com/stack/drupal)

---

### Post by TheFu on 2020-06-24
WSL and WSL2 are slow compared to straight Ubuntu: [https://www.phoronix.com/scan.php?page=article&item=wsl-wsl2-tr3970x&num=8](https://www.phoronix.com/scan.php?page=article&item=wsl-wsl2-tr3970x&num=8)

Beware.  WSL2 is faster than WSL almost always, however.

it is always best to develop on the platform for which production will be deployed.

---

