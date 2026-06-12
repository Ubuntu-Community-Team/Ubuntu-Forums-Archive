---
title: "Grub Screen, wrong Resolution"
date: 2014-05-03
forum: New to Ubuntu
---

### Post by Quarkrad on 2014-05-03
Just installed burg on 12.04 and at opening screen the text was too large so I pressed F3 and changed the resolution.  Problem is monitor cannot support this res so on further boots the grub screen does not display - the monitor just says it cannot support this res.  I reinstalled burg via SuperBootManager but the resolution is still set to the wrong setting.  Is there a config folder somewhere that holds the resolution setting that did not get over written when I reinstalled?  (This machine dual boots so although there is no grub screen the pc does eventually boot to Ubuntu but there is now no option (visible grub/burg screen) to boot to the other os.  Thanks.

---

### Post by oldfred on 2014-05-03
Do not know about burg.

 From a grub command line to see available settings pressing <c> & escape to get back to menu
vbeinfo

      
 Details on settings in /etc/default/grub
 info -f grub -n 'Simple configuration'
> `GRUB_GFXMODE'
     Set the resolution used on the `gfxterm' graphical terminal.  Note
     that you can only use modes which your graphics card supports via
     VESA BIOS Extensions (VBE), so for example native LCD panel
     resolutions may not be available.  The default is `auto', which
     tries to select a preferred resolution.  *Note gfxmode::.


 Changing grub to 640x480 eliminates Windows screen boot issue
[http://ubuntuforums.org/showthread.php?t=2169115](http://ubuntuforums.org/showthread.php?t=2169115)
[http://askubuntu.com/questions/54067/how-do-i-safely-change-grub2-screen-resolution](http://askubuntu.com/questions/54067/how-do-i-safely-change-grub2-screen-resolution)
vga=xxx is a deprecated boot option
Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1024x768
replace "set gfxmode=auto" by "set gfxmode=1366x768"

---

### Post by Quarkrad on 2014-05-03
Thank you - that helped me solve the probelm.  Having sorted you can also do via Grub Customizer - using the Appearance Settings tab.  Uncheck the Custom Resolution tab.

---

