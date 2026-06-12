---
title: "Updated to 24.04 and now LibreOffice products won't start..."
date: 2024-08-30
forum: New to Ubuntu
---

### Post by yatski on 2024-08-30
(I don't know should this go to LibreOffice forums, but..)

Well, I updated(see [https://ubuntuforums.org/showthread.php?t=2500333](https://ubuntuforums.org/showthread.php?t=2500333) ) my Ubuntu to 24.04(via terminal) and now LibreOffice products won't start.

My laptop is old Sony Vaio.

---

### Post by ajgreeny on 2024-08-30
Try starting LO-Writer from terminal with command **libreoffice --writer** and see if any errors show in the output which you should then report back here..

---

### Post by yatski on 2024-08-30
```
heta@heta-vaio:~$ libreoffice --writer
Warning: failed to launch javaldx - java may not function correctly
ERROR 4 forking process
```

Am I missing Java?

---

### Post by Dennis N on 2024-08-30
> Am I missing Java? 

libreoffice does not show a dependency on java:

```
dmn@Kayleigh:~$ apt depends libreoffice | grep java
  Recommends: libreoffice-java-common (>= 4:24.2.5~)
 |Suggests: <java-runtime> (>= 8)
 |Suggests: <java8-runtime>
  Suggests: libofficebean-java

```
But, I would install the Recommended package **libreoffice-java-common** and see if that helps. If it is already installed, it will tell you.

---

### Post by ajgreeny on 2024-08-30
The &#314;ack of java will not stop LO from starting so your problem must be a result of something else. 
Some users feel java is a utility they prefer not to use at all and make sure all java packages are missing but it does not stop LO.

You do not seem to have error messages about java from the command I mentioned, merely that warning but I have not seen the error you do show about "forking process". 
How long did you wait after the warning appeared for LO to start?

---

### Post by yatski on 2024-08-31
(Well, after catching some zzz:s, I'm back..)

I installed **libreoffice-java-common** and we have *some* progress... 

It will show splash picture but stops loading there.

> **ajgreeny said:**
> 
How long did you wait after the warning appeared for LO to start?

I was going to use LibreOffice Calc right away I knew my laptop was okay to use, if that's what you mean..

---

### Post by Dennis N on 2024-08-31
If you search for "ERROR 4 forking process" with Google you will get a good number of hits with a lot of discussion, and even an old bug report filed for Debian. This stuff is not easy to follow and dig out an answer. Much easier solutions are possible starting with removing the existing LibreOffice install. Then you have several choices:

1 - reinstall it from Ubuntu Software or a terminal and see if the problem goes away.
2 - install a Flatpak package of LibreOffice.
3 - Install a Snap package of LibreOffice.
4 - Install with a .deb file downloaded from the LibreOffice web site.
5 - Use an AppImage of LibreOffice.

I would favor choice 2 since I use a lot of Flatpak packages and like them. You have to set up Flatpak support by following a few easy steps given on **[https://flathub.org/setup](https://flathub.org/setup)**

Ubuntu created and promotes Snap packages, and is already set up to install them from Ubuntu Software. So choice 3 is easy because of that. You can also install them with a terminal command.

---

### Post by yatski on 2024-08-31
I tried choices 1 and 3 and they didn't help..

(Currently trying choice 2. Edit: worked!)
```
heta@heta-vaio:~$ flatpak install flathub org.libreoffice.LibreOffice
Looking for matches&#8230;
Required runtime for org.libreoffice.LibreOffice/x86_64/stable (runtime/org.freedesktop.Platform/x86_64/23.08) found in remote flathub
Do you want to install it? [Y/n]: y 

org.libreoffice.LibreOffice permissions:
    ipc                 network               fallback-x11    pulseaudio
    wayland             x11                   dri             file access [1]
    dbus access [2]     bus ownership [3]

    [1] host, xdg-config/fontconfig:ro, xdg-config/gtk-3.0, xdg-run/gvfsd
    [2] com.canonical.AppMenu.Registrar, org.gtk.vfs.*
    [3] org.libreoffice.LibreOfficeIpc0


        ID                                   Branch      Op Remote  Download
 1. [&#10003;] org.freedesktop.Platform.GL.default  23.08       i  flathub 170,4*MB / 170,7*MB
 2. [&#10003;] org.freedesktop.Platform.GL.default  23.08-extra i  flathub  19,2*MB / 170,7*MB
 3. [&#10003;] org.freedesktop.Platform.Locale      23.08       i  flathub   1,8*MB / 372,5*MB
 4. [&#10003;] org.freedesktop.Platform.VAAPI.Intel 23.08       i  flathub  13,3*MB / 13,4*MB
 5. [&#10003;] org.freedesktop.Platform.openh264    2.2.0       i  flathub 886,7*kB / 944,3*kB
 6. [&#10003;] org.gtk.Gtk3theme.Yaru-dark          3.22        i  flathub 134,1*kB / 196,5*kB
 7. [&#10003;] org.freedesktop.Platform             23.08       i  flathub 177,7*MB / 228,2*MB
 8. [&#10003;] org.libreoffice.LibreOffice.Locale   stable      i  flathub   2,3*MB / 85,1*MB
 9. [&#10003;] org.libreoffice.LibreOffice          stable      i  flathub 299,1*MB / 320,0*MB

Installation complete.
heta@heta-vaio:~$ flatpak run org.libreoffice.LibreOffice
Failed to open display

```

Despite the last line,  LibreOffice started...

Now, onto that backlog...

Thanks again. You've been great help these past few days.

---

### Post by Dennis N on 2024-08-31
Good choice. As I said, that is what I would have done. You shouldn't need to use the terminal to run the program. After installing, the LibreOffice Flatpak should have an entry in Applications Menu (if you use that extension) and and show up when searching on the Activities Overview. I pin it to my dock, of course.

---

### Post by J0nD33 on 2024-09-01
This is not a fix, just a work around.  Similar problems have come up before.  My logs indicate problem with apparmor and the initial call.  I run this line in a terminal after a restart to get LO to boot in Ubuntu 24:

$ sudo apparmor_parser -R /etc/apparmor.d/usr.lib.libreoffice.program.oosplash

---

### Post by ndangerfield on 2024-11-10
I had a similar problem - if I selected a file on my server (for example a .docx file) libre wouldn't open. I ran: sudo apt-get install libreoffice-java-common and now it works fine.

---

### Post by ndangerfield on 2024-11-10
I had a similar problem. I couldn't open files (for example .docx files) on NAS. I ran: sudo apt-get install libreoffice-java-common as suggested and now works fine.

---

