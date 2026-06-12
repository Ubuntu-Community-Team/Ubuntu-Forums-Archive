---
title: "Wireless Not Working"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by biggiemokey on 2008-05-04
Hey, my I'm very new to Ubuntu (8.04 through Wubi, going to go dedicated partition soon).  The Network Config Tool shows Point-to-Point and Wired Connection, but no Wireless Connection.  I went to Troubleshooting in Ubuntu help but can't find the Device Manager anywhere (says it should be System->Preferences->Hardware Information) but it's not there.  I downloaded gnome-device-manager or something and it shows up in System Tools but I really can't use it, at least I can't figure it out.

I could really use some help with this, I want to stick with Ubuntu and I need wireless.  I have a Dell TrueMobile 1300 Wireless USB Adapter.  So please, what do I do, or how do I at least get to Hardware Information so I can try and figure it out.:confused:  I'm sure once I find Hardware Information I'll be able to search for a driver.

Thanks for any help.

---

### Post by Wobblybob on 2008-05-04
You may be looking for Hardware drivers in [System], [Admin] if your wireless driver is still not showing, try opening teh [synaptic package manager], [setting], [repos] and the [third party] tab and ticking the boxes to enable anything in it. ok and exit then click on the blue [reload] icon on the top bar and exit synaptic. when all done go look in hardware drivers again.

---

### Post by manosdvd on 2008-05-04
You sound like you're having the same problem I had. I'm pretty new myself. You probably want some Windows-based wireless drivers. To do that you're gonna need an internet connection so you're probably returning to windows for a bit. You need to find and download drivers for your wireless card from the company's website. Then find "ndisgtk" and download the deb file (easier for us newbies than the tar.gz file). When you come back, go into synaptic and look for ndiswrapper (you may have to change you're [Settings][Repositories] to include everything including the cd). Once you install that and ndisgtk (ndisgtk is just a much easier graphical front end so you're not compiling it by hand in the terminal), open up you're system administration menu and go to the Windows Wireless Drivers. Install new, find you're .inf file from the driver download, and install. Within seconds the network icon should spring to life. 

You may find you have to reinstall the driver every time you restart the computer. To fix that, I had to open in the terminal: "sudo gedit" and from there open the file "etc/modules". At the bottom, if ndiswrapper isn't there, type it in and save it. You should restart with it running every time now.

There's probably an easier way, but this is what worked for me and hopefully it's in proper newbie speak.

---

