---
title: "unable to open downloads"
date: 2023-12-10
forum: New to Ubuntu
---

### Post by cyr-s on 2023-12-10
I just started on Ubuntu and I've tried to download a couple applications but I can't open them by double clicking. I downloaded Minecraft, which I was able to download and open thanks to a Youtube video, but when I did the same process to download and open ATLauncher it didn't open. 
The part I'm having issues with is the very last opening part. When I opened Minecraft in the terminal it was opened by typing "Minecraft-launcher" which wasn't the name of the download. So how do I find out the secret keyword to open this application. I've tried to call the name of the application but it didn't work. :confused:

---

### Post by tea for one on 2023-12-10
> **cyr-s said:**
> I just started on Ubuntu and I've tried to download a couple applications
Probably best to start here:-
Show applications > Help > Install and remove Software

---

### Post by cyr-s on 2023-12-10
omg thank you, i feel so stupid it was on the second page of my application list. Now it just won't open :(

---

### Post by MAFoElffen on 2023-12-10
Please show / post the full file name of the files you  downloaded. Usually something like that is a compressed archive file. 

Without further information on what you downloaded, how, and what it is, then without those, we are just guessing on those details.

---

### Post by Impavidus on 2023-12-11
You tried to download an application from some random website and run it. That's something we rarely do on Ubuntu. It's the hard and insecure way to get software.

The normal way to get software is, as explained in post #2, to get them from the Ubuntu repositories. It has been packaged and tested for your release of Ubuntu and properly secured. There are multiple styles of packages and it's good to know the pros and cons of each style, but that can wait for some other time.

For downloading something from a website, there are no rules. Maybe it comes with instructions, otherwise you have to monitor the installation process and see where the files end up. It should provide some executable somewhere, or maybe (typical for GUI applications) some .desktop file. If there's a .desktop file in a standard location, the GUI for starting applications (whatever version you use; this varies with Ubuntu flavours) can find it for you. If the executable is in a directory known to your shell as part of the PATH environment variable (like /usr/bin, where most applications reside), you can start it in the terminal by typing the name of the executable. If not in the PATH, you have to type the full path to the executable.

---

### Post by SeijiSensei on 2023-12-11
If you're downloading Windows software, it will not run on Linux without some extensive additional work on your part.

---

### Post by yancek on 2023-12-12
Did you download the Debian/Ubuntu(deb) version from their download page?

[https://atlauncher.com/downloads](https://atlauncher.com/downloads)

Did you see the link below which gives an expalanation on how to install it?

ATLauncher i

---

### Post by yancek on 2023-12-12
Did you download the Debian/Ubuntu(deb) version from their download page?

[https://atlauncher.com/downloads](https://atlauncher.com/downloads)

Did you see the link below which gives an expalanation on how to install it?

[https://github.com/DavidoTek/linux-install-atlauncher](https://github.com/DavidoTek/linux-install-atlauncher)

---

