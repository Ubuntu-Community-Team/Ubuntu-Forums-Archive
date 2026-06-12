---
title: "May help to Basic things for Beginners???"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by nachinew on 2012-09-03
Hi Experts and Intermediates of Linux Users,


I am a Beginners, So i have some basic questions with this forum so this may help for upcoming beginners, My question are simple to all and to me so please share your different approaches how to handle it.
I am using latest version of Ubuntu desktop

1. How to install new fonts to our system?
2. How to mount and demount the external device? (if i want to remount again after safely remove)
3. Make a shortcut to desktop (Workspace)?
4. Use of Workspace and how can we use workspace efficiently?
5. Browse the installed application?
6. Apart from Ubuntu software center, other way or other format to install programs new programs.
7. Terminal basic uses and how we can use efficiently.
8. Format the external device through GUI and Terminals?
9. Minimize all window at once time like in windows is this possible in Ubuntu?
Some other basic questions will added after involving Linux.

Thanks.
Nachi:guitar:

---

### Post by Frogs Hair on 2012-09-03
Hello nachinew

Much of what you ask can be found by searching the forum or with your
favorite search engine.

7. Command line learning resources sticky on the top this forum.
 
4.[http://www.webupd8.org/2012/07/download-getting-started-with-ubuntu-pdf.html](http://www.webupd8.org/2012/07/download-getting-started-with-ubuntu-pdf.html)

1. download, extract the package, and select install or double click. MS core fonts are in the software center.

5. synaptic package manager or view installed packages from the software center which only displays official packages. Commands can also be used.   

6.Unbutu uses Debian or .deb packages and I use Opera and Chrome which are .debs downloaded from the websites. You can compile/build packages also if you comfortable with learning how. Items in the software center have been screened for malicious code and the package dependencies are available. Packages from other sources  may not included all the dependencies this is why compiling is sometimes required.

---

### Post by grahammechanical on 2012-09-03
It helps if you tell us which version of Ubuntu that you are using as the directions we give might be different. We are assuming that you are using Ubuntu Precise Pangolin, also called 12.04.

Have you read the Ubuntu Desktop Guide? You can find it by opening the Dash (tap the super/windows key) and typing help.

If you have Truetype font (ttf) that you wants to use in Ubuntu 12.04 simply copy the font file into any folder of your choice. Use the File Manager (Nautilus) to browse to that folder. Right click the font file and selct Open with Font Viewer and thne click the button that says Install Font and that font will be available for use in applications like Libreoffice in the same way as any other font.

Regards.

---

### Post by newb85 on 2012-09-03
> **nachinew said:**
> 
2. How to mount and demount the external device? (if i want to remount again after safely remove)


External devices should mount automatically.  They will show up in the launcher.  You can unmount them by right-clicking them in the launcher and clicking "unmount".  The easiest way to then remount them is to unplug them and plug them back in, thereby triggering another automatic mount.

> **nachinew said:**
> 
4. Use of Workspace and how can we use workspace efficiently?

That's going to depend on what you use your computer for and the way you organize your thoughts.  Just experiment and see what works for you.

> **nachinew said:**
> 
5. Browse the installed application?


In the software center, there's an option to view just the installed applications.  Note: By default, the Software Center hides what it calls "technical applications".  You can click at the bottom of the list to show them.


> **nachinew said:**
> 
6. Apart from Ubuntu software center, other way or other format to install programs new programs.


You can bypass the GUI and install from the CLI.  For example, to install Xiphos,

```
sudo apt-get install xiphos
```


> **nachinew said:**
> 
9. Minimize all window at once time like in windows is this possible in Ubuntu?


There are keyboard shortcuts built into the Unity DE for interactions like this.  Hold down the Windows button on your keyboard to view a list of them.

---

### Post by gavv on 2012-09-03
> **nachinew said:**
> Hi Experts and Intermediates of Linux Users,
3. Make a shortcut to desktop (Workspace)?


Hey nachinew, I can help you with this, although I am a beginner myself. I recently learned how to do this in Ubuntu 12.04 LTS,  but here it goes (*to make a short-cut on the desktop*): 

First you need to install gnome-panel if you haven't already.

Open up a terminal and type, or copy and paste
```
sudo apt-get install --no-install-recommends gnome-panel
```Type in your password, and go through the install. Once you have gnome-panel, you can start creating desktop short-cuts by inserting the following into the terminal:
```
gnome-desktop-item-edit ~/Desktop --create-new
```*~/Desktop* specifies the location, in your home directory inside the Desktop directory

From there, a graphics window should pop up asking for information to create the short-cut. You can change the icon, name it, comment it, and, most importantly, insert a command. The command should point to the application. Click browse, find the location of the application, click ok, and voila!

Edit: This may or may not have been what the OP needed help with...

---

### Post by newb85 on 2012-09-03
There are keyboard shortcuts for switching workspaces.  No desktop shortcut required.

---

### Post by nachinew on 2012-09-03
> **Frogs Hair said:**
> Hello nachinew
5. synaptic package manager or view installed packages from the software center which only displays official packages. Commands can also be used.   

6.Unbutu uses Debian or .deb packages and I use Opera and Chrome which are .debs downloaded from the websites. You can compile/build packages also if you comfortable with learning how. Items in the software center have been screened for malicious code and the package dependencies are available. Packages from other sources  may not included all the dependencies this is why compiling is sometimes required.

5...I can`t understand the line **Commands can also be used.**
6... Is software center have been screened for malicious code?

Please make me the clear picture....:P

---

### Post by nachinew on 2012-09-03
> **grahammechanical said:**
> It helps if you tell us which version of Ubuntu that you are using as the directions we give might be different. We are assuming that you are using Ubuntu Precise Pangolin, also called 12.04.

Have you read the Ubuntu Desktop Guide? You can find it by opening the Dash (tap the super/windows key) and typing help.

If you have Truetype font (ttf) that you wants to use in Ubuntu 12.04 simply copy the font file into any folder of your choice. Use the File Manager (Nautilus) to browse to that folder. Right click the font file and selct Open with Font Viewer and thne click the button that says Install Font and that font will be available for use in applications like Libreoffice in the same way as any other font.

Regards.

I am using 12.04 LTS version.:smile:
No I am not started the Desktop Guide fully.

---

### Post by nachinew on 2012-09-03
> **newb85 said:**
> External devices should mount automatically.  They will show up in the launcher.  You can unmount them by right-clicking them in the launcher and clicking "unmount".  The easiest way to then remount them is to unplug them and plug them back in, thereby triggering another automatic mount.

**Without unplug can any other option to remount the external device?**

> **newb85 said:**
> 
That's going to depend on what you use your computer for and the way you organize your thoughts.  Just experiment and see what works for you.

In the software center, there's an option to view just the installed applications.  Note: By default, the Software Center hides what it calls "technical applications".  You can click at the bottom of the list to show them.


**Interesting**

> **newb85 said:**
> 
You can bypass the GUI and install from the CLI.  For example, to install Xiphos,

```
sudo apt-get install xiphos
```
 

> **newb85 said:**
> There are keyboard shortcuts built into the Unity DE for interactions like this.  Hold down the Windows button on your keyboard to view a list of them.



**I will try and get back to you keyboard shortcuts**

:guitar:

---

### Post by nachinew on 2012-09-03
> **gavv said:**
> Hey nachinew, I can help you with this, although I am a beginner myself. I recently learned how to do this in Ubuntu 12.04 LTS,  but here it goes (*to make a short-cut on the desktop*): 

First you need to install gnome-panel if you haven't already.

Open up a terminal and type, or copy and paste
```
sudo apt-get install --no-install-recommends gnome-panel
```Type in your password, and go through the install. Once you have gnome-panel, you can start creating desktop short-cuts by inserting the following into the terminal:
```
gnome-desktop-item-edit ~/Desktop --create-new
```*~/Desktop* specifies the location, in your home directory inside the Desktop directory

From there, a graphics window should pop up asking for information to create the short-cut. You can change the icon, name it, comment it, and, most importantly, insert a command. The command should point to the application. Click browse, find the location of the application, click ok, and voila!

Edit: This may or may not have been what the OP needed help with...


While using the first command i getting command not found.
Why this happens ?:guitar:

---

### Post by roger_1960 on 2012-09-03
Hi

To show the desktop, hold down the alt key and press TAB repeatedly until you get to "show desktop" and release.  Do it again to get back where you were or to any other running app.

---

### Post by gavv on 2012-09-03
> **nachinew said:**
> While using the first command i getting command not found.
Why this happens ?

Sometimes that happens if you mistype something in the terminal. 

Try copying and pasting the code into the terminal.

"sudo apt-get install --no-install-recommends gnome-panel" (without the quotes)

---

### Post by nachinew on 2012-09-03
> **gavv said:**
> Sometimes that happens if you mistype something in the terminal. 

Try copying and pasting the code into the terminal.

"sudo apt-get install --no-install-recommends gnome-panel" (without the quotes)

OK I will try
To copy and paste the commands to terminals the same CTRL + C and CTRL + V is used?

---

### Post by jerome1232 on 2012-09-03
To remount a device after safely removing a device, simply open nautilus and click on it's icon in the upper portion of the left-hand pane.

Also terminal is ctrl+shift+c and ctrl+shift+v to copy and paste. You can also simply highlight text, and click the middle mouse button to paste the highlighted text.

---

### Post by nachinew on 2012-09-03
> **jerome1232 said:**
> To remount a device after safely removing a device, simply open nautilus and click on it's icon in the upper portion of the left-hand pane.
 
Also terminal is ctrl+shift+c and ctrl+shift+v to copy and paste. You can also simply highlight text, and click the middle mouse button to paste the highlighted text.
 
 
I will try and get back to you. nautilus is defaultly available or i need to install from Software center.

---

### Post by jerome1232 on 2012-09-03
> **nachinew said:**
> I will try and get back to you. nautilus is defaultly available or i need to install from Software center.
[INDENT] nautilus is the default file browser for Ubuntu, you open it by clicking the orange folder icon on your launcher on the lefthand side of your screen.
[/INDENT]

---

### Post by newb85 on 2012-09-04
> **roger_1960 said:**
> Hi

To show the desktop, hold down the alt key and press TAB repeatedly until you get to "show desktop" and release.  Do it again to get back where you were or to any other running app.

Quicker: (from the list I mentioned earlier) Ctrl+Super+D 
Your Super key probably bears the insignia of a not-so-super OS.

---

