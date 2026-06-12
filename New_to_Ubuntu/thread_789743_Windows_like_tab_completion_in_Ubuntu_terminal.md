---
title: "Windows like tab completion in Ubuntu terminal"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by nilzee on 2008-05-10
Hi,

Is there any way that i can modify the bash settings (which file are they in?) to get windows like tab completion? For example in the windows terminal if you type 'd' it will display desktop and any other folders which starts with either 'd' or 'D'.

In the Ubuntu terminal typing 'd' wouldn't get anything. It has to be 'D'. Is there any way to get around this? Or is it how the way Ubuntu has designed the command line... Thanks in advance for any help. :D

Nilu

---

### Post by halitech on 2008-05-10
Ubuntu (and all *nix systems) are case sensitive so Desktop is not the same as desktop. I think I heard about a way of setting up aliases for programs but I don't think there is anyway of having D and d both work the same

---

### Post by sdennie on 2008-05-10
If you create a file called ~/.inputrc and add the following to it, it should ignore case in tab completion.

```

set completion-ignore-case On 

```

Edit:
You'll have to exit your terminal and start a new one for the change to take work.

---

