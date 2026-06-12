---
title: "Program files where are you?"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by mzdutchdoll on 2008-07-02
I am so confused right now by the Ubuntu file system. I recently installed a few programs but for some reason there are no shortcuts whatsoever for them so I have been opening programs through a terminal window. I want to know where the equivalent of the programs folder is on Ubuntu so I can find Ubuntu's equivalent of a .exe to create the shortcuts I need. If anyone can help me that would be great because I feel like a lost puppy searching through everything. :confused:

---

### Post by drs305 on 2008-07-02
They are often in /usr/bin. You can look for where the files for an app are stored by typing "whereis *appname*". You can also open synaptic, click on the package, then Properties and see where the installed files are.

---

### Post by Roinator on 2008-07-02
Where were you expecting shortcuts?  If they don't appear in your applications menu that can easily be edited.  (If you are running Hardy 8.04)
System -> Preferences -> Main Menu

Hope that helped.  I remember having a similar problem not being able to find an app.

---

### Post by nothingspecial on 2008-07-02
Right click on the desktop to create a launcher. Fill in the blanks and you'll have your icon.

---

### Post by mzdutchdoll on 2008-07-02
How do I tell which file is the '.exe' equivalent?

---

### Post by kevmitch on 2008-07-02
Stuff that is system critical will go in /bin (usable by user) and /sbin (usable by root). As stated previously, most applications installed from synaptic will go in /usr/bin, though there's also a /usr/sbin for root only stuff. Finally, if you compile something from source, it will go into /usr/local/bin or /usr/local/sbin. These latter locations are also good places to put scripts you might write yourself. All files in these directories can be thought of as .exe, or in the case of scripts, .bat equivalents. You can tell by the fact that they're green when you do an ls. You should just be able to type their name on the command line or add them to a launcher and have something happen, though it's usually a good idea to run "man <executable name>" to get an idea of what they're going to do first (especially if you have to be root to use them).

Configuration files go in /etc (you can think of it as a more transparent version of the Windows registry). An other handy thing to know about is that every package has a directory in /usr/share/doc that often contains useful information especially if the manpage is lacking.

---

### Post by Lod on 2008-07-02
> **mzdutchdoll said:**
> How do I tell which file is the '.exe' equivalent?If you're used to Windows than the answer will not be easy. Because in Linux there is no need for a specified extension for a file to be executable. The file-permissions are. 
In the shell they often have a different colour.

If you could tell us which program you've installed maybe we can provide with some more specific information for educational purposes :)

And installing new software should best be done by synaptic if possible. Then there should be a shortcut in the menu's for the program.

---

### Post by mzdutchdoll on 2008-07-02
Good news I figured out that what I needed could be copied and pasted from usr/share/applications to the desktop. I was looking for lime and I found it! yay! While I have a thread running does anyone know the command to permanently mount an external usb hardrive. It's mounted but has limited permissions and i need to run a command each time to access it.

---

### Post by hyper_ch on 2008-07-02
if it's a command line program it will (normally) not appear in the menu list....

however you just (a) open a terminal and (b) type the name of it to run e.g.

```

top

```

---

### Post by Lod on 2008-07-02
> **mzdutchdoll said:**
> While I have a thread running does anyone know the command to permanently mount an external usb hardrive.Read this page:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
Skip the partitioning and formatting parts if you don't need them.
Hope it helps.

---

