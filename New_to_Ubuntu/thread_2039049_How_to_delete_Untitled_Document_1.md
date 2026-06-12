---
title: "How to delete Untitled Document 1"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by Hadaka on 2012-08-08
Hi, I was in the middle of writing a script in gksudo gedit when a lightning
strike reset the power. and somehow i ended up with a file named
Untitled Document 1, or its possible i invoked gksudo gedit without including
a file name and the power hit added to a bad situation. The Untitled Document 1
file is in my home directory and it wont delete with ...sudo rm... because of the
3 field spacing in the title Untitled...Document...1    
I know there is a way to delete the spaces but i dont know how...to use the 
slash whatever in the command. I am also getting this error when i use gksudo gedit

(gksudo:1903): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:1905): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.19TUIW': No such file or directory

thanks to anyone that can guide me to fix this.

---

### Post by mikewhatever on 2012-08-08
sudo rm "Untitled Document 1"

or 

sudo rm Untitled\ Document\ 1

or

sudo rm Untit #...and hit Tab key to autocomplete

---

### Post by Hadaka on 2012-08-08
Thanks Mikewhatever, I had already tried both those commands and
it told me to go pound sand. "sorry file doesn't exist"    So I got out my
digital baseball bat and beat it into submission with.

```
sudo rm -f "Untitled Document 1" 
```->   -f option being "force" and that did the trick.

I'm going to mark this thread SOLVED even though i still get the error
codes when i access gksudo gedit.  It's the middle of the night here and
i doubt i will get any help with the error messages.  I'll post a new thread
later for that issue if i cant get it fixed with more research.
thanks again for responding

---

