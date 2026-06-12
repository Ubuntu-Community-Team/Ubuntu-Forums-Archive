---
title: "i'm getting so sick of hardy"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by T2manner on 2008-05-26
every session i have on hardy, EVERY SINGLE one, something always goes wrong.

somewhere, somehow, some program freezes up.
which results later in all the programs freezing up, or atleast most of them.
eventually, the panels are non respondant.
and i have to restart my computer via ctrl alt backspace
then restart it from the options.

this ALWAYS happens

i have to do this multiple times daily.

is there anything i can do

---

### Post by spiderbatdad on 2008-05-26
Run ```
dmesg
```in the terminal and copy the contents to a text file. Right click the text file and select "create an archive." Upload the archive here using the manage attachment tool below.

---

### Post by T2manner on 2008-05-26
okay there ya go

---

### Post by T2manner on 2008-05-26
bump

---

### Post by Joeb454 on 2008-05-26
I know it's frustrating, but please try not to bump more than once every 24 hours :) There will be people looking into your issue (myself included) :)

---

### Post by T2manner on 2008-05-26
oh
sorry. 
i didn't know that.
thanks for telling me :):)

---

### Post by Joeb454 on 2008-05-26
No problem :) (Still looking)

---

### Post by spiderbatdad on 2008-05-26
Thanks. I am no expert on boot parameters, but have been able to get my own system booting and running smoothly.
There appears to be at least a few issues:
>  ACPI: PCI Root Bridge [PCI0] (0000:00)
[   27.630577] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   27.630580] * this clock source is slow. If you are sure your timer does not have
[   27.630582] * this bug, please use "acpi_pm_good" to disable the workaround and there are some other instances of acpi conflict...not sure where they are severe.

I recommend experimenting with several boot parameters by editing the end of the kernel line in /boot/grub/menu.lst If you have a problem during a boot, no worries, boot into recovery mode and re-edit the kernel line.

This is what mine looks like:
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=(some #'s) ro **lapic pci=routeirq**
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault
```
You can see, in bold, above the parameters, lapic pci=routeirq, I have added in place of "--quiet splash."

On your system I might start by trying the same parameters...or acpi_pm_good

Some others might include: 1.) acpi_pm_good pci=routeirq
2.) noapic lapic
3.) noapic nolapic

Good luck.

---

### Post by T2manner on 2008-05-26
uh..
i'm confused with this.
how do i edit it?
and 

i just replace the end with one of the others?
that's it?

---

### Post by Sanoski on 2008-05-26
> **T2manner said:**
> every session i have on hardy, EVERY SINGLE one, something always goes wrong.

somewhere, somehow, some program freezes up.
which results later in all the programs freezing up, or atleast most of them.
eventually, the panels are non respondant.
and i have to restart my computer via ctrl alt backspace
then restart it from the options.

this ALWAYS happens

i have to do this multiple times daily.

is there anything i can do



I thought I was the only one feeling frustrated. I don't know if it's just my computer or what. But I wasn't having the amount of problems I'm having now until I upgraded to Hardy. Here's a brief outline of the issues I'm having. 

[LIST]
[*]When I try to get updates, the manager stops responding: it never even asks me for my password.
[/LIST]

[LIST]
[*]Printing documents is acting very unusual. It'll print in green, and only about 99% comes out printed correctly. There's always some paragraph that bunches up with other words and doesn't print.
[/LIST]

[LIST]
[*]If Firefox is open, 99% of the time no videos or music on my hard drive will work. If they play and doesn't crash, there will be no sound until I close Firefox.
[/LIST]

[LIST]
[*]Everything lags.
[/LIST]

[LIST]
[*]Those grayed out screens keep popping up all the time, no matter what program I'm using. "Press 'Home' in my browser-- screen turns gray for 6.3 seconds.
[/LIST]

All this happens throughout various periods of the day. Talk about frustration. Can anything be done to fix this?

---

### Post by spiderbatdad on 2008-05-26
Use the gedit command is super user mode:
```
gksu gedit /boot/grub/menu.lst
```Scroll down to the first section under ####END DEFAULT OPTIONS####
This is your default kernel. Edit the end of the line that begins with the word 'kernel,' as in the example of my kernel line. Save the file, and reboot. Revisit the previous post for other examples and how to resolve problems by booting into recovery mode to re-edit. In recovery mode, 'gksu' is not required before the gedit command, as you are looged in as root in recovery mode.

---

### Post by Duck2006 on 2008-05-26
> **T2manner said:**
> uh..
i'm confused with this.
how do i edit it?
and 

i just replace the end with one of the others?
that's it?

In ubuntu from the terminal type.

gksudo gedit /boot/grub/menu.lst

---

### Post by vegavov on 2008-05-26
> **Sanoski said:**
> 
[LIST]
[*]If Firefox is open, 99% of the time no videos or music on my hard drive will work. If they play and doesn't crash, there will be no sound until I close Firefox.
[/LIST]

I've had that very same problem. I did a top command and firefox was using 50% CPU. Maybe it is some bugs in the new firefox beta hardy comes with. It seems strange that nothing can run when firefox runs.

---

### Post by js_anoop on 2008-05-26
This could be the problem I had a year ago. Even though I had a swap partition, I didn't assign it as ubuntu's swap drive. Later somehow I managed to correct it..

---

### Post by roderick on 2008-05-26
Here are some other things to try:

1) If you have an older kernel in your boot list, try booting with the older kernel.
2) Try disabling compiz from running (you can install a nice systray applet to control compiz called fusion-icon).
3) Try installing Firefox 2 and uninstalling Firefox 3.

With some systems, there are various issues that crop up, but no one specific root. It could be kernel related or graphics related. It could be scheduler issues in the kernel, or it could be ACPI/APIC (BIOS) related.

Anyway, feel free to try my suggestions if the previously meantioned kernel lapic option does not work.

---

### Post by hesjnet on 2008-05-27
I have compiz and firefox 3. My system also freezes more often than I feel is appropriate for a linux system:)

> **vegavov said:**
> I've had that very same problem. I did a top command and firefox was using 50% CPU. Maybe it is some bugs in the new firefox beta hardy comes with. It seems strange that nothing can run when firefox runs.

Same here for me. Firefox is always open when my 8.04 frezees. I love the new FF 3 features and I don't want to uninstall it.  I hope this bug is fixed at the full release in june.

And it seems for me that if i am having some media playing. when a video in totem and firefox tries to launch a flash or avi streem(or something like any type media) my whole system crashes. ctrl Alt backspace doesnt work when it freezes like this. 

My system also crashed less requently when I didnt have Compiz installed. I love the wobbly window effects, so unstalling this is out of the question:cool:

---

