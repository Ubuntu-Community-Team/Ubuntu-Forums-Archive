---
title: "Black Screen of Death"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by WriteGirl on 2008-11-24
About two hours ago, I was using this forum to fix a problem I had installing medibuntu and it turned out that updating intrepid had gotten mixed with hardy heron and someone suggested putting this into my terminal.

```
sudo apt-get update
sudo apt-get upgrade
```

I copied and pasted the first and it worked fine. I copied and pasted the second and it was working, telling me that it was installing certain things and had twelve minutes left. When it reached six minutes left, the screen when black, didn't respond to any of the keys I pressed. I turned it off, and tried to restart it, but it just made air fan sounds for ten seconds and shut off by itself. That's all it does now.

It's a HP laptop about three or four years old, the battery is charged, and it's plugged in right now. 

(My original problem was over on this thread. [http://ubuntuforums.org/showthread.php?p=6246659#post6246659](http://ubuntuforums.org/showthread.php?p=6246659#post6246659) I hope it's okay to start a new thread, since it's a new problem and I'm not sure if it's even related.)

---

### Post by phidia on 2008-11-25
That doesn't sound good. I would unplug the A/C and pull the battery. Leave it like that for a minute or two and place the battery and the power plug back in. Try and start it up and see if resetting it like that made any difference.

You can also try a live cd but if you are not seeing the normal bios screen there might be hardware problems of some kind.

---

### Post by WriteGirl on 2008-11-25
I took out the cord and tried to turn it on. Nothing again, just the same black screen. Do I need to use a screwdriver to take out the battery? Because I can't see where else it would be. I tried putting in the CD I used to install hardy heron on it, which was my first linux distro and nothing changed.

---

### Post by Bucky Ball on 2008-11-25
Can you get to the BIOS at boot (press F1 or possibly Delete) and have you got another bootable cd of any kind, other than the Ubuntu installer?

Also, where does hitting Ctl/Al1/F1 get you when you are looking at the black screen (with the machine on, of course. LOL). Does that take you to a command shell? You could also try hitting esc as it is booting up. Might be something odd like the changes have hidden the grub menu.lst. Wild guess but:

nano /boot/grub/menu.lst

... and in there you might find

hiddenmenu

Make that:

# hiddenmenu  

... presuming that you can get that far.

---

### Post by phidia on 2008-11-25
Turning off power completely resets the computer (well there could be arguments over that-but generally speaking) with a laptop you do need to remove the battery to accomplish that.
Recent hp laptops I've used/seen have a little spring loaded plastic "pull" you press while nudging the battery. (The battery is accessed from the bottom) Do you have the laptop manual?

Added: Do you hear the system beep when you press the power button? There should be just one short beep.

---

### Post by WriteGirl on 2008-11-25
I can't get to anything. None of the buttons I press change the screen. There's no BIOS. I tried putting in a CD to a game and nothing happened. 

I only know that hitting the power button does anything at all because the power light goes on and I can hear the sound of the air fan, that usually comes on when you turn on a computer. Five seconds after I hit the button, the light goes off, and the sound stops.

---

### Post by Bucky Ball on 2008-11-25
Perhaps a faulty battery? Probably nearing the end of its life if as old as the machine (4 years?). You are saying you switch on, machine stays on for 5 seconds then switches off again? But, if you get the battery out, plug the machine in and try booting, and it still switches off after 5 seconds, then something dodgy further along the power chain. Tech time.

---

### Post by WriteGirl on 2008-11-25
Phidia - I don't hear any beep. I found some sort of pull for the battery on the back like you described, but there was no battery to nudge. It's next to a square plastic thing that has a screw, so that's why I thought I might need a screwdriver.

If the battery did just die, would the hard drive be erased, or recoverable if I got a new battery? I got this laptop used from a friend, so I'm going to ask him about taking out the battery tomorrow.

---

### Post by phidia on 2008-11-25
A faulty battery wouldn't cause this since the computer was connected to power.

It would be useful to know if the POST sound the little beep you hear when the computer first starts is heard.

I have also seen the operating system shut off the backlight and for some reason that setting can stick-unless you reset the laptop by removing the battery but that only a guess. 

You probably need to have a geeky friend or service tech person look at it.

---

### Post by WriteGirl on 2008-11-25
All right. I'm going to try the battery thing tomorrow, and if that fails, go find a sufficiently talented computer person. Thanks for the suggestions.

---

### Post by phidia on 2008-11-25
> **WriteGirl said:**
> Phidia - I don't hear any beep. I found some sort of pull for the battery on the back like you described, but there was no battery to nudge. It's next to a square plastic thing that has a screw, so that's why I thought I might need a screwdriver.

If the battery did just die, would the hard drive be erased, or recoverable if I got a new battery? I got this laptop used from a friend, so I'm going to ask him about taking out the battery tomorrow.

The battery is a long (almost as long as the computer is wide object) no screw removal should be required. I've noticed with hp's that you need to push the "tab" I tried to describe earlier and tilt the computer a little sometimes using a fingernail to get the battery to drop out. And maybe it's better to get help anyway-good luck.

---

### Post by Olivier2371 on 2008-11-25
Sorry to drop in, what is the model of your hp laptop?

---

### Post by madverb on 2008-11-25
Seems like you got yourself a brick... no fault of Ubuntu though. Seems like some hardware has failed, I'd be surprised if you can get it working again without replacing hardware.

---

