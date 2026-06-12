---
title: "Hardy network switch"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by RH9R on 2008-07-07
This one may sound dumb, but with my 3rd version of Ubuntu (hardy), I now have to learn how to switch off the network connection again. So how does Hardy go incommunicato? In Feisty, you opened the network mgr., unchecked the wired connection checkbox. Hardy doesn't seem to work w/ a checkbox. How is it done now?

---

### Post by AndyCee on 2008-07-07
*removed*

---

### Post by jpkotta on 2008-07-07
This way will not change for some time.  

```
sudo ifconfig eth0 down
```
Repeat for each network interface, except "lo".  You can get a list by just running ```
ifconfig
```

You can get it back with
```
sudo ifconfig eth0 up
```

---

### Post by aktiwers on 2008-07-07
You could also right-click on the network icon in the taskbar and untick wireless, like you said.

Or kill network manager and open it again.

Kill it:```
sudo killall nm-applet
```

Start it again:
```
nm-applet
```

---

### Post by RH9R on 2008-07-07
aktiwers & jpkotta, thank you both for your kind help. I appreciate it.
 
The network dialogue box (like feisty) is still there, but instead of displaying a checkbox with a check, it displays a line inside the box. I click inside the box and it doesn't do anything. Perhaps a permissions issue?
 
I don't know if anyone else sees or experiences this. If its a process permission issue, I'd love to know the command. in the mean time, I can use jp's method.
 
Again, thank you both!

---

### Post by RH9R on 2008-07-10
'Stepped in it now. 'Searched 'network manager' threads and ran across one talking about uninstalling and reinstalling the network manager. there were two packages in synaptic - network-manager, and network-manager-gnome. The thread said to completely uninstall. I did. Now no internet from which to reinstall. Is there any way to reload from the liveCD? Am I looking at a reinstall from scratch?

---

### Post by aktiwers on 2008-07-11
Go to synaptics (System => Administration => Synaptics Package manager)
And in the edit menu pick repositories
Then enable CD-rom.
(sorry cant remember the exact steps, I am on OSX now)

Then put the Ubuntu CD in the drive (while still in ubuntu). 

And install the network-manager again..  it should be able to use the CD as repositories now

---

### Post by RH9R on 2008-07-12
Aktiwers, Thank You for your kind help. I wasn't able to get the live CD to act as a repository. Each attempt gave some exception that it wasn't able to get something it needed from another repository. I tried checking the CD as repository - as suggested, then unchecking the other repositories so it would look exclusively at the cd. 
 
I had work I needed from the machine today & reverted to a 'plan B' reinstall. 
 
I do  very much appreciate your kindness. All best to you.

---

