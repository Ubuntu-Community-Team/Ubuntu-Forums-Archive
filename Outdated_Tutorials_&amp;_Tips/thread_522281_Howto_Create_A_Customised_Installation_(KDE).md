---
title: "Howto: Create A Customised Installation (KDE)"
date: 2007-08-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Vince4Amy on 2007-08-10
Sometimes people, including myself have no use for half of the applications that come with Kubuntu. So here's how to perform an installation with only your preferred applications.

Firstly I used a DVD Disc of Ubuntu. But you can download the Alternative Disc Image.

Once you have loaded the DVD or Alternative Image select install a command line system. 

Go through the various steps to install the Command Line System. Once You've booted your new Command Line system you'll have a few things to do in able to get KDE running.

Once you're at the command line type:

```
sudo apt-get install x-window-system
```

This will allow anything to display, you cannot use a Window manager until you have this. You may have to tell it what screen resolutions you can use. Normally it's automatic.

```
sudo apt-get install kde-core
```

This will allow you to have the KDE Window manager & it will also add the required packages to make KDE work.

Next you'll have to install the login manager .

```
sudo apt-get install kdm
```

This is the Login manager you'll need this. 

```
sudo reboot
```

This will reboot your machine. You now have a KDE system with virtually nothing extra than needed installed. You can now customise your installation.

---

