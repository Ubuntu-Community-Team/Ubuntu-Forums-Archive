---
title: "Which graphics drivers for Thinkpad T420?"
date: 2013-05-29
forum: New to Ubuntu
---

### Post by eddyc1 on 2013-05-29
Hello,

I'm sorry if this is a stupid question but I'm really new to ubuntu. I hope I can explain this clearly but let me know if I need to give more detail.

I just installed 13.04 on a Lenovo Thinkpad T420 which has a Nvidia Quadro NVS 4200M discreet graphics card. All seems to be working fine but I am not getting as much battery life as I'd expected. Only about 2 hours. I've read around and I think the issue is probably that everything is running on the discreet card rather than switching to the integrated Intel graphics when the discreet is not needed.

In Settings I've found a list of about 6 available drivers that I can pick from. Should I choose one of these?

I've also read about Bumblebee which apparently should let the laptop use Nvidia Optimus, switching between discreet and integrated automatically as needed. Should I ignore the drivers and use this instead?

Any help would be amazing. Thanks in advance.

---

### Post by 3rdalbum on 2013-05-29
> **eddyc1 said:**
> Hello,

I'm sorry if this is a stupid question but I'm really new to ubuntu. I hope I can explain this clearly but let me know if I need to give more detail.

I just installed 13.04 on a Lenovo Thinkpad T420 which has a Nvidia Quadro NVS 4200M discreet graphics card. All seems to be working fine but I am not getting as much battery life as I'd expected. Only about 2 hours. I've read around and I think the issue is probably that everything is running on the discreet card rather than switching to the integrated Intel graphics when the discreet is not needed.

In Settings I've found a list of about 6 available drivers that I can pick from. Should I choose one of these?

I've also read about Bumblebee which apparently should let the laptop use Nvidia Optimus, switching between discreet and integrated automatically as needed. Should I ignore the drivers and use this instead?

Any help would be amazing. Thanks in advance.

First, install the Nvidia driver so you can have full features on the graphics card. You may see a battery life improvement from that alone.

Bumblebee works in conjunction with the Nvidia driver. It isn't automatic switching though.

---

### Post by eddyc1 on 2013-05-29
Thanks very much for the reply :)

Do I need to just select one of the drivers already available in system settings? Or should I download a new one? I think this is the right one from the Nvidia site, but it mentions that I might be better off using my distribution's native package:

[http://www.nvidia.co.uk/object/linux-display-amd64-319.17-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-amd64-319.17-driver-uk.html)

---

### Post by bela42 on 2013-05-29
Its usually better to use system settings to install the proprietary nvidia driver. I usually choose the driver version from the list of proprietary drivers that is labelled "ubuntu tested" and not "experimental". This should also be the recommended option in that list.

---

### Post by eddyc1 on 2013-05-29
Ok awesome. Thanks a lot for the help.

I'll try that tonight and post back with results.

---

### Post by cRaZyBisCuiT on 2013-05-29
...I also heard, that the latest nVidia driver supports optimus by itself without bumblebee. Maybe you should go for that since the performance is much better. I don't have any additional information though I don't got an optimus notebook.

---

### Post by eddyc1 on 2013-05-29
> **cRaZyBisCuiT said:**
> ...I also heard, that the latest nVidia driver supports optimus by itself without bumblebee. Maybe you should go for that since the performance is much better. I don't have any additional information though I don't got an optimus notebook.

Cool! Do you know if that will be the one already found in system settings as [**[COLOR=#000000]bela42[/COLOR]**]("http://ubuntuforums.org/member.php?u=120243") suggested?

---

### Post by eddyc1 on 2013-05-29
[IMG]http://i40.tinypic.com/4ih1ro.png[/IMG]

Right so I've picked this one because it has the biggest number! (313 updates).

Do you think this is the right one to be using?

Also I'm not sure which BIOS setting I should be using. I can choose from Optimus, Integrated and Discreet. If I select Optimus then I think it is just running on integrated. The graphics performance seems to be the same as if I select integrated and the various propitiatory driver options don't appear as above.

---

### Post by eddyc1 on 2013-06-01
Bump?

Any help with this would be great.

---

### Post by Rob Sayer on 2013-06-01
As mentioned, you should use the one labelled 'tested', which isn't the one you picked.  The update number there doesn't necessarily refer to how many updates there have been, and if it did it wouldn't mean it was better.

I'd stick with whatever bios setting you were using before (assuming it worked) until you get this part finished.

It is very, very important with this sort of  thing to change *just one thing at a time*.

---

### Post by eddyc1 on 2013-06-01
Thanks very much for the reply. I didn't read bela42's reply carefully enough ... sorry.

Have now selected the Tested one. Seems to be working ok so far.

---

