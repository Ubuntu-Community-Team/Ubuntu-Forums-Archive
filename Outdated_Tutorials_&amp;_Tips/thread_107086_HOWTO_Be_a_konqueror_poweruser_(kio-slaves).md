---
title: "HOWTO: Be a konqueror poweruser (kio-slaves)"
date: 2005-12-22
forum: Outdated Tutorials &amp; Tips
---

### Post by GoldBuggie on 2005-12-22
I want to provide you with a way of getting to know konqueror and KDE's KIO-slaves. For many newcomers to KDE it isn't obvious that these things exist.
[B]
[COLOR=SeaGreen]Description[/COLOR] [/B]*(from wikipedia)*[B]
KIO[/B] (KDE Input/Output) is part of the KDE architecture. It provides access to files, web sites and other resources through a single consistent API. Applications written using this framework can operate on files stored on remote servers in exactly the same way as they operate on those stored locally.
**KIO** **slaves** are programs that provide support for individual protocols.

[COLOR=SeaGreen]**Why do I need this?**[/COLOR]
It makes life **easier** and more **fun**.

[COLOR=SeaGreen]**How do I use it?**[/COLOR]

[COLOR=RoyalBlue]*1st.*[/COLOR]
Start a konqueror session.

[COLOR=RoyalBlue]*2nd.*[/COLOR]
In the URL section (where you often type a local pathname or www address) you can enter some other commands/URL's that give you easy access to documentation, cd's or remote systems. Below are a few(there are plenty more) kio-slaves to get you started.

Type the command marked in **[COLOR=DarkRed]red[/COLOR]** in your konqueror URL.

[COLOR=DarkRed]**apt:/**[/COLOR]
This will provide you with an easy to use search form for searching for packages or files within packages.

[COLOR=DarkRed]**locate:**<search-criteria>[/COLOR]
Same as locate in the konsole but instead you get the results in konqueror. *Usage example: locate:fstab*

**[COLOR=DarkRed]man:/[/COLOR]** or [COLOR=DarkRed]**man:**<command>[/COLOR]
Provides access to the man pages(that is help documentation for different commands).

[COLOR=DarkRed]**ftp://**username:_password@your.ftp.site.org/some/folder/[/COLOR]
Provides nice ftp capabilities. You can also just type the ftp address and it will automatically use the ftp kio.

[COLOR=DarkRed]**fish://**username:_password@yadayada.isp.no[/COLOR]
This is the kio for the** shh** protocol

[COLOR=DarkRed]**fonts:/**[/COLOR]
Gives you a virtual directory to your system fonts, (very handy)

[COLOR=DarkRed]**info:/**[/COLOR]
Nice interface to your installed GNU info pages. (you probably didn't know you had this information, did you?)

[COLOR=DarkRed]**audiocd:/**[/COLOR]
Browse your audiocd. Also provides rip & encode(mp3/ogg) when you drag and drop. [I](The names for the files are created using a internet CDDB. For more configuration kcontrol->Sound & Multimedia->Audio CDss)
[/I]
**[COLOR=DarkRed]mac:/[/COLOR]**
The mac ioslave lets you read an HFS+ partition from Konqueror or any other KDE file dialog.

[COLOR=DarkRed][B]settings:/
[/B][/COLOR]Instead of Control Center or System Settings

[COLOR=DarkRed]**tar:/path/filename**[/COLOR] and **[COLOR=DarkRed]zip:/path/filename[/COLOR]** 
Browse into TAR and ZIP files without unpacking them, opening a command prompt, or opening a packaging application. You can even edit the archive as though it were unpackaged.

[COLOR=DarkRed]** camera:/**[/COLOR]
To browse a digital camera.


To see which kio-slaves you have on your system goto *KInfoCenter->Protocols*

Hope this gives you some insight in how to use KDE and konqueror a bit more.

[SIZE=1]*Catchy title? I wanted to attract some newcomers since this is something that isn't obvious to use at start.*[/SIZE]

---

### Post by evs on 2005-12-22
This is some nice stuff!! I didn't even know about all of these, like apt:/ and fonts:/ which are really cool.  Thanks a lot!

---

### Post by GoldBuggie on 2005-12-22
You are welcome! I'm glad you enjoyed the info.

---

### Post by veloct on 2005-12-23
Thanks, good info.

---

### Post by GameManK on 2005-12-26
very nice.
another one i commonly use:
camera:/
to browse a digital camera

---

### Post by GoldBuggie on 2005-12-26
>  camera:/
to browse a digital cameraAhhh..that's a good one to point out. I'll add that one. Thank you very much.

---

