---
title: "Unbuntu Won't Load"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by bootvolume on 2013-02-18
Hi I installed unbuntu's latest iso to a dvd and when I put it in my computer a light purple screen saying unbuntu pops up but it just loads forever and won't come on. Can anyone help me please?

---

### Post by Andrew Binek on 2013-02-18
You must burn the disc as an image disc. So there will be more the just one iso file on the disc.

---

### Post by bootvolume on 2013-02-18
I did. I used imgburn and burned image to disc on a dvd.

---

### Post by cetoka on 2013-02-18
I hope you have more than 1GB of RAM.Because Live CD works from the RAM.

---

### Post by Bashing-om on 2013-02-18
bootvolume; Hi ! Welcome to the forum.

Let's suppose ubuntu is having difficulties loading a graphics driver. Try this.

Cold boot the liveDVD -> at the purple splash screen (stick figure and keyboard image at bottom of screen) press any key -> language screen -press escape to accept the default - ->boot options menu -> press the f6 key for preset boot options -> choose the "nomodeset" option. F10 key to continue the boot process.

Can you now boot to the desktop ?
Further advise pending.
[INDENT][INDENT]try'n to help 

[/INDENT][/INDENT]

---

### Post by bootvolume on 2013-02-18
> **Bashing-om said:**
> bootvolume; Hi ! Welcome to the forum.

Let's suppose ubuntu is having difficulties loading a graphics driver. Try this.

Cold boot the liveDVD -> at the purple splash screen (stick figure and keyboard image at bottom of screen) press any key -> language screen -press escape to accept the default - ->boot options menu -> press the f6 key for preset boot options -> choose the "nomodeset" option. F10 key to continue the boot process.

Can you now boot to the desktop ?
Further advise pending.[INDENT][INDENT]try'n to help 

[/INDENT][/INDENT]

I see the screen of the stick figure and keyboard then it says unbuntu and gold lights flash under the unbuntu name like it's loading. Is there another version of unbuntu that works better than 12.0 that I should try downloading?

---

### Post by Bashing-om on 2013-02-18
bootvolume;

The current long term support version (stable) is version 12.04 Precise Pangolin.

In any event, still need to get a graphics driver loaded that is compatible with your hardware. The simplest method from your standpoint is as advised.
At the purple splash screen, press any key to progress to the boot options screen.
When at that screen pressing any key should take you to the language screen, pressing the escape key should take you to the boot options screen. no ?

[INDENT][INDENT]hth

[/INDENT][/INDENT]

---

### Post by bootvolume on 2013-02-18
> **Bashing-om said:**
> bootvolume;

The current long term support version (stable) is version 12.04 Precise Pangolin.

In any event, still need to get a graphics driver loaded that is compatible with your hardware. The simplest method from your standpoint is as advised.
At the purple splash screen, press any key to progress to the boot options screen.
When at that screen pressing any key should take you to the language screen, pressing the escape key should take you to the boot options screen. no ?
[INDENT][INDENT]hth

[/INDENT][/INDENT]

Thanks. when I pushed any key at the purple screen it took me to language I selected english and was brought to the menu screen like u said but then when I clicked try unbuntu without installing it froze again??

---

### Post by Bashing-om on 2013-02-18
bootvolume;

Making progress.
> english and was brought to the menu screen like u saidAs instructed -> at this time press the f6key for preset boot options, try the "nomedeset" option -> f10 key to continue the boot process.
[INDENT][INDENT]hth

[/INDENT][/INDENT]

---

### Post by bootvolume on 2013-02-18
> **Bashing-om said:**
> bootvolume;

Making progress.
As instructed -> at this time press the f6key for preset boot options, try the "nomedeset" option -> f10 key to continue the boot process.[INDENT][INDENT]hth

[/INDENT][/INDENT]

Ok, I set it to nomedeset then i click f10 and it says power off halt the system now? ok or cancel? Then what do I do?

I clicked cancel then selected try unbuntu without installing and a unbuntu 12.10 came up with the gold dots flashing underneath then some weird screens popped up that were blurry and now it says the system is running in low graphics mode . Your screen, graphics card and input device settings could not be detected correctly. You will need to correct these yourself. Do you know what I should do next??

Update I clicked Ok then a new screen popped up it says what would you like to do with these options: 1.) run in low graphics mode for just one session 2.) Reconfigure graphics 3.) Troubleshoot the error 4.) Exit to console login which one should I select??

Another update I selected run in low graphics mode one session and it went to a black screen that said unbuntu 12.10 and it froze

---

### Post by Bashing-om on 2013-02-18
bootvolume;

For now you can choose to run in "low graphics mode" -> when you get to the desk top;
launcher(on left side of screen) ->Ubuntu Software Center -> software Sources (task bar menu) -> Additional Drivers (tab): Install the recommended driver. ( I have not seen 12.10 to this time, regret my directions not as concise as could be desired)

This is not persistent, the procedure will have to be repeated each time you boot up the liveDVD . Play with ubuntu ensuring all devices function properly.

Have you installed ubuntu onto the hard drive ?

[INDENT][INDENT]hope this helps 

[/INDENT][/INDENT]

---

### Post by bootvolume on 2013-02-19
> **Bashing-om said:**
> bootvolume;

For now you can choose to run in "low graphics mode" -> when you get to the desk top;
launcher(on left side of screen) ->Ubuntu Software Center -> software Sources (task bar menu) -> Additional Drivers (tab): Install the recommended driver. ( I have not seen 12.10 to this time, regret my directions not as concise as could be desired)

This is not persistent, the procedure will have to be repeated each time you boot up the liveDVD . Play with ubuntu ensuring all devices function properly.

Have you installed ubuntu onto the hard drive ?
[INDENT][INDENT]hope this helps 

[/INDENT][/INDENT]

Thanks for help. I still can't get into unbuntu desktop it freezes maybe I should try unbuntu 12.04?

---

### Post by Asatru9 on 2013-02-19
I haven't encountered your problem so I can't offer technical advice. Although I CAN say that if you do decide to install 12.04 back up your data if that is possible.

I have installed 12.04 on a machine using default settings so I hope that you are able to do so as well.

---

### Post by Bashing-om on 2013-02-19
bootvolume;
Installing 12.04 is your choice. I will say that 12.4 is the current long term support and as such (stability ) is better suited for the newer user. However, you may experience the same difficulties to boot it as in 12.10.

From the liveDVD's boot options, try the other options and see what results. The "nomodeset" option is generally effective in 85% of problematic installs. The other preset options exist for a reason .

It is past my bed time, will continue this in my AM.
[INDENT][INDENT]where there is a will there is a way

[/INDENT][/INDENT]

---

### Post by bootvolume on 2013-02-19
> **Bashing-om said:**
> bootvolume;
Installing 12.04 is your choice. I will say that 12.4 is the current long term support and as such (stability ) is better suited for the newer user. However, you may experience the same difficulties to boot it as in 12.10.

From the liveDVD's boot options, try the other options and see what results. The "nomodeset" option is generally effective in 85% of problematic installs. The other preset options exist for a reason .

It is past my bed time, will continue this in my AM.[INDENT][INDENT]where there is a will there is a way

[/INDENT][/INDENT]

Hey, I put in my windows recovery cd and I went to edit partition's and it says that /dev/sda2 ERROR: This software has detected that the disk has at least 2 bad sectors. It says we suggest making a full backup urgently by running 'ntfsclone --rescue..' then run 'chkdsk /f /r' on windows and reboot it TWICE! then you can resize. NTFS safely by additionally using the -bad sectors option of ntfsresize


Does anybody knows what this means? It says it has 101 gb on this sector I don't want to lose it :(

---

### Post by Bashing-om on 2013-02-19
bootvolume;

Ouch !Would of certainty heed Window's warning and comply. I have not been a user of Windows in ages, and do not have the ability to advise directly on window's matters.

But, I do not see this as a hindrance to getting the liveDVD to boot. But the harddrive sector errors need to be addressed ASAP - save your data !

If and when we can get the liveDVD booting, we have a number of options to look at that hard drive and see it's state of health. From windows I can no longer advise, tools are available- I just am not familiar with them.

I hope those with the knowledge/experience responds to this thread.


[INDENT][INDENT]my best regarding

[/INDENT][/INDENT]

---

