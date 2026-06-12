---
title: "HPLIP Toolbox Won't load in Ubuntu 11.10"
date: 2011-11-20
forum: New to Ubuntu
---

### Post by simon0404 on 2011-11-20
The Hplip toolbox wouldn't load from the menu.

So I did ~$ hp-toolbox

and got;

[HTML]Traceback (most recent call last):
  File "/usr/local/bin/hp-toolbox", line 39, in <module>
    from base import status, tui, module
  File "/usr/local/share/hplip/base/status.py", line 45, in <module>
    import hpmudext
ImportError: /usr/lib/python2.7/dist-packages/hpmudext.so: undefined symbol: hpmud_make_par_uri[/HTML]Could anybody point me in the right direction to solving this please??

Thanks in advance,
Simon

---

### Post by lechien73 on 2011-11-20
Are you using the latest version of hplip?

If you run

```
hp-toolbox -h
```

What version number does it report?

---

### Post by simon0404 on 2011-11-20
> **lechien73 said:**
> Are you using the latest version of hplip?

If you run

```
hp-toolbox -h
```What version number does it report?


This gives me the output;

[PHP]Traceback (most recent call last):
  File "/usr/local/bin/hp-toolbox", line 39, in <module>
    from base import status, tui, module
  File "/usr/local/share/hplip/base/status.py", line 45, in <module>
    import hpmudext
ImportError: /usr/lib/python2.7/dist-packages/hpmudext.so: undefined symbol: hpmud_make_par_uri[/PHP]

---

### Post by lechien73 on 2011-11-20
My first idea would be to reinstall hplip.

If you run:

```
dpkg -l | grep -i hplip
```

You can check the version numbers from there.

---

### Post by simon0404 on 2011-11-20
> **lechien73 said:**
> My first idea would be to reinstall hplip.

If you run:

```
dpkg -l | grep -i hplip
```You can check the version numbers from there.

That gave me the following output;

[PHP]ii  hplip                                  3.11.7-1ubuntu3                         HP Linux Printing and Imaging System (HPLIP)
ii  hplip-cups                             3.11.7-1ubuntu3                         HP Linux Printing and Imaging - CUPS Raster driver (hpcups)
ii  hplip-data                             3.11.7-1ubuntu3                         HP Linux Printing and Imaging - data files
ii  hplip-gui                              3.11.7-1ubuntu3                         HP Linux Printing and Imaging - GUI utilities (Qt-based)[/PHP]

---

### Post by Automat2 on 2011-11-20
> rc  hplip                                  3.11.7-1ubuntu3                         HP Linux Printing and Imaging System (HPLIP)
I can't install hplip either, again on Oneiric. What I don't understand is that I downloaded hplip 3.11.10 and it seems that it has installed version 3.11.7 (?)

---

### Post by fleamour on 2011-11-20
Last time I checked HPLIP only officially supports 11.04, such is being at the cutting edge...

Mine installs but works wonky.

---

### Post by Automat2 on 2011-11-20
> **fleamour said:**
> Last time I checked HPLIP only officially supports 11.04, such is being at the cutting edge...

Mine installs but works wonky.
On their website, they claim to support Ubuntu 11.10
> **Automatic Install**We recommend that most users use the Automatic Installer (provided your Linux distribution is supported by this method).
 Linux distributions supported by the automatic installer:
 
[LIST]
[*]SUSE Linux (11.3, 11.4)
[*]Fedora (14, 15)
[*]Ubuntu (8.04, 10.04, 10.10, 11.04, **11.10**)
[*]Debian (5.0, 5.0.1, 5.0.2, 5.0.3, 5.0.4, 5.0.5, 5.0.6, 5.0.7, 5.0.8, 6.0, 6.0.1, 6.0.2)
[/LIST]
 

---

### Post by lechien73 on 2011-11-20
I'm using hplip 3.11.1-2 on Oneiric, which seems to work ok.

Maybe you could try removing your current version, and then installing that. It's available from the [project page here]("http://sourceforge.net/projects/hplip/files/hplip/3.11.1/").

---

### Post by Automat2 on 2011-11-20
Ok. I'll try now.

---

### Post by fleamour on 2011-11-20
> **Automat2 said:**
> On their website, they claim to support Ubuntu 11.10

Really?  No drop down menu entry for 11.10 here:

[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

---

### Post by Automat2 on 2011-11-20
I tried to install hplip from the website and it doesn't work.

However, installing it from the repos, does but a bit weird. For example, it doesn't let me go any further than "Step 2" when I try to set up the device.

If I click the blue hp icon on the panel, as options I get two "HP Device Manager", two "Settings" and two "Quit", one of them doesn't work.

Despite all these problems, I can print, and with the correct colour correction; which is a lot better than before, when I couldn't print. Me thinks.

---

### Post by Automat2 on 2011-11-20
> **fleamour said:**
> Really?  No drop down menu entry for 11.10 here:

[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)
I saw it on the home page of the website, mate. I don't know how can claim they *support* Oneiric and then, do not give the option to download the proper version.

---

### Post by simon0404 on 2011-11-21
> **lechien73 said:**
> I'm using hplip 3.11.1-2 on Oneiric, which seems to work ok.

Maybe you could try removing your current version, and then installing that. It's available from the [project page here]("http://sourceforge.net/projects/hplip/files/hplip/3.11.1/").


Thanks for the assistance, it's now working!! :-)))) In summary, here's what I did:-


I have uninstalled everything related to Hplip in Synaptic.


I chose and downloaded the latest version here; [http://sourceforge.net/projects/hplip/files/hplip/](http://sourceforge.net/projects/hplip/files/hplip/)


I installed by these instructions; [http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)


I ran ~$ hp-toolbox

---

