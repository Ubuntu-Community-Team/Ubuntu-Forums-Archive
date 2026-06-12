---
title: "AMD Compatibility"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by newjorkcity on 2013-02-23
Hi,

Brand new to Ubuntu and the forum and hoping for some help.  Thinking of building a computer and want to make sure we use compatible components.  Right now we are considering an Asus F2A85-V Pro Mobo, and an AMD Quad-Core A10-5800K 3.8GHz processor.  I've been looking through the forums and can't find a list of compatible AMD hardware.  I checked the listing on the Ubunbtu site, and although they list AMD I cannot find the processor listed above, nor the mobo.

Can anyone either tell us if these components are compatible, or, even better, direct me to a more comprehensive list?

Thanks!

---

### Post by DuckHook on 2013-02-23
The processor is fine, The mobo must have proper support for UEFI, but if it is of recent build, it will likely give you no problems. ASUS is especially good with Linux. The biggest issue is actually video. What video were you thinking?

After video, these forums have seen posts about USB, audio and network, but video is the biggest problem by far.

---

### Post by newjorkcity on 2013-02-23
> **DuckHook said:**
> The processor is fine, The mobo must have proper support for UEFI, but if it is of recent build, it will likely give you no problems. ASUS is especially good with Linux. The biggest issue is actually video. What video were you thinking?

After video, these forums have seen posts about USB, audio and network, but video is the biggest problem by far.

Hi. Not sure what you mean by video.  Video card maybe? To be honest, I am 13 and have never built a computer before. My dad is helping me and we are looking at kits, but might buy parts separately if it costs less. I have been saving a long time and want it to be as good as it can be for the money. Right now we are looking at this kit: 
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=7669721&CatId=332](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=7669721&CatId=332)

Does that give you the info you need about video? I use a MAC at home but want to built one and use Ubuntu so I can start to learn Linux and programming and how computers work. If you can think of a better one please let me know.  Dad said some he read that some hardware in the past did not work with Linux, so we just want to be sure.

Thanks!:)

---

### Post by deadflowr on 2013-02-23
The motherboard you're looking at comes with an intergrated graphics card. A radeon HD 7000 series.
Linux/Ubuntu comes with open source graphics drivers, so video should work out of the box.
However, if you want to get the best performance, you can also install the closed source linux drivers provided by AMD.
There are several methods to install the closed drivers, either through Ubuntu's additional drivers program, or directly from the AMD site.
Look here for more info on installing closed source drivers
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

The motherboard you cite also has PCIe slot so if you wanted to use a different card you could.

Outside of that, I don't forsee any real problems with running Ubuntu on that rig, outside of what DuckHook has mentioned.

---

### Post by DuckHook on 2013-02-23
Welcome to the forums and to a great new adventure before you!

A big part of me wishes I were 13 again and discovering this stuff for the first time. Very exciting.

Just looked at your link. Pretty sweet deal and I think you will be happy with the result as far as Ubuntu goes. I glanced through the specs and can see nothing glaring that might be problematic. However, I'm no HW expert so can't guarantee you a good experience. But solving any potential problems is what this forum is for.

By video, I do mean the video subsystem, which in your case is the video chip on the motherboard. It amazes me the power that comes on motherboards these days, but indeed, the system you are looking at will run Ubuntu very nicely. Let me emphasize: it will run Ubuntu very nicely. If you want to do highly demanding gaming, that's a completely different matter.

The biggest drawback I can see with your package is not enough system RAM. 4 GB is too small, especially when a big portion of it will be stolen by the video subsystem (system RAM is "shared" with most on-board video chips). I strongly recommend that you upgrade to 2x4GB Dimms which will give you 8 GB altogether. You should be quite happy with the result and it will allow you to run virtual machines (computer within a computer) quite nicely with the additional memory.

Good luck and enjoy discovering all these new things!

---

### Post by newjorkcity on 2013-04-04
Ok so I built the computer and Im about to try to boot from a USB disk But i read somewhere on these forums that I need to format it. How would i do that Please remember Im only 13, have no experience about this and have no idea what im doing. Thanks!

> **DuckHook said:**
> The processor is fine, The mobo must have proper support for UEFI, but if it is of recent build, it will likely give you no problems. ASUS is especially good with Linux. The biggest issue is actually video. What video were you thinking?

After video, these forums have seen posts about USB, audio and network, but video is the biggest problem by far.

---

### Post by sandyd on 2013-04-04
> **newjorkcity said:**
> Ok so I built the computer and Im about to try to boot from a USB disk But i read somewhere on these forums that I need to format it. How would i do that Please remember Im only 13, have no experience about this and have no idea what im doing. Thanks!

Format the USB Drive to fat32.

You can do this by plugging it into a Windows Computer, then going to My Computer -> right-select usb drive -> choose format -> make sure it it set to fat32 with the quickformat box checked, and click the format button.

Afterwards, you can use [UNETBootin]("http://unetbootin.sourceforge.net/") to put the iso on the USB drive.

Good luck!

---

