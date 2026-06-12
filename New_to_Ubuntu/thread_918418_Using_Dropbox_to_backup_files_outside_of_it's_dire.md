---
title: "Using Dropbox to backup files outside of it's directory?"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by chris062689 on 2008-09-12
I want to keep my Dropbox in /home/chris/Dropbox.
But I want to back up folders such as.. /home/chris/School or /home/chris/Games.  Isn't it possible to create some kind of link (symlink?) to point to those folders for syncing?

---

### Post by chris062689 on 2008-09-12
[http://learn.clemsonlinux.org/wiki/Symlink](http://learn.clemsonlinux.org/wiki/Symlink)
Found the answer myself! :)
Works great.

---

### Post by caue.rego on 2008-11-25
you can also create that symlink using regular ubuntu file manager (nautilus) drag n' drop a file or a directory (folder, whatevah). just drag with middle mouse button (same as right button in windows) and choose link from the drop menu after releasing the button, or drag while holding CTRL+SHIFT, like in windows.

plus, i used a symlink in the default location (~/Dropbox) to be able to store my dropbox into my custom location (in a different partition), and it works great!

---

