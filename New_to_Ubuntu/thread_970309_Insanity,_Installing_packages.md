---
title: "Insanity, Installing packages"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by manners2345 on 2008-11-04
One of the things that drives me insane is: I go to let us say "Synaptic Package Manager" To do anything I have to supply my admin password, so I do. I choose a package to install, and install it. Who is the owner?? Root!!! not me!!! It does not show up in the Applications Menu or any where else.
 So I go to places, choose computer, then file system, do a search on the package name, for example it will return 100 items in that package, folders another things. Random sample of properties shows all owned by root, one of the folders has almost 500 items in it.
 
In the example that I am talking about there are 11+ .exe's, Spread out all over the file system in different places.

There is a "USERS GUIDE"  I have downloaded it, but it is so generic, and talks in TWAIN( Tech With An Important Name) 

How do I get it to show up in let us say the system part of the Applications Menu. 

It is an application!!! How do I get it "TO RUN", SO I CAN USE IT!!

NO TWAIN PLEASE!!!


Thank you 
Manners2345

---

### Post by PierreDeKat on 2008-11-04
Okay, Linux is not Windows:

1) Having to enter a password is a significant part of the security function of Linux. This is one of the reasons why you don't need antivirus in Linux: because a virus would have to know your password to install itself. Likewise, your kids, your cat walking on your keyboard, your soon-to-be ex-girlfriend, etc., cannot just totally screw up your operating system, unless they get lucky and key in your password by accident.

2) An .exe file is considered by Linux to be a "DOS/Windows executable" file type. Any .exe files on your computer are only there because whoever put some particular package together included it in the package. Heaven only knows why they would do such a thing, because in Linux, .exe files are not "programs"; they're archives, of sorts. Perhaps the maintainers just needed a peculiar way to archive something.

3) Yes there are literally hundreds of applications and application components that do not show up in your Menus, even though they are installed on your computer. But chances are, if every one of those applications or components were listed in the menus, it would take you hours of searching through the menus to find them. (Of course you can edit your menus and add or remove anything you want by going to Preferences->Main Menu.)

Moreover, if you are interested in a particular application, search google, see if the maintainers have a webpage or site, go there, *read the documentation*, and learn how to use the application in question. Then, if you want and/or need to, create your own launcher in your Menu.

---

### Post by philinux on 2008-11-04
> **manners2345 said:**
> One of the things that drives me insane is: I go to let us say "Synaptic Package Manager" To do anything I have to supply my admin password, so I do. I choose a package to install, and install it. Who is the owner?? Root!!! not me!!! It does not show up in the Applications Menu or any where else.
 So I go to places, choose computer, then file system, do a search on the package name, for example it will return 100 items in that package, folders another things. Random sample of properties shows all owned by root, one of the folders has almost 500 items in it.
 
Thank you 
Manners2345

When your are installing with synaptic click the installed files tab. Then look for the files under /usr/bin or /sbin these are the binaries, equivalent to exe files. If the app does not produce a menu item then you can either run the app from a terminal using its's binary name or create a launcher.

---

