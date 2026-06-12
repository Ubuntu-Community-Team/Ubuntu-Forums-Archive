---
title: "Nvidia gt 610 X Server"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by binaryperson on 2012-11-23
Hello everyone, I have just fresh installed Kubuntu 10.04 AMD64 LTS. I installed my video drivers, atleast I think I did, by typing:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
```
```
sudo apt-get update 
```
```
 sudo apt-get install nvidia-current
```

I tried running X Server but it says:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run nvidia-xconfig as root), and restart the X server.

My video card is Nvidia gt 610. Is it alright that I typed those three lines of code considering I have Kubuntu and not Ubuntu, or does it not make a difference?

---

### Post by binaryperson on 2012-11-24
Wow, almost 100 views and no one could tell me that it really is a simple as typing 

 ```
sudo nvidia-xconfig
```

and restarting the computer. 
Everything works fine now.

---

