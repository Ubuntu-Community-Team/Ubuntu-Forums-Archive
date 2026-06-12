---
title: "Thoughts on Windows bootloader and GRUB"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by Andavane on 2012-07-21
Wit all the interesting things occurring for me lately I looked at the attached screen which I must have seen 1,000's of time now and wondered why boter with the windows bootloader when the Ubuntu GRUB does it?
In fact once dual-boot is there I've never used te Windows booter at all.

--Jon

---

### Post by oldfred on 2012-07-21
If you have two drives, you might want the Windows boot loader in the MBR. 

You actually are using most of the Windows boot loader. The Windows boot loader in the MBR just looks for the primary partition with the boot flag and jumps to that partition's boot sector or PBR for more code. All grub does is not use MBR, but chainload or jump to the Windows PBR and let Windows continue to boot.

More info on Windows booting, quick overview just by reviewing pictures:

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Andavane on 2012-07-23
> **oldfred said:**
> If you have two drives, you might want the Windows boot loader in the MBR. 

You actually are using most of the Windows boot loader. The Windows boot loader in the MBR just looks for the primary partition with the boot flag and jumps to that partition's boot sector or PBR for more code. All grub does is not use MBR, but chainload or jump to the Windows PBR and let Windows continue to boot.

More info on Windows booting, quick overview just by reviewing pictures:

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
Thank you, I have found this very informative, and so good to be able to form a mental picture of the sort of thing which goes on  and how the first small program, the BIOS is written onto the chip itself, as well as finding out that the Initual Program Loader is also the same as the Master Boot Record. Of that one, I remember that a techie man told me once that there is a Windows virus which can infect the Master Boot Record. I think this "High Memory" thing I also hear about (and see there us an option to free up some High Memory in this BIOS is somehow linked with what the BIOS does.

I'm letting this sink in slowly: It's certainly less mystical than it used to appear to me! :)

---

