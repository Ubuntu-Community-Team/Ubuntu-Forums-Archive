---
title: "just starting out"
date: 2013-07-02
forum: New to Ubuntu
---

### Post by anthonyc42 on 2013-07-02
Hello, I have just installed Ubuntu and I am trying to figure out how to (or if its even possible) install windows programs onto Linux? My goal once I have all of my files transferred is to turn it into a media server that I can access from anywhere on my android device and other computers so I can watch my TV and Movies with it but I need to go one step at a time :)  I have 2 android devices a laptop and an apple TV. What my thoughts where was to install ITunes onto Linux and then from their I could still watch all of the shows I downloaded and then using an app on my phone (I forget the name of it) get live access to the desktop to run iTunes remotely. would this work or is their a better way to do this that could simplify things a bit? Thanks in advance :)

---

### Post by BBQdave on 2013-07-02
> **anthonyc42 said:**
> ...install windows programs onto Linux?

[**WINE**]("http://www.winehq.org/") is your best shot - though I think you are heading down a painful path, trying to intermix Linux, Windows and Apple software.

---

### Post by anthonyc42 on 2013-07-02
I don't have to use the apple TV necessarily I really just want to make it so I can access my files from Linux to my laptop or Android soon the Apple TV will be tossed and replaced for a mini tower I'm just trying to save what investment (which was not the best investment) I have already started not trying to go down any painful routes :)

---

### Post by BBQdave on 2013-07-02
> **anthonyc42 said:**
> ...I really just want to make it so I can access my files from Linux to my laptop or Android...

I have an old eMac that I use as a FTP file server on a protected home network. Linux, Mac, and Windows machines access it with [**FileZilla**]("https://filezilla-project.org/").

[**vsftpd**]("https://security.appspot.com/vsftpd.html") may be helpful, if you access data - your file server - through the web.

---

### Post by 3rdalbum on 2013-07-03
Itunes doesn't work on Linux, so that's out. Only a small number of Windows programs can be made to work in Wine, so personally I don't bother even trying, and you should use Linux programs where possible.

To start a basic file server, you can install the system-config-samba package and then open the Samba program and set it up.

---

### Post by coldraven on 2013-07-03
You could try using VirtualBox to run Windows in a virtual machine. Installing Vbox is easy, the boring part is installing Windows in a VM.
You would need to have a Windows disc with a product key for the least painfull option.

---

### Post by nothingspecial on 2013-07-03
FX is a nice android app for accessing your files remotely. I've only used it with ssh but you can use it with ftp. Also sshdroid for maintaining it. You would need to install openssh-server on your ubuntu. There are plenty of music managers and media players available in the software centre, as other have said forget about iTunes. You didn't mention what os your laptop is running.

---

### Post by Dozy Van on 2013-07-03
I run my Ubuntu box as a media center. I installed [XBMC]("http://wiki.xbmc.org/index.php?title=Archive:HOW-TO:Install_XBMC_on_Ubuntu/HOW-TO_1") as an extra and boot into it for movies but I burned all my dvds onto an internal hard drive over a few days so I have them on the PC physically and that works well for me. I can use my phone as a remote controll using the [XBMC Remote]("https://play.google.com/store/apps/details?id=org.xbmc.android.remote&hl=en"). works really well for me.

---

### Post by anthonyc42 on 2013-07-03
Hello, thanks to everyone that replied I am running windows 7 Home. I am also wondering how I use my domain name for my server I seen that I need Samba to get everything going. Then everyone says their are other music managers that will work but I made the bad mistake of buying Movies and TV shows as well so are their any players out their that will play them with the file protection or should I just start over with new movies and TV shows?

---

