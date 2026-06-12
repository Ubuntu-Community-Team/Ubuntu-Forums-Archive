---
title: "Ubuntu not booting anymore"
date: 2013-08-25
forum: New to Ubuntu
---

### Post by nexor2 on 2013-08-25
As the title says my Ubuntu won't boot anymore. (BTW I ran Ubuntu on an external harddrive, or at least it is intalled on there) I wanted to install a game and therefore installed Wine and new graphic card driver (I hope this is the right word, sorry I'm German :) ). Using **jockey-gtk **I went to "additional drivers" and installed the driver for ATI/AMD (the bottom one), as I have an ASUS G73J which runs ATI Mobility Radeon HD 5870.

**[SIZE=2]My system Specs:[/SIZE]**

[TABLE]
[TR]
[TD="class: DocText"]component[/TD]
[TD="class: DocText"]Details[/TD]
[TD="class: DocText"]Teilbewertung[/TD]
[TD="class: DocText, width: 100"]Gesamtbewertung[/TD]
[/TR]
[TR]
[TD="class: DocText, width: 125, bgcolor: #eaeaea"]Processor[/TD]
[TD="class: DocText, bgcolor: #f0f0f0"]Intel(R) Core(TM) i7 CPU Q 740 @ 1.73GHz[/TD]
[TD="class: DocText, width: 75, bgcolor: #f5f5f5"]7,1[/TD]
[TD="class: DocText, width: 100, bgcolor: #e0e0e0"][TABLE="width: 100"]
[TR]
[TD="align: center"]5,9[/TD]
[/TR]
[TR]
[TD="align: center"]  Ergibt sich aus der niedrigsten Teilbewertung (not important)[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[TD="class: DocText, width: 125, bgcolor: #eaeaea"]main memory (RAM)[/TD]
[TD="class: DocText, bgcolor: #f0f0f0"]8,00 GB[/TD]
[TD="class: DocText, width: 75, bgcolor: #f5f5f5"]7,5[/TD]
[/TR]
[TR]
[TD="class: DocText, width: 125, bgcolor: #eaeaea"]Grafik[/TD]
[TD="class: DocText, bgcolor: #f0f0f0"]ATI Mobility Radeon HD 5870[/TD]
[TD="class: DocText, width: 75, bgcolor: #f5f5f5"]6,4[/TD]
[/TR]
[TR]
[TD="class: DocText, width: 125, bgcolor: #eaeaea"]Grafik (games)[/TD]
[TD="class: DocText, bgcolor: #f0f0f0"]4826 MB overall available graphic space[/TD]
[TD="class: DocText, width: 75, bgcolor: #f5f5f5"]6,4[/TD]
[/TR]
[TR]
[TD="class: DocText, width: 125, bgcolor: #eaeaea"]primary harddrive[/TD]
[TD="class: DocText, bgcolor: #f0f0f0"]30GB frei (116GB overall)[/TD]
[TD="class: DocText, width: 75, bgcolor: #e0e0e0"]5,9[/TD]
[/TR]
[TR]
[TD="class: SubText, colspan: 4"]Windows 7 Home Premium[/TD]
[/TR]
[/TABLE]


After installing the graphic card drivers, I had to restart the laptop. But Ubuntu wouldn't boot anymore. After selecting Ubuntu (other option would be windows 7) right at the beginning, the screen just stayed black. After pressing the "Power-button" the laptop turned off immediately, no shutting down. Windows still works perfectly fine. Funny thing is: When I start windows and shut it down again and select Ubuntu after booting again I get to the menu where I can choose between Ubuntu and Ubuntu recovery. If I select Ubuntu it tells me "out of memory" and the screen simply turns purple and nothing happens anymore. If I select Ubuntu recovery it tells me that i have to boot Kernel first  and takes me back to the screen where I can choose between booting Windows 7 or Ubuntu.

I am a complete beginner and have no idea how to fix this. Thank you for any help! :)

---

### Post by Boab1993 on 2013-08-25
Hi there nexor2,

Lets try some experiementing.

Does the screen where it allows the selection look like the attachment below?

If so press 'E' while over the ubuntu option.

There should be now an editable box infront of you.

There should be a line with ="quiet splash" 

Change it to ="quiet splash nomodeset"

Follow the command to boot.

If it works then we can set it permantly, if not, more thinking shall be done.

Hope this helps

---

### Post by eternal243 on 2013-08-25
To me it sounds like you installed the wrong drivers, anyway, it would help if you told us what version of linux you are using and which kernel you have.

It doesn't sound like it would be impossible to fix though, I have had worse problems than that, even though I did need some help to fix it. You could try to boot from a live cd/usb, and then mount your linux system from terminal and then revert back to your original drivers. I'm not really sure on the specific commands to use though, and I don't want to mess up your system more than it already is. Maybe someone else can help.

**EDIT: try Boab1993's suggestion first, the nomodeset option is easier if it works.**

---

### Post by nexor2 on 2013-08-25
[SIZE=3]Thanks for your help! I am using [COLOR=#333333][FONT=Ubuntu]Ubuntu 12.04.3 LTS. I don't know which kernel I'll try to tell you soon. The screen does look similar though not the same (purple and only 2 options). There is the line with "quiet splash" and I did change it. But I am not quite sure what to do afterwards. Do I have to save/confirm? It doesn't seem to change anything. "Follow the command to boot" I did go to the command menu and typed "boot" but it still told me out of memory.> out of memory. [/FONT][/COLOR][/SIZE] WRONG! Sorry it told me: You have to load Kernel first.

---

### Post by nexor2 on 2013-08-25
Ah and btw it doesn't matter if you mess up Ubuntu (I have hardly anything on there), as long as windows stays fine. Changing stuff for Ubuntu won't affect windows right?

---

### Post by nexor2 on 2013-08-25
I unfortunately don't know my Kernel, it only shows: Ubuntu, with Linux 3.5.0-39-generic But I may have found the problem (?). When trying to boot it tells me in the booting command list: 

error: out of memory (several times)
error: stack overflow detected
**no such device: D49610369610K14**
no such partition
out of memory
you need to load kernel first

And in grub it tells me:

some lines with commands...
linux /boot/vmlinux - 3.5.0-39-generic  **root=UUID=D49610369610K14  **loop=/ubuntu/disks/root.disk ro quiet splash vt.handoff=7
initird/boot/initrird.img-3.5.0.39-generic

Root is **D49610369610K14 **and it can't find it. Maybe that has some relevance? Don't forget I have no idea about this kind of stuff...

---

### Post by eternal243 on 2013-08-25
> Linux 3.5.0-39-generic This is your kernel.

> When trying to boot it tells me in the booting command list:

error: out of memory (several times)
error: stack overflow detected
no such device: D49610369610K14
no such partition
out of memory
you need to load kernel first

And in grub it tells me:

some lines with commands...
linux /boot/vmlinux - 3.5.0-39-generic root=UUID=D49610369610K14 loop=/ubuntu/disks/root.disk ro quiet splash vt.handoff=7
initird/boot/initrird.img-3.5.0.39-generic

Root is D49610369610K14 and it can't find it. Maybe that has some relevance? Don't forget I have no idea about this kind of stuff... 

Hmm, I'm not very confident in analyzing these kinds of problems, but the stack overflow and out of memory messages suggests that you get stuck in some sort of infinite loop that keeps trying to load something that it can't find, and it keeps trying until your RAM gets overloaded.

The **"no such device"** and **"no such partition"** messages I have no idea about, since I don't know what **D49610369610K14** is referring to, but I imagine it is trying to find the harddrive and partition where linux is installed, this happened to me about 2 years ago and the problem turned out to be in a messed up boot configuration file. But I don't remember enough of that episode to tell you if you got the same problem or if it is something else. It could also be that you have a damaged sector on your harddrive where ubuntu is installed. I got help from a friend to solve it for me, although everyone else just suggested that I should reinstall my OS. But it was actually quite simple once we figured out what was wrong.

---

### Post by nexor2 on 2013-08-25
Ok thanks for you help :) I think I will simply reinstall my OS now... Is it ok if I simply delete the folder "Ubuntu" on my external harddrive (I can access it from windows) or do I have to more stuff (like deinstalling)?

---

### Post by eternal243 on 2013-08-25
Dunno, depends on how you installed it I guess, I have never had linux installed on any external device.

---

### Post by nexor2 on 2013-08-25
Ok thanks for you help :) I think I will simply reinstall my OS now... Is it ok if I simply delete the folder "Ubuntu" on my external harddrive (I can access it from windows) or do I have to more stuff (like deinstalling)?


Oops accidently posted again... Can i delete the post somehow?

---

### Post by oldrocker99 on 2013-08-25
Don't delete the "Ubuntu" folder on the external HD; just reinstall, and it should offer to reformat the external drive and go from there.

---

### Post by Boab1993 on 2013-08-25
Sorry i took so long to reply, i was dog sitting for a friend.

For using the 'nomodeset' fix, you press ctrl-x or f10 to continue once you have edited the quiet splash line.

As for your errors, since you have 8 GB of RAM, and this being a graphical error, i imagine your out of graphical memory, the device with the long string of number and letters i imagine will be your graphics card. Could be wrong.

Re-Installing shouldnt be necessary but if you want to re-install then all you have to do is use an ubuntu install CD image and go to the option 'erase 'ubuntu' and install 'ubuntu' at the begining of the setup.

Hope this helps.

---

