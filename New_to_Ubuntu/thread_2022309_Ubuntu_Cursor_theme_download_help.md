---
title: "Ubuntu Cursor theme download help"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by AbhiKap on 2012-07-10
Hello,
 
I would like to get a cursor/pointer from gnome-look.org, I downloaded it but when I try to extract it to usr/share/icons, it says you do not have permission. What should I do?
 
Thanks, Help is appreciated.

---

### Post by GreatDanton on 2012-07-10
That means you have to extract it as super user. Open terminal (shortcut is ctrl+alt+t) copy and paste:
```
gksudo open nautilus
```Now you should be able to extract it. However be careful not to delete something important.

P.s I assume you have Ubuntu. If you don't have Ubuntu installed this command will not work, because Xubuntu, Kubuntu or Lubuntu have different file managers.

Regards.

---

### Post by AbhiKap on 2012-07-10
GreatDanton, I wrote that code in the Terminal, but it just opens up the hoem folder, and when I try to extract it it says the same thing. What do I do? 

.P.S. Yes I do have Ubuntu, not other versions of it.

---

### Post by GreatDanton on 2012-07-10
Well, you have to navigate to the folder you want to extract. At the left side of the Nautilus you have Sidebar: Devices, Computer, and Network. Under Computer click on File System. After that navigate to the folder you want to extract. In your case that is /usr/share/icons.

It's better you extract your files before, and then just copy and paste it into the folder you choose.

Hope this helps.

---

### Post by AbhiKap on 2012-07-10
Ok.... Can you please explain step by step exactly what I have to do. Sorry because I always used windows so I am a complete beginner for Ubuntu. Thanks.

---

### Post by GreatDanton on 2012-07-10
1. Open Nautilus (the big folder at the left side of the desktop)
2.Extract your files. If you have your file in Downloads, go to Downloads, right click on your file, and select extract here.
3.Don't close Nautilus. You will need it in few minutes.
4.Open terminal
5.Type: gksudo open nautilus
6.Now you have opened nautilus. At the left side of nautilus click on File System.
7.Navigate to folder you want to extract your files. In your case that is usr/share/icons.
8.Open icons folder.
9.Grab the files from the first Nautilus, and put them to the second Nautilus (the one you have opened it with terminal).

10. Enjoy!

Regards.

---

### Post by AbhiKap on 2012-07-10
Thanks a lot. I did that and copied it over. Now how do I select it I opened Gnome Tweak tool, but it doesn't appear on the list of pointers. What should I do? Thanks.

---

