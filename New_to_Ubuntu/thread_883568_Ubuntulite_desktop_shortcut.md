---
title: "Ubuntulite desktop shortcut"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by xsilvergs on 2008-08-08
Hi

I've just started using Ubuntulite on an old Sony laptop, if it goes well I'll probably migrate away from Windows.

I would like to create a Desktop shortcut for .jar program I run. In Windows I would right click and select "Create Shortcut" or drag it to "Start - All Programs".

In Ubuntulite I guess it has to be done from Terminal, is this right and how is it done?

Thanks in advance

---

### Post by iaculallad on 2008-08-08
You can directly create a shortcut or launcher (Ubuntu's term") when in the Desktop. Right-click on your desktop, select "Create Launcher":

i.e:

> Type: Application
Name: Filezilla Browser
Command: filezilla
Comment: Download and upload files via ftp, sftp and ftps (optional)

and click on Close. Your launcher can be available in your Desktop.

---

### Post by xsilvergs on 2008-08-08
I've tried right clicking the Desktop but in my version of Ubuntulite Create Launcher is not available, is it something I have to enable?

I don't have the laptop with me but from memory the options are to swap desktops and,,,,,,, I can't rember the rest, sorry.

---

### Post by rdchin on 2008-08-28
I just tried out Ubuntulite 0.8 rc2 today. I put it on an Intel Pentium II 450 MHz with 512 MB RAM and a 400 MHz Pentium II 756 MB RAM.

As far as icons on the desktop, I have yet to figure out how to change the appearance of the default executable icon.

For example: Installing Firefox and making a shortcut on the desktop.

Install firefox either through Applications | System Tools | Synaptic Package Manager or on the command line by Accessories | LXTerminal and typing at the $ prompt:
$ sudo apt-get install firefox.

Then in the terminal type:
find /usr -name firefox

/usr/share/doc/firefox
/usr/lib/firefox
/usr/lib/firefox-3.0.1/firefox
/usr/bin/firefox

This means that the actual firefox program is located at /usr/bin folder.
To put a shortcut icon on your desktop type:
$ ln -s /usr/bin/firefox ~/Desktop/firefox

Then the icon should be created for this shortcut but I still cannot figure out how to change the appearance of the default icon to the firefox icon.

So far I have Samba file sharing, pyNeighborhood, CUPS printing, K3b, mplayer, Kaffeine all working ok.

I miss the Applications | Places | System menu which is in Ubuntu. Ubuntulite just has the Applications menu. But it's better than KDE's menu which is so confusing to ex-MS Windows users (if KDE had Ubuntu Gnome's menu that would be great) ok enough editorializing.

It did take some playing around to figure out how to have more than 2 desktops, change the wallpaper and theme. Some nice stuff that you can do in gnome such as easily putting icons on the desktop and changing the wallpaper by right-clicking on the desktop I do miss.

Some stuff just makes no sense to me. For instance, to change the desktop wallpaper, you have to open the PCMan file manager | Edit | Preferences | Desktop tab | Wallpaper. Likewise to add more desktops, in the same menu check mark, "Show menus provided by WM when desktop is clicked." Now you can right-click on the desktop to add more desktops. Going through the file manager to change desktop config makes no sense; the windows manager should pre-enable right-clicking on the desktop to do these things.

But in closing a really do appreciate having a windows manager which is closer to Ubuntu Gnome and fast. Puppy is the fastest, Ubuntulite and Fluxbuntu are about the same speed (but I like LXDE more than Fluxbox), then Slackware derivatives Zenwalk, Wolvix on these 400/450 MHz Pentium 2 PCs.

I also like the humongous repsositories of Ubuntu(lite) versus Puppy, Zenwalk, and Wolvix.

---

### Post by doas777 on 2008-08-28
> **xsilvergs said:**
> I've tried right clicking the Desktop but in my version of Ubuntulite Create Launcher is not available, is it something I have to enable?

I don't have the laptop with me but from memory the options are to swap desktops and,,,,,,, I can't rember the rest, sorry.

interesting. I havnt tried ubuntuLite. do you get an option "Edit Menus" when you R-click the Application menu?

if so there should be a button to create a "New Item". Just select the desired program group in the left pane, and then click "New Item".
Name: AppName
Command: java -jar <path to app>
comment: this is an app!

Once you have a launcher, you should be able to drag it anywhere.

if not, there may be a way to enable it, but thats deeper into gnome than I've gotten thus far. you should be able to find something about it online however.

Good luck,
Frank

---

