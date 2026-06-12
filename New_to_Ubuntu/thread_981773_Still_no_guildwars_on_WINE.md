---
title: "Still no guildwars on WINE"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by Arsin on 2008-11-14
[PHP]aaron@aaron-desktop:~$ wine "C:\Program Files\Guild Wars\Gw.exe" -dsound
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec20,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x13b2a8) Dialogs cannot be disabled yet
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x13b2a8) Dialogs cannot be disabled yet
Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max temporary reg
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22
aaron@aaron-desktop:~$ 
[/PHP]

is what i get when i try to run guildwars. Someone please help.

---

### Post by Brandel Valico on 2008-11-14
Probably a silly question but did you configure Wine all ready. Just surprised since Guild Wars runs like a dream for me on several different computers. Hopefully someone with the knowledge to actually help you will come along quickly. Until then I hope my post will at least bump this up for them to see.

---

### Post by Arsin on 2008-11-14
ive read a few things on wine and guildwars on it. ive configured it as much as ive read.

---

### Post by Sirron on 2008-11-14
What graphics card are you using, and if it is an ATI or NVIDIA card, do you have the appropriate proprietary driver installed for it?

---

### Post by Arsin on 2008-11-15
integrated dell graphics. i used to play guildwars on the same pc when i had windows fyi.

---

### Post by binbash on 2008-11-15
i used to play guild wars with playonlinux, try that also if you dont want to mess with wine configurations or tweaks

---

### Post by Brandel Valico on 2008-11-15
Okay lets check to see if you have the video drivers you need. Click "system" goto Administrator then goto Hardware Drivers and click it.

That will pop up a box asking for your password type it in then see if the video driver is enabled. If not enable it if it is well at least thats one check mark next to not the issue.

---

### Post by moggy812 on 2008-11-15
Hi im still new to this game...
and am looking for reassurance in buying guild wars for my pc, i am running ubuntu 8.10, have wine 1.0.1, and also have crossover too...
oh and my graphics card is a lowly ati thing, to which i cant remember what it is, i know it's not great and is getting on years now though, lol, not that it is much help, but in response to the above question to the person who started this thread, i did the same and have the following...

3D-accelerated proprietary graphics driver for ATI cards.

This driver is required to fully utilise the 3D potential of some ATI graphics cards, as well as provide 2D acceleration of newer cards.

i hope you can help, as it is my birthday coming up next month, and wanted someone to get me this game as a present :D 
but if it's not going to work, then i'll find something else...

and another thing, i emailed play NC about playing on a linux system and got a reply back saying that 'Guild Wars is being developed on and will initially be released for the PC.  We are aware that there is an interest in having the game available using other operating systems or on other platforms, and we will continue to evaluate these possibilities.'
alot of use that was.

i look forward to your replies.

My thanks
Mogg.

---

### Post by Arsin on 2008-11-19
nothing comes up in my hardware drivers screen. theres nothing in the box at all.

---

### Post by Arsin on 2008-11-20
well i finally got it to somewhat load through playonlinux and some winetricks stuff. but now it attempts to load the log in screen and gets all messed up and the music plays and stuff but then it will crash or just continue to look crappy and be really slow. I know none of that is in technical terms but its the best way to describe it.

---

### Post by Brandel Valico on 2008-11-22
Do you have Compiz-Fusion running?

If So try shutting it down before starting the game. My guess is you probably don't have it since it honestly does seem like you don't have the correct video driver installed.

If not then we need to get your video card drivers installed.

Type "sudo lshw -C video" into a terminal enter your password and post the results here. It should give you the make and model of your video card so we can figure out what driver you need and go from there to help you get it.

It seems like you don't have full 3d rendering. This is a guess based on my computer doing what yours is doing when I first tried KOTOR on it. I was also able to get it to start to the login and get sound. But not actually play the game. While not exactly the same it seems similar.

---

### Post by moggy812 on 2008-11-27
I am just following this thread in the hope that when I do decide to buy guild wars I will be able to get it to work straight off without any problems, and seeing the last post on here i thought I would post my details as asked for above as well, that way I can have your opinion if you think the game will work on my pc too...
So here are my details:
 *-display:0             
       description: VGA compatible controller
       product: RV370 5B60 [Radeon X300 (PCIE)]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=fglrx_pci latency=0 module=fglrx
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV370 [Radeon X300SE]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress bus_master cap_list
       configuration: latency=0
I look forward to your opinions on this and if you think the game will work or not, if not, then perhaps some details on what i should do or need to do.

Many thanks.
Mogg.

---

### Post by Brandel Valico on 2008-11-28
to the best of my limited knowledge it looks like it should work for you. Since your running the fglrx driver for your video card. An easy check is to right click your desktop and see if your able to enable desktop effects. If you are you will probably have no problems running Guild Wars.

---

### Post by moggy812 on 2008-11-29
umm...
When I right click on desk top all I get is:

Create Folder
Create Launcher
Create Document>
Clean Up By Name
Keep Aligned
Paste and
Change Desktop Background

But no Enable Desktop Effects
Any ideas?

---

### Post by Brandel Valico on 2008-12-03
sorry my fault for a lousy job of explaining. When you right click, goto Change Desktop Background, Then click the Visual Effects tab. Then try and select Extra from the three choices (You should see None,Simple,Extra) If you can enable extra then normally as long as your actual hardware is compatible and you have wine configured you should be able to play games like guildwars which are listed as platinum on WineHQ.

---

### Post by moggy812 on 2008-12-06
ok, I can do that, great :)
so I should be ok with guildwars... I'm assuming that I wouldn't go for the extras though, as I am sure I see somewhere before, that it should be switched to none for some games.

Thanks for the info, I'll see about getting the game, and then I'll probably be in here hunting the how-to's to get it working, lol

again, my Thanks.

---

### Post by Brandel Valico on 2008-12-08
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194)

Gives you the heads up on Guild Wars in Wine.

As for the Extra Settings. That depends on your computer hardware. I run Guild Wars with Compiz running the whole time and have no issues any longer. But I used to shut it off for other games that wouldn't work with it running.

---

