---
title: "intel 915G x86/MMX/SSE2  Drivers"
date: 2014-05-22
forum: New to Ubuntu
---

### Post by kazica on 2014-05-22
For some reason my inbuilt graphtics aren't showing to update the drivers now I tryed playing Guns of Icirus earlier adn it weas so laggy and quality of the grapathics them selves so bad I had no clue what I was doing so had to quit the game. Any one know how I can get Ubuntu to recognise them? Any how ran a thingy to find out what they are and this poped up.



```
00:02.0 VGA compatible controller [0300]: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller [8086:2582] (rev 04)

```


Any help is apricated. Much thanks.

---

### Post by Vladlenin5000 on 2014-05-22
You won't have any pleasurable experience playing games with that chip and it's not because of drivers. Intel drivers are open-source and usually included so you don't need to do further steps in order to have proper video output (games are an all different beast).
Here's the system requirements for the game Guns of Ic**a**rus: [http://gunsoficarus.com/faq/#reqs](http://gunsoficarus.com/faq/#reqs)
Hopefully by now you understand why that happened and why it would happen as well in Windows.

---

### Post by deadflowr on 2014-05-22
I have that card on some machine, and performance overall is okay.(not great, but workable; to a degree)
The real problem might be that Ubuntu's desktop(unity) is probably too overbearing on the card, as it is a graphics heavy interface.
Perhaps if you install a lighter desktop interface, such lxde, the performance will improve.

Of course, whether or not you are running Ubuntu's default interface is a wild guess, by me.

---

### Post by kazica on 2014-05-22
[IMG]https://scontent-b-lhr.xx.fbcdn.net/hphotos-prn2/t1.0-9/p526x296/10313467_10152417257425349_8678118737501379343_n.jpg[/IMG]

Ok so Here's my specs ( this machine was built to play THAT game). And yuops I'm runniing Ubuntu's defualt settings ( AS I'm that new to this and it was recomneded by a freind whio uses Ubuntu that I could easily work the game on this). If this is the case then I'm not sure what else to do. I have no idea how to use any other os's Linux has to offer and I can't be arsed with Windows any more.

---

### Post by Yellow Pasque on 2014-05-22
> For some reason my inbuilt graphtics aren't showing to update the drivers
What does that mean?
```
glxinfo
```

---

### Post by Vladlenin5000 on 2014-05-22
> **Temüjin said:**
> What does that mean?
```
glxinfo
```

It means there's no additional (proprietary) drivers suggested. The reason for that is in my previous post. 
Now, @deaflowr, I wasn't saying that particular system, namely the Intel graphics, are bad. It can run Unity acceptably but just by reading the minimum requirements for that game one must wonder why someone would so ignorantly say the OP's machine is good for that. It isn't, never was, never will be... Just ask yourselves one simple question: Would this machine run Windows 7 acceptably? There's your answer... Please pay attention to the following:

*- Windows 7 or Mac OS X 10.6 or later, or Ubuntu 12.04 LTS, 32-bit *-> CHECK
*- 2 GHz processor* -> CHECK but... Am I the only one thinking that gamers nowadays when writing this requirements are thinking about at least a Intel dualcore @2GHz or higher, not a Pentium 4?
*- 2 GB RAM -> CHECK (the bare minimum...)*
***- Dedicated video card with 256 MB VRAM*** -> _NO dedicated video card and probably NO 256MB VRAM_

This is the problem, not the OS, not drivers or anything else the user could change or tweak...

Then there's this pearl of wisdom: *As a general rule of thumb, if you can run a recent game like Portal 2, you can run Guns of Icarus Online. *The point being, from the start, you can't run Portal 2 in such old hardware, not even in your dreams.

---

### Post by kazica on 2014-05-26
To you who stated it won't run it never will and never couldl. Tghis machine was built round the Minium specs to do so. Not by me mind you. To this day I wisdh UI still had my Acer qaspire laptop with  the Ati- radon card that had 550 mb of Dedicated graptjhics that little beast ( even though if it was still working) was a glorious 4 years old and built for gameing. Just a shame that this thing wont be able to do that. Ah well. Live and let learn.

---

### Post by Vladlenin5000 on 2014-05-26
Even assuming you can build a machine for gaming around the minimum specs of a not-so-demanding game, yours isn't there yet, as already clearly and inequivocally shown. 
You need to learn the difference between a dedicated graphics card with dedicated VRAM and what you have, an embedded one, relatively old and using a reserved part of your system's memory.

---

