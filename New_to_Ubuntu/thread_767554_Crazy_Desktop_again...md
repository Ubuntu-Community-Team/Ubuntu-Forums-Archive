---
title: "Crazy Desktop again.."
date: 2008-04-25
forum: New to Ubuntu
---

### Post by yngvrr on 2008-04-25
Okey.. I have finally managed to download compizconfig-settings-manager but now I cant use it..

Desktop effects dont work... Ive installed compiz config settings manager and when I open it and select effects nothing happens so I opened Appearence Preferences-Visual Effects and selected Extra - and the computer said : Desktop effects could not be enabled.

What do I have to do to get this thing working?

---

### Post by russo.mic on 2008-04-25
did you install support for your 3d acceleration? why don't you run compiz from a terminal and give us the output.  Include what kind of graphics card your using.

Russo

---

### Post by Joeb454 on 2008-04-25
Sounds like you need to install the drivers for your graphics card.

---

### Post by yngvrr on 2008-04-25
I just installed ubuntu 8.04 so I have not yet installed any drivers that dont come with it.. um also I dont know how to install drivers...
Anyways..

Here is the output: 

GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

And my graphic card.. Ive been told I could find in this.. but I dont know :   

VGA compatible controller: ATI Technologies Inc Radeon Mobility U1 (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Video
	Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 10
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 9000 [size=256]
	Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at d0120000 [disabled] [size=128K]
	Capabilities: <access denied>
Is this it?

---

### Post by hermes0710 on 2008-04-25
Go to "System" > "Administration" > "Hardware Drivers". You should see an entry for your card driver. Tick to enable it (You must have an internet connection established in order to have the driver downloaded by the restricted drivers manager). Reboot and tell us if you can enable the effects

---

### Post by yngvrr on 2008-04-25
Hardwere drivers is empty.. nothing to tick..

---

### Post by russo.mic on 2008-04-25
Go to a terminal and hit a sudo apt-get update, then open up the hardware manager.

Russo

---

### Post by stephentheh on 2008-04-26
i'm having this same issue... even just tried running the apt-get update command and then tried to view hardware drivers, still nothing.

i think compiz might actually be running though, how do i tell? my desktop effects are already turned on but i don't know how to use them or what to look for. any thoughts/help?

---

### Post by russo.mic on 2008-04-27
Hit Control Alt Left/Right

Do you see the plane switcher?

sudo apt-get install compizconfig-settings-manager

That will get you the compiz settings.

Russo

---

### Post by WinterWeaver on 2008-04-27
Also check if you have the advanced effects enabled.

right-click the desktop, and select change background. Then under the Visual effects tab, make sure you have Extra selected.

---

