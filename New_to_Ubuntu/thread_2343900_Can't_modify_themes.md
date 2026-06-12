---
title: "Can't modify themes"
date: 2016-11-20
forum: New to Ubuntu
---

### Post by jerboa2 on 2016-11-20
I've just installed Ubuntu Studio 16.04 LTS. I've been using various KDE distros. Things are ok so far except there is no GUI for controlling the various theme parameters. I'm not able to edit the "gtkrc" file directly because I can't open it as root. My old file managers have had a context menu allowing to do root actions. So am I going to have learn an extensive library of command line tools for working with this OS? Specifically, the Window borders aren't wide enough to grab with my touchpad or mouse so moving the windows around is impossible unless you can accept the default size. I really like total control over everything and I can't find the GUI tools to do that.

Thanks,

JB

---

### Post by jerboa2 on 2016-11-20
I'm so frustrated. I have a similar post. It's all relating to lack of access to GUI settings for changing window settings and lack of root access to the files that have the settings. In all of the other Linux distros I've used there have been either configuration editors or much easier access to root privileges.  Anyway, I tried using information listed here to edit the file:  "usr/share/themes/Greybird/gtk-2.0/gtkrc" , which is the default theme for Ubuntu Studio. I got the file opened in nano and edited the sections but it wouldn't let me save the file.  I've just about had enough. I like a lot of things about this OS but I never had this much trouble getting things to work. I want to be able to recommend Linux to friends but Ubuntu is not looking like something I can help them with. I used Mint for years and Debian for main system with KDE. I guess I didn't realize Ubuntu would be so different.

My specific problem is the window borders are to narrow to drag. I can't catch them with my mouse or touchpad.

JB

---

### Post by Dennis N on 2016-11-20
> I got the file opened in nano and edited the sections but it wouldn't let me save the file. I've just about had enough.

If you can't save your edited file, it's probably because the file you want to edit requires sudo to open it for editing with saving. Without sudo, you can only open it.

**sudo nano usr/share/themes/Greybird/gtk-2.0/gtkrc**

Then to save (write out), the keys are at the bottom: ^O means Control+O key combination. then ^X to exit.

---

### Post by TheFu on 2016-11-20
It is unlikely that 'usr/share/themes/Greybird/gtk-2.0/gtkrc' is the correct location.  You are probably missing the initial '/'.  When you are the system admin, it is expected that an understanding of absolute and relative paths has been mastered.  

Try 
```
 sudoedit  /usr/share/themes/Greybird/gtk-2.0/gtkrc 
```
Whatever editor you like can be used, provided the EDITOR environment variable has been set as I explained above.

There is nothing odd or funny about this. This is a very standard Unix method to modify config files used by the OS for 40+ years.

---

### Post by CantankRus on 2016-11-20
Ubuntu Studio uses Xfce with thunar as the file manager I believe.
Use [**[COLOR="#B22222"]THIS[/COLOR]**]("http://docs.xfce.org/xfce/thunar/custom-actions#opening_a_root_thunar") page to set up a custom action.

In Xfce you can use:
alt+leftmouse to move a window
alt+rightmouse to resize a window

---

### Post by jerboa2 on 2016-11-21
Thanks,  
I've been digging and finally found two posters with the exact same complaint. Both decided that the keyboard shortcuts were the best solution. I found the solution acceptable but I have some extenuating circumstances. Without rambling--I have disabilities that make typing extremely difficult. Additionally,  my purpose for trying Linux is to eliminate Microsoft from the planet. I've been working with MS since my XT-286 IBM running DOS. I stopped upgrading at Win7.  Everyone I know has been begging me to come out of retirement to help them with their Win10 systems. I won't install Win10 on any of my machines (I did try it!). So I try to convert Windows users to Linux. I have to try things before I can recommend them. Mint has been great. Ubuntu Studio offered software that would help me introduce Linux to some close friends that (mostly Mac users) needed multimedia capabilities without spending $5000. Well I can't expect Windows and Mac users to learn the CLI. I can't deal with the phone calls either. GUI solutions are critical teaching them tons of new keyboard shortcuts to manage windows is not going to work (especially since I need to learn them first). Please understand that I love Linux and will try on my systems but I can't expect anyone else to.  With my typing issues the CLI is as huge hassle because of the typing errors. 

Finally--- in:re the screenshots---how did you accomplish the context menu additions. I've been using Dolphin.  I tried the sudo launcher on the desktop but it didn't work. I read the "root/sudo" popular pages help section.
  I also tried this: sudoedit /usr/share/themes/Greybird/gtk-2.0/gtkrc
the nano editor wouldn't let me save the edited file.

Thanks,

JB

---

### Post by CantankRus on 2016-11-21
In nano, after editing you press ctl+x where it will ask to confirm.
Press y then Enter to save.
(In the menu at the bottom of nano, ^ is a symbol for the control key)
If you don't like using nano you can set your text editor to open for "sudoedit".

Run this command to set your default editor to mousepad...
```
echo "export EDITOR=mousepad" >> ~/.bashrc
```
Substitute whatever text editor you normally use for mousepad.

The method to get context menus for "open as root" is dependant upon
which file manager you are using.

Are you using Ubuntu-studio with thunar as the file manager?

Typing shouldn't be an issue even when using the terminal.
Up/down Arrow keys can be used to show command history and you mostly use copy and paste.
You can get the path of files by navigating to them in the file browser and right click > copy.
A clipboard manager becomes a necessity. I use glipper.

In the terminal you can use [**[COLOR="#A52A2A"]TAB completion[/COLOR]**]("http://www.howtogeek.com/195207/use-tab-completion-to-type-commands-faster-on-any-operating-system/")
and many other shortcuts to limit typing.

---

### Post by vasa1 on 2016-11-21
Just to muddy things a bit, window decorations such as borders maybe determined by the window manager and *not* by the gtk theme. I don't know about apps which use client-side decorations.

---

### Post by Dennis N on 2016-11-21
> It is unlikely that 'usr/share/themes/Greybird/gtk-2.0/gtkrc' is the correct location. You are probably missing the initial '/'.

It depends on the present working directory. Could be /, in which case it works fine. Posting terminal output in #9 would have made that clear.

---

### Post by jerboa2 on 2016-11-21
Ok thanks to all!  Just so you know, I consider myself a Linux newbie  even though I've been playing around with various flavors since we used  Red Hat in my networking class in 2000.  I want people to stop using  Microsoft! I try to use Linux as someone migrating from Windows would.  So when the user interface doesn't work then that's a huge problem. Most  people want e.mail and Internet for Facebook. That can be done on just  about anything and I think there must be Linux systems that can do that  for those people.  I'm willing to try these Root options for  manipulating the "Window Manager" or individual files, wherever they may  be located but most people won't tolerate it.
 Anyway, I don't know anything about the CLI and I can copy and paste code that has been suggested. 
 I used this:  sudoedit  /usr/share/themes/Greybird/gtk-2.0/gtkrc
 I  spent an hour trying to edit that file and I studied the "Nano" help  files to learn how to navigate and save files. When it was all done it  denied my the option to save "access denied." It's embarrassing to have  done so much with Windows but feel like such an idiot with Linux.(My  networking teacher said "You just don't get it") I always understood  Windows-where things were what files did what. This theme file was where  I found settings that looked like they would help. All I can say is  that the borders are too narrow to drag for resizing with my mouse or  touch-pad. The scroll-bars are also too narrow. An earlier post helped  someone edit a file to fix his issue with the scroll-bars.

I would like to add the Root options to my file manager context menu.
I  may have to go back to a system that doesn't have Root locked down so  tightly or at least has better GUI options for tweaking the system.

Thanks for your patience-----I am a Linux lover.

JB

---

### Post by CantankRus on 2016-11-22
If you are using thunar use this method to create an "Open as Admin" option in the right click context menu.

menu > edit > configure custom actions
Hit the add button and copy and paste these in the fields as shown...
```
Open as Admin
Open directory as root
pkexec thunar %f

```
[ATTACH=CONFIG]272291[/ATTACH]


Click on the "no icon" box and select "All Icons" in the dropdown.
Enter **lock** in the search field and then select the locked icon.
[ATTACH=CONFIG]272292[/ATTACH]


Goto the "Appearance Conditions" tab and put an asterisk in the File Pattern field
and select Directories.
[ATTACH=CONFIG]272293[/ATTACH]

You should now have a context menu item for "Open as Admin" when you click on a blank space or a folder in thunar.
May have to log out/in for it to appear.
[ATTACH=CONFIG]272294[/ATTACH]

---

