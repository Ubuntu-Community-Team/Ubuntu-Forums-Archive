---
title: "graphical seperation/scaling?"
date: 2024-06-04
forum: New to Ubuntu
---

### Post by waiyertv on 2024-06-04
Hi!
I started trying ubuntu few days ago, and work as well as windows  for games at this point. I just keep running into what i think is a  nvidia scaling issue?

some examples
first is Hunt: Showdown
second is EU 4 
third is just a random screenshot.

[https://imgur.com/a/evEIRY2](https://imgur.com/a/evEIRY2)

i have no clue where to really post this

My specs
Ubuntu 24.04 LTS
Intel i7 8700k
Asus prime z370
Asus GTX 1080 ti

535 driver from the distro.

---

### Post by waiyertv on 2024-06-12
the drivers are the latest from the distro, no clue how to find and install something from nvidia. the nvidia settings were very bare bones and the scaling i found was grayed out.
Unless i am looking in the wrong place, everyone kept saying nvidia-settings
that seemed to open up the xorg settings aswell though, so i dont know which are nvidia settings and which are xorg. cus everything seems to be from "Nvidia corp" but have bunch of x display and stuff

---

### Post by waiyertv on 2024-06-21
sorry for slow response, things are litterally just breaking more and more, everything just gives errors even tho i dont change anything and now all downloads fail.

[https://i.imgur.com/sAYEFHN.png](https://i.imgur.com/sAYEFHN.png)
all i can find is nvidia shapening, but that is grayed out still after  running "sudo apt update" and "sudo apt full-upgrade" and i can kinda just keep looping those two, it seems to just never be done.

I also have NO clue which driver to get from thier website, cus it is just big list of versions. How do i know which version that is working with my gpu?

[https://www.nvidia.com/en-us/drivers/unix/linux-amd64-display-archive/](https://www.nvidia.com/en-us/drivers/unix/linux-amd64-display-archive/)
and you said there would be a installation instructions, i tried running it from the terminal and just double clicking. nothing happens, dont know why installing things is made to be such a pain in the ass. but i guess that is the reason people dont like linux.

---

### Post by nicolasdentremont on 2024-06-21
> **waiyertv said:**
> sorry for slow response, things are litterally just breaking more and more, everything just gives errors even tho i dont change anything and now all downloads fail.

[https://i.imgur.com/sAYEFHN.png](https://i.imgur.com/sAYEFHN.png)
all i can find is nvidia shapening, but that is grayed out still after  running "sudo apt update" and "sudo apt full-upgrade" and i can kinda just keep looping those two, it seems to just never be done.

I also have NO clue which driver to get from thier website, cus it is just big list of versions. How do i know which version that is working with my gpu?

[https://www.nvidia.com/en-us/drivers/unix/linux-amd64-display-archive/](https://www.nvidia.com/en-us/drivers/unix/linux-amd64-display-archive/)
and you said there would be a installation instructions, i tried running it from the terminal and just double clicking. nothing happens, dont know why installing things is made to be such a pain in the ass. but i guess that is the reason people dont like linux.

From what I know, Nvidia has always had poor compatibility with Linux.

The driver downloads section of the Nvidia website should have a form where you input your specific GPU and OS to search for the latest drivers for your hardware.

I've seen many people recommend against installing drivers directly from Nvidia. I tried at one point and the Nvidia driver installer actually said not to install it and to instead use the OS recommend driver versions.

You should be able to switch between a few different driver version in "additional drivers" normally located in the program/applications list.

But going back you your original issue about scaling while playing games. You mentioned they were Windows games? If so are you using Wine to play them? The command winecfg brings up a window with various settings, in the display tab, theres an option to adjust screen DPI that helps when games and applications running with Wine don't appear to be the proper size that they should be.

---

### Post by waiyertv on 2024-06-22
yeah there are 3 version, only 535 says "tested" but tried the other two aswell and nothing changes, beside 510 forces my screen into 59.95 hz instead of 165hz

running things via steam.

EU4 have native Linux support
and the font is just from firefox were some letters just always have seperation
Hunt:showdown isnt linux, but protondb says it works fine with tweaks and all i find people do to solve everything is run proton experimental or if they have fedora/nobara they get proton GE. no clue why both those struggle.

and tried downloading from nvidia website, but it just couldent get it to run. so there are no instructions on how to install nvidia drivers. and most things i find online. they bypass like 90% of the help and just expect you to have installed all programs you need to run all formats, but i guess that is just the internet. very unhelpful.

---

### Post by nicolasdentremont on 2024-06-22
> **waiyertv said:**
> yeah there are 3 version, only 535 says "tested" but tried the other two aswell and nothing changes, beside 510 forces my screen into 59.95 hz instead of 165hz

running things via steam.

EU4 have native Linux support
and the font is just from firefox were some letters just always have seperation
Hunt:showdown isnt linux, but protondb says it works fine with tweaks and all i find people do to solve everything is run proton experimental or if they have fedora/nobara they get proton GE. no clue why both those struggle.

and tried downloading from nvidia website, but it just couldent get it to run. so there are no instructions on how to install nvidia drivers. and most things i find online. they bypass like 90% of the help and just expect you to have installed all programs you need to run all formats, but i guess that is just the internet. very unhelpful.

The "additional information" tab of the driver download page has a bit of info.

Basically you would right click inside the folder that you downloaded the driver to and open a terminal window. Then use the command to run the driver install. I got the below one from the first driver on the Nvidia website link from earlier in this thread. The actual name of the file would vary depending on what driver you downloaded.

```
sh ./NVIDIA-Linux-x86_64-555.52.04.run

```

It's been a while since I last did this but the installer should start and go through the process. You will probably have to remove the old drivers first before attempting this.

As an alternative, which may help you...

When I encounter a Steam game that won't work with any of the versions of Proton or with any of the launch options that people have used listed on ProtonDB I install the game using the Windows version of Steam running through Lutris. So far Lutris has been able to run any game that I can't get to work on Steam.

I know it's kinda annoying to have two steam installations and all these extra programs installed just to run games but that's just the reality of running Windows games on Linux.

Besides that, the place you got your Linux Steam installation from matters. If you have the Snap version from the Ubuntu Software app/Snap Store you may want to try either the Flatpak version or the .deb package directly from the Steam website. I've had issues with the Steam Snap and most people will advise you to steer clear of that version of Steam.

---

### Post by waiyertv on 2024-06-24
well the version on Nvidia download is the same version that i install via the distro, but i dont see how what proton have to do with my browser and a game that runs natively on linux. snap version on steam just refused to start so i gave up on that.

but i also dont  know how to install something as if it was a windows os then booting it via lutris. i keep trying to install things via lutris, but it just get stuck on every config and after 2h i tend to just give up and try something else.

if you want i could find other games that have the same shadow blocking as hunt doesnt but with native linux.

but i am gonna look at removing driver and reinstalling it, kinda ****ed up how it can break on the first install...

---

