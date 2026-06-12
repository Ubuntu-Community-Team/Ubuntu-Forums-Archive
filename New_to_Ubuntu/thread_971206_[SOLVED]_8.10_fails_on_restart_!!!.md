---
title: "[SOLVED] 8.10 fails on restart !!!"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by simontaylor on 2008-11-04
Dear Ub-users,

performed a full upgrade from 8.04 from site to 8.10. Got to restart and received this message - among others (something about Red Hat) -

> CCS [4394] unable to add membership

and later in the chain:

> cman_admin_init error 2

this was repeated with variations. Then:

> fence_tool: waiting for cman to start
fence_tool: waiting for cman to start
fence_tool: waiting for cman to start
CCS [4394]: [CCS ] Unable to connect to cluster infrastructure after 30 seconds

fence_tool: waiting for cman to start
fence_tool: waiting for cman to start
fence_tool: waiting for cman to start
CCS [4394]: [CCS ] Unable to connect to cluster infrastructure after 60 seconds

etc.

Tried restarting in recovery mode, basically working my way down the list of options: generic / recovery / generic etc. - all with same result

> waiting for cman

Now, waiting for Godot, I understand but > cman?

Please help me. I'm having to write this on the fly on XP, not my preferred way to fly.

Yours,
desperate for ubuntu,

simon taylor

---

### Post by simontaylor on 2008-11-04
cube3x3 writes in an earlier thread:

> 1. Get a Live CD of Ubuntu 8.10 (I think any linux live CD should work though)
2. Boot with that live cd
3. After booting, mount your computer's root partition to /mnt/repair using following command (assuming your root partition is in /dev/sda1

Code:
sudo mount /dev/sda1 /mnt/repairIf you have separate /home partition then mount it also to /mnt/repair/home
4. Next give following command

Code:
sudo chroot /mnt/repair
5. Then change to your computer user using su [your_username]
6. Then remove the cman and libfence3 packages using,

Code:
sudo apt-get remove cman libfence3
7. Then 'exit' and reboot.
8. Enjoy Intrepid

how do I know if sda1 is right for me? 
and + I only have feisty on disc ---- since hardy refused to burn discs for me! (Sounds a bit like CSS is coming back to haunt the machine.)

Please help.

Is there an easier fix than Cube3x3's

---

### Post by simontaylor on 2008-11-04
tried cube3x3's fix. Did not work: returned this: 

> mount point /mnt/repair does not exist

Please help.

Simon

---

### Post by simontaylor on 2008-11-04
anyone?

advice would be greatly appreciated.

---

### Post by simontaylor on 2008-11-04
?

---

### Post by poopteam on 2008-11-04
If the mount point doesn't exist all you have to do is create the directory before you execute the mount command

$sudo mkdir /mnt/dirname

Hope that helps.

---

### Post by simontaylor on 2008-11-05
Thanks for the advice. However I get the same response:

mount: mount point /mnt/repair does not exist

still DESPERATE.

simon

---

### Post by simontaylor on 2008-11-09
see [http://ubuntuforums.org/showthread.php?t=959822&highlight=cman](http://ubuntuforums.org/showthread.php?t=959822&highlight=cman)

---

### Post by mariusandreus on 2008-11-10
I upgraded to 8.10 and had the same problem. You don't actually need to wait for 5 min like in the cube3x3 thread to get a prompt, you just do 
Ctrl+Alt+Del 
and get an options window, there, choose the one that says drop to root prompt or something like it and just type: 
sudo apt-get remove cman libfence3 (like cube3x3 suggested)  
and you're good to go.

---

