---
title: "Evolution starts up on Email that causes it to lock up"
date: 2014-01-16
forum: New to Ubuntu
---

### Post by cwmoser on 2014-01-16
I have Email in my Junk Folder that causes Evolution to freeze.
When I force quit and then restart Evolution, it goes to that email and freezes.

How can I force Evolution to start up in something like a "safe mode"?

Carl

---

### Post by cwmoser on 2014-01-16
Found the solution.
I was so focused on the GUI that I forgot that Evolution could be run from the command line.
Another case of "senior-itis" I guess:-)

$  evolution  --help

This let me start Evolution with the mail contents preview turned off:
$ evolution --disable-preview

---

