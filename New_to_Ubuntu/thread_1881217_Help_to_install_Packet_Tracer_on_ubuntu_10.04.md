---
title: "Help to install Packet Tracer on ubuntu 10.04"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by kiedis on 2011-11-15
I downloaded PacketTracer to my Downloads folder, but when I try to run that chmod... command, I get error "cannot find file in directory''. why this file cannot be found if i can see it with my own eyes in Downloads folder?

---

### Post by ajgreeny on 2011-11-15
> **kiedis said:**
> I downloaded PacketTracer to my Downloads folder, but when I try to run that chmod... command, I get error "cannot find file in directory''. why this file cannot be found if i can see it with my own eyes in Downloads folder?
Make sure you are in the correct Downloads folder, get all the letter cases correct (Packet Tracer is not the same as packet tracer) and either use " " around the name if there are spaces, or escape the spaces with a backslash, eg **packet\ tracer**.

---

### Post by kiedis on 2011-11-15
Packet Tracer was downloaded to Downloads folder. And when I try to "set the permission to be executable" by typing **chmod +x PacketTracer53_*.bin**, I get ''no such file in the directory" as seen in printscream

---

### Post by corncob on 2011-11-15
Open the Places dropdown menu and click on 'Downloads'.  Locate the file.  Open the terminal like you're doing and type in
```
chmod +x
``` 
plus a space.  Drag the file from the Downloads window into the terminal and hit ENTER.  I see you're logged on as root so I guess 'sudo' isn't necessary.  I don't know if you can drag the file from that list in your screenshot but Places > Downloads should do it.

---

### Post by muteXe on 2011-11-15
No need to double-post

---

### Post by haqking on 2011-11-15
> **kiedis said:**
> Packet Tracer was downloaded to Downloads folder. And when I try to "set the permission to be executable" by typing **chmod +x PacketTracer53_*.bin**, I get ''no such file in the directory" as seen in printscream

you need to be in the location of the file, so change to ~/Downloads directory before issuing the chmod command or specify path in the command, you can also right click on the file in nautilus and change it to be an executable file also

---

### Post by kiedis on 2011-11-15
I did exactly what you've sggested, corncob, but when i hit ENTER i get no results/reaction from the terminal

---

### Post by corncob on 2011-11-15
Yes.  In more detail: Places > Downloads > right-click the file > Properties > Permissions > Execute and check the box.  I've been assuming you're downloading to your Downloads directory.  If your downloads are going to your Desktop or somewhere else, please take that into account.

---

### Post by corncob on 2011-11-15
> **kiedis said:**
> I did exactly what you've sggested, corncob, but when i hit ENTER i get no results/reaction from the terminal

You didn't put the x after the +

---

### Post by kiedis on 2011-11-15
ok i typed in **sudo sh**, dragged and dropped the file and hit ENTER and it looked very promissing. i accepted agreement and then some unpackings went on but again, no further reaction from the terminal. tried to search for Packet tracer in software management center, no results...

---

### Post by kiedis on 2011-11-15
didn't refresh this page before writing my latter post... tried to run again with 'x' included, but it seems that packet tracer is already installed and is lurking somewhere in my system, the only problem is to open this application somehow

---

### Post by haqking on 2011-11-15
why dont you just use the deb to install ?

[http://www.ubuntubuzz.com/2011/05/installing-and-running-cisco-packet.html](http://www.ubuntubuzz.com/2011/05/installing-and-running-cisco-packet.html)

---

### Post by kiedis on 2011-11-15
seems that i posted my last reply somewhere else...

so i cite from my memory: 

didn't refresh this page before writing and didn't noticed your latter comments, corncob. i marked the file as executable under properties menu and then typed in chmod with x included and dragged-dropped the file. the typed sudo sh and dragged-dropped again that file. what i got was the info that packet tracer is already installed. so, how do i launch it and use it then?

---

### Post by corncob on 2011-11-15
> **kiedis said:**
> ok i typed in **sudo sh**, dragged and dropped the file and hit ENTER and it looked very promissing. i accepted agreement and then some unpackings went on but again, no further reaction from the terminal. tried to search for Packet tracer in software management center, no results...

I'm reaching the end of my knowledge here as I'm not familiar with Packet Tracer.  Is this an application that you run from the command line?  I wouldn't be logged onto the terminal as root like you're doing for fear of things getting lost in the root home folder rather than going into my own.  Just start the command with 'sudo'.  If you right-click on the upper panel you'll get a drop down menu.  Click on 'add to panel....' and select the search tool.  This will put a magnifying glass icon on the panel and you can use this to search.

---

### Post by duke.tim on 2011-11-15
You can launch packet tracer from the terminal by typing

```
packettracer
```

It is located here on my machine, if you have any additional problems :)
> duke.tim@ubuntufourms:/$ which packettracer
/usr/local/bin/packettracer


Packet Tracer is a network construction simulator from Cisco. In my experience the linux binary/deb is buggy and installing it on wine works better. 

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3352](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3352)

(Don't bother asking Cisco for help...they will tell you to ask your instructor...Don't bother reporting bugs either for the same reason)

---

### Post by corncob on 2011-11-15
Maybe you should uninstall it and start all over with what haqking or duke.tim suggest.  Possibly System > Administration > Computer Janitor will do the removal job.

---

