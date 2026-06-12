---
title: "VirtualBox"
date: 2009-06-19
forum: Philippine Team
---

### Post by badrra on 2009-06-19
Meron na ba sanyong nakagawa ng ganitong scenario? 

I just have an icon on my Ubuntu Desktop and when I click on it, it will pull up an XP Client application say ym. Virtual machine should be running on the background (headless). 

I was thingking or file sharing and call an EXE file withing XP Guest. But wouldnt that invoke wine? If wine is installed. 

Any suggestions? 

Thanks in advance.

---

### Post by jsgotangco on 2009-06-19
Try checking Virtualbox seamless mode.

Parralles and VMWare on the Mac has such features called Coherence and Unity respectively

---

### Post by konqueror7 on 2009-06-19
either use Wine or VirtualBox

Wine if just want to directly execute the app; with VirtualBox, you still have to boot to the OS, and switch to seamless mode for what you require, but you can add a startup entry in which a XP VM would automatically start during startup (though depends on your comp specs)

---

### Post by wersdaluv on 2009-06-19
You can access files on your host OS (Ubuntu) on your virtual Windows by adding a shared folder. Just go to the settings of the virtual machine then "Shared Folders" tab. Click the folder icon with the plus sign then you'll know what to do from there :)

---

