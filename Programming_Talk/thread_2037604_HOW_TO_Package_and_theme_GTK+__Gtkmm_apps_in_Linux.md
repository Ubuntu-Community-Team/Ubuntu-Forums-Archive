---
title: "HOW TO: Package and theme GTK+ / Gtkmm apps in Linux for Windows"
date: 2012-08-05
forum: Programming Talk
---

### Post by SuperCamel on 2012-08-05
Hi, 

If you are developing platform independent software in Linux using Gtk+/Gtkmm and you've managed to cross compile for Windows, this guide is for you. 

I'm posting this because after researching the topic myself, I encountered many posts where people have abandoned Gtk+/Gtkmm for wxWidgets because of Gtks ugly default appearance in Windows/Wine. Gtk+ is just as themeable in Windows/Wine as GNOME. You just have to set it up correctly . . . here's how. 

This guide is for Gtkmm but Gtk+ would be very similar. 

(1) Firstly, download and install Gtkmm for Windows using Wine. (You will already have this if you have cross compiled your app for windows)
[https://live.gnome.org/gtkmm/MSWindows](https://live.gnome.org/gtkmm/MSWindows)

(2) Run these commands to create the proper directory structure. (Substitute 'proj' for whatever your project is called)

mkdir ~/proj
mkdir ~/proj/bin
mkdir ~/proj/etc
mkdir ~/proj/etc/gtk-2.0
mkdir ~/proj/lib
mkdir ~/proj/lib/gtk-2.0
mkdir ~/proj/lib/gtk-2.0/2.10.0
mkdir ~/proj/lib/gtk-2.0/2.10.0/engines
mkdir ~/proj/share
mkdir ~/proj/share/themes


(3) Move to the directory where Gtkmm was installed (probably ~/.wine/drive_c/gtkmm/)
Copy all the .dlls from the redist folder into ~/proj/bin

cp redist/*.dll ~/proj/bin

(4) Cross compile your software for Windows and copy your built executable into ~/proj/bin

There are several decent guides and forum posts on how to do this so if you aren't sure, have a google. 

(5) Download and install the Gtk+ Theme Selector for Windows 
[http://gtk-win.sourceforge.net/home/index.php/Main/GTKPreferenceTool](http://gtk-win.sourceforge.net/home/index.php/Main/GTKPreferenceTool)

(6) The Theme Selector comes with a heap of themes and all the popular engines, built for Windows. You'll have to copy them into your project folder so go to the directory where they were installed (try ~/.wine/drive_c/Program Files/GTK/2.0) 

Copy the lib and share folders into ~/proj

Really, you don't need every engine and theme but now you'll be able to try them all and choose your favorite. Also, you should be able to download a theme and copy it into the correct directory. 


(7) Move to ~/proj/etc/gtk-2.0

Create a file and name it gtkrc
Copy this into gtkrc but substitute Aurora with the name of your preferred theme
gtk-theme-name = "Aurora"

Move to ~/proj/bin and run your program in Wine. Much more sexy, isn't it?? 

Now if you were to give your ~/proj directory to a windows user, it will run correctly AND look good. Comments?

---

