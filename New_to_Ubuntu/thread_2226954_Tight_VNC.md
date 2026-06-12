---
title: "Tight VNC"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by Paul_Wike on 2014-05-29
Evening, 

I have now installed tightvnc and can access this from my laptop but just get a grey screen and a cross. 

the below starts up on my server 

New 'X' desktop is hpserver:1

Starting applications specified in /home/wikey/.vnc/xstartup
Log file is /home/wikey/.vnc/hpserver:1.log

What do I need to edit to see my desktop?

Any help would be appreciated, 

Paul

---

### Post by steeldriver on 2014-05-29
Standalone vncservers (such as vnc4server and tightvncserver) use their own session startup file located at $HOME/.vnc/xstartup,  and the default file that ships with the package just starts a simple X  terminal window on a plain gray root window (which is probably what  you're seeing). 
 
You can find a sample $HOME/.vnc/xstartup file in the Ubuntu Community Help Wiki at [VNC/Servers - Customizing your session]("https://help.ubuntu.com/community/VNC/Servers#Customising_your_session") which you can copy and edit to start your chosen desktop session - which must correspond to one of the available .desktop files in your /usr/share/xsessions directory if you want to start it via gnome-session. Note that the ubuntu-2d session referred to in the Wiki is no longer available in 13.10

If you're using the regular desktop edition of Ubuntu, and want to connect to "your desktop" via VNC, you should  probably use the default 'Desktop Sharing' application (vino-server)  that is provided as part of the ubuntu-desktop package, rather than a  separate vncserver session. You can configure it by entering 'Desktop Sharing' in the dash search, or from the command line by running vino-preferences.

---

