---
title: "HOWTO: Install MintMenu without Dependencies from LinuxMint"
date: 2009-04-21
forum: Outdated Tutorials &amp; Tips
---

### Post by har02052 on 2009-04-21
So I did it myself. After some searching I found someone else that had created a deb with version 3.0 but there was some lost functionality to it. After much more searching, I found someone that had installed it on PCLinuxOS. They kind of showed the steps how they did it with modifications for PCLinux. So I took those and backwards enginered some of it to work with Ubuntu. Now I have a working MintMenu with no dependencies and it hasn’t altered my system to think that I am running linux mint. There is no deb file (I don't know how to make one) and I am sure there could be mistakes in what I did because I really don't know how to code. But it works for me. This is what I did, at the bottom of the post is a tar file that you won't have to go through all of the steps, you just have to copy the contents of the tar file in the /usr folder into your /usr folder and that's it. But here are the steps anyway.
Here is what you do:

Download the source for the menu from here:
[http://packages.linuxmint.com/pool/main/m/mintmenu/](http://packages.linuxmint.com/pool/main/m/mintmenu/)

If you want the right-click uninstall to work, download the MintSystem source from here:
[http://packages.linuxmint.com/pool/main/m/mintsystem/](http://packages.linuxmint.com/pool/main/m/mintsystem/)

unpack both of them somewhere like your desktop.
Copy all the files and folders within:
(unpacked mintsystem folder here)/usr/lib/linuxmint/

And paste them into
(unpacked mintmenu folder here)/usr/lib/linuxmint/

Now, copy all of the files and folders within:
(unpacked minmenu folder here)/usr/

And sudo or root paste them into your /usr/ folder.

On one of the gnome menu bars right-click and select add applet to this panel. Scroll down and there will be MintMenu. Go ahead and add it.

Next, in the System menu there is a LinuxMint icon that says Software Manger (or it might say MintInstall) but it doesn’t work because you didn't also install mintinstall, you have to change that to whatever you want. I changed it to the update manager. You do that by manually editing the file to point to something else.
So:
sudo gedit /usr/lib/linuxmint/mintmenu/plugins/system_management.py

Scroll down to line 100. There you will see:

Button1 = easyButton( "/usr/lib/linuxmint/mintSystem/icon.png", self.iconsize, [_("Software manager")], -1, -1 )

Button1.connect( "clicked", self.ButtonClicked, "/usr/lib/linuxmint/mintInstall/frontend.py" )

Button1.show()

self.systemBtnHolder.pack_start( Button1, False, False )
s
elf.mintMenuWin.setTooltip( Button1, _("Browse and install available software") )

As you can see, it points to mintinstall. You can now change it to whatever you want. I changed it to the system update manager by editing it to this:

Button1 = easyButton( "update-manager", self.iconsize, [_("Software Update")], -1,-1
Button1.connect( "clicked", self.ButtonClicked, "update-manager" )

Button1.show()

self.systemBtnHolder.pack_start( Button1, False, False )

self.mintMenuWin.setTooltip( Button1, _("Update Your Software") )


You could change it to whatever you want, that is just what I did.
Last of all you can change the icon for both the menu button and then the “All” in the applications list. The main menu icon is easy to change, just right-click on it and click preferences and on the main button tab, you can change the icon and the title.

The All aplications icon is a little harder, but simple enough. The icon is found within:
/usr/lib/linuxmint/mintsystem

sudo replace that icon with an icon of your liking, making sure that the one you put in there has the same name as the one that you replaced.

That's it. You now have a working MintMenu without all of the other stuff that would go with it if you had installed it from the mint repos. I will try to upload a modified tar file with the mintsystem folder, modified system_management file, and changed icons so that all you would have to do is copy and paste them into your /usr folder to make it work. If anybody else wants to run with this and make it a deb or a self installing script, go ahead, I don't know how.

---

### Post by Chainy on 2010-03-09
Thank you for the instructions. I wonder if there is now an easier way to do this? I seem to remember hearing that Linux Mint was working on making their stuff available without all the branding. Does anyone know whether it is now easier to install the Mintmenu into Ubuntu? Does it create any problems with performance or anything? You know, any unexpected bugs due to it not being designed for working within the Ubuntu system...?

---

### Post by markosjal on 2010-07-03
Yes there is an easier way!

[http://www.webupd8.org/2010/05/install-linux-mint-main-menu-mintmenu.html](http://www.webupd8.org/2010/05/install-linux-mint-main-menu-mintmenu.html)

I just installed this even on Ubuntu 10.04 PPC and it works. I like this better than some of the solutions i see for "Mint on PPC"

---

