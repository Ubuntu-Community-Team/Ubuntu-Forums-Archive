---
title: "How to install X11 lib with apt-get(needed for Xboard)"
date: 2007-12-04
forum: Packaging and Compiling Programs
---

### Post by BenBush on 2007-12-04
How to install X11 lib with apt-get(needed for Xboard)

---

### Post by cinematography on 2007-12-04
I hate to say this about a Linux program, but Xboard is very dated by today's standards. For Chess, I highly recommend the Arena gui. It runs perfectly with WINE. 

[http://www.playwitharena.com/](http://www.playwitharena.com/)

---

### Post by BenBush on 2007-12-04
> **cinematography said:**
> I hate to say this about a Linux program, but Xboard is very dated by today's standards. For Chess, I highly recommend the Arena gui. It runs perfectly with WINE. 

[http://www.playwitharena.com/](http://www.playwitharena.com/)

I just want to compile my C programs(include xboard) under Ubuntu, not for playing chess. But it lacks some X11 header files, I am not familiar with the X11, so I need some help to find the correspond files to be installed.:guitar:

---

### Post by dholbach on 2007-12-05
Try:
```
sudo apt-get build-dep xboard
```

What's wrong with the xboard package in the archive?

---

### Post by RealMabu on 2008-01-22
**dholbach** said:
> What's wrong with the xboard package in the archive?

Simple: xboard won't start, with the error message:
```

xboard: no fonts match pattern -*-helvetica-bold-r-normal--*-*-*-*-*-*-*-*

```
I don't know if there is a fix to this out there, I am googling to find it but haven't found yet.

Regards.
Mabu

---

### Post by stroyan on 2008-01-22
Fonts matching that pattern are available in the xfonts-75dpi and xfonts-100dpi packages.

---

### Post by RealMabu on 2008-01-23
> **stroyan said:**
> Fonts matching that pattern are available in the xfonts-75dpi and xfonts-100dpi packages.

That's strange.
I have both installed, as shown by Synaptic and Aptitude (it's in italian but the bold sentence is understendable):
```

 $ aptitude show xfonts-75dpi xfonts-100dpi
Pacchetto: xfonts-75dpi
**Stato: installato**
Installato automaticamente: sì
Versione: 1:1.0.0-3
Priorità: opzionale
Sezione: x11
Responsabile: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Dimensione pacchetto installato: 4674k
Dipende: xfonts-utils (>= 1:1.0.0-6)
Consiglia: xfs | xserver
Descrizione: Caratteri per X a 75 dpi
 ...
Pacchetto: xfonts-100dpi
**Stato: installato**
Installato automaticamente: sì
Versione: 1:1.0.0-3
Priorità: opzionale
Sezione: x11
Responsabile: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Dimensione pacchetto installato: 5014k
Dipende: xfonts-utils (>= 1:1.0.0-6)
Consiglia: xfs | xserver
Descrizione: Caratteri per X a 100 dpi
...

```

What's wrong with my fonts?

Any idea?

Thanks,
Mabu

---

### Post by stroyan on 2008-01-23
You could look for clues in /var/log/Xorg.0.log, assuming you are using the local X server with DISPLAY set to :0.0 .
In particular look at the lines reporting FontPath- ```
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
```
You can also see what fonts are available with the xlsfonts command from the xlsfonts package.
```
xlsfonts -fn '-*-helvetica-bold-r-normal--*-*-*-*-*-*-*-*'
```

---

### Post by RealMabu on 2008-01-23
> **stroyan said:**
> You could look for clues in /var/log/Xorg.0.log, **assuming you are using the local X server with DISPLAY set to :0.0**
Hhmm this gives me an hint. Actually I'm trying to start xboard from a remote display. Actually the setup is a freenx server (ubuntu) + nxclient (win32).
Now that I'm physically sitting in front of my ubuntu box, a simple "xboard -ncp" starts smoothly.
So the problem arises when I'm remote....

Nevertheless the code:
```
xlsfonts -fn '-*-helvetica-bold-r-normal--*-*-*-*-*-*-*-*'
```
shows A LOT of fonts:
```
$ xlsfonts -fn '-*-helvetica-bold-r-normal--*-*-*-*-*-*-*-*'
-adobe-helvetica-bold-r-normal--0-0-100-100-p-0-iso10646-1
-adobe-helvetica-bold-r-normal--0-0-100-100-p-0-iso10646-1
-adobe-helvetica-bold-r-normal--0-0-100-100-p-0-iso8859-1
-adobe-helvetica-bold-r-normal--0-0-100-100-p-0-iso8859-1
-adobe-helvetica-bold-r-normal--0-0-75-75-p-0-iso10646-1
-adobe-helvetica-bold-r-normal--0-0-75-75-p-0-iso10646-1
-adobe-helvetica-bold-r-normal--0-0-75-75-p-0-iso8859-1
-adobe-helvetica-bold-r-normal--0-0-75-75-p-0-iso8859-1
-adobe-helvetica-bold-r-normal--10-100-75-75-p-60-iso10646-1
-adobe-helvetica-bold-r-normal--10-100-75-75-p-60-iso10646-1
-adobe-helvetica-bold-r-normal--10-100-75-75-p-60-iso10646-1
-adobe-helvetica-bold-r-normal--10-100-75-75-p-60-iso10646-1
-adobe-helvetica-bold-r-normal--10-100-75-75-p-60-iso8859-1
-adobe-helvetica-bold-r-normal--10-100-75-75-p-60-iso8859-1
-adobe-helvetica-bold-r-normal--10-100-75-75-p-60-iso8859-1
-adobe-helvetica-bold-r-normal--10-100-75-75-p-60-iso8859-1
-adobe-helvetica-bold-r-normal--11-80-100-100-p-60-iso10646-1
-adobe-helvetica-bold-r-normal--11-80-100-100-p-60-iso10646-1
-adobe-helvetica-bold-r-normal--11-80-100-100-p-60-iso10646-1
-adobe-helvetica-bold-r-normal--11-80-100-100-p-60-iso10646-1
-adobe-helvetica-bold-r-normal--11-80-100-100-p-60-iso8859-1
-adobe-helvetica-bold-r-normal--11-80-100-100-p-60-iso8859-1
-adobe-helvetica-bold-r-normal--11-80-100-100-p-60-iso8859-1
-adobe-helvetica-bold-r-normal--11-80-100-100-p-60-iso8859-1
-adobe-helvetica-bold-r-normal--12-120-75-75-p-0-iso10646-1
-adobe-helvetica-bold-r-normal--12-120-75-75-p-0-iso10646-1
-adobe-helvetica-bold-r-normal--12-120-75-75-p-0-iso10646-1
-adobe-helvetica-bold-r-normal--12-120-75-75-p-0-iso10646-1
-adobe-helvetica-bold-r-normal--12-120-75-75-p-0-iso8859-1
-adobe-helvetica-bold-r-normal--12-120-75-75-p-0-iso8859-1
-adobe-helvetica-bold-r-normal--12-120-75-75-p-0-iso8859-1
-adobe-helvetica-bold-r-normal--12-120-75-75-p-0-iso8859-1
-adobe-helvetica-bold-r-normal--12-120-75-75-p-70-iso10646-1
-adobe-helvetica-bold-r-normal--12-120-75-75-p-70-iso10646-1
-adobe-helvetica-bold-r-normal--12-120-75-75-p-70-iso10646-1
-adobe-helvetica-bold-r-normal--12-120-75-75-p-70-iso10646-1
-adobe-helvetica-bold-r-normal--12-120-75-75-p-70-iso8859-1
-adobe-helvetica-bold-r-normal--12-120-75-75-p-70-iso8859-1
-adobe-helvetica-bold-r-normal--12-120-75-75-p-70-iso8859-1
-adobe-helvetica-bold-r-normal--12-120-75-75-p-70-iso8859-1
-adobe-helvetica-bold-r-normal--14-100-100-100-p-82-iso10646-1
-adobe-helvetica-bold-r-normal--14-100-100-100-p-82-iso10646-1
-adobe-helvetica-bold-r-normal--14-100-100-100-p-82-iso10646-1
-adobe-helvetica-bold-r-normal--14-100-100-100-p-82-iso10646-1
-adobe-helvetica-bold-r-normal--14-100-100-100-p-82-iso8859-1
-adobe-helvetica-bold-r-normal--14-100-100-100-p-82-iso8859-1
-adobe-helvetica-bold-r-normal--14-100-100-100-p-82-iso8859-1
-adobe-helvetica-bold-r-normal--14-100-100-100-p-82-iso8859-1
-adobe-helvetica-bold-r-normal--14-140-75-75-p-82-iso10646-1
-adobe-helvetica-bold-r-normal--14-140-75-75-p-82-iso10646-1
-adobe-helvetica-bold-r-normal--14-140-75-75-p-82-iso10646-1
-adobe-helvetica-bold-r-normal--14-140-75-75-p-82-iso10646-1
-adobe-helvetica-bold-r-normal--14-140-75-75-p-82-iso8859-1
-adobe-helvetica-bold-r-normal--14-140-75-75-p-82-iso8859-1
-adobe-helvetica-bold-r-normal--14-140-75-75-p-82-iso8859-1
-adobe-helvetica-bold-r-normal--14-140-75-75-p-82-iso8859-1
-adobe-helvetica-bold-r-normal--17-120-100-100-p-92-iso10646-1
-adobe-helvetica-bold-r-normal--17-120-100-100-p-92-iso10646-1
-adobe-helvetica-bold-r-normal--17-120-100-100-p-92-iso10646-1
-adobe-helvetica-bold-r-normal--17-120-100-100-p-92-iso10646-1
-adobe-helvetica-bold-r-normal--17-120-100-100-p-92-iso8859-1
-adobe-helvetica-bold-r-normal--17-120-100-100-p-92-iso8859-1
-adobe-helvetica-bold-r-normal--17-120-100-100-p-92-iso8859-1
-adobe-helvetica-bold-r-normal--17-120-100-100-p-92-iso8859-1
-adobe-helvetica-bold-r-normal--18-180-75-75-p-103-iso10646-1
-adobe-helvetica-bold-r-normal--18-180-75-75-p-103-iso10646-1
-adobe-helvetica-bold-r-normal--18-180-75-75-p-103-iso10646-1
-adobe-helvetica-bold-r-normal--18-180-75-75-p-103-iso10646-1
-adobe-helvetica-bold-r-normal--18-180-75-75-p-103-iso8859-1
-adobe-helvetica-bold-r-normal--18-180-75-75-p-103-iso8859-1
-adobe-helvetica-bold-r-normal--18-180-75-75-p-103-iso8859-1
-adobe-helvetica-bold-r-normal--18-180-75-75-p-103-iso8859-1
-adobe-helvetica-bold-r-normal--20-140-100-100-p-105-iso10646-1
-adobe-helvetica-bold-r-normal--20-140-100-100-p-105-iso10646-1
-adobe-helvetica-bold-r-normal--20-140-100-100-p-105-iso10646-1
-adobe-helvetica-bold-r-normal--20-140-100-100-p-105-iso10646-1
-adobe-helvetica-bold-r-normal--20-140-100-100-p-105-iso8859-1
-adobe-helvetica-bold-r-normal--20-140-100-100-p-105-iso8859-1
-adobe-helvetica-bold-r-normal--20-140-100-100-p-105-iso8859-1
-adobe-helvetica-bold-r-normal--20-140-100-100-p-105-iso8859-1
-adobe-helvetica-bold-r-normal--24-240-75-75-p-138-iso10646-1
-adobe-helvetica-bold-r-normal--24-240-75-75-p-138-iso10646-1
-adobe-helvetica-bold-r-normal--24-240-75-75-p-138-iso10646-1
-adobe-helvetica-bold-r-normal--24-240-75-75-p-138-iso10646-1
-adobe-helvetica-bold-r-normal--24-240-75-75-p-138-iso8859-1
-adobe-helvetica-bold-r-normal--24-240-75-75-p-138-iso8859-1
-adobe-helvetica-bold-r-normal--24-240-75-75-p-138-iso8859-1
-adobe-helvetica-bold-r-normal--24-240-75-75-p-138-iso8859-1
-adobe-helvetica-bold-r-normal--25-180-100-100-p-138-iso10646-1
-adobe-helvetica-bold-r-normal--25-180-100-100-p-138-iso10646-1
-adobe-helvetica-bold-r-normal--25-180-100-100-p-138-iso10646-1
-adobe-helvetica-bold-r-normal--25-180-100-100-p-138-iso10646-1
-adobe-helvetica-bold-r-normal--25-180-100-100-p-138-iso8859-1
-adobe-helvetica-bold-r-normal--25-180-100-100-p-138-iso8859-1
-adobe-helvetica-bold-r-normal--25-180-100-100-p-138-iso8859-1
-adobe-helvetica-bold-r-normal--25-180-100-100-p-138-iso8859-1
-adobe-helvetica-bold-r-normal--34-240-100-100-p-182-iso10646-1
-adobe-helvetica-bold-r-normal--34-240-100-100-p-182-iso10646-1
-adobe-helvetica-bold-r-normal--34-240-100-100-p-182-iso10646-1
-adobe-helvetica-bold-r-normal--34-240-100-100-p-182-iso10646-1
-adobe-helvetica-bold-r-normal--34-240-100-100-p-182-iso8859-1
-adobe-helvetica-bold-r-normal--34-240-100-100-p-182-iso8859-1
-adobe-helvetica-bold-r-normal--34-240-100-100-p-182-iso8859-1
-adobe-helvetica-bold-r-normal--34-240-100-100-p-182-iso8859-1
-adobe-helvetica-bold-r-normal--8-80-75-75-p-50-iso10646-1
-adobe-helvetica-bold-r-normal--8-80-75-75-p-50-iso10646-1
-adobe-helvetica-bold-r-normal--8-80-75-75-p-50-iso10646-1
-adobe-helvetica-bold-r-normal--8-80-75-75-p-50-iso10646-1
-adobe-helvetica-bold-r-normal--8-80-75-75-p-50-iso8859-1
-adobe-helvetica-bold-r-normal--8-80-75-75-p-50-iso8859-1
-adobe-helvetica-bold-r-normal--8-80-75-75-p-50-iso8859-1
-adobe-helvetica-bold-r-normal--8-80-75-75-p-50-iso8859-1

```

Let's say 70% of the problem is solved.
But for the remaining 30%... I'm lost now more than before.
Any clue on why I cannot start xboard remotely?

Thanks
Mabu

---

### Post by stroyan on 2008-01-23
It would be very odd indeed if xlsfonts sees the fonts on the freenx server but xboard does not.

I haven't experimented with the freenx server.  Its configuration is discussed in this thread-
[http://ubuntuforums.org/showthread.php?t=467219](http://ubuntuforums.org/showthread.php?t=467219)
Have a look at the log file of freenx and look for font related errors.

---

### Post by kayvan on 2008-07-09
> **RealMabu said:**
> Hhmm this gives me an hint. Actually I'm trying to start xboard from a remote display. Actually the setup is a freenx server (ubuntu) + nxclient (win32).
Now that I'm physically sitting in front of my ubuntu box, a simple "xboard -ncp" starts smoothly.

So the problem arises when I'm remote....
Any clue on why I cannot start xboard remotely?

Thanks
Mabu

Did you ever get this working? I am running into this same issue with NX Client on windows and xboard.

Thanks for any replies.

---Kayvan

---

### Post by elpechos on 2008-08-17
I fixed this issue by installing font packages from;

[http://www.nomachine.com/download-client-windows.php](http://www.nomachine.com/download-client-windows.php)

nxfonts-75dpi and nx-fonts-100dpi are required to run some applications remotely, including xboard.

---

### Post by malkdude on 2009-06-17
I solved the xboard fonts problem on my ubuntu jaunty by installing xfonts-jmk from the repositories, and then restarting my system. Then I was able to run xboard and play versus GNU chess 5.07 without any problem. I hope this helps...

---

