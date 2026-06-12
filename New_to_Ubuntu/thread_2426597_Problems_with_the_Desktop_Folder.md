---
title: "Problems with the Desktop Folder"
date: 2019-09-11
forum: New to Ubuntu
---

### Post by hk42 on 2019-09-11
Hi
In order of :
Saving diskspace
Keeping them up to date on various machines and OS's.
I replaced some Desktop files by a symlink to them on my NAS.
Mainly html,txt and m3u.
On the screen they kept their name  and default icon  fine!
But if I click on them the associated program doesn't launch any more.
If I open the menu and choose the same program in the "open with other application"  option it works.

---

### Post by kalinkitechukat on 2019-09-11
The issue occurs because multimedia programs are not associated by default for opening symlinks.

---

### Post by SeijiSensei on 2019-09-11
If you can group the files into one or a few directories, you can create a symlink to the directory rather than to the individual files.  For instance, the $HOME/Downloads directory on all my machines is symlinked to the one on my server so all downloaded files go to the same location.  So in your case, I'd make $HOME/Desktop point to a directory on the NAS.

---

### Post by hk42 on 2019-09-11
Thanks 
So it seems I have not broken anything Good.
My Download directories are already linked to one on the NAS.
Inspired by your answers I tested choosing XFCE as window manager and the problem is not there.
May be Gnome is not the best for me but sure it looks beautiful.

---

