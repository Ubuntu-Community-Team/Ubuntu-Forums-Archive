---
title: "NVidia screen-tearing making Oneiric unusuable in some parts"
date: 2011-07-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by tghe-retford on 2011-07-30
And according to this [bug report](https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/600178) it's both Nouveau and NVidia's proprietary drivers which suffer the same problem, and whether you use Compiz or KWin, same problem there too.

One thing that I have noticed during testing of Kubuntu and Ubuntu is that screen tearing has always been an issue, but it has seemed to have got a lot worse with Oneiric, to the point where moving windows, viewing video and the like causes noticeable screen tearing to the point where it has become impractical to view video. Every workaround I have seen does not fix the problem.

Will the curse of the screen tear be fixed by Oneiric's release or is it going to be the continuing curse of Ubuntu's NVidia users?

---

### Post by wojox on 2011-07-30
I have the option of rolling back from the 210.xx to the 173.xx and it helped a lot.

---

### Post by tghe-retford on 2011-07-30
> **wojox said:**
> I have the option of rolling back from the 210.xx to the 173.xx and it helped a lot.
Not an option for me sadly as I have a GT 555M.

---

### Post by garthecho on 2011-09-02
I was starting to think I was the only one!  

I have the same problem with my 9600gt.  Graphics were like butter on Natty.  No tearing in Compiz, Kwin, or Gnome Shell.  Not sure if it's Xorg or the new Nvidia driver, but performance has really regressed in Oneiric.

I was using the 270 Nvidia binaries in Natty, but they won't build against the 3.0 kernel, so hopefully something is fixed soon.

---

### Post by PhantmKllr on 2011-09-02
I think that it's just the older cards that are having this problem.

Still, I've got a GTS 250 and the performance is noticeably slower than Natty, so, yeah (proprietary drivers installed).

---

### Post by sgage on 2011-09-02
> **tghe-retford said:**
> And according to this [bug report](https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/600178) it's both Nouveau and NVidia's proprietary drivers which suffer the same problem, and whether you use Compiz or KWin, same problem there too.

One thing that I have noticed during testing of Kubuntu and Ubuntu is that screen tearing has always been an issue, but it has seemed to have got a lot worse with Oneiric, to the point where moving windows, viewing video and the like causes noticeable screen tearing to the point where it has become impractical to view video. Every workaround I have seen does not fix the problem.

Will the curse of the screen tear be fixed by Oneiric's release or is it going to be the continuing curse of Ubuntu's NVidia users?

I'm not seeing any screen tearing (Nvidia GeForce 8500 GT), and haven't in over 10 years of using various Nvidia cards. I wonder if it is just certain models combined with certain drivers. I think the first step would be to isolate the models affected. But I don't sense any "curse of Ubuntu's Nvidia users" in a general way.

---

### Post by VinDSL on 2011-09-02
> **tghe-retford said:**
> Will the curse of the screen tear be fixed by Oneiric's release or is it going to be the continuing curse of Ubuntu's NVidia users?
I'm running a nVidia GeForce 7600GT in UbuOO beta 1 with nVidia 285.03 drivers.

It's working like a champ; even on fullscreen HD YouTube vids, e.g. no tearing, slowness, et cetera...

---

### Post by lucazade on 2011-09-02
I've seen some performance degradation in oneiric about opengl 3D and it seems common for different graphic cards.
Not sure what is the cause and when it was introduced during the dev cycle.. my mere speculation is about mesa 3d graphic library.

glxgears decreased in frame per second compared to natty.
unfortunately I can't bench  with a better tool because is no more present in Oneiric:
/usr/lib/xscreensaver/glblur -fps -window

---

### Post by VinDSL on 2011-09-02
> **lucazade said:**
> unfortunately I can't bench  with a better tool because is no more present in Oneiric [...]
These are what I use...


[INDENT](Click to expand)
[[IMG]http://vindsl.com/images/vindsl-desktop-2-sep-2011(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-2-sep-2011.png")[/INDENT]


Not bad for an old dog.  :)

---

### Post by lucazade on 2011-09-02
> **VinDSL said:**
> These are what I use...
..

Not bad for an old dog.  :)

yep, not bad... don't you have a natty partition to compare them?
just 2d gtkperf seems a bit slow.. from what I recall i get 3/4 sec as result on a nvidia 250gts 1gb and around 30sec with the gma500 8mb.
unfortunately can't test it now cos i'm not at home.

---

### Post by garthecho on 2011-09-02
Well, here's glxgears from an old Maverick install I have on the same machine...



and here's Oneiric...



So, in Oneiric, performance is almost half what it used to be.


It's not clear in the screenshot, but I should state that in Oneiric glxgears starts out at about 8000fps, but then drops and stays at around 3-5000.  In Maverick I get a constant 8-10000fps.

---

### Post by lucazade on 2011-09-02
> **garthecho said:**
> Well, here's glxgears from an old Maverick install I have on the same machine...



and here's Oneiric...



So, in Oneiric, performance is almost half what it used to be.


It's not clear in the screenshot, but I should state that in Oneiric glxgears starts out at about 8000fps, but then drops and stays at around 3-5000.  In Maverick I get a constant 8-10000fps.

i get more or less the same result, half of performance (at least from what glxgears says and it is not strictly a benchmark tool).
seems a regression, probably worth a bug report.

---

### Post by lucazade on 2011-09-03
> **lucazade said:**
> i get more or less the same result, half of performance (at least from what glxgears says and it is not strictly a benchmark tool).
seems a regression, probably worth a bug report.

attached screenshots of glxgears in oneiric and natty (nvidia 250gts)
In oneiric I get half of performances in 3D.
Same bad result also using an Intel gma500..

going to open a bug report.. if anyone else could try in both natty and oneiric and attach results in bug report would be nice.

this is the output when installing nvidia-current inOO, maybe it is related to the issue:
```
Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap», at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 7.
Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap», at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 7.
Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap», at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 7.
Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap», at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 7.
Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap», at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 7.
Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap», at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 7.
Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap», at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 7.
Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap», at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 7.
Selezionato il pacchetto patch.
(Lettura del database... 123075 file e directory attualmente installati.)
Estrazione di patch (da .../patch_2.6.1-2_i386.deb)...
Selezionato il pacchetto dkms.
Estrazione di dkms (da .../dkms_2.2.0.2-1ubuntu1_all.deb)...
Selezionato il pacchetto fakeroot.
Estrazione di fakeroot (da .../fakeroot_1.17-1_i386.deb)...
Selezionato il pacchetto nvidia-current.
Estrazione di nvidia-current (da .../nvidia-current_280.13-0ubuntu2_i386.deb)...
Selezionato il pacchetto python-central.
Estrazione di python-central (da .../python-central_0.6.17_all.deb)...
Selezionato il pacchetto screen-resolution-extra.
Estrazione di screen-resolution-extra (da .../screen-resolution-extra_0.14build2_all.deb)...
Selezionato il pacchetto nvidia-settings.
Estrazione di nvidia-settings (da .../nvidia-settings_280.13-0ubuntu2_i386.deb)...
Elaborazione dei trigger per man-db...
Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap», at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap», at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap», at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap», at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap», at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap», at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap», at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap», at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Configurazione di patch (2.6.1-2)...
Configurazione di dkms (2.2.0.2-1ubuntu1)...
Configurazione di fakeroot (1.17-1)...
update-alternatives: viene usato /usr/bin/fakeroot-sysv per fornire /usr/bin/fakeroot (fakeroot) in modalità automatica.
Configurazione di nvidia-current (280.13-0ubuntu2)...
update-alternatives: viene usato /usr/lib/nvidia-current/ld.so.conf per fornire /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in modalità automatica.
update-alternatives: attenzione: saltata la creazione di /usr/lib32/libOpenCL.so poiché il file /usr/lib32/nvidia-current/libOpenCL.so associato (del gruppo i386-linux-gnu_gl_conf) non esiste.
update-alternatives: attenzione: saltata la creazione di /usr/lib32/vdpau/libvdpau_nvidia.so.1 poiché il file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 associato (del gruppo i386-linux-gnu_gl_conf) non esiste.
update-alternatives: attenzione: saltata la creazione di /usr/lib32/libvdpau_nvidia.so poiché il file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so associato (del gruppo i386-linux-gnu_gl_conf) non esiste.
update-alternatives: viene usato /usr/lib/nvidia-current/alt_ld.so.conf per fornire /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in modalità automatica.
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-280.13 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-9-generic
Building for architecture i686
Building initial module for 3.0.0-9-generic
Done.

nvidia-current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-9-generic/updates/dkms/

depmod......

DKMS: install Completed.
Configurazione di python-central (0.6.17)...
Configurazione di screen-resolution-extra (0.14build2)...
Elaborazione dei trigger per python-central...
Configurazione di nvidia-settings (280.13-0ubuntu2)...
update-alternatives: viene usato /usr/lib/nvidia-settings/ld.so.conf per fornire /etc/ld.so.conf.d/nvidia_settings.conf (nvidia_settings_conf) in modalità automatica.
Elaborazione dei trigger per bamfdaemon...
Rebuilding /usr/share/applications/bamf.index...
Elaborazione dei trigger per gnome-menus...
Elaborazione dei trigger per initramfs-tools...
update-initramfs: Generating /boot/initrd.img-3.0.0-9-generic
```

NOTE: I tested these in Unity-2D with metacity compositor disabled in order to exclude and be sure the issue it is not related to compiz/unity/composite but to drivers/mesa/opengl/whatever

---

### Post by tghe-retford on 2011-09-03
> **sgage said:**
> I'm not seeing any screen tearing (Nvidia GeForce 8500 GT), and haven't in over 10 years of using various Nvidia cards. I wonder if it is just certain models combined with certain drivers. I think the first step would be to isolate the models affected. But I don't sense any "curse of Ubuntu's Nvidia users" in a general way.

> **VinDSL said:**
> I'm running a nVidia GeForce 7600GT in UbuOO beta 1 with nVidia 285.03 drivers.

It's working like a champ; even on fullscreen HD YouTube vids, e.g. no tearing, slowness, et cetera...
I don't think the problem is with the NVidia driver myself, using full screen VLC and Kega Fusion (desktop compositioning disabled) has no problem running at 60fps tear free, but I have found tearing occurs when two things are running:

- KWin - bad enough it seems to default to 30fps when running some applications, I also noticed tearing when in windowed mode. Turning off compositioning and it becomes tear free.
- Adobe Flash's official 64-bit beta player. Regardless of which browser you use and with KWin off. Nothing we can do there aside from raising a bug report and hoping Adobe fix it on their own accord.

People have also noticed problems using Compiz and with Nouveau. It makes you wonder..?

---

### Post by Wise Ferret on 2011-09-03
lucazade, can you give us a link to the bug report?

---

### Post by lucazade on 2011-09-03
> **Wise Ferret said:**
> lucazade, can you give us a link to the bug report?

see next post

---

### Post by lucazade on 2011-09-05
> **Wise Ferret said:**
> lucazade, can you give us a link to the bug report?

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/841636](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/841636)

---

### Post by karmila on 2011-09-05
And I can not open nvidia-settings :confused:
It is installed...
```
me@Oneiric:~$ dpkg --status nvidia-settings
Package: nvidia-settings
Status: install ok installed
Priority: optional
Section: contrib/x11
Installed-Size: 2152
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 280.13-0ubuntu2
Replaces: libxnvctrl-dev
Depends: screen-resolution-extra (>= 0.12), libc6 (>= 2.7), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.8.0), libpango1.0-0 (>= 1.14.0), libx11-6, libxext6, libxxf86vm1
Conflicts: libxnvctrl-dev
Description: Tool of configuring the NVIDIA graphics driver
 The nvidia-settings utility is a tool for configuring the NVIDIA
 Linux graphics driver.  It operates by communicating with the NVIDIA
 X driver, querying and updating state as appropriate.  This
 communication is done with the NV-CONTROL X extension.
 .
 Values such as brightness and gamma, XVideo attributes, temperature,
 and OpenGL settings can be queried and configured via nvidia-settings.
Original-Maintainer: Debian NVIDIA Maintainers <pkg-nvidia-devel@lists.alioth.debian.org>
```

---

### Post by VinDSL on 2011-09-05
> **karmila said:**
> And I can not open nvidia-settings :confused:
It is installed...
It's working here.

The only difference in the command line output is:

```
Version: 285.03-0ubuntu1~edgers~oneiric1
```

---

### Post by karmila on 2011-09-09
> **VinDSL said:**
> It's working here.

The only difference in the command line output is:

```
Version: 285.03-0ubuntu1~edgers~oneiric1
```

Latest update (from 280.13-0ubuntu2 to 280.13-0ubuntu3) solved the problem.
I can now open nvidia-settings :)

---

### Post by lucazade on 2011-09-16
the performance drop is no more present.. if anyone can confirm I can close this bug.
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/841636](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/841636)

---

