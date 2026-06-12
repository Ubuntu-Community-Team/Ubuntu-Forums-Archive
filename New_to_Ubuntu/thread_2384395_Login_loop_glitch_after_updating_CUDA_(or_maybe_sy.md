---
title: "Login loop glitch after updating CUDA (or maybe system update). (16.04 Ubuntu)"
date: 2018-02-06
forum: New to Ubuntu
---

### Post by saya18 on 2018-02-06
Hi guys.   I was having trouble getting Tensorflow running due to a missing cuda file, and the folks in this thread help me solve the problem.  [https://ubuntuforums.org/showthread.php?t=2383261&page=2](https://ubuntuforums.org/showthread.php?t=2383261&page=2)    Bascially I needed to run this file:      ```
  sudo apt-get install libcuda1-340 
```     Having thought everything was okay for the time being, I didn't restart my computer for a few days.    However after restarting, I'm getting this weird login bug. Meaning, the login screen shows up, and then after logging in, the screen will turn black for a few seconds, and then the login screen will return.  This seems to be common bug, via the Nvida forums but I'm not getting any help there.    Despite not being able to login via Unity,  I can enter tty1 from the console so I can enter commands via the tty1 terminal.   So far I tried:( from the tty1 console):   ```
  nvidia-bug-report
```   I get something like:       ```
 modprobe:libkmod/libkmod-module"c:832 kmod_module Error   could not find module by name = 'Nvidia_340'     modprobe: Error could not insert 'nvidia-340' Unknown Symbol      modprobe: Error could not find module by name = 'Nvidia_340'      modprobe: Error could not insert 'nvidia-340'      Complete:    
```    Nvidia-smi doesn't seem to work anymore as well  ```
  NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver  What should I do? I just want to install CUDA and my graphics card drivers. 
```   Now, I'm not exactly sure what happened. It could be a system update that took effect after restarting?   This was my graphics card driver info (prior to the restart):   ```
 ------------------------------------------------------+                        | NVIDIA-SMI 340.104    Driver Version: 340.104        |                        |-------------------------------+----------------------+----------------------+ | GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC | | Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. | |===============================+======================+======================| |   0  GeForce GTX 260     Off  | 0000:01:00.0     N/A |                  N/A | | 40%   46C   P12    N/A /  N/A |    226MiB /   895MiB |     N/A      Default | +-------------------------------+----------------------+----------------------+      +-----------------------------------------------------------------------------+     | Compute processes:                                               GPU Memory |     |  GPU       PID  Process name                                     Usage      |     |=============================================================================|     |    0            Not Supported    
```       Before purging the nvida drivers, is there a way to get back to Unity and maybe switch drivers (under Software and Updates --  I think)   If I'm not mistaken I would be able to try out different drivers there, and see which ones are safe.     Reading around someone suggested to do this:    ```
    sudo mv ~/.Xauthority ~/.Xauthority.backup  sudo service lightdm restart"       
```    to get back a login screen?Is this okay to do?   Thank you    PS: Did the formatting of this site change? I don't see the [CODE] option and my line breaks don't seem to be working.

---

### Post by saya18 on 2018-02-25
I'm still stuck at this problem. I'm not exactly sure how to proceed. Thank you.

---

