---
title: "Can OEM Windows Key be used to install a VM on Ubuntu on same PC?"
date: 2015-03-15
forum: New to Ubuntu
---

### Post by Geoffrey_Arndt on 2015-03-15
Have a couple PC's running Windows 7 now.   No install disks etc.   On one of the PC's, am thinking of converting it to Ubuntu only, but installing Win 7 using Virtual Box (have never used it before but would like to try it).   Anyway, from what I've read, that install on a VM will need the windows serial # or key (whatever it's called).

Can I just use the same key from the tag at bottom of laptop, to register win7 when doing the install in Virtual Box?  (I would not keep the other standard install on the laptop - in other words, laptop would boot only into Ubuntu, then I could use Windows as needed in the VM?) 

Thanks for input.

---

### Post by SeijiSensei on 2015-03-15
Are you talking about burning a set of installation DVDs from your current machine?  The product key on your machine's sticker will probably not work with a generic copy of Windows.  It might work with DVDs make from the machine's own installation, but it may not.  Often the OEM versions look for specific hardware features to insure they are running on the machines to which they were licensed.  

But rather than worrying and speculating, just give it a try.  You'll know soon enough whether it will work or not.

Otherwise you can buy an OEM version of Windows from a seller like Newegg.  They cost $100.

---

### Post by Geoffrey_Arndt on 2015-03-15
Thanks SeijiSensei,  think I'll have a go with Newegg version.   

ga

---

### Post by kerry_s on 2015-03-15
just grab a copy of windows 10 preview, it's free. it's like a updated windows 8.

---

### Post by sandyd on 2015-03-15
> **kerry_s said:**
> just grab a copy of windows 10 preview, it's free. it's like a updated windows 8.

Until April 15th, 2015.

---

### Post by PhilGil on 2015-03-15
> **kerry_s said:**
> just grab a copy of windows 10 preview, it's free. it's like a updated windows 8.That's a good idea, but do be aware that the TOS allows Microsoft to collect a lot of data about your usage habits. Using the tech preview is probably not a good idea if you are exceptionally concerned about privacy or will be working with confidential data.

[I]When you acquire, install and use the Program, Microsoft collects information about you, your devices, applications and networks, and your use of those devices, applications and networks. Examples of data we collect include your name, email address, preferences and interests; browsing, search and file history; phone call and SMS data; device configuration and sensor data; and application usage. For example, when you:

[/I]
[LIST]
[*][I]install the Program, we may collect information about your device and applications and use it for purposes such as determining or improving compatibility,
[/I] 
[*][I]use voice input features like speech-to-text, we may collect voice information and use it for purposes such as improving speech processing,
[/I] 
[*][I]open a file, we may collect information about the file, the application used to open the file, and how long it takes any use it for purposes such as improving performance
[/I] 
[*]*[I]or *enter text, we may collect typed characters and use them for purposes such as improving autocomplete and spellcheck features.[/I] 
[/LIST]

As far as using the Win 7 OEM license you already have, my understanding is that a Pro license allows virtualization, a Home license does not. You would need to obtain clean media for the install as recovery disks typically won't work in Virtualbox.

---

### Post by Geoffrey_Arndt on 2015-03-15
Good points about privacy . . . I thought about the test version but am thinking a pro-license may make sense.   Only need windows for a couple engineering and mapping programs anymore.    Thanks again!

---

### Post by PhilGil on 2015-03-15
> **Geoffrey_Arndt said:**
> Good points about privacy . . . I thought about the test version but am thinking a pro-license may make sense.   Only need windows for a couple engineering and mapping programs anymore.    Thanks again!Just to clear up any misunderstanding - my comments about Win 7 Home vs. Professional were directed specifically at OEM licensed versions. A full retail version of Win 7 Home should be fine to install in VirtualBox. No need to pay the premium for a Pro license unless you need the added functionality.

---

