---
title: "Scanning Problem - HP PSC 1510 - XSANE, WINE??"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by Journeyman1962 on 2011-12-07
Hello All,

I need some help with scanning software.

The HP PSC 1510 comes with its own (windows-based) software, which is very good. I'm trying to avoid rebooting in windows every time I have more than two or three pages to scan.

Essentially, the HP software allows me to set up resolution, file type, and save-to-directory values which are retained. it scans, lets me crop and then accept the selected image, saves it to file and names it sequentially and automatically, and then asks if I want to scan another page.

I've tried Xsane, but I can't see a way round having to specify filename and target folder every time I save a scan. It's very inefficient on time.

I've tried to access the HP software via Wine - but it doesn't work by accessing the files in the windows partition, or by trying to set it up (in the "wine" folder) from the installation CD (I still have the original). I can't find a downloadable version to set up in the wine environment. The HP site offers only drivers for Linux (I've already got those).

So, in short, I need to be able either to:

find, install and run the HP software under wine, or
work out how to set up xsane so it works like the HP software described above.

I've been looking all over the place and failed to find a solution.
Any help would be extremely gratefully received.

Tim

---

### Post by tjoff on 2011-12-07
According to the xsane manual page:

 >       $HOME/.sane/xsane/xsane.rc
              This  files  holds  the  user  preferences.  Normally, this file
              should not be manipulated directly.  Instead,  the  user  should
              customize the program through the "Preferences" menu.

and

 >       When the flag --force-filename or -N is given then xsane reads the next
       option  as  default  image  filename.  The name should be of the format
       "name-###.ext". The selection  box  for  filenames  is  disabled.  This
       option  normally should be used with the option --no-mode-selection and
       --save.

I have not tried any of this before, but it sounds like this could help you do at least some of what you want.

---

### Post by Journeyman1962 on 2011-12-07
Thanks Tjoff,

You're right - maybe I just go straight to the last resort - read the bloody manual! :)

Cheers
Tim

---

### Post by Journeyman1962 on 2011-12-07
All done. Thanks very much

---

