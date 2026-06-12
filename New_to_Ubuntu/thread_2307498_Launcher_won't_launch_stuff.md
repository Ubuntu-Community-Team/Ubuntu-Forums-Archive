---
title: "Launcher won't launch stuff"
date: 2015-12-25
forum: New to Ubuntu
---

### Post by BarePaw on 2015-12-25
I just switched up to Ubuntu 14.04. This is the first version I've used with the fancy desktop launcher thingy. For some reason Skype and Rhythmbox won't launch from the bar. I can get their icons to show up in the bar, but when I click on them, nothing happens. I can't even get Skype to come up at all from the search function. When I click on it there, it puts it in the launcher, but doesn't open the program. I can't log in or anything. Right clicking just gives me three options: "Skype" "Unlock from toolbar" or "Quit". Clicking on "Skype" does nothing. Right clicking on Rhythmbox gives me six options: Controls for play/paus/next/previous, "rhythmbox music player" and "unlock from toolbar". Clicking on "Rhythmbox music player" does nothing, though the play functions seem to work. Sure would be nice to see my playlist.

---

### Post by cwmoser on 2015-12-26
Is the target executable file's executable bit set?
If not do  **chmod  ugo+x  <filename>**

I often run into this issue.

---

