---
title: "Editing      /etc/modprobe.d/sound"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by allalogie on 2008-07-26
Hi there

I am trying to configure my sb live soundcard using the following......

[I]Excute "cat /proc/asound/modules" from command line to know which module
are loaded. Perhaps the output will be:
Code:

0 snd_??? <- module for on-board soundchip
1 snd_emu10k1

Then describe the following in /etc/modprobe.d/sound .

Code:

options snd-emu-10k1 index=0
options snd-??? index=1

Execute "sudo-update modules", and restart the system.
[/I]

but I'm unable to enter the above in [I]/etc/modprobe.d/sound
[/I]

All I get in the terminal is

bash: /etc/modprobe.d/sound: No such file or directory

How can I edit this file?

Many thanks in advance

Allalogie

---

### Post by talsemgeest on 2008-07-26
You can try ```
gksudo gedit /etc/modprobe.d/sound
``` but based on what you said before it is probably going to come up with a blank file.

Hope this helps :)

---

### Post by caljohnsmith on 2008-07-26
Can you give us a link to the directions you are following? We can help you do that simple task you want to do, but it usually helps to state what you are ultimately trying to accomplish; that /etc/modprobe.d/sound is not a standard file that comes with ALSA in Ubuntu, and you may actually need to add those options for your sound card in /etc/modprobe.d/alsa-base instead. 

It's up to you, but that's my recommendation. :)

---

### Post by allalogie on 2008-07-27
Hi

Thanks for the reply regarding your recommendation. I'm trying to get my SB live soundcard to work on 8.04 on an old Dell Dimension desktop. 

I actually edited the file /etc/modprobe.d/sound, as above, and it worked for a while, then started getting feedback from the speakers. I was just about to try again when I saw your reply.

I was following this post......( apologies, for some reason I can't quote it
properly)

[B][I] Re: Sound blaster live
Hi Chris,

Please try my solution .

Excute "cat /proc/asound/modules" from command line to know which module
are loaded. Perhaps the output will be:
Code:

0 snd_??? <- module for on-board soundchip
1 snd_emu10k1

Then describe the following in /etc/modprobe.d/sound .

Code:

options snd-emu-10k1 index=0
options snd-??? index=1

Execute "sudo-update modules", and restart the system.

To know the sound cards which the system recognize and the order
of them, execute "cat /proc/asound/cards" .

Here is the output of my system.
Code:

$ cat /proc/asound/cards
0 [YMF744         ]: YMF744 - Yamaha DS-XG (YMF744)
                     Yamaha DS-XG (YMF744) at 0xe9000000, irq 11
1 [SI7018         ]: SI7018 - SiS SI7018
                     SiS SI7018 PCI Audio at 0xd000, irq 11

I hope this will help.
Last edited by FarEast; January 10th, 2006 at 10:56 AM. 
[/I][/B]
The 12 post thread is here.......


[http://ubuntuforums.org/showthread.php?t=114551&highlight=sb+live](http://ubuntuforums.org/showthread.php?t=114551&highlight=sb+live)

If you have a better solution, it would be much appreciated

Cheers

---

