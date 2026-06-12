---
title: "Update/upgrade failure 12.04"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by Diggla on 2012-06-14
I am using Ubuntu 64bit, when I upgraded to 12.04 there was a problem in that it didn't complete correctly.

Now I cannot get the updates to install

I have tried several suggestions on the forums and have now got the point where I get this message

> installArchives() failed: 
Extract templates from packages: 5%%
Extract templates from packages: 11%%
Extract templates from packages: 17%%
Extract templates from packages: 23%%
Extract templates from packages: 29%%
Extract templates from packages: 35%%
Extract templates from packages: 41%%
Extract templates from packages: 47%%
Extract templates from packages: 53%%
Extract templates from packages: 59%%
Extract templates from packages: 65%%
Extract templates from packages: 71%%
Extract templates from packages: 77%%
Extract templates from packages: 83%%
Extract templates from packages: 89%%
Extract templates from packages: 95%%
Extract templates from packages: 100%%
Preconfiguring packages ...

Extract templates from packages: 5%%
Extract templates from packages: 11%%
Extract templates from packages: 17%%
Extract templates from packages: 23%%
Extract templates from packages: 29%%
Extract templates from packages: 35%%
Extract templates from packages: 41%%
Extract templates from packages: 47%%
Extract templates from packages: 53%%
Extract templates from packages: 59%%
Extract templates from packages: 65%%
Extract templates from packages: 71%%
Extract templates from packages: 77%%
Extract templates from packages: 83%%
Extract templates from packages: 89%%
Extract templates from packages: 95%%
Extract templates from packages: 100%%
Preconfiguring packages ...

Extract templates from packages: 5%%
Extract templates from packages: 11%%
Extract templates from packages: 17%%
Extract templates from packages: 23%%
Extract templates from packages: 29%%
Extract templates from packages: 35%%
Extract templates from packages: 41%%
Extract templates from packages: 47%%
Extract templates from packages: 53%%
Extract templates from packages: 59%%
Extract templates from packages: 65%%
Extract templates from packages: 71%%
Extract templates from packages: 77%%
Extract templates from packages: 83%%
Extract templates from packages: 89%%
Extract templates from packages: 95%%
Extract templates from packages: 100%%
Preconfiguring packages ...

Extract templates from packages: 5%%
Extract templates from packages: 11%%
Extract templates from packages: 17%%
Extract templates from packages: 23%%
Extract templates from packages: 29%%
Extract templates from packages: 35%%
Extract templates from packages: 41%%
Extract templates from packages: 47%%
Extract templates from packages: 53%%
Extract templates from packages: 59%%
Extract templates from packages: 65%%
Extract templates from packages: 71%%
Extract templates from packages: 77%%
Extract templates from packages: 83%%
Extract templates from packages: 89%%
Extract templates from packages: 95%%
Extract templates from packages: 100%%
Preconfiguring packages ...
dpkg: error: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)


There's probably an easy solution to this but I think I may have missed something or I'm not maybe not using the correct commands.

---

### Post by Diggla on 2012-06-21
After a bit more research I managed to solve my problem.

The error message I was getting was telling me that the "/var/lib/dpkg/available" file was missing. On investigation I found the file "/var/lib/dpkg/available-old" one thread I read suggested that this could be renamed to "/var/lib/dpkg/available" however I was unable to do this as the function was greyed out. I could copy the file and on doing so moved it to the desktop where I could rename it. When I then tried to move it back into the "/var/lib/dpkg/" folder I then got the "You are not the owner, so you can't change permissions" message.

I then found a suggestion of using the command "gksu nautilus". On using this in the terminal I was able to replace the file "/var/lib/dpkg/available"  and now I am able to install updates on my computer.

---

