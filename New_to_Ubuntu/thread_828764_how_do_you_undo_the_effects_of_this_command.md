---
title: "how do you undo the effects of this command"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by balagosa on 2008-06-14
```
sudo update-pciids
```

need help, i think this code messed up something in my laptop.

---

### Post by ajmorris on 2008-06-14
hi there,
i really cant see this doing anything detrimental to your system... all this command does it identify your devices, incase you do a hardware change or something...
I doubt you could reverse the effects of this...

AJ

---

### Post by dracayr on 2008-06-14
I agree. What exactly is messed up?

dracayr

---

### Post by ukripper on 2008-06-14
Can you explain what has been gone wrong?

---

### Post by balagosa on 2008-06-14
hmm...it is a bit complicated.

you see, back on my first install of hardy, i worked on my wifi. and i got it working just fine with the hep of ndiswrapper. Specifically with the driver (net5211.inf). after a few days i did ```
sudo update-pciids
```(by this time i didnt blame this code for the mishap) and **voila,** after hours of executing it is just then that i noticed my wifi wasnt working anymore. for weeks i have been trying to make it work again. but to no avail, it **all** failed (by all i mean every suggestion that i could think of, will be enumerating some that i remember down below). so i turned to my last resort which was to reinstall hardy. Re-installation came, my first commands to do were update my ids via ```
sudo update-usbids
sudo update-pciids
```. Those two are the first commands i did because i wanted my PCI and USBs to be updated (i have a webcam and that is the reason why i wanted to update). I tried to put everything back that i had with my old Hardy. Then came again the Wifi installation, and i loaded with the same driver which is (net5211.inf). After doing the process, i was expecting my wifi to be okay already. But it still wasnt, this is when i thought it was because of the update on PCIs. Again, I was back on the internet researching for a solution my WiFi problem. I stumbled upon a thread where the OP suggested to use net5416.inf for my ndiswrapper driver instead of net5211.inf. So i tried his suggestion and to my amazement, it **WORKED.** 

To conclude, I am not sure if the update on my PCIs cause it. I was just theorizing that it might be the one that cause it due to my **experience**.

Phew! that was months of explanation all rolled up to one thread.

**Alternatives i did**
```
1) Reinstalled ndiswrapper for 32bit architectures
2) Installed ndiswrapper for 64bit architecture
3) Reinstalled ndiswrapper for 64bit architecture
4) Tried Madwifi for 32bit architecture
5) Reinstalled Madwifi to their latest patch which was the r3366 patch
```

---

### Post by ajmorris on 2008-06-14
the change in it not working for that version of the windows driver could have been because of a change in Ndiswrapper versions, or kernel version, i doubt update-pciids did anything to it, but, im glad your wireless works now :)

AJ

---

