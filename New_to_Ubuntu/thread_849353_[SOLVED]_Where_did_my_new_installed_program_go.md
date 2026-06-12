---
title: "[SOLVED] Where did my new installed program go?"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by arepaking on 2008-07-04
Hello,I downloaded skype. I right-clicked on the file to install it but after the installation finished I'm not able to see where my new program went. 

How can I added to my application list? How could I add a shortcut in my desktop?

Thanks,
AK

---

### Post by spiderbatdad on 2008-07-04
Look under System>>Preferences>>Main Menu

---

### Post by ChameleonDave on 2008-07-04
> **arepaking said:**
> Hello,I downloaded skype. I right-clicked on the file to install it but after the installation finished I'm not able to see where my new program went. 

How can I added to my application list? How could I add a shortcut in my desktop?

Thanks,
AK

What did you download?  A .deb file?

The best way to install Skype is to enable the Medibuntu repositories and then install it via Synaptic.

Once it is installed, it ought to appear in your program menus.  If it doesn't, you can always run it from a terminal.

---

### Post by arepaking on 2008-07-04
> **spiderbatdad said:**
> Look under System>>Preferences>>Main Menu

Hi.. Unfortunately, the skype program is not there.

---

### Post by arepaking on 2008-07-04
> **ChameleonDave said:**
> What did you download?  A .deb file?

The best way to install Skype is to enable the Medibuntu repositories and then install it via Synaptic.

Once it is installed, it ought to appear in your program menus.  If it doesn't, you can always run it from a terminal.

Hi,
Thanks for helping me out.

I downloaded a .deb file. When I right-clicked on it I got the option to install it via "GDebi Package Installer". After that the process seemed to be successful but I don't find the application anywhere.

I was able to run it using the terminal and typing "skype" but I don't want to do this every time. In fact, when I close the terminal the Skype app shuts down as well.

Thanks again,
-AK

---

### Post by alsamman on 2008-07-04
go to system>pref>main menu, go to one of the menus (ie. Internet) and then click New Item then for Name: Skype Command: skype and you can choose an icon
Once thats done, click Ok and it should show up in the menu that you put it in

---

### Post by ChameleonDave on 2008-07-04
> **arepaking said:**
> Hi,
Thanks for helping me out.

I downloaded a .deb file. When I right-clicked on it I got the option to install it via "GDebi Package Installer". After that the process seemed to be successful but I don't find the application anywhere.
-AK
If you want software such as Skype, you should probably enable the Medibuntu repos.

Open up your list of repos by typing this on the command line:

```

sudo *nano* /etc/apt/sources.list

```

You may replace *nano* with your favourite text editor.

Add the following line to the file.

```

deb http://packages.medibuntu.org/ *hardy* free non-free

```

Replace *hardy* with *gutsy* if you aren't using the latest Ubuntu.

You will then get extra software available for installation in Synaptic.  When later versions of Skype come out, you will be able to upgrade to them without checking the Skype website and downloading stuff manually.

---

