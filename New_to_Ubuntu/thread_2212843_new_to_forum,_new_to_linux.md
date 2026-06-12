---
title: "new to forum, new to linux"
date: 2014-03-23
forum: New to Ubuntu
---

### Post by chris196 on 2014-03-23
Hello all  
I'm new to linux. I had some success with my hackintosh running 10.6.8 on my hp mini 110-3000 but i still found it laggy and had video issues. I wanted to try linux on this netbook with a ssd and see if there could be improvements on it.
I havent got very far and am already stuck. I got 12.04 live iso and used unetbootin to use a bootable usb. I have no windows os anymore so all of this is from a older macbook(which i successfully installed 10.9.2 on). After some work i was able to make the usb bootable for my netbook but I am now getting stuck at the install process for ubuntu.
I'm getting stuck at the busybox. I cannot decipher what exactly is causing this "panic". The language is sort of new to me so please bare with me. I worked with kexts and kernels with my hackintosh so I hope that should help me a little to be able to grasp the ubuntu install.
System is a hp mini netbook with n270 atom processor 1.6G
1G of ram
new patriot warp 32G ssd (my dog dropped my old platter hdd while it was running 'toast')

Thank you in advance for any help
[IMG][[IMG]http://i1129.photobucket.com/albums/m515/Christopholus1/Mobile%20Uploads/DB03EFB8-6426-4726-8D95-1EA0ABCAED66.jpg[/IMG]]("http://s1129.photobucket.com/user/Christopholus1/media/Mobile%20Uploads/DB03EFB8-6426-4726-8D95-1EA0ABCAED66.jpg.html")[/IMG]

---

### Post by kc1di on 2014-03-23
Hi chris196,
Welcome to Linux and Ubuntu.  I'm not sure since I've never owned one of those netbooks, but on my laptop here I had to boot it with nomodeset.  
You do that on the live CD/DVD by hitting the tab key when it's first booting the select f6 and click on nomodset.  Try booting it that way see if it works for you.

---

### Post by chris196 on 2014-03-23
Thank you for the prompt

no luck using 'nomodeset'. it didnt get me any farther than before.
i went ahead and formatted and installed 13.10 on my usb using unetbootin again. not getting any farther still. however, if i use 'nomodeset' and 'exit' busybox, i get a panic of "cant open /root/dev/console: no such file

---

### Post by mastablasta on 2014-03-24
did you check the md5sum of the downloaded image?

otherwise the hp mini works out of the box i believe. the SSD appears to have linux support. hmm... odd. evenso, the boot is from USB so SSD wont' be mounted if osmehting is wrong but boot should still continue. is hardware good? no issues?

---

### Post by oldfred on 2014-03-24
You add nomodeset or other boot parameters to grub menu or BIOS boot screen. Often Intel needs different settings than nomodeset, but you add those the same way.

 Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1

      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by chris196 on 2014-03-24
verified my md5sum. its ok. i did just realize my boot menu (unetbootin) doesnt have any options other than "default" boot. 
I followed all instructions to a "T". Not sure what I missed

---

