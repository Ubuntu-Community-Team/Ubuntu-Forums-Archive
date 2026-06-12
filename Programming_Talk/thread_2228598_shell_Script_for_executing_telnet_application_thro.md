---
title: "shell Script for executing telnet application through firefox"
date: 2014-06-08
forum: Programming Talk
---

### Post by kedarbhatia on 2014-06-08
On my Ubuntu 64bit, I have a virtual lab having routers and switches running on top of VM ware virtuized cent OS.
 
I open the GUI for the routers and switches in the firefox browser. when i try to telnet to the devices, there is a popup asking the application to be used.

I manually select the gnome-terminal to login to these devices. To make things easier  i tried to run a script so when i click any device it should directly open up gnome and telnet to respective IP and port,(so for example if router IP:port  is 192.168.1.5 : 2012 then the click on device should result in opening up of gnome-terminal window  telnetting to the IP and port combination )

below is the script i saved on my drive and ask the popup to execute, but nothing happens. .no gnome terminal opens up....
any idea if there is issue in the script or anything i might be doing wrong

please find the attached screen shot of trying to run script through pop up (pardon my bad gimp skills!)
##########################################################################################
#!/bin/sh

address=`echo ${*##telnet://} | sed 's/:/ /g'`

/usr/bin/gnome-terminal -e "telnet $address"
##########################################################################################

---

