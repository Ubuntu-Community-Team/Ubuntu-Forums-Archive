---
title: "How to associate a script or program with an icon?"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by burnsmicro on 2011-12-02
Is there any way to associate a program or script with an icon so as to be able to launch the script or program by clicking on the icon?

Can this be placed on the desktop or the launcher for convenient execution?

Specifically, I want to execute a script to set some environment variables and launch Eclipse. In Windows, I wrote a batch file and attached the Eclipse icon to it and placed this on my desktop. This allowed me to launch Eclipse with one click.

Is this possible on Linux? On Obuntu-11?

---

### Post by cariboo on 2011-12-02
Just right click the script, and select properties, then click the icon in the upper left, and navigate to where the icon you want to use is located, and click it.

---

### Post by lechien73 on 2011-12-02
Yes, it certainly is. Since the ability to right-click and create a launcher (or "shortcut" in Windows-speak) has been disabled in Ubuntu 11.10, you need to install a program first. So open a terminal window and type:

```
sudo apt-get install --no-install-recommends gnome-panel
```

To create a new launcher on the desktop type:

```
gnome-desktop-item-edit ~/Desktop/ --create-new
```

Click on the little springy icon to change it. Give the launcher a name in the "name" field, and supply the path and name of your script in the "command" field.

---

### Post by matt_symes on 2011-12-02
Hi

I think you need to create a .desktop file for it.

Here's an example one.

```
matthew@matthew-Aspire-7540:~$ cat /usr/share/aptdaemon/aptdaemon.desktop
[Desktop Entry]
Name=Aptdaemon Software Management Service
Exec=/usr/sbin/aptd
Icon=softwarecenter
Type=Application
Categories=PackageManager;System;Settings;
MimeType=application/x-deb;application/x-debian-package;
X-Ubuntu-Gettext-Domain=aptdaemon
Hidden=True
matthew@matthew-Aspire-7540:~$ 
```Kind regards

---

### Post by burnsmicro on 2011-12-02
Doh!

Obvious, after your explanation.

Now I have a minor irritant: When I click on the icon on my desktop, a dialog window opens asking if I want to execute or display the item, which in this case is a script which launches Eclipse.

Is there some way of executing this script with only one click to the associated icon?

---

### Post by lechien73 on 2011-12-02
Hi...which solution did you take in the end? I've tested the solution I provided and it has never asked me the "Execute or display" question.

---

### Post by burnsmicro on 2011-12-02
```
gnome-desktop-item-edit ~/Desktop/ --create-new
```Click on the little springy icon to change it. Give the launcher a name in the "name" field, and supply the path and name of your script in the "command" field.[/QUOTE]

This worked really well and it does not ask me whether to execute or display. It starts execution immediately.

If I had any say, I would like to see this accessible through an icon/launcher in the System Settings. Then I would not have to memorize the command.

Thanks,

RF

---

### Post by lechien73 on 2011-12-03
Great - if you get chance, could you please mark the thread as [SOLVED] using the **Thread Tools** menu at the top?

Thanks & enjoy :)

---

### Post by matt_symes on 2011-12-03
Hi

@lichien73 Are you sure you need to install gnome panel to create a .desktop file using gnome-desktop-item-edit ?

The reason i ask is because i do not need to and i am wondering why you added that step. My install is an upgrade to 12.04 from Natty.

Kind regards

---

### Post by burnsmicro on 2011-12-03
gnome-desktop-item-edit ~/Desktop/ --create-new

This worked great...

BUT...

I am becoming addicted to U-11.10's Dash and the newly created launcher does not show up in the Dash.

For     instance, to open LibreOffice Writer, Meta+w brings up a number of     programs, starting with LibreOffice Writer.

But Meta + TSe does not bring up my TSeclipse launcher.

Is there any way of "registering" a launcher with the Dash?

Thanks,

RF

---

### Post by Jacobonbuntu on 2011-12-03
> **burnsmicro said:**
> gnome-desktop-item-edit ~/Desktop/ --create-new

This worked great...

BUT...

I am becoming addicted to U-11.10's Dash and the newly created launcher does not show up in the Dash.

For     instance, to open LibreOffice Writer, Meta+w brings up a number of     programs, starting with LibreOffice Writer.

But Meta + TSe does not bring up my TSeclipse launcher.

Is there any way of "registering" a launcher with the Dash?

Thanks,

RF

If I understand correctly what you mean, try alacarte (it is already installed)
choose "new" and "properties" to make a new entry for Dash

---

### Post by lechien73 on 2011-12-03
> **matt_symes said:**
> Hi

@lichien73 Are you sure you need to install gnome panel to create a .desktop file using gnome-desktop-item-edit ?

The reason i ask is because i do not need to and i am wondering why you added that step. My install is an upgrade to 12.04 from Natty.



Hi Matt,

I added it so that it could be created through a GUI interface. You can, of course, create a .desktop file using whatever flavour of text editor you prefer, but since the question was posted here in "Absolute Beginner Talk", I thought that the GUI method was better :)

---

### Post by matt_symes on 2011-12-03
Hi

> Is there any way of "registering" a launcher with the Dash?

If you want the launcher to appear in the dash when you search, move the launcher to

```
/usr/share/applications
```

and it will appear in the dash when you type.

> For     instance, to open LibreOffice Writer, Meta+w brings up a number of     programs, starting with LibreOffice Writer.

But Meta + TSe does not bring up my TSeclipse launcher.

Not quite sure what you mean here.

Kind regards

---

### Post by matt_symes on 2011-12-03
Hi

> **lechien73 said:**
> Hi Matt,

I added it so that it could be created through a GUI interface. You can, of course, create a .desktop file using whatever flavour of text editor you prefer, but since the question was posted here in "Absolute Beginner Talk", I thought that the GUI method was better :)

No worries lechien. That is a good idea to use the GUI.

I can use gnome-desktop-item-edit without gnome panel being installed and i was wondering if it a legacy of the upgrade path i have used, that's all (Natty->Oneiric->Precise). My install does some strange things at times because of it you see :D

Kind regards

---

### Post by lechien73 on 2011-12-03
> **matt_symes said:**
> Hi
I can use gnome-desktop-item-edit without gnome panel being installed and i was wondering if it a legacy of the upgrade path i have used, that's all (Natty->Oneiric->Precise). My install does some strange things at times because of it you see :D


Ah yes...quite probably. It was the same for me...you only have to install the gnome panel if it's a vanilla 11.10 install :)

Haven't taken a look at *Precise* yet, but you've piqued my curiosity now!

---

