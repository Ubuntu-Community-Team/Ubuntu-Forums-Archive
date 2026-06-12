---
title: "how do i install a patch to module"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by muted1987 on 2008-11-16
hey all i have found some patchs to apply to gspca to hopefully get my webcam working can anyone tell me how to do it correctly please. thanks in advance

---

### Post by unutbu on 2008-11-16
I don't have gspca, but after watching this video ([http://www.linuxjournal.com/video/get-your-webcam-working-gspca](http://www.linuxjournal.com/video/get-your-webcam-working-gspca))
I think I understand the general steps:
[list]
[*]Install the build-essential package. It is in the official repositories. This package will draw in tools you'll need to compile other programs.
[*]Download the gspca source code. The video shows how to do this. You might want to google around to see if there is a newer version however.
[*]Put the patch file either in the directory above the gspca source or at the top level of the source. You need to look inside the patch file to determine this. Then read 
[http://www.cpqlinux.com/patch.html](http://www.cpqlinux.com/patch.html)
to determine the right command. If you are unsure, post the patch file, or a url to the patch file.
[*]After you've successful run the patch command,
you should be able to follow the rest of the instructions as shown in the video.
[*]Note that other Linux distros use "su" to gain a root shell. Ubuntu uses "sudo -i" to gain a root shell.
[/list]

---

### Post by muted1987 on 2008-11-16
ok so that shows howto instal gspca but the patching part for it is ruybbish

i have been trying to use the patch -p0 command but it isnt working

---

