---
title: "64-bit Hybrid graphic card"
date: 2012-09-10
forum: New to Ubuntu
---

### Post by AmjAdAsh2Ar on 2012-09-10
[SIZE="4"]People I really need a similar solution to this post [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)
... for ATI Radeon 5xxx/intel hybrid graphic cards .. my discrete card is Ati Radeon 5650m (ubuntu 12.04, 64-bit arch.)[/SIZE]


[SIZE="3"]that post was very useful to many people I know[/SIZE]
**_[SIZE="3"]PLEASE[/SIZE]_**

---

### Post by LowSky on 2012-09-11
That post should work for you if your system supports this function.

---

### Post by AmjAdAsh2Ar on 2012-10-15
I still not got a solution !! I'm running on unity 2-D .. this sucks :(

---

### Post by QIII on 2012-10-15
Unfortunately, there is no solution like that for 5xxx series graphics.  You will either have to use BIOS/EFI to disable one or the other; or use the open source Radeon driver and vgaswitcheroo.

---

### Post by AmjAdAsh2Ar on 2012-10-15
> **QIII said:**
> Unfortunately, there is no solution like that for 5xxx series graphics.  You will either have to use BIOS/EFI to disable one or the other; or use the open source Radeon driver and vgaswitcheroo.

I want a step-by-step solution .. whatever it was .. can u do that ?
I just want Unity 3-d to work :(

---

### Post by AmjAdAsh2Ar on 2012-10-16
:( :( :(

---

### Post by QIII on 2012-10-17
I'm on the road right now using my cell phone, so this will be brief.

If available, the instructions for how to enable/disable the discrete or integrated graphics will vary depending on the model/manufacturer of your motherboard. I can't help you there.

You need to remove the fglrx driver and use the open source Radeon driver if you want to use vgaswitcheroo.

If you installed the fglrx driver through the repo, do the following:

```
sudo apt-get purge fglrx fglrx-amdcccle
```If you installed using the instructions from the AMD website, do:

```
sudo aticonfig --uninstall
```or

```
sudo amdconfig --uninstall
```Then, look at the community hybrid graphics wiki [here.]("https://help.ubuntu.com/community/HybridGraphics")

---

### Post by AmjAdAsh2Ar on 2012-10-17
thanks for the quick reply. Unfortunately after doing the first code .. the second two .. didn't work ,, neither the first ones from  the community hybrid graphics wiki

```
amjad@amjad-HP-PC:~$ sudo aticonfig --uninstall
sudo: aticonfig: command not found
amjad@amjad-HP-PC:~$ sudo amdconfig --uninstall
sudo: amdconfig: command not found

amjad@amjad-HP-PC:~$ grep -i switcheroo /boot/config-2.6.*
grep: /boot/config-2.6.*: No such file or directory
amjad@amjad-HP-PC:~$ ls -l /sys/kernel/debug/vgaswitcheroo/switch
ls: cannot access /sys/kernel/debug/vgaswitcheroo/switch: Permission denied

```
What to do now ?

---

### Post by QIII on 2012-10-17
The second and third commands for uninstalling would be expected to fail if the first had worked.  So don't worry about that.

It looks like the wiki is outdated and needs to be updated for the current version.  Unfortunately, as I said, I am limited to my cell phone and can't give you an updated directory without looking.  

vgaswitcheroo should be included by default in your kernel if you are using Precise, I believe.  If you could post your kernel version, someone may be able to help you adjust the commands.

---

