---
title: "Nvidia"
date: 2011-11-10
forum: New to Ubuntu
---

### Post by jpba on 2011-11-10
About this post: [http://ubuntuforums.org/showthread.php?t=1877746&highlight=jpba](http://ubuntuforums.org/showthread.php?t=1877746&highlight=jpba) one of the problems were solved, but my Ubuntu (11.10), doesn't recogneize my monitor, whit the older Ubuntu version it recognizes, but not now.
I went to the HP web page, and there are the "inf" files for my monitor, the files are: [http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=pt&prodTypeId=382087&prodSeriesId=298743&prodNameId=30495&swEnvOID=20&swLang=13&mode=2&taskId=135&swItem=vc-10499-1](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=pt&prodTypeId=382087&prodSeriesId=298743&prodNameId=30495&swEnvOID=20&swLang=13&mode=2&taskId=135&swItem=vc-10499-1) Can i install it? This way the Ubunt recogneize the monitor, right? 
The monitor is a "HP D2837A" and my Nvidia Card is a G-Force MX440SE AGP8X"
Thanks

---

### Post by grahammechanical on 2011-11-10
Can you make things clearer?

Have you installed the Nvidia drivers? Did you do it through Addtional Drivers? How do you know that Ubuntu does not recognise the monitor? Are you able to use Ubuntu with that monitor?

It is my experience that when you install Nvidia drivers you also get a utility called **Nvidia X Server Settings** and the standard Ubuntu **Displays** utility is disabled.

On my system the **Displays** utility says Monitor Unknown. But with the **Nvidia X Server Settings** utility I am told that I have a Samsung SyncMaster, which is correct.

Which utility are you using to find out if Ubuntu recognizes your monitor?

I also think that Ubuntu gets information about the monitor through the video card adapter. It reads information stored in the monitor. We do not need ini files like you do with Windows. From experience I know that when a video card is overheating it loses the ability to read the monitor configuration information stored in the monitor. Then Ubuntu becomes unable to use that monitor because it does not know the configuration for the monitor 

Regards.

---

### Post by 7h3 Wh173 R4bb17 on 2011-11-10
> **grahammechanical said:**
> Can you make things clearer?

I also think that Ubuntu gets information about the monitor through the video card adapter. It reads information stored in the monitor. We do not need ini files like you do with Windows. From experience I know that when a video card is overheating it loses the ability to read the monitor configuration information stored in the monitor. Then Ubuntu becomes unable to use that monitor because it does not know the configuration for the monitor 

Regards.

Do you have any heat sensing equipment within your computer?, my desktop uses a utility that informs me of the temperature of the CPU, Graphics cards and other components, as well as fan speed and many more, I fixed an overheating graphics card once by increasing the rpm of the fans inside the computer, alternatively invest in an extra extractor fan for peanuts

---

### Post by jpba on 2011-11-10
Ok... i install the drivers, and in the Nvidia XServer settings, i receive this message: 

Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0.

???
Another think, how do i open this file?

[http://www.geforce.com/Drivers/Results/35554](http://www.geforce.com/Drivers/Results/35554)

It's this kind of file: NVIDIA-Linux-x86-96.43.20-pkg1.run

---

