---
title: "Trying to install RemoteMouse on Ubuntu, but not working."
date: 2017-11-17
forum: New to Ubuntu
---

### Post by socorob on 2017-11-17
Has anyone installed RemoteMouse server on Ubuntu? It's a program that lets you use your smartphone as a wifi keyboard and mouse. I was able to download it, and install it. It was a tar.gz file, but has an .exe in it and uses mono. I followed all the instructions that were in the readme files, and they seemed to install correctly, and in the end, its says to type      mono RemoteMouse. When I do that, it says not found. I just switched to ubuntu from windows 3 days ago, and even though it's a learning curve and frustration, I really want to keep it and not go back to windows. Any help will be greatly appreciated.

---

### Post by #&amp;thj^% on 2017-11-17
This has always worked well for me: [http://www.remotemouse.net/get_started.php](http://www.remotemouse.net/get_started.php)
Can you provide a link you used in installing remotemouse server on Ubuntu.
EDIT: I do now remember having to allow it through the firewall, (UFW)

---

### Post by Holger_Gehrke on 2017-11-17
Please read carefully. It say "mono <path>/Remote.exe". You need to give the extension and if mono behaves like the shell does it won't search the current directory, so you have to force it to do so by typing a path, for example './' for the current working directory or '~/bin/' ofr the directory 'bin' in your home directory.

Holger

---

### Post by leunam12 on 2017-11-17
Unified remote works on 16.04

---

### Post by socorob on 2017-11-17
I downloaded and extracted the folder to desktop. I double click to go inside the extracted remote mouse folder. I right click and choose open terminal. I typed mono ./RemoteMouse.exe.  it comes back with unhandled exception.system.typeloadexception:could not load type of field  main window indicator due to could not load file or assembly appindicator-sharp

It goes on for 8 more lines. Is appindicator a program I'm missing?

---

### Post by Holger_Gehrke on 2017-11-18
It's not missing appindicator itself, it's missing a library for programs using mono to talk to appindicator. appindicator might be missing or not, it's not saying either. What you do need to install is that library and it can be found in the package libappindicator0.1-cil. Install it by typing```
sudo apt install libappindicator0.1-cil
``` into a terminal and apt will get all the dependencies of the package automatically, so if you don't have appindicator yet this will install it along the library.

Holger

---

### Post by socorob on 2017-11-18
Thanks! That got me a little further along. Now when I type mono....exe it does 3 things. 
1. It pops up a window that says tcp error, it seems remote mouse server is already running
2. Behind that window is another that says remote mouse on the header with computer name and password for connection boxes, but as soon as I click on ok on the tcp error window, both these windows go away and..
3. It gets an error in terminal that says 
(REmotemouse:2126): Gtk-CRITICAL **: IA__gtk_main_quit:assertion 'main_loops  !=NULL failed

My old phone now sees the computer in the remote mouse app when I open it, but it doesn't connect.

Thanks for the progress, anything else I should try?

---

### Post by Holger_Gehrke on 2017-11-18
The FAQ-page on remotemouse.net says that this comes up when any program is already using the ports the remote mouse server wants to use. Those port are 1978 for both TCP and UDP. To find out if some program is using those port and which, you can run ```
sudo netstat -evpan --inet
``` in a terminal. (It would run without sudo, but then you'd only get the pid. With sudo netstat can find out the name of the offending program.

Holger

---

### Post by socorob on 2017-11-18
Thank you so much for your help. I was trying to use it on my android, and t wouldn't connect. we also have 2 very old iphones that are used only as a mouse/keyboard, so I went and got them out, and it works. For some reason the android app doesn't work with this. Another strange thing, is on the windows version all 3 phones could be controlling the mouse at the same time. In this version, you have to close the app on one before the other will work. Once again, thanks for your help. you made our day much better!

---

