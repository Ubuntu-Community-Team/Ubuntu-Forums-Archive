---
title: "Customized Boot Manager"
date: 2006-06-13
forum: Programming Talk
---

### Post by krypto_wizard on 2006-06-13
I have to create a small visual interface program called as Boot Manager which is customized accoring to the needs.

I have around 8 pc's and 2 linux boxes. One Linux box is always on and all other are closed in sleep state. 

I have to perform the following things:

1. Boot up all of them. I used Wake on LAN and wrote a small python script for that. It works fine.
2. To shutdown all pc's when the work is done. For this I installed an OpenSSH server for Windows in PC. When I send a command using ssh it shuts it down.


Now, I have to create a visual interface for such kind of small program.  

I have 2 questions
(i) How can we use operating system specific commands like ssh within the python program (ii) Which grphics library (wxPython or any other) would be the fastest with least learning curve to get this thing done.

Thanks

---

