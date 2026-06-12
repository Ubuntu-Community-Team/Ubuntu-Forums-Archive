---
title: "Gtk::FileChooserDialog"
date: 2010-05-26
forum: Programming Talk
---

### Post by tbastian on 2010-05-26
I'm writing a program that reads from a file while that file is being written to by another program. All those details are working, my issue is: When I try to select a file while another file in that directory is being modified, the path that my  Gtk::FileChooserDialog returns isn't what I clicked on in the first place!

Also, when I click on one file, I can't change my mind and select another file. I must press 'OK' or 'Cancel'

I don't have this issue under normal circumstances (eg, the file isn't being written to)

If I hardcode the filename (and its path) into my program, it opens and reads no problem.

---

### Post by alterpinguin on 2010-05-27
> **tbastian said:**
> I'm writing a program that reads from a file while that file is being written to by another program. All those details are working, my issue is: When I try to select a file while another file in that directory is being modified, the path that my  Gtk::FileChooserDialog returns isn't what I clicked on in the first place!

Also, when I click on one file, I can't change my mind and select another file. I must press 'OK' or 'Cancel'

I don't have this issue under normal circumstances (eg, the file isn't being written to)

If I hardcode the filename (and its path) into my program, it opens and reads no problem.

have already posted the problem:
> [http://ubuntuforums.org/showthread.php?t=1493666](http://ubuntuforums.org/showthread.php?t=1493666)

and workaround for python is to use the old fileselect-box (for me)

---

### Post by tbastian on 2010-05-27
Thanks for your help. There isn't a fileselection widget in gtkmm. I submitted a bug report, and hopefully they'll fix it.

---

