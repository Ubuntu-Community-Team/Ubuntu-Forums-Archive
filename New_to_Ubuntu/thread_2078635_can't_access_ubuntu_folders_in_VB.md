---
title: "can't access ubuntu folders in VB"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by cmcanulty on 2012-10-31
I have searched for hours and every post is how to access windows files. But I am trying to access my Ubuntu files from a win 7 virtual box. I added them to shared folders in VB and marked them as shared in Ubuntu but I can't get them to show in WIN 7 I tried mapping network drive as shown on this page but that didn't work either.

[http://news.softpedia.com/news/How-to-Fix-Windows-7-Sharing-in-VirtualBox-123021.shtml]("http://news.softpedia.com/news/How-to-Fix-Windows-7-Sharing-in-VirtualBox-123021.shtml")

---

### Post by pandacookie on 2012-10-31
> **cmcanulty said:**
> I have searched for hours and every post is how to access windows files. But I am trying to access my Ubuntu files from a win 7 virtual box. I added them to shared folders in VB and marked them as shared in Ubuntu but I can't get them to show in WIN 7 I tried mapping network drive as shown on this page but that didn't work either.

[http://news.softpedia.com/news/How-to-Fix-Windows-7-Sharing-in-VirtualBox-123021.shtml](http://news.softpedia.com/news/How-to-Fix-Windows-7-Sharing-in-VirtualBox-123021.shtml)

You need to install VBox's Guest Additions before you can access shared folders in VBox. To install, go to the top panel in your Windows VM and click on "devices". The option to install Guest Additions should be the last option there.

---

### Post by cmcanulty on 2012-10-31
There is no devices in the VB window see screenshot. So I went to synaptic and checked to install it but then it said VB would be uninstalled and it took me forever to get VB to accept my win 7 key so I sure don't want to uninstall it!

---

### Post by pandacookie on 2012-10-31
No, I think you misunderstand. It's the window where Windows 7 is. Make that your main window. In the panel on top of your screen, hover your mouse and you will see that one of the menus is called "Devices". Click on that (you don't need to have any devices available for the menu to be present). The option to install Guest Additions will be the last option in the list. You need that to be installed to have shared folders.

---

### Post by cmcanulty on 2012-10-31
OK I have the regular win 7 desktop running but I moved my mouse everywhere and no devices pops up I am attaching screenshots of the desktop and the VB window. As I said above if I try to add guest additions in synaptic it says VB will be removed.
Also I am attaching 3 screenshots of all the menus in VB, this seems awfully difficult.I am using version 4.2.4 of Oracle Virtual Box

---

### Post by dannyboy79 on 2012-10-31
i've always had better luck installing VB straight from Oracle's website
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

Apparently whatever VB you installed from the repositories doesn't like the guest additions in the repo which again, is why I always install from the website. PLus I know it's always the latest build.

---

### Post by pandacookie on 2012-10-31
> **dannyboy79 said:**
> i've always had better luck installing VB straight from Oracle's website
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

Apparently whatever VB you installed from the repositories doesn't like the guest additions in the repo which again, is why I always install from the website. PLus I know it's always the latest build.

This!!!

Yes, get the latest VBox from [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads). I know you said you don't want to get rid of your Windows 7 install, but it doesn't look like your setup is right, anyway. There should be more menus available when you hover your mouse over the top panel. If you want shared folders the best advice I can give would be to try installing the latest build from virtualbox.org. Because you NEED the Guest Additions to make shared folders work.

---

### Post by mosaic2s on 2012-10-31
machine win7 will be saved as a vdi file and will work under the vbox installation as suggested in previous posts.
so no sweat.
virtualbox additions is needed before you can access ubuntu folders from vboxed windows.

---

### Post by Swagman on 2012-10-31
install from [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

[img]http://img189.imageshack.us/img189/8961/vboxdev.jpg[/img]

---

### Post by cmcanulty on 2012-10-31
Ok I reinstalled it from that web site which is where I got it before and menus are exactly the same and again if I try to install the guest additions synaptic wants to remove virtual box. I am stuck. Is there a way to force installing the guest adds? Again no devices are in any menus.Are you using version 4.2.4 that is what I installed.

---

### Post by Swagman on 2012-10-31
Yes I'm on the latest.  I have /home on a separate partition and just clean installed Quantal. On seeing your issue I tried firing up Vbox  but it wasn't there so I just went to that link and re-installed.

Of course all my previous VB settings were still in /Home


I've got to go to work in a minute but tomorrow I will dual boot into Win 7 and install vbox in that to see if I get the same results as you.

---

### Post by cmcanulty on 2012-10-31
OK thanks, the reinstall kept the win 7 and bodhi I had installed but the devices are nowhere

---

### Post by dannyboy79 on 2012-10-31
how you installing the guest additions?

---

### Post by cmcanulty on 2012-10-31
I don't know how please read OP if I install guest additions synaptic will remove VB. I have a screenshot above showing the synaptic view. Well I did the guest install which removed vb and installed some other type of it but no change .Then I removed the synaptic older version and went back to 4.2.4 from the VB website. I have spent all day just trying to get the stupid devices menu to show!***I think the problem may be that guest additions is not in 4.2.4 but instead they use Extension Pack and so maybe the whole procedure is different. I do have the extension pack installed.I have the shared folders set up correctly I think see screenshots.Or maybe I am not mapping the network drive correctly in win 7 I am chossing to map it to \\vboxsvr\Desktop and \\vboxsvr\Documents

---

