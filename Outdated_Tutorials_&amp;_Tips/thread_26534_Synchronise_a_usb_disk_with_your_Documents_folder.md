---
title: "Synchronise a usb disk with your Documents folder"
date: 2005-04-13
forum: Outdated Tutorials &amp; Tips
---

### Post by adrian440 on 2005-04-13
Here's a one-line script you can use in a custom application launcher on your panel. Paste the following command into the 'command' space. It uses zenity for visual feedback, and assumes your usb stick is already mounted on /media/sda1. The star of the show, of course, is rsync:

rsync -rtvz --stats /media/usbdisk/Documents/ `echo $HOME`/Documents/ | zenity --text-info --width=600 --height=600 --title="Rsync Output"

To have your documents folder synced to usb disk, just swap the source & destination:

rsync -rtvz --stats `echo $HOME`/Documents/ /media/usbdisk/Documents/ | zenity --text-info --width=600 --height=600 --title="Rsync Output"

So that's two launchers you can use to organise your documents, with just one catch. If you delete a file in your documents directory (or a subdirectory thereof), you may find it turn up again there. To solve this, if you delete a file, delete it from both your usb disk and your documents foler.

---

### Post by kuleali on 2005-04-13
Nice!

---

### Post by razaza on 2005-04-13
[QUOTE=adrian440]If you delete a file in your documents directory (or a subdirectory thereof), you may find it turn up again there. To solve this, if you delete a file, delete it from both your usb disk and your documents foler.[/QUOTE]

Or use the --delete option. From the manpage:

       --delete
              This tells rsync to delete any files on the receiving side  that
              aren’t  on  the  sending  side.    Files  that are excluded from
              transfer  are  excluded  from  being  deleted  unless  you   use
              --delete-excluded.

              This  option  has  no  effect  if  directory  recursion  is  not
              selected.

              This option can be dangerous if used incorrectly!  It is a  very
              good idea to run first using the dry run option (-n) to see what
              files would be deleted  to  make  sure  important  files  aren’t
              listed.

              If  the sending side detects any I/O errors then the deletion of
              any files at the destination  will  be  automatically  disabled.
              This  is  to  prevent temporary filesystem failures (such as NFS
              errors) on the sending side causing a massive deletion of  files
              on   the   destination.    You   can   override  this  with  the
              --ignore-errors option.

---

### Post by z0mbix on 2005-06-16
Or if you wanted to keep both dirs in sync, use unison:

[http://www.zombix.org/?page_id=68](http://www.zombix.org/?page_id=68)

---

### Post by pdk001 on 2005-06-16
thank you for the tip

---

### Post by guyomarj on 2005-10-25
Excellent... Unison works perfect.

Maybe you could turn this thread (rsync and unison way) into an HOW-TO on the current Breezy "Customization Tips & Tricks" forum.

---

### Post by TuxDaddy on 2005-12-18
i could get this to work at all.  my usb drive functions but i dont know what it is mounted as.

---

### Post by guyomarj on 2005-12-18
[QUOTE=TuxDaddy]i could get this to work at all.  my usb drive functions but i dont know what it is mounted as.[/QUOTE]


Look in /media. For me, either on Gnome or KDE, it is mounted as /media/usbdisk

---

