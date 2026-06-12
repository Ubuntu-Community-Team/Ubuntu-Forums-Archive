---
title: "Old internal hdd problem"
date: 2014-05-01
forum: New to Ubuntu
---

### Post by chriswill2 on 2014-05-01
I have an old internal hdd the one that still uses an Ide. I don't have an Ide to sata adapter. So I use my Ide to usb adapter. I install ubuntu on it and I can't boot from it. Yes I have change my bios setting to boot from usb hdd. And when I want to boot from it looks like my computer stuck on the post?  Because there's b4 sign on my bottom right corner of the screen. So why can't I boot from it?  Do I have to use Ide to sata adapter? 

My mobo : msi zh77a g-43 plus

---

### Post by sudodus on 2014-05-01
Welcome to the Ubuntu Forums :-)

I can boot from old IDE disks via an  adapter that is named 'USB 2.0 to IDE & SATA cable'.

Are you sure your adapter is connecting the disk? Can you see the disk when connected in another computer (or this computer while running another operating system)?

Is your computer is really trying to boot from USB?

How did you create the bootable system?

Can it boot in another computer?

-o-

See this link for more tips

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

particularly
[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

-o-[I]

Edit[/I]: What operating system are you trying to boot? Linux can boot from USB, Windows cannot.

---

### Post by chriswill2 on 2014-05-01
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

I can boot from old IDE disks via an  adapter that is named 'USB 2.0 to IDE & SATA cable'.

Are you sure your adapter is connecting the disk? Can you see the disk when connected in another computer (or this computer while running another operating system)?

Is your computer is really trying to boot from USB?

How did you create the bootable system?

Can it boot in another computer?

-o-

See this link for more tips

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

particularly
[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

-o-[I]

Edit[/I]: What operating system are you trying to boot? Linux can boot from USB, Windows cannot.

I'm trying to boot Ubuntu / Mint from it. I already install Ubuntu / Mint on the old hdd ( I use live cd and install Ubuntu / MInt on it ). Everything seems to be okay, but I can't boot from it.
The old hdd seems to be pretty good though.

Yes my computer can see the hdd is connected and I have already formatted the disk with linux mint live cd
Yes my computer is boot from the USB, I already change the bios setting and right now I don't have my primary hdd. And I always use my mint that I boot from USB

Is it because the adapter that doesn't support boot with it ? ( My adapter seems to be the same with yours, mine also IDE & SATA to USB )
Or is it because of the old hdd ( I don't think so though ) ???

---

### Post by sudodus on 2014-05-01
I don't think it is because of the old HDD. Maybe because of the adapter. Maybe because of the mobo.

- Can your computer boot from USB at all?
- Does it boot and then get stuck? Or does it not boot at all?
- Can you try if the IDE drive plus the USB adapter can boot in another computer?

I don't know your mobo : msi zh77a g-43 plus. If someone reading this thread knows about this mobo, please chip in and help :-

---

### Post by chriswill2 on 2014-05-02
> **sudodus said:**
> I don't think it is because of the old HDD. Maybe because of the adapter. Maybe because of the mobo.

- Can your computer boot from USB at all?
- Does it boot and then get stuck? Or does it not boot at all?
- Can you try if the IDE drive plus the USB adapter can boot in another computer?

I don't know your mobo : msi zh77a g-43 plus. If someone reading this thread knows about this mobo, please chip in and help :-

- Yup I'm certain it can boot from the USB, cuase right now while I'm typing this I'm using linux mint that I installed on my flashdisk
- Hmmm, how can I say this... In Ubuntu case it doesn't boot at all. But when I installed mint on it, it shows the mint logo and I can see the mouse cursor but the background is all black and I can't do a thing.
- Don't you think it's unecessary to do that ? 

Well I think that the problem is in the adapter, because my mobo is support boot from the USB. Should I try the IDE to SATA adapter ?

---

### Post by sudodus on 2014-05-02
> **chriswill2 said:**
> [QUOTE=sudodus;13009810]I don't think it is because of the old HDD. Maybe because of the adapter. Maybe because of the mobo.

- Can your computer boot from USB at all?
- Does it boot and then get stuck? Or does it not boot at all?
- Can you try if the IDE drive plus the USB adapter can boot in another computer?

I don't know your mobo : msi zh77a g-43 plus. If someone reading this  thread knows about this mobo, please chip in and help :-

- Yup I'm certain it can boot from the USB, cuase right now while I'm  typing this I'm using linux mint that I installed on my flashdisk
- Hmmm, how can I say this... In Ubuntu case it doesn't boot at all. But  when I installed mint on it, it shows the mint logo and I can see the  mouse cursor but the background is all black and I can't do a thing.
- Don't you think it's unecessary to do that ? [/QUOTE]I think it will help sort out the causes of your problem, if you try if the IDE drive plus the USB adapter in another computer.> 

Well I think that the problem is in the adapter, because my mobo is  support boot from the USB. Should I try the IDE to SATA adapter ?


- The problem could be the graphics, that the graphics driver and graphics card do not cooperate. Try some [boot options]("https://help.ubuntu.com/community/BootOptions"), for example ***nomodeset***.

- I have also seen cases when there are problems to boot grub via USB. Try [chainloading]("https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB") or an IDE to SATA adapter.

---

### Post by piotrasbl on 2014-05-02
Please maku sure,l the partition with system is set as boot (check in gparted). 
That small thing made me almost resign from my old toshiba laptop...

---

### Post by sudodus on 2014-05-02
Windows wants the boot flag, but Ubuntu does not care about it. I have made many (internal drive as well as USB) boot systems without any boot flag.

---

### Post by chriswill2 on 2014-05-02
> **sudodus said:**
> I think it will help sort out the causes of your problem, if you try if the IDE drive plus the USB adapter in another computer.

- The problem could be the graphics, that the graphics driver and graphics card do not cooperate. Try some [boot options]("https://help.ubuntu.com/community/BootOptions"), for example ***nomodeset***.

- I have also seen cases when there are problems to boot grub via USB. Try [chainloading]("https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB") or an IDE to SATA adapter.

Can you give me the step by step instruction on how can I do the 'nomodeset' & 'chainloading' thing ?

Just want you to know that I don't have any OS on my computer right now, I only have live CD that I've always been using ( my hdd is in service )

---

### Post by sudodus on 2014-05-03
- See these links

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

> ***GRUB_CMDLINE_LINUX_DEFAULT=***"quiet splash" 


[LIST]
[*]This  line imports any entries to the end of the 'linux' line (GRUB legacy's  "kernel" line). The entries are appended to the end of the normal mode  only. 
[*]To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 
[/LIST]

Add boot options in grub via this line in **/etc/default/grub** and run ```
sudo update-grub
```

- See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)
[URL="http://ubuntuforums.org/showthread.php?t=2196858"]
Howto help USB boot drives[/URL]

---

