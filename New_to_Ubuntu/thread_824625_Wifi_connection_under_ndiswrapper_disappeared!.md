---
title: "Wifi connection under ndiswrapper disappeared!"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by geomur on 2008-06-10
I have an old Tecra 8000 running xubuntu 8.04 that I got going with a zyxel g-260 usb wifi adapter and ndiswrapper.  When I started it up today, no wifi, no wireless icon in network settings (only a point-point icon).  As a noob, I've no idea why it seems to have uninstalled itself.  Any help would be much appreciated.

Thank you, Geoff.  :confused:

---

### Post by cardinals_fan on 2008-06-10
Have you installed any updates recently?

---

### Post by geomur on 2008-06-11
Hi and thanks for your response.

I did install the standard batch recommended by the update manager...would this have had an effect?  How do I undo it!?

Many thanks

Geoff

---

### Post by sam_delta on 2008-06-11
try running the module again. go into a terminal and type
```
sudo modprobe ndiswrapper
```

tell us if it works
sam

---

### Post by cardinals_fan on 2008-06-11
> **sam_delta said:**
> try running the module again. go into a terminal and type
```
sudo modprobe ndiswrapper
```

tell us if it works
sam
Exactly what I was going to suggest ;)

If a kernel upgrade was performed, ndiswrapper might have been removed.  Just follow sam_delta's suggestion and see what happens.

---

### Post by geomur on 2008-06-12
Hi Folks

Yes, that worked first time!

Many thanks to you all, where would us newbs be without you guys!

Best wishes

Geoff

---

### Post by sam_delta on 2008-06-12
glad it worked
enojoy ubuntu :)
sam

---

### Post by geomur on 2008-06-14
Hi Sam

Your fix clearly works....but I have to do it every time I restart the laptop!  Somehow ndiswrapper is not installing the adapteron power-up.  Any ideas?  Many thanks.

Geoff

---

### Post by balagosa on 2008-06-14
hmmm....weird. a quick fix would be adding ```
sudo modprobe ndiswrapper
``` to the start-up commands. But that is just being downright lazy and I am sure there is a more **formal** fix. Did you follow a guide on installing NDiswrapper? If so, did it include command to make NDiswrapper load on startup?

---

### Post by sam_delta on 2008-06-14
> **geomur said:**
> Hi Sam

Your fix clearly works....but I have to do it every time I restart the laptop!  Somehow ndiswrapper is not installing the adapteron power-up.  Any ideas?  Many thanks.

Geoff

yes, try this command ```
sudo ndiswrapper -m
``` 

reboot
tell us if it works
sam

---

### Post by balagosa on 2008-06-14
> **sam_delta said:**
> yes, try this command ```
sudo ndiswrapper -m
``` 

reboot
tell us if it works
sam

I am not sure what ```
-m: write configuration for modprobe
``` does, but this might me the **formal fix**. if you dont mind sam, can you explain to non-OP what the command does.

---

### Post by sam_delta on 2008-06-14
alright sure no problem

each time you boot up, you have to load the module by typing 
"sudo modprobe ndiswrapper"
in other words, you are manually running the module

"sudo ndiswrapper -m" writes the configuration to the modprobe config file,,,,
so everytime you boot up, ndiswrapper module already appears under the modprobe config, and therefore starts at boot time

modprobe is the command that fires up a module, and it has a config file which contains info of all the modules and configurations it needs to run, thats why you do not type "sudo modprobe <module> for every module in the computer, so we just simply adding ndiswrapper to that config

if you have more questions, feel free to ask, thats how we learn

sam

---

### Post by geomur on 2008-06-16
Hi Sam,

Yes, that instruction worked.  Many thanks, and also good to read the follow-on answer on why it works.

Best wishes

Geoff

---

### Post by sam_delta on 2008-06-16
alright, glad its working

good thing you guys asked why it works, its always better to know what you are doing cuz thats how you start learning how the system works, most of the times, i try to explain the solution and explain each command, instead of just telling everyone to copy paste commands.

again, thanks for asking

enjoy ubuntu :)
sam

---

### Post by SPRC on 2008-11-16
Thanks Sam_Delta,

your solutions helped me, too. 

However, when I try to use that last command "**sudo ndiswrapper -m**", I get the message "**module configuration already contains alias directive**", and after reboot, the problem is not solved, and I must use "sudo modprobe ndiswrapper" once again...:(

Can u please help me?

---

