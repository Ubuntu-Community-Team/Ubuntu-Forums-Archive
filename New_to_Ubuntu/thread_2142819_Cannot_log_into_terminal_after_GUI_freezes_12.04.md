---
title: "Cannot log into terminal after GUI freezes 12.04"
date: 2013-05-06
forum: New to Ubuntu
---

### Post by UncleAsriel on 2013-05-06
My GUI froze while multiple actions were taken in the web browser. I activate Ctrl + Alt + F2 to open the terminal, in the hopes of restarting it as described [here.]("http://askubuntu.com/questions/151049/how-to-deal-with-a-frozen-screen")


The terminal opens up, listing the computer name, version of ubuntu, etc. I am prompted for 'ubuntu login'. I enter the username of my Super User account (The only account I have here, after the default guest). I enter in the same password I use to authenticate sudo commands, knowing that it will return no characters (shows a blank screen), and that this is merely a security feature.

However, when I press Enter, I get a 'Login incorrect' message.  

Is what I am doing approrpiate for someone trying to access the command line? Is there another approach which I should be doing instead?

---

### Post by Bashing-om on 2013-05-06
UncleAsriel;

Nope, your procedure is valid and correct to login.

Assuming that the problem yet continues that you are experiencing with textual login; Let's look and see if the authorizations have been changed.
Text login procedure from the grub menu:
Boot ubuntu, as soon as the bios screen clears depress and hold the shift key -> grub menu;
With the top menu entry highlighted, press the 'e' key for edit mode -> kernel boot parameter screen;
Arrow down to a line similar to this "linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff" and arrow across to the terms "quiet splash" ;
Remove (delete) these terms and all after and insert the term "text" -with out the quotes- --> Boot logging is enabled and you should boot to a textual login.
Enter your usual username, followed by your pass word - and yes - there is no response to the screen.

Check if ".ICEauthority" is owned by you:
```

ls -al .ICEauthority
```
4. If it isn't (but possibly by root), change it to you:
```

sudo chown USERNAME:USERNAME .ICEauthority
``` where USERNAME == your actual "username"

At this time re-boot and see if the GUI is accessible now.
```
sudo shutdown -r now
```
  
This is one possibility[INDENT=3] hope this gets ya back up

[/INDENT]

---

### Post by UncleAsriel on 2013-05-06
Right out of the gate, I'm running into hurdles.

I boot up the computer. Once it goes through the hardware check, it allows me to load two operating systems: Windows Vista (the default OS which came with the unit) and Ubuntu. I select Ubuntu. If I do what I typically do during startup and avoid interacting with the keyboard, the screen goes blank for a moment, then GUI loads and everything appears to be business-as-usual for a GUI-trained user like myself. However, when I depress the shift key like you said, the screen merely reamisn blank, before the computer shuts down (a message on the monitor  explaining how the monitor has fallen asleep). My computer's power button also turns the color it does when the machine hibernates.
 
In either instance, I cannot access GRUB (the linux version of DOS, as far as I understand it). 

Could you please advise my next move?

---

### Post by DuckHook on 2013-05-06
Also check that your <Caps Lock> key is not engaged.

---

### Post by DuckHook on 2013-05-06
On some installations, getting to GRUB requires you to press <Esc> instead of <Shift>.

---

### Post by Bashing-om on 2013-05-06
UncleAsriel;
See          DuckHook's last.
I have never dual booted with Windows,(triple booting 'buntu) but I expect the procedure to work. At that grub selection menu arrow to the ubuntu entry and hit the 'e' key to edit; the remaining procedure remains in effect.[INDENT=3]
regards

[/INDENT]

---

### Post by UncleAsriel on 2013-05-06
Well, this got interesting.

Still trying to get to the GRUB menu. As soon as I select the Ubuntu option from the "Which OS to boot?" screen, I depress the <Esc> key like there's no tomorrow. The screen remains dark for a number of seconds, then lines of streaming text appear. In the foreground the text appears to be static, while behind it in grey text whisks past like The Matrix. I remove my hand from the <Esc> key (thinking this is causing the machine to blink) and am left with a screen which turns back and forth between the Ubuntu logo and a static wall of this text (listing how various things ate [OK]). When I input anything (such as <e> + <return>), nothing happens. Whenever I leave the static text screen for the ubuntu frame for long enough, I get the GUI login.
 
Am I being impatient, or is there something the matter?

---

### Post by Bashing-om on 2013-05-06
UncleAsriel;

IDK for sure// This should be proper. boot the computer at that grub boot selection screen arrow to ubuntu --- DO NOT hit the enter key, press the 'e' key to enter edit mode ///
OH did I forget that after the edit to the kernel command boot line, to continue the boot process key combo ctl+x ...my oversight.[INDENT=2]
we will keep trying

[/INDENT]

---

### Post by UncleAsriel on 2013-05-08
I do no see the GRUB boot selection screen. I see a screen that lets me choose between Windows Vista and Ubuntu (pressing <e> here does nothing). Once I slect Ubuntu, I get the aforementioned problem.  

Could a Windows Dual-Booting expert advise, mayhaps?

---

