---
title: "Mouse works fine, until it doesn't"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by ryanryanryan on 2012-01-29
Ubuntu 10.10, HP laptop dv6000 series.

USB mouse (Targus - AMU59US)

Problem - It works when I plug it in, then a minute later it stops. Sometimes, it works intermittently - that is, it will work freeze, then work, freeze, and so on.

Any help would be appreciated!

---

### Post by lechien73 on 2012-01-29
Hi Ryan,

I remember others having the same issue when 10.10 was first released.

Could you try the following:

[LIST=1]
[*]Reboot your PC and - after the self-test screen - hold down the Shift key so that the Grub menu appears.
[*]Press **e** to edit the Grub command line.
[*]After where it says "quiet splash", add "noapic nolapic"
[*]Press Ctrl-X to boot
[/LIST]
If that works, please let me know and we can make it permanent :)

---

### Post by ryanryanryan on 2012-01-29
Hey Matt - Thanks for the reply. Gonna give it a try.

Will keep u posted

---

### Post by ryanryanryan on 2012-01-29
PREFACE - I'm new to linux/ubuntu, and computers in general.

I have a dual-boot, with XP and 10.10. When I restart, i hit esc, then select the OS to boot from. After that, I did not see a self-test screen... 10.10 just loaded up. 

Any advice?

---

### Post by lechien73 on 2012-01-29
No problem. When you press Esc to select the operating system, does the screen look like the attached image?

If so, just highlight the Ubuntu entry, press **e** and then follow the rest of the instructions I posted above :)

---

### Post by ryanryanryan on 2012-01-29
Ahhh - Now I know what u r referring to. thx.

---

### Post by ryanryanryan on 2012-01-29
Still having difficulty. 

I did what you said, and it takes me to the RECOVERY MODE screen with various options (like RESUME, CLEAN, DPKG). Which option should i select?

---

### Post by lechien73 on 2012-01-29
Ok, sorry - the image I gave you had "Recovery Mode" selected. Please highlight the *first* reference to Ubuntu in the list - the one you would normally select to boot Ubuntu, then press **e** and follow the rest of the instructions.

My bad! :rolleyes:

---

### Post by ryanryanryan on 2012-01-29
Ok - did it. 

What's next?

---

### Post by ryanryanryan on 2012-01-29
Update - It's working! You are the man, Matt. 

Should I make the changes permanent?

---

### Post by lechien73 on 2012-01-30
Excellent & sorry for the delayed response - I had to go to bed :) yep, we can make the changes permanent now. This is where it gets fun!!

So, firstly open a terminal window (you can press Ctrl+Alt+T as a shortcut).

Now type the following:

```
gksu gedit /etc/default/grub
```

This will prompt you for your password and then open a text editor with a complex-looking file open (see the attached screenshot).

Scroll down to the line that reads:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

(I've highlighted it in the screenshot)

Add "noapic nolapic" between the quotes, so the line now reads:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic nolapic"
```

Save the file and quit from the text editor.

Now, at the command prompt, type:

```
sudo update-grub
```

That will make the changes permanent, and you won't have to add it each time you boot.

---

### Post by ryanryanryan on 2012-01-30
Ok. I have not changed my GRUB settings yet, and have rebooted several times WITHOUT making the "noapic nolapic" change, and my mouse is working fine!?!? 

Somehow, the mouse now works, but it is still choppy on occasion...  

Will keep you updated.

btw, I left a reply to you in the private message regarding the tutoring. I had not yet read this message, so you can disregard it.

---

### Post by ryanryanryan on 2012-01-30
Re-booted again, and the mouse is working... so that is good news. however, as I open more programs, and surf the web, I notice that the mouse cursor freezes up more often, and flash videos on youtube, or sites like pandora, the audio is choppy. 

When I first boot, and I go directly to pandora to stream music, for example, all is fine, until I start opening up different applications and the like. My hunch tells me its a RAM allocation issue.

---

### Post by lechien73 on 2012-01-30
Is the audio choppy with, or without, the "noapic nolapic" parameters?

I remember a few queries regarding choppy audio and video in 10.10.

---

### Post by ryanryanryan on 2012-01-30
Good morning Matt - (in LA)

Pardon my ignorance, but if I load into GRUB and change the settings, then Control-x to boot, the changes i made to the settings will only be active for that current session? If I reboot again, the changes are lost and the GRUB goes back to its original configuration?

PS - The mouse is working like a champion. Strangely, 10.10 keeps on working better and better the more I use it!!

---

### Post by lechien73 on 2012-01-30
No apology necessary :) yes, you are correct. If you make the changes to the Grub command line by pressing **e**, then editing it, and pressing Ctrl+X, then the changes are active until you reboot again.

The other instructions (editing /etc/default/grub) make it default for every session.

---

### Post by ryanryanryan on 2012-01-30
You are a very patient man, Matt. 

I understand now the basics of GRUB, editing, and making permanent changes.

Last thing I want to ask you, Matt. I plan on using Craigslist to find a tutor. I have A LOT of beginner-type issues that i need to resolve, not including Linux. Any tutor at this point will help get me running in the right direction. If you know of any computer tutor in LA area, let me know... and no rush.

I have hundreds of basic questions... XP, linux, hardware, basic networking, servers, programming... you name it.

Thanks again!

---

### Post by lechien73 on 2012-01-30
You're very welcome, it's no problem at all. I've emailed some contacts I have, so I'll let you know when they respond. I'll PM you my email address as well. And, in the meantime, feel free to send any questions you have on to me :)

---

