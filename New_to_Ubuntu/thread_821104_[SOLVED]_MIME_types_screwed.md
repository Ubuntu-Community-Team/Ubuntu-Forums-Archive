---
title: "[SOLVED] MIME types screwed"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Gripp on 2008-06-06
yes, plural.  if i try to open a zip or other compressed file type, it says that there is no application associated with it.  if i try to open a PDF, one that i have opened before, it tells me the same.  even more than that, if i try to open any PDF file using Document Viewer it tells me that it cant read it. even the ones that i have opened before.  .odt for open office - screwed. 

this happened very randomly.  I just booted up and...
the only thing that i have done with computer lately is install emacs just to try and learn.  cant think of anything that may have been the cuase (other than updates of coarse)
please help

---

### Post by forger on 2008-06-06
open up a gnome terminal window and execute:
```

rm -rf $HOME/.local/share/mime/
sudo update-mime-database /usr/share/mime/
gtk-update-icon-cache /usr/share/icons/Human/

```

It's going to revert to the default mime types, as well as their icons. A log out & log in would be good I think. You might have to re-link some custom file types (not sure).

---

### Post by Gripp on 2008-06-06
i think i posted too soon... i was running update in an attempt to fix while typing the last post and after the post i opened "kcmshell filetypes" to see if i couldn't fix things manually.. and it appears to have fixed it instantly.  not sure which of the two solved it... but nonetheless it is solved.

soo, thanks to me! eh

edit: and thanks to you too there forger.  just for being on top of things :)

---

### Post by forger on 2008-06-06
ok

---

