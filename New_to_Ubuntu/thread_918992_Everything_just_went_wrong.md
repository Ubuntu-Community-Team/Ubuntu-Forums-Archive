---
title: "Everything just went wrong"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by fignig on 2008-09-13
okay so every possible thing has probably gone wrong trying to make this desktop cooler. i tried to install cairo-dock and i was trying to install the animations for compiz and i installed xgl instead of the nvidia server x and now all of my toolbars are gone, i can't move any windows, and nothng is really working. this is probably the oddest problem ever. is tehre anything like a system restore so i can go back? b/c i'm pretty much ****** right now...

---

### Post by Ub1476 on 2008-09-13
There's no system restore in Ubuntu. Just remove the packages you installed. If you installed via terminal, you can press the up key (arrow) to see previous history. Just change the "install" command to "remove". 

See here to install cairo-dock:
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

Otherwise AWN and Kiba-dock are good too.

Install the nvidia driver from Hardware Drivers and Advanced Desktop Effects from add/remove. Reboot. Should hopefully fix the missing stuff.

---

### Post by overdrank on 2008-09-13
> **fignig said:**
> okay so every possible thing has probably gone wrong trying to make this desktop cooler. i tried to install cairo-dock and i was trying to install the animations for compiz and i installed xgl instead of the nvidia server x and now all of my toolbars are gone, i can't move any windows, and nothng is really working. this is probably the oddest problem ever. is tehre anything like a system restore so i can go back? b/c i'm pretty much ****** right now...

Hi and you may try and boot into recovery mode which is usually the second choice from the grub and use the xfix option.

---

### Post by fignig on 2008-09-13
> **overdrank said:**
> Hi and you may try and boot into recovery mode which is usually the second choice from the grub and use the xfix option.

may i just say never listen to overdrank. i did what he said boot into recovery mode and i tried to use xfix. and what i got was worse problems. now i can't even boot from my hard disk i'm running off a live cd right now. is there anyway to fix the problem from here? can i even access file so i can back them up?

---

### Post by Sub101 on 2008-09-13
Probably shouldn't insult the Forum Staff. But on your problem...

You should be able to access all your files on your pc as you normally would. 

Can you boot into any kernel?  How far does booting get you?

---

### Post by fignig on 2008-09-13
i tried going into the filesystem and it says i can't mount it. i think i'm totally ****'d right now...i can't even boot into my old system. is there anyway to access my files so i can save some stuff? you guys totally let me down...

---

### Post by fignig on 2008-09-13
> **Sub101 said:**
> Probably shouldn't insult the Forum Staff. But on your problem...

You should be able to access all your files on your pc as you normally would. 

Can you boot into any kernel?  How far does booting get you?

well he shouldn't give the worst advice i've ever gotten on this forums then....but right after it gives me the option to the grub modes. and it's going into the login screen, everything goes blue. and my 2nd monitor is just flashing green lines. i can't boot into it at all...

---

### Post by northern lights on 2008-09-13
> **fignig said:**
> may i just say never listen to overdrank. i did what he said [...] and what i got was worse problems
:roll:
Humility is said to be an applaudable trait...

Further it's in the best interest of those needing help to remain courteous to those that can provide such.

---

### Post by Sub101 on 2008-09-13
The guys on the forum are individuals that try to help out of an interest in helping the community. All they can do is offer advice on what they think will fix your problems. Nothing more. So the idea of you blaming those that try and help seems rude to me. However.

When you say you cant boot, do you mean grub wont load? Or after grub your system gets no further? The more information you can offer the more we can help.

---

### Post by fignig on 2008-09-13
> **northern lights said:**
> :roll:
Humility is said to be an applaudable trait...

quit trying to be cool, if ur not gonna help then don't post..

---

### Post by dRock1286 on 2008-09-13
> **fignig said:**
> ...you guys totally let me down...
Again...You'll get a lot better information from people if you are nicer.  It's just how the world works.

[quote=fignig]well he shouldn't give the worst advice i've ever gotten on this forums then....[/quote]
C'mon man.  What he told you to do made perfect sense.  In your situation, it just didn't work.  It happens.  Thats all apart of the game of Linux.  


[quote=fignig]but right after it gives me the option to the grub modes. and it's going into the login screen[/quote]

Are you able to login or does it change screens before you can?

---

### Post by fignig on 2008-09-13
> **Sub101 said:**
> The guys on the forum are individuals that try to help out of an interest in helping the community. All they can do is offer advice on what they think will fix your problems. Nothing more. So the idea of you blaming those that try and help seems rude to me. However.

When you say you cant boot, do you mean grub wont load? Or after grub your system gets no further? The more information you can offer the more we can help.

i don't know what more information i can give. right after grub menu counts down it goes blue and i can't see anything. i'm pretty sure grub could load b/c i didn't really mess w/ it. all i can tell you really is that i can't boot into it, and i can't access my files from this live cd. is there anway i can reverse an xfix? b/c that's really the root of the problem

---

### Post by fignig on 2008-09-13
> **dRock1286 said:**
> Are you able to login or does it change screens before you can?

no i can't login b/c the screen goes blue. i can't even see the login screen.

---

### Post by dRock1286 on 2008-09-13
Why can't you access files with a live cd?  it should mount your harddrive no problem.  I am so confused by your situtaion.

---

### Post by fignig on 2008-09-13
> **dRock1286 said:**
> Why can't you access files with a live cd?  it should mount your harddrive no problem.  I am so confused by your situtaion.

it says unable to mount the seleted volume and gives me this.
error: device /dev/sda1 is not removable

error: could not execute pmount

so nope i can't access anything and i can't even boot into it. i'm stuck here. and i need help badly...

---

### Post by northern lights on 2008-09-13
> **fignig said:**
> quit trying to be cool, if ur not gonna help then don't post..

I feel inclined to really start flaming, but I'll control myself.

Apart from the Linux community being more responsive than any proprietary support you'll ever encounter, you might want to remind yourself that all people trying (or due to your attitude formerly trying) to help you are people with a day job and are doing so in their spare time.

If you ain't satisfied, ask for a refund. Wait a minute, you got your OS and the support for free, right?!



P.S. Millwall 4 life.

P.P.S. Just kidding.

---

### Post by Sub101 on 2008-09-13
So the hard drive you are trying to access does appear in your "Places".

Can you see the drive when you type mount at the terminal?

---

### Post by egalvan on 2008-09-13
> **northern lights said:**
> I feel inclined to really start flaming, but I'll control myself.

Apart from the Linux community being more responsive than any proprietary support you'll ever encounter, you might want to remind yourself that all people trying (or due to your attitude formerly trying) to help you are people with a day job and are doing so in their spare time.

If you ain't satisfied, ask for a refund. Wait a minute, you got your OS and the support for free, right?!


absolutely spot on
+1

---

### Post by fignig on 2008-09-13
> **Sub101 said:**
> So the hard drive you are trying to access does appear in your "Places".

Can you see the drive when you type mount at the terminal?

i can see the drive when i go to places -> computer 

but when i click on it, it gives me those errors. is there another way to access the drive?

---

### Post by dRock1286 on 2008-09-13
Then obviosuly Linux is not for you.  If you are unable to help the community out, then the community won't help you.  You obviously should pick an easier OS like Mac OSX or even Windows.  Good luck on your endeavors.

---

### Post by Sub101 on 2008-09-13
You could try navigating to it from the home folder (address "/media" but don't think that will help all to much. 

What might work although can not be certain is: 
```
mount /dev/sd** 
```

or perhaps

```
sudo mount /dev/sd** 
```

There are those amongst the community who would be far more adept to help you here than myself but i suspect your earlier attitude may have put some off.

---

### Post by lukjad on 2008-09-13
Removed by user

---

### Post by Rocket2DMn on 2008-09-13
OK, notes on behavior and attitude stop now.

Please only speak if you are contributing to solving the OP's problem.  Thank you.

---

### Post by fignig on 2008-09-13
> **Rocket2DMn said:**
> OK, notes on behavior and attitude stop now.

Please only speak if you are contributing to solving the OP's problem.  Thank you.

exactly what i wanted. so can anyone help me mount my drive or get into my system so i can extract some stuff out

---

### Post by overdrank on 2008-09-13
> **fignig said:**
> okay so every possible thing has probably gone wrong trying to make this desktop cooler. i tried to install cairo-dock and i was trying to install the animations for compiz and i installed xgl instead of the nvidia server x and now all of my toolbars are gone, i can't move any windows, and nothng is really working. this is probably the oddest problem ever. is tehre anything like a system restore so i can go back? b/c i'm pretty much ****** right now...

If you installed xserver-xgl this can cause the issues. Are you able to boot into any other kernel, like a older kernel from the grub.

---

### Post by fignig on 2008-09-13
> **overdrank said:**
> If you installed xserver-xgl this can cause the issues. Are you able to boot into any other kernel, like a older kernel from the grub.

i tried booting into all of them, none of them work.

---

### Post by Orange_and_Green on 2008-09-13
EDIT: as requested by admin, I revert to my original post. Although it will be of no use to th OP, I hope others can benefit from it...

(problem: If just clicking on the drive gives you mount errors (in this case, the error mentioned the device /dev/sda1, modify the following according to the drive your problem refers to), one possibilty could be:)

1)Mounting as root:
```
mkdir my_drive
sudo mount /dev/sda1 my_drive
```

You can then access your data via the command line (if you are familiar with the commands), or you can
```
gksu nautilus
```
and browse.

(when getting mount errors on ntfs partitions, another thing you can do is:)
```
sudo mount -o force /dev/sda1 my_drive
```
It is not deemed to be a 100% safe operation and gives you warnings but to be honest, I used it a lot of times and never lost any data;

2)Make sure the hard disk is OK
```
sudo fsck /dev/sda1
```

Disclaimer: all of my advice is genuinely meant, I always recommend what I would do myself. However, I decline any responsibility for anything that might happen...:)
Peace

---

### Post by overdrank on 2008-09-13
> **fignig said:**
> i tried booting into all of them, none of them work.

Ok by none of them working, that would mean the distorted graphics? If so you may also try to reconfigure your xorg but as I stated previously with the installation of the xserver-xgl this also is likely to fail. So if you can remember the command used to install the xgl then you can try and remove.

---

### Post by fignig on 2008-09-13
> **overdrank said:**
> Ok by none of them working, that would mean the distorted graphics? If so you may also try to reconfigure your xorg but as I stated previously with the installation of the xserver-xgl this also is likely to fail. So if you can remember the command used to install the xgl then you can try and remove.

okay i finally made it in. but now i'm back at my old problem. all of my windows and everything at the top will not work, it's hard to explain. the level where you close, minimize, maximize windows is currently gone, and i have no idea where it went and how it disappeared. i can't move windows at all so to see something else i have to close it. i have grab windows binded but it's not even working. i just want to uninstall xgl and install my nvidia x server so everything will go back to normal.

---

### Post by Sub101 on 2008-09-13
To remove it simply ```
sudo apt-get remove xserver-xgl
```

That should be all you need.

Also, once you've sorted your problem i would be interested to know how you got in.

EDIT: You would need to install the nvidia one first i believe.

---

### Post by dRock1286 on 2008-09-14
any updates on this?  did it work?  if so, mark as solved with what you did to fix it so others will know.

---

### Post by fignig on 2008-09-14
> **dRock1286 said:**
> any updates on this?  did it work?  if so, mark as solved with what you did to fix it so others will know.

nope, i got nothing solved. i just reinstalled.

---

