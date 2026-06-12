---
title: "other file managers"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by Zopiac on 2008-11-08
ive used Nautilus, Thunar, and Dolphin, but none of those are as minimalistic as i want (visually), which is just the window to show the folders and the titlebar; i dont want to have to see the 'file view etc' bar, just an area where the actual files/folders are (and perhaps a toggle-able sidebar)

anyone know of one? :P

---

### Post by tvtech on 2008-11-08
command line?

---

### Post by randy78 on 2008-11-08
Flux?

---

### Post by Zopiac on 2008-11-08
> **randy78 said:**
> Flux?

perhaps i should have said File Browser?

---

### Post by perlluver on 2008-11-08
Have you tried midnight commander?  From what I have heard it is pretty minimal.

---

### Post by whitethorn on 2008-11-08
you could pcmanfm it's available in the repositories.  Or you could also try Midnight Commander which is also available in synaptic.  There's even a guide explaining how to replace nautilus with pcman

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=692238](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=692238)

---

### Post by m_duck on 2008-11-09
Rox (or rox-filer) is pretty minimal. I think fiddling the preferences in nautilus you can also get that to be quite minimal as it is with a default debian install.

---

### Post by mojoman on 2008-11-09
[http://www.linux.com/articles/113952]("http://www.linux.com/articles/113952")

For lightweight I like pcmanfm or emelfm2. mc if you want a CLI option.

/mojoman

---

### Post by kerry_s on 2008-11-09
> **Zopiac said:**
> ive used Nautilus, Thunar, and Dolphin, but none of those are as minimalistic as i want (visually), which is just the window to show the folders and the titlebar; i dont want to have to see the 'file view etc' bar, just an area where the actual files/folders are (and perhaps a toggle-able sidebar)

anyone know of one? :P

you just described rox-filer.

---

### Post by Zopiac on 2008-11-09
> **kerry_s said:**
> you just described rox-filer.

no, that shows a menu bar. this is pretty much what i want, but , of course, it is an image edit:

---

### Post by kerry_s on 2008-11-09
> **Zopiac said:**
> no, that shows a menu bar. this is pretty much what i want, but , of course, it is an image edit:

i don't think there's a minimalistic filemanager with icons for that, i've been playing with a few, currently pcmanfm, which you might want to check out if you want simple and light.

---

### Post by Zopiac on 2008-11-09
the main thing is, i only want the folders and window border showing. if this is not possible, im fine with what ive got

---

### Post by kerry_s on 2008-11-09
> **Zopiac said:**
> the main thing is, i only want the folders and window border showing. if this is not possible, im fine with what ive got

sounds good, i'll let you know if i come across a filemanager with nothing but icons. :)

take a look at dfm, it's old and feels funny but has only icons. :)
[http://www.kaisersite.de/dfm/](http://www.kaisersite.de/dfm/)

it's in the repo's( sudo apt-get install dfm )

---

### Post by kerry_s on 2008-11-09
it's interesting, i only played with it a little bit in DSL linux.
make sure you read the man page.
also the path is wrong, the sample file is at /etc/X11/dfm
copy it to ~/.dfmext , then tweak it.

mine so far:

```
#filename match;iconfile;startcommand
#
core;/usr/share/dfm/icons/icon_core.xpm;ddd !0!
Makefile;/usr/share/dfm/icons/icon_makefile.xpm;xterm -e make --file=!0!
xterm;/usr/share/dfm/icons/icon_xterm.xpm;!0! -sb -sl 500 -fn 9x15
lpr;/usr/share/dfm/icons/icon_printer.xpm;!0!
leafpad;/usr/share/dfm/icons/icon_editor.xpm;!0!
*.exe;/usr/share/dfm/icons/icon_binary_ms.xpm;wine !0!
*.au;/usr/share/dfm/icons/icon_audio.xpm;cp !0! /dev/audio
*.wav;/usr/share/dfm/icons/icon_audio.xpm;totem !0!
*.mod;/usr/share/dfm/icons/icon_audio.xpm;totem !0!
*.s3m;/usr/share/dfm/icons/icon_audio.xpm;totem !0!
*.669;/usr/share/dfm/icons/icon_audio.xpm;totem !0!
*.xm;/usr/share/dfm/icons/icon_audio.xpm;totem !0!
*.mid;/usr/share/dfm/icons/icon_audio_midi.xpm;totem !0!
*.pdf;/usr/share/dfm/icons/icon_pdf.xpm;xpdf !0!
*.dip;/usr/share/dfm/icons/icon_phone.xpm;dip !0!
*.ps;/usr/share/dfm/icons/icon_ps.xpm;ghostview !0!
*.dvi;/usr/share/dfm/icons/icon_document_print.xpm;xdvi !0!
*.tex;/usr/share/dfm/icons/icon_document_tex.xpm;leafpad !0!
*.lyx;/usr/share/dfm/icons/icon_document_lyx.xpm;lyx !0!
*.txt;/usr/share/dfm/icons/icon_text.xpm;leafpad !0!
*.mov;/usr/share/dfm/icons/icon_video.xpm;totem +Sr +B +b +f !0!
*.avi;/usr/share/dfm/icons/icon_video.xpm;totem +Sr +B +b +f !0!
*.mpg;/usr/share/dfm/icons/icon_video.xpm;totem +Sr +B +b +f !0!
*.mp?;/usr/share/dfm/icons/icon_audio.xpm;totem !0!
*.fli;/usr/share/dfm/icons/icon_video.xpm;totem +Sr +B +b +f !0!
*.flc;/usr/share/dfm/icons/icon_video.xpm;totem +Sr +B +b +f !0!
*.htm;/usr/share/dfm/icons/icon_html.xpm;iceweasel !0!
*.html;/usr/share/dfm/icons/icon_html.xpm;iceweasel !0!
*.c;/usr/share/dfm/icons/icon_c.xpm;leafpad !0!
*.cc;/usr/share/dfm/icons/icon_cc.xpm;leafpad !0!
*.c++;/usr/share/dfm/icons/icon_cc.xpm;leafpad !0!
*.C;/usr/share/dfm/icons/icon_cc.xpm;leafpad !0!
*.h;/usr/share/dfm/icons/icon_h.xpm;leafpad !0!
*.o;/usr/share/dfm/icons/icon_o.xpm;leafpad !0!
*.a;/usr/share/dfm/icons/icon_a.xpm;leafpad !0!
*.png;/usr/share/dfm/icons/icon_picture.xpm;feh !0!
*.gif;/usr/share/dfm/icons/icon_picture.xpm;feh !0!
*.jpg;/usr/share/dfm/icons/icon_picture.xpm;feh !0!
*.bmp;/usr/share/dfm/icons/icon_picture.xpm;feh !0!
*.ppm;/usr/share/dfm/icons/icon_picture.xpm;feh !0!
*.pgm;/usr/share/dfm/icons/icon_picture.xpm;feh !0!
*.tga;/usr/share/dfm/icons/icon_picture.xpm;feh !0!
*.pbm;/usr/share/dfm/icons/icon_bitmap.xpm;feh !0!
*.tif;/usr/share/dfm/icons/icon_picture.xpm;feh !0!
*.tiff;/usr/share/dfm/icons/icon_picture.xpm;feh !0!
*.xpm;/usr/share/dfm/icons/icon_picture.xpm;feh !0!
*.xbm;/usr/share/dfm/icons/icon_bitmap.xpm;feh !0!
*.fig;/usr/share/dfm/icons/icon_fig.xpm;xfig !0!
*.tar*;/usr/share/dfm/icons/icon_archive.xpm;xtar !0!
*.tgz;/usr/share/dfm/icons/icon_archive.xpm;xtar !0!
*.taz;/usr/share/dfm/icons/icon_archive.xpm;xtar !0!
*.gz;/usr/share/dfm/icons/icon_gzip.xpm;xterm -e zless !0!
Trashcan/;/usr/share/dfm/icons/icon_folder_trashcan.xpm;dfm !0! -detail
.linktohomedir/;/usr/share/dfm/icons/icon_folder.xpm;dfm !0!
.linktorootdir/;/usr/share/dfm/icons/icon_folder.xpm;dfm !0! 
*/;/usr/share/dfm/icons/icon_folder.xpm;dfm !0!
.*;/usr/share/dfm/icons/icon_settings.xpm;leafpad !0!
*;/usr/share/dfm/icons/icon_file.xpm;leafpad !0!
/usr/share/dfm/icons/icon_binary.xpm;!0!

```

---

### Post by kerry_s on 2008-11-10
hey you still there?
have you tried dfm?
do you need help with it?

i'm pretty much done with it and i'm getting ready to move on, later i'm not going to remember, so if you need help, let me know quick.

---

### Post by Mark76 on 2008-12-12
> **Zopiac said:**
> no, that shows a menu bar. this is pretty much what i want, but , of course, it is an image edit:


Maybe like this?

---

### Post by bobotoes on 2008-12-31
I have not used nautilus in a while. I may get the exact option description wrong. In preferences, you can deselect something like "Open New Windows in Browser Mode." This will give the minimal look I think you're searching for. I thought it was annoying to have a new window open up every time you open a folder. Maybe there is another setting for this. hth

---

