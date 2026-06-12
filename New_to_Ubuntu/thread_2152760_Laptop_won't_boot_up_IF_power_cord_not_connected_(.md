---
title: "Laptop won't boot up IF power cord not connected (but battery is OK)"
date: 2013-06-08
forum: New to Ubuntu
---

### Post by GregA on 2013-06-08
Laptop Specs:

HP model # tx1210us
1.9 GHz Turion 64x2 dual-core technology TL-58
NVIDIA GeForce Go 6150
160 GB sata hd
2048 MB DDR2 memory

Installed Kubuntu 12.04 in May.   The only real problem is the laptop won't boot up into Kubuntu (it's the only OS installed), IF the laptop is just using battery - - it just displays the Kubuntu logo and eventually times out.  Attaching the power cord results in a normal bootup into the login screen, etc.

From what I recall, she has an additional battery for extended operation connected.    She also says in Win 7, the laptop would start up using battery only, but battery life was just under 2 hours.

She has also checked the Power Settings in System Settings, and the laptop is set up to conserve power (lower screen brightness etc.)

Are there any diagnostic steps she can take to see what the problem is . . . or any other actions, tweaks that would at least allow the KDE to boot up for an hour or hour and a half?

Thanks for the any help (I/we appreciate it).

---

### Post by GregA on 2013-06-10
Here's an email I sent this evening to our new Kubuntu user - in my ongoing effort to diagnose and fix the power issue she's having.  Perhaps this will trigger some other points I can try after getting the laptop back:

Hi Trudy,

I've been checking out potential causes for your laptop not starting while using battery only.

I don't have a definite answer, but I'd like to see if I can borrow the laptop again for a few days and try some things.

Also, I do have a couple questions that might help clarify things a bit:

    >  If the laptop is started with power cord connected, and KDE boots up normally, and you then unplug, will the laptop run?  For how long?
    >  Do you get normal light indication that the battery is charging properly?  On my laptops, I have a orange light indicating battery is charging, and then it turns blue on the Acer and Green on the Lenovo to indicate the battery is fully charged.
    >  Does your extra-extended battery plug into the standard battery (kinda like "piggy-backing")?  What happens if only one battery is connected vs two?
    >  Did you install the power mgmt widget (with the battery icon in the panel)?   If yes, how much  charge and time show upon clicking the widget?
    >  What was the average and max time the laptop ran under battery power in Windows OS?  Was this recently (past year)?

Anyway, those are a few basic things that might help to diagnose the problem.   I have a couple configuration files I'd like to check in your "/etc" directory, that also provide the "battery state" for batt0 and batt1.  

So, let me know and I can pick it up at your convenience some day this week.

---

### Post by GregA on 2013-06-12
UPDATE:  today, I found out the HP1210 laptop will run on battery power IF it's first booted up while connected via AC plug.   Total battery up time estimated at between 2'15" to 2'30".  Average Windows 7 battery life was about 3 hours, so, this appears as an acceptable work-around, and we may yet declare victory . . . . ( : = > ) . . . . . (fyi, if user attempts to start up on battery power only - she sees the Kubuntu logo, then screen just goes black - - no login screen etc.)

---

### Post by sandyd on 2013-06-12
this sounds like a ACPI issue.
Have you checked if any of the acpi options (i.e. acpi_osi, .etc .etc) does anything?
Try using one of those acpi options with quiet/splash off in the kernel option (just remove splash/quiet from the end of the linux line)

---

### Post by GregA on 2013-06-20
Thanks Sandyd,

If I can get some time with Trudy's laptop, I'll try a few acpi related mods & see if any changes.  I suspect Trudy is basically OK with the overall operation of the laptop, especially now that she  knows how to run it on battery power only.   Another thing I asked her to do is disconnect the usb powered chill-pad before she starts the laptop (if running battery only).

---

