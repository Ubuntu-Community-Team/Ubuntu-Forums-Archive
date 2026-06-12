---
title: "Crashed Oneric in VirtualBox"
date: 2011-06-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2011-06-13
I have Oneric running in virtualbox so I don't know if the following is a problem with VB or Oneric in general. Can someone try opening the workspace switcher and dragging an icon from the launcher to a new workspace (I used Libre). 

I was hoping that the application would open on that workspace - instead the whole VM went down.

---

### Post by coffeecat on 2011-06-13
> **Peter09 said:**
>  Can someone try opening the workspace switcher and dragging an icon from the launcher to a new workspace (I used Libre). 

I was hoping that the application would open on that workspace

Can you do that in Oneiric anyway? In Natty if you try that, the icon simply slides back into the launcher when you release it.

> **Peter09 said:**
> instead the whole VM went down.

It did for me too - very suddenly. :sad: That's in a virtual Oneiric in Vbox 4.0.8. Then the VirtualBox Manager shows the "Aborted" message for the Oneiric machine

I've had sudden collapses of Oneiric in VB before, but I've never really  determined what the triggering factor was. I've not tried a drag of a  launcher to a workspace before so I guess it's just Oneiric being flakey  in Vbox. It'll be interesting to see what people running "real"  Oneirics experience.

---

### Post by coffeecat on 2011-06-13
> **Peter09 said:**
> I don't know if the following is a problem with VB or Oneric in general.

As no one has posted of their experience in a "proper" install of Oneiric, I booted up my laptop Oneiric, updated it and booted into the new 3.0.0 kernel and I cannot get it to crash by trying this. It behaves the same way as in Natty. I didn't try this with the 2.6.39 kernel.

However, after updating my virtual Oneiric with the 3.0.0 kernel, I managed to get it to collapse by dragging the LO icon to a workspace - but only on the 3rd attempt. It also collapsed once when I merely minimised the VM window.

---

### Post by Peter09 on 2011-06-13
Looks like a VB bug. I have also noted (as an aside ) that VB does not catch the Meta key, so attempting to bring up the dash using keyboard shortcuts triggers the 'host' interface.

---

### Post by coffeecat on 2011-06-13
> **Peter09 said:**
> Looks like a VB bug. I have also noted (as an aside ) that VB does not catch the Meta key, so attempting to bring up the dash using keyboard shortcuts triggers the 'host' interface.

Yes, that's interesting. I've also found that combos such as ctrl-alt-F1 are captured by the host even when the guest is focussed. Which is tedious when a guest like Oneiric is misbehaving and you need a virtual console. (Philosophical question: how do you get a virtual console in a virtual machine? :?)

The other thing that happened to me when virtual Oneiric was playing up and the shutdown button wasn't responding to mouse clicks, so I tried to kill the virtual xserver with alt-Print-k. Big mistake! The xserver on the host went down as though pole-axed taking with it VirtualBox, the virtual Oneiric machine, Firefox and a half-written forum post, Banshee playing my favourite music and probably an open terminal and a nautilus window.

I was not amused. :(

---

### Post by lucazade on 2011-06-13
> **coffeecat said:**
> (Philosophical question: how do you get a virtual console in a virtual machine? :?)


Using ctrl and altgr (+f1) on the right side of the keyboard ;)

---

### Post by coffeecat on 2011-06-13
> **lucazade said:**
> Using ctrl and altgr (+f1) on the right side of the keyboard ;)

Unfortunately, it doesn't work. :(

Also - I know it's a different matter - but I'm fairly sure I used AltGr+Print+k to try to kill the xserver in the virtual machine. I did that because I've got into the habit of using the AltGr for magic key combinations   after using a machine/keyboard where only the AltGr key, not the Alt, worked for this.

Whatever, I'm not trying that one again in a hurry. :|

---

### Post by lucazade on 2011-06-13
> **coffeecat said:**
> Unfortunately, it doesn't work. :(

Also - I know it's a different matter - but I'm fairly sure I used AltGr+Print+k to try to kill the xserver in the virtual machine. I did that because I've got into the habit of using the AltGr for magic key combinations   after using a machine/keyboard where only the AltGr key, not the Alt, worked for this.

Whatever, I'm not trying that one again in a hurry. :|

it looks like my virtualbox is special! 
it can switch to vts but cannot handle gnome-shell. who knows!! :)

---

### Post by coffeecat on 2011-06-13
> **lucazade said:**
> it looks like my virtualbox is special! 
it can switch to vts but cannot handle gnome-shell. who knows!! :)

For some reason, it suddenly worked! \o/ \o/ \o/.

I definitely had the virtual window focussed before when it didn't work, because I typed something into the terminal in the virtual machine to be sure. My virtual machine must have moods, and I just caught it in a good one. :)

Thanks for the tip!

---

