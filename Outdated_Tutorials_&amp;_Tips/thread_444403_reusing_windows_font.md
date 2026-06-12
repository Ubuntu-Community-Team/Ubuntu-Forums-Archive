---
title: "reusing windows font"
date: 2007-05-15
forum: Outdated Tutorials &amp; Tips
---

### Post by vanozky on 2007-05-15
You may do this when you have font from windows that located on c:\windows\fonts or you may
download it from various place over the internet.

note 1. on console you may write 
sudo nautilus

note 2. copy windows font to /usr/share/fonts/Windows

note 3. change your xorg configuration file with your nautilus (gedit) 
etc/X11/xorg.conf 

in my ubuntus appear like this one :

Section "Files"
   FontPath   "/usr/share/fonts/Windows"
   FontPath   "/usr/share/fonts/X11/misc"
   FontPath   "/usr/share/fonts/X11/cyrillic"
   FontPath   "/usr/share/fonts/X11/100dpi/:unscaled"
   FontPath   "/usr/share/fonts/X11/75dpi/:unscaled"
   FontPath   "/usr/share/fonts/X11/Type1"
   FontPath   "/usr/share/fonts/X11/100dpi"
   FontPath   "/usr/share/fonts/X11/75dpi"
   # path to defoma fonts
   FontPath   "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

note 4. restart your X windows by pressing ctrl + alt + backspace

note 5. try the new installed font from your openoffice or others.


_vanozky_
./ hmmm... ikatlah ilmu dengan menulisnya..

---

