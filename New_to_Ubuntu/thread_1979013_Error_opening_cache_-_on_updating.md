---
title: "Error opening cache - on updating"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by vinod407 on 2012-05-12
This is the error which I am getting while opening the Synaptic Package Manager.
Upon reloading/updating the package manager, it was downloading the updates but suddenly this error came and it closed down.
Now I can't open the synaptic manager, as this error message appears always.

Encountered a section with no package header, problem with mergelist/var/lib/apt/lists


screen shot attached.

Please help.

---

### Post by Rubi1200 on 2012-05-13
Hi and welcome to the forums :-)

To open the terminal use Ctrl+Alt+T and run the following commands:
    
```
      sudo rm /var/lib/apt/lists/* -vf 
``````
      sudo apt-get update 
```the first one removes corrupted package lists, the second one refreshes them.

---

### Post by vinod407 on 2012-05-14
Hi Rubi1200,

Executed the command. Now I can open the package manager.
Thanks a ton, 

Vinod

---

### Post by Rubi1200 on 2012-05-14
You are more than welcome :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

