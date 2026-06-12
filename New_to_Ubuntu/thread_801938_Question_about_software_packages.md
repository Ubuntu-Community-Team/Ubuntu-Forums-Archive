---
title: "Question about software packages"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by somewho on 2008-05-21
Hello, i'm a new Ubuntu user and confused about something. I want to migrate from Windows to Ubuntu. Recently i've received my ShipIt CD (Ubuntu 8.04LTS for AMD64). And did the installation under Windows. What i want to ask is, EXACTLY what packages i should download so i can work like before in my Ubuntu. The problem is, i don't have internet connection at home. So i have to download the packages somewhere else and install it on my PC. But when i'm trying to download that, i see a whole lot of dependand package. So, exactly what packages should i download, including all the dependant that's not already available on my PC (after installation under windows like installing other program, without dedicated partition)?

Here's what i need to do with my computer, that has not available yet :
- Driver for hardware (non-generic version)
- Creating 3D game with Java and OpenGL
- Creating web application with PHP
- MySQL database
- Watching .avi, .mkv, and DVD movies
- Listening to .mp3 music (I want to use audacious, is this ok?)
- Using adobe photoshop? (If could, freely, i've Photoshop already)
- Playing DirectX game?

For additional notes, here my PC specs :
- AMD Athlon X2 4000+ (Brisbane)
- ECS AMD690GM-M2
- 2x 1GB Corsair DDR2/667MHz (Value Select)
- Maxtor 250GB SATAII
  > 3 Partition : NTFS 16GB Windows, NTFS 16GB Ubuntu+Additional Windows Program, NTFS 200GB Data
- dagraphic ATi Radeon HD2400Pro

Thank you very much in advance!

---

### Post by Inxsible on 2008-05-21
You would be better off getting [AptOnCD]("http://aptoncd.sourceforge.net/")

---

### Post by Xiong Chiamiov on 2008-05-21
As Inxsible alluded to, there are quite many packages that you'd have to download separately to get all of that working; *buntu isn't really built for computers that aren't connected to the 'net.

That said, I can give you a few pointers to some apps you'll want for a few of those tasks.
Although you can [install the full LAMP stack]("https://help.ubuntu.com/community/ApacheMySQLPHP") for web development, if it's just local, you might want to try [XAMPP]("http://ubuntuforums.org/showthread.php?t=223410&highlight=xampp") instead.  It's quite easy to use.
Playing most 3d games will require a proprietary driver from your manufacturer.
There are many media players, mplayer being one of the kings.  I've had success with Totem on my Xubuntu install, and on Kubuntu I use Kaffeine and KPlayer.  VLC will, of course, play anything, but it has terrible Matroska support and subtitle rendering.
You [may or may not]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=17") be able to get Photoshop working through Wine.  Though the interface is quite different, you should give GIMP a try.  It's not quite up to par in some features, but it makes many tasks multitudes simpler than the equivalent in PS.

---

### Post by hyper_ch on 2008-05-21
> **somewho said:**
> - Driver for hardware (non-generic version)
You have to check the manufacturer's homepage for that... but I doubt there is any and if there is, you'll probably have to compile it yourself. And piece of hardware you have problems with?
> **somewho said:**
> - Creating web application with PHP
What do you need for that? A text editor? An IDE? A WYSIWYG editor?
> **somewho said:**
> - MySQL database
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p4](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p4)  --> Step 14
and maybe: [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p6](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p6) --> Step 16 and 17
> **somewho said:**
> - Watching .avi, .mkv, and DVD movies
- Listening to .mp3 music (I want to use audacious, is this ok?)
(1) install the package ubuntu-restricted-extra
(2) browse synaptic for matroska (I think there are a few extra packages needed)
(3) if you still can't watch dvds, add the Medibuntu repos (google for medibuntu and there's a repository howto) and then install libdvdcss2
(4) That should be all
> **somewho said:**
> - Using adobe photoshop? (If could, freely, i've Photoshop already)
Possible through wine or then virtualisation
> **somewho said:**
> - Playing DirectX game?
Some stuff runs through wine - otherwise dualboot Windows

---

### Post by somewho on 2008-05-21
@ Inxsible :
So, i have to use that software and download all the packages all need from another computer that is connected to the internet and running Ubuntu. I think it's kinda impossible for me. Since all the connected-to-thenet pc i can access all use Windows. However, i can run DSL under windows on that PCs. Any other possible alternative?

@ Xiong Chiamiov :
Of course i won't download all of the packages, i just confused which packages already installed on my PC. Any option to check what packages is installed on my PC?
I'll use XAMPP then, used this on Windows for long time and feel happy with it...

@ hyper_ch :
Actually all hardware works well except the video driver won't do that much so i think i'll download the driver. Checked on ATi site and found one for linux (.run format) i hope it works.
Well, something like Dreamweaver, WYSIWYG for the HTML part, and self coding for the underlying PHP.

I think i really should keep my Windows intact and dual booting right?

---

### Post by iaculallad on 2008-05-21
> **somewho said:**
> @ Inxsible :
So, i have to use that software and download all the packages all need from another computer that is connected to the internet and running Ubuntu. I think it's kinda impossible for me. Since all the connected-to-thenet pc i can access all use Windows. However, i can run DSL under windows on that PCs. Any other possible alternative?

@ Xiong Chiamiov :
Of course i won't download all of the packages, i just confused which packages already installed on my PC. Any option to check what packages is installed on my PC?
I'll use XAMPP then, used this on Windows for long time and feel happy with it...

@ hyper_ch :
Actually all hardware works well except the video driver won't do that much so i think i'll download the driver. Checked on ATi site and found one for linux (.run format) i hope it works.
Well, something like Dreamweaver, WYSIWYG for the HTML part, and self coding for the underlying PHP.

I think i really should keep my Windows intact and dual booting right?

You could still keep your windoze as Ubuntu's dual boot, if you have your usual applications that you need working with windoze. But when time comes, that you can live without windoze as dual boot, get rid of it :lolflag:

---

### Post by Xiong Chiamiov on 2008-05-21
You can get a listing of all the installed packages on your system in a nice text file like so:
```

aptitude search ~i > ~/installedPackages

```
which will put a list of them in a text file in your home directory called installedPackages.  It'll be a bit long, though, so be warned.

The problem I see is more of a dependecy problem.  Some packages might require a newer version of another package than what you have installed, and very often you get dependecy chains where updating one thing updates many others.

---

