---
title: "[SOLVED] Help! I'm locked out of my own backup!"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by Charlie Chick on 2008-06-01
Hello Everybody,

I just used Clonezilla to make a backup of my entire computer. Unfortunately, things did not quite go according to plan. It was supposed to have backed up to my external 750 USB hard drive, but instead it backed up to my local hard drive, which is now full and is preventing me from using the computer.

The backup file is in root, but it says that I don't have permission to do anything with it and I need to delete it urgently to regain my computer. How can I gain ownership of this file?

Thanks,

Charlie

---

### Post by sayakb on 2008-06-01
Can you boot in to the recovery mode through GRUB? If so, then just enter recovery mode and do:
```
rm -rf /whatever directory
```
BUT **CAREFUL WITH rm -rf**. Delete only that which you know you don't need. You can harm your system since rm -rf can delete anything.

---

### Post by Charlie Chick on 2008-06-01
I haven't tried that. I seem to remember something called chown which gives you the necessary permissions. I just need to delete this backup folder.

---

### Post by Sinkingships7 on 2008-06-01
Enter
```
gksudo nautilus
```
into the terminal. You now have a window where you have super user privileges. Do what you need to do and get out. Running nautilus as root can be very dangerous.

---

### Post by Charlie Chick on 2008-06-01
I found the solution to my problem in an Ubuntu book. I typed sudo rm rf /filename and it worked! My computer is working properly again!

Thanks to everybody for your help.

---

### Post by sayakb on 2008-06-01
You didn't have to look into the Ubuntu book. I posted the same thing. The Recovery mode boots you in as root, so it'll issue commands same as sudo ;)

---

