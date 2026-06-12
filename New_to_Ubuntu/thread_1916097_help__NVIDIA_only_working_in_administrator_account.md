---
title: "help:  NVIDIA only working in administrator account"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by volido on 2012-01-27
Yesterday i had some issues making the NVIDIA FX1400 to work ... the drivers look as they were working  properly but the system was keeping saying monitor unknown at the same time video and 3d applications were working very slow(apparently no hardware acceleration.Finally after some hours everything was fine, acceleration and system recognizing the monitor.This morning the monitor appears  unknown again but hardware acceleration is working fine. I can live with it. The problem  is when I set up an standard account for my assistant in the same machine. nor guest nor new standard account have hardware acceleration. When I log-in as administrator, hardware acceleration works fine again. I really like the OS but this situation is important since we work mainly with graphic applications as Maya, blender and different CAD's. 
????

---

### Post by Frogs Hair on 2012-01-27
I don't know why the drivers would not be applied in the user account if installed via the additional drivers jockey .  After installing Nvidia drivers the monitor and GPU information   can be viewed in the' Nvidia X Server Settings.'

---

### Post by grahammechanical on 2012-01-27
Hi

First, in System Settings there is the Displays Utility. It is disabled when we install a proprietary driver because the driver comes with its own settings utility. I am getting the same result as you.

Also in 11.10 and onwards there is a System Info utility that works with open source video drivers and not with proprietary video drivers. So, that says Graphics Unknown and Graphics Standard, even when it is not. Do not be confused by these things.

Secondly, in these other accounts (standard accounts) are you sure that the person is not logging in as Ubuntu 2D? We do not get hardware acceleration effects in Ubuntu 2D only in Ubuntu (3D).

Ubuntu 2D is a fall-back mode for computers that do not have video cards capable of video acceleration. Due to the great variety of hardware Ubuntu 2D is installed by default. Ubuntu (3D) becomes available when we activate the proprietary video driver and it should be available to all users.

Also, remember Ubuntu will always load the last used User Interface be it 3D or 2D. It could be that your assistant tried out Ubuntu 2D and now it is loading by default. You have to select Ubuntu from the menu. Click the cog icon.

Regards.

---

### Post by volido on 2012-01-27
In the attachment you can see how the monitor appears in the NVIDIA driver settings but at the same time is not recognized by the system. It's like the system is not fully agree with the driver recommended by the software center. 
Im not sure but I think I should install manually last version of the driver from  NVIDIA's site.  It  should be do it as root, am I wrong?  do you know how to get root privileges?
thank you

---

### Post by volido on 2012-01-27
thank you for your prompt response. the user account is not logging into ubuntu2d. actually in ubuntu 2d the  graphic performace is higher in this account without the presence of hardware acceleration.
in some point yesterday the system was recognizing the monitor. at the same time I had hardware acceleration.

---

### Post by volido on 2012-01-27
i think lthe driver proposed by the system is not right...shoulI download from NVIDIA last uypdate?...do you know how to install it?

---

### Post by volido on 2012-01-28
Finally I uninstalled Nuveau driver and the NVIDIA 
proposed by ubuntu. I installed last version of  NVIDIA drivers from [http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")
The conclusion is that graphic hardware acceleration is working  in Unity only when log-in as main user account. if guest or standard secondary accounts want to have hardware acceleration  in software as Draft-sight or Blender they will have to log in with Gnome classic option....kind of strange.... but I can live with it.
best

---

