---
title: "Thunar on live DVD?"
date: 2015-02-13
forum: New to Ubuntu
---

### Post by coastie2 on 2015-02-13
I am trying to test drive Xubuntu 14.04.1 LTS on live DVD. How do you open Thunar as root on live DVD? I want to test Synaptic and using some of my files, etc. Also what is the root password on the live DVD?

---

### Post by yancek on 2015-02-13
I don't use Xubuntu but I would try:  sudo thunar
There should not be a password, just hit the enter key if you are prompted.

---

### Post by Bucky Ball on 2015-02-13
Might work. Use:

```
gksudo thunar
```

... though. ;)

---

### Post by coastie2 on 2015-02-13
:redface: Thanks guys but I don't do terminal if I can help it. I am use to right clicking on a file or menu bar file> open as administrator then typing in my root password. Xubuntu is not giving me either option. Then I can paste into a file.

---

### Post by Bucky Ball on 2015-02-13
What exactly are you attempting to do. A little unclear. ;)

---

### Post by Yellow Pasque on 2015-02-13
You can create your own custom action in Thunar:
[https://help.ubuntu.com/community/ThunarCustomActions#Open_Folder_As_Root](https://help.ubuntu.com/community/ThunarCustomActions#Open_Folder_As_Root)

> I am used to right clicking on a file or menu bar file> open as administrator then typing in my root password. Xubuntu is not giving me either option.
That sounds like the behavior of the nautilus file manager back in the Gnome 2.x days if one had nautilus-gksu package installed. Nowadays, Gnome 2.x has become the MATE desktop and nautilus 2.x was renamed caja. I don't think Ubuntu 14.04.x has MATE packages in the main repos, but I'm sure you can find a PPA if you insist on using caja. Still, it seems easier just to create custom actions in Thunar for us xfce users...

---

### Post by kerry_s on 2015-02-13
i used: sudo thunar /
when running live, gksu is not installed by default.

>  Thanks guys but I don't do terminal if I can help it.

thats not good, terminal can be faster & easier some times.

---

### Post by coastie2 on 2015-02-13
I was trying to copy .mozilla, .thunderbird, and a theme into themes. Found the answer at 5:42 [https://www.youtube.com/watch?v=blJvcDT8Pk4](https://www.youtube.com/watch?v=blJvcDT8Pk4)

---

### Post by JeQhdMD on 2015-02-14
In case you haven't thought to try it . . . . but a LIVE "persistent" usb-stick will run substantially faster than cd/dvd media.   Use "Startup Disk Creator" to handle the setup.

---

### Post by coastie2 on 2015-02-14
Well answer at the answer at 5:42 [https://www.youtube.com/watch?v=blJvcDT8Pk4](https://www.youtube.com/watch?v=blJvcDT8Pk4) did not work on live DVD. Got other things to work and found a similar dark theme with Synaptic to try out. Never tried a live "persistent" usb-stick because I have some DVD RW for 'test driving." May try on usb-stick.

Thanks any way. No big deal should work on installation or usb.

---

### Post by ajgreeny on 2015-02-14
If you really must run a gui program as root you can first open a root terminal with sudo -i then from the same terminal window, which will now show a different prompt eg **root@xubuntu:~#**.

However it would be really worth your while putting aside your fear or dislike of the terminal and learning to love and use it for such activities.  It is made a lot easier than you might think by autocomplete, ie type the first few letters of a command, or a folder or file name, and hit tab.  One tab will show the full file or folder name if only one is present, tab x 2 will show all the available items with those first few letters and let you add another one or two letters and then tab again.

---

### Post by maclenin on 2015-02-14
**ajgreeny!**

+1 for learning to love the terminal, without which I never would have been able to fully appreciate the beauty of [this!]("http://xkcd.com/149/")

---

### Post by coastie2 on 2015-02-16
> **ajgreeny said:**
>  ... putting aside your fear or dislike of the terminal and learning to love and use it for such activities...

Thanks, but I couldn't figure out your suggestion. :confused:  I am not likely to love using the command line any more than I liked using it in DOS in the Dark Ages. I used a GUI menu and went to Windows 3.1 ASAP.

I saw on one of Jeff Linux Turner's videos [http://www.youtube.com/user/0658james/featured](http://www.youtube.com/user/0658james/featured) a simple way to open Thunar as root: sudo thunar which worked for me. :)

---

### Post by ajgreeny on 2015-02-16
> **coastie2 said:**
> Thanks, but I couldn't figure out your suggestion. :confused:  I am not likely to love using the command line any more than I liked using it in DOS in the Dark Ages. I used a GUI menu and went to Windows 3.1 ASAP.

I saw on one of Jeff Linux Turner's videos [http://www.youtube.com/user/0658james/featured](http://www.youtube.com/user/0658james/featured) a simple way to open Thunar as root: sudo thunar which worked for me. :)
You should **never use sudo** for any GUI application such as thunar when using an installed OS or you could lock yourself out of the system; it will still boot but you could be unable to login as user because using sudo for a GUI app can conceivably change permissions of files in your home.  See Root-Sudo in my signature for more details.

It may not happen often, but it has been reported, so if you use an installed OS avoid it and find another way such as **sudo -i** to get a root terminal then thunar in the same terminal to open thunar, or **sudo -H thunar**.

We used to use **gksu** instead of **sudo** for GUI apps, and the package is still available but not installed by default.

There is an intention to start using **pkexec** for all GUI apps needing root permissions instead of the sudo or gksu alternatives but at present it does not work for most applications in a way that is simple to use.

---

### Post by coastie2 on 2015-02-17
Thanks for the heads up, **ajgreeny!**. :)  Not sure I understand everything you wrote but "**sudo -i** to get a root terminal then thunar in the same terminal to open thunar, or **sudo -H thunar**." worked and I will use it it the future when needed.

For what it is worth, I recommend that "open as administrator" be installed as an option in the next version or update of Xubuntu.

---

