---
title: "Adding some enhancements to Ubuntu"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Canis familiaris on 2008-05-17
Hi there
I want to enhance my Ubuntu in the following ways. Can you help?

(1) Whenever I want to launch a folder with root permission I have to:
```
sudo nautilus
```
Is there any way that I add an option to the context menu and open the folder as root?

(2) To add a context menu option to open a folder in terminal?

(3) Is there any way that I could Double-Click an ISO and mount it and then unmount it with a context menu option?

(4) Is there a GUI where I can define the mount points,etc. I know I can use fstab, it's good. But I would like also a GUI?

(5) Is there an applet which can connect with my IMAP server and notify me if new mails arrived without opening Evolution or Thunderbird?

(6) Is there a way that I could have a CPU temp., CPU fan monitoring applet in my desktop. I do not use compiz.

Thank you in advance.

---

### Post by muximus on 2008-05-17
(3) u can mount the iso using:
properties > open with > Add > custom command

specify the custom command as : mount -o loop -t iso9660 %M /media/iso

and then define this as the default action.

of course, u would hv to create the /media/iso folder, and you wont be able to mount more than 1 iso at one time, but there are no other limitations to it. 


(6)&(5) Try screenlets, there are loads of screenlets for the functions you are looking for. i think it works without compiz.

---

### Post by Kevbert on 2008-05-17
Screenlets can be found at [http://screenlets.org/index.php/Download]("http://screenlets.org/index.php/Download")
This is the basic screenlet manager.  Additional screenlets and other Desktop enhancements can be found at: [http://gnome-look.org/]("http://gnome-look.org/")
For most of these items Compiz is not required.

---

### Post by Apple Ink on 2008-05-17
Right click on ur menubar (where the system date is displayed)
Click Add
Firstly search for system monitor and add it!

Secondly, click on add applet launcher (2nd option from the list)

Name it as SuDo Nautilus and in the command line enter "gksudo nautilus"
Click Add!!!

This is just an example, u can add tons of more command lines in both the menubar and the desktop in similar fashion!

---

### Post by Canis familiaris on 2008-05-17
> **Apple Ink said:**
> Right click on ur menubar (where the system date is displayed)
Click Add
Firstly search for system monitor and add it!

Secondly, click on add applet launcher (2nd option from the list)

Name it as SuDo Nautilus and in the command line enter "gksudo nautilus"
Click Add!!!

This is just an example, u can add tons of more command lines in both the menubar and the desktop in similar fashion!

This is good but I would prefer if I could right click a folder and open it as Root.

---

### Post by oldos2er on 2008-05-17
> **Anurag_panda said:**
> This is good but I would prefer if I could right click a folder and open it as Root.

 Install the package nautilus-gksu, and you can.

---

### Post by legatek on 2008-05-17
Download the nautilus scripts at Gnomefiles:

[http://gnomefiles.org/app.php/NScripts](http://gnomefiles.org/app.php/NScripts)

Rootilus is what you're after.

---

### Post by Canis familiaris on 2008-05-18
> **legatek said:**
> Download the nautilus scripts at Gnomefiles:

[http://gnomefiles.org/app.php/NScripts](http://gnomefiles.org/app.php/NScripts)

Rootilus is what you're after.

Worked pretty well:KS

---

### Post by Canis familiaris on 2008-05-18
I would love to know alternate ways as well.

---

### Post by tom56 on 2008-05-18
If you want to monitor temperatures then install sensors-applet, then add it by right-clicking the panel, clicking "Add to panel" and adding "Hardware Sensors Applet".

---

### Post by autocrosser on 2008-05-18
For a GUI-way to edit fstab:

Open Synaptic & search for: PySDM  

Graphical Storage Device Manager
PySDM is a PyGTK Storage Device Manager that allows full customization of hard
disk mountpoints whitout manually access to fstab.
It also allows the creation of udev rules for dynamic configuration of storage
devices

You should have all you repositories open (universe & mulitverse)

---

### Post by Canis familiaris on 2008-05-18
Any way Can I monitor CPU Fan speed?

---

### Post by Canis familiaris on 2008-05-18
> **autocrosser said:**
> For a GUI-way to edit fstab:

Open Synaptic & search for: PySDM  

Graphical Storage Device Manager
PySDM is a PyGTK Storage Device Manager that allows full customization of hard
disk mountpoints whitout manually access to fstab.
It also allows the creation of udev rules for dynamic configuration of storage
devices

You should have all you repositories open (universe & mulitverse)

Will try it

---

### Post by autocrosser on 2008-05-18
I use a "old school" app--GKrellm. It sits to the side of your monitor with several "krells" open--there are a fair amount of add-ons for it & if you Google-search for GKrellm, you will find the theme archive & usefull information.....I've used it for going on 8 years now & have over 100 themes I've found & made.

Installs thru Synaptic.

---

### Post by the8thstar on 2008-05-18
There is also Ubuntu Tweak which allows you to fine-tune a lot of details and preferences: [http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/") 

The little + is that it's all GUI based.

---

