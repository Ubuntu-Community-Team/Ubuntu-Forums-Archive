---
title: "Ndiswrapper + Dynex USB wi-fi adapter = trouble"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Folith on 2008-07-14
Alright, after a lot of help in someone else's thread, I decided to make my own because my problem became a lot different than his I didn't want to hijack the thread or anything.

Basically...  I searched for ndiswrapper under "Add/Remove Applications".

This is what I downoaded:

> "Windows Wireless Drivers"

graphical frontend for ndiswrapper (installation of Windows WiFi drivers)

ndisgtk is a GTK based frontend for ndiswrapper, allowing an easy way to install Windows wireless drivers.
Version: 0.6-0ubuntu3 (ndisgtk)
Windows Wireless Drivers integrates well into the Ubuntu desktop


I was told that I would need the .inf and .sys files to install with ndiswrapper.  I managed to get "ndiswdm.inf" and "ndiswdm.sys" from the driver .exe provided on Dynex's product page.

[http://www.dynexsupport.com/product/?pid=DX-BUSB](http://www.dynexsupport.com/product/?pid=DX-BUSB)

When I ran the app and clicked "Install New Driver", it asked for the .inf file.  I gave it the location, clicked "Install," and then it did nothing.  Nothing even appeared in the "Installed Drivers" box on the left of the window.  When attempting again, it says "Driver <b>driver</b> is already installed."  The app never even asks for the .sys.

Under System>Preferences>Hardware Information, Ubuntu recognizes the adapter as "802.11b/g LP/SC USBeless Adapter".  That's about it though.

---

### Post by anewguy on 2008-07-14
Ndisgtk is just a graphical front-end to ndiswrapper - ndiswrapper is still needed.  When you installed ndisgtk, did you do it through synaptic?  Did it say it required and would also install ndiswrapper?

Here's what I would try:

(1) Move/copy the 2 driver files to your desktop

(2) Open a terminal windows (Applications/Accessories/Terminal)

(3) sudo ndiswrapper -l <enter> that's a lower case "L" for list

(4) If the above returns something saying the file/directory ndiswrapper can't be found, then you need to go into synaptic and install ndiswrapper and utils itself

(5) If the above returned what appears to be a driver list, remove all of those listed by repeating the following for each listed:

sudo ndiswrapper -e xxxxxx <enter> where xxxxxx is a name returned in the list

(6) When the above list is returned empty:

cd ~/Desktop <enter>

sudo ndiswrapper -i ndiswdm.inf <enter>

sudo depmod -a <enter>

sudo modprobe ndiswrapper <enter>

sudo ndiswrapper -m <enter>

cd /etc <enter>

sudo gedit modules <enter>

at the end of the file add this line:

ndiswrapper <enter>

now, "Save" the file and "Close"

reboot


Now check your network manager and see if the wireless networks show.




I think your adapter needs to be plugged in prior to boot in order for this to work as well.

Let me know what happens.

:)

---

### Post by Folith on 2008-07-14
No luck :(

It still isn't giving me any kind of option for a wireless network.  Just 'wired' and 'modem'.

---

### Post by anewguy on 2008-07-14
Well, you're beyond what I know at this point.  Maybe there is something you need to do under system/administration/network tools like configure ethx or wlanx - I wish I could help you further.  The above *should* have worked from what I've done in the past.

Sorry I can't help you further.  Perhaps a Google or Yahoo search on Ubuntu Dynex USB wireless can yield you more help.

---

### Post by anewguy on 2008-07-14
I did find this for you, which would indicate that perhaps a different set of drivers is needed.  Look where "Ralph" starts posting and read from there.

[http://ankurs.com/2008/04/installing-ndiswrapper-on-ubuntu-804/]("http://ankurs.com/2008/04/installing-ndiswrapper-on-ubuntu-804/")


If you find you need the Broadcom driver as mentioned, let me know.  If you need the Atheros, I can't help at this time as I am unfamiliar with it (I could research if needed).

Dave

BTW - what does ndiswrapper -l show?

---

