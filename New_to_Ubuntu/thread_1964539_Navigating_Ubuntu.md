---
title: "Navigating Ubuntu"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by mlempenau on 2012-04-24
I'm in a terminal trying to navigate to "cd VirtualBox VMs".  It does not like the space so I put a _ and it doesn't like that either.  I'm afraid to rename the directory ... probably screw things up.  I probably just have a mind lock ... but for the life of me I can't remember what to do.  Please help!  

I'm using 11.04 with VB 404.  I was certain that I had installed VB so that I would have enough storage space, but I screwed up somewhere, so need to enlarge.  The trials of growing old ... Thanks for helping.  Mike

---

### Post by westie457 on 2012-04-24
> **mlempenau said:**
> I'm in a terminal trying to navigate to "cd VirtualBox VMs".  It does not like the space so I put a _ and it doesn't like that either.  I'm afraid to rename the directory ... probably screw things up.  I probably just have a mind lock ... but for the life of me I can't remember what to do.  Please help!  

I'm using 11.04 with VB 404.  I was certain that I had installed VB so that I would have enough storage space, but I screwed up somewhere, so need to enlarge.  The trials of growing old ... Thanks for helping.  Mike

Hi.
The VirtualBox VMs directory is hidden. To find it in Nautilus, In your /Home folder hit Ctrl+H. This will show all hidden files and folders.

In the terminal try ```
c ~/.VirtualBox
```

---

### Post by mlempenau on 2012-04-24
The file I'm trying to modify is not in the ~/.VirtualBox directory.  It is in the /mike/home/VirtualBox VMs directory.  But when I type this into the terminal it doesn't like the space between the Box and VMS.  Tells me there is no such directory when I know there is.

---

### Post by audiomick on 2012-04-24
Have a look here. I think this is it...

[http://askubuntu.com/questions/18852/how-to-rename-file-with-whitespaces-in-filename]("http://askubuntu.com/questions/18852/how-to-rename-file-with-whitespaces-in-filename")

---

### Post by mlempenau on 2012-04-24
Thank you.  I don't remember that I ever used that before.  I printed out the page to put with my tips ... but that does not guarantee I will figure it out next time. :(

---

### Post by audiomick on 2012-04-24
> **mlempenau said:**
> .. but that does not guarantee I will figure it out next time. :(

Hmmm, sounds familiar... ;)

---

### Post by codemaniac on 2012-04-24
I believe you are trying to navigate to the directory called "VirtualBox VMs".
Please note that when you place "cd VirtualBox VMs" to command line , there are two arguments to the command cd , because of the space between VirtualBox and VMs .You need to escape the space , or wrap "VirtualBox VMs" in quotes so that shell cannot see it .Do this on your terminal .
```
cd "VirtualBox VMs"
```

---

### Post by codemaniac on 2012-04-24
the full path .

```
cd "/mike/home/VirtualBox VMs"
```

---

