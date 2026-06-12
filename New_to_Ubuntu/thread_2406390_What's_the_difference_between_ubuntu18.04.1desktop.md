---
title: "What's the difference between ubuntu18.04.1desktop-64bit &amp; ubuntu18.04.1server-64bit?"
date: 2018-11-20
forum: New to Ubuntu
---

### Post by michaelcc2 on 2018-11-20
What's the major difference between ubuntu18.04.1desktop-64bit & ubuntu18.04.1server-64bit?

Right now, I made a mistake to install the ubuntu18.04.1desktop-64bit instead of the ubuntu's server version in my server computer, of course I want some server software to run in the server computer.
So, is it necessary to switch it into the ubuntu-server? 
If it's very necessary, how could switch it if I don't want to reinstall the whole operating system?

---

### Post by Tadaen_Sylvermane on 2018-11-20
Only difference is preinstalled packages, nothing more. They both have the ability to install the same stuff from the same place. One has a graphical interface, the other is command line only. For stability's sake the server install is better for a server mainly due to the fact that the less software running, the less likely something will have a problem. Servers by definition need or are expected to be rock solid stable with 100% reliability. A gui is never required for a linux server, though some do install a gui and access it over VNC or something similar. Generally no sense leaving a GUI running and eating hardware muscle or ram when you won't use it though. Exception to this rule in my case anyway is my "server" also serves as my living room HTPC, hence direct boot to Kodi. Everyone is different whether or not they can live without a GUI. That is really the question, do you need the graphical interface or not? Decide from there.

---

### Post by The Cog on 2018-11-20
I think the desktop version defaults to using DHCP for its networking, but the server has to have its networking configured in configuration files. This makes sense as servers generally require fixed IP addresses, and don't have a GUI where the networking can be quickly edited.

I suggest that being that much of a newcomer to Linux, you would prefer to have a GUI style desktop available to you. For a real server that sits in a rack with no screen and keyboard such a GUI would be a waste of resources. You can of course fix the IP address using the GUI.

---

### Post by michaelcc2 on 2018-11-20
OK. Thanks. It's a bit clear.

---

### Post by michaelcc2 on 2018-11-20
Yeah, I agree with you. Actually, I plan to use the server without GUI, now I just want to find an easy way to switch the current desktop version into the server version so as to reduce much time than re-install a new OS.

---

### Post by oldfred on 2018-11-21
Not sure with new Subiquity installer, but last part of server install runs this, so you can choose which server apps you want.

 Used by Server install to choose what you want
sudo apt-get install tasksel
sudo tasksel
sudo apt install ubuntu-server
[URL="https://help.ubuntu.com/community/Tasksel"]https://help.ubuntu.com/community/Tasksel

      [/URL]
 The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment) 
    

But not sure if you uninstall the ubuntu-desktop, if it uninstalls too much. I would review what it wants to uninstall carefully.
[URL="https://help.ubuntu.com/community/Tasksel"]
[/URL]

---

