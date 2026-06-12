---
title: "First major hiccup"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by Penfold1971 on 2012-06-26
And there I was, feeling good about the machine I'd built and the installation of Ubuntu (12.04).

Today, I had shut the machine off, then a couple of hours later I switched it back on.  It seemed to start the operating system in the normal way, with the purplish desktop and the row of red lights in the centre. But that disappeared and now all that I have is [ OK ] at centre top of a black screen, with a winking cursor/prompt on the next line to the left of the screen.

I'm stumped.

I finished building this machine yesterday afternoon. Switched it on, and after the Gigabyte welcome/splashscreen I was asked to insert a boot disk. I assumed it meant the Ubuntu install disk. Everything went just fine. Ubuntu up and running, downloaded software updates and assumed all was fine.

---

### Post by jmfal on 2012-06-26
Reboot to your grub screen and select the recovery kernal, and from the menu select update grub,  and follow prompts ..

If that brings youback to the menu select resume normal boot, if you get a command prompt enter:
```
  startx    
```

And follow prompts.

If the grub screen didn't appear and you end up at the ubuntu with the row of lights,
reboot and as your bios/setup screen disappears tap the shift key, this should get you to the grub menu .

---

### Post by Penfold1971 on 2012-06-26
Well, I'd left the machine in the state I'd described it while I posted the above from another machine. Came back to this one and found the Ubuntu screen asking me for my password. That got me into the Desktop etc. I'm posting this from my new build machine.

It seems everything is OK.

Maybe I shut down wrongly, although I'm sure I went to the top right of the Desktop menu bar and selected 'Shutdown'.

Does 'Suspend' mean the same as 'Sleep' in Mac OS X?

---

### Post by Penfold1971 on 2012-06-26
> **jmfal said:**
> Reboot to your grub screen and select the recovery kernal, and from the menu select update grub,  and follow prompts ..

If that brings youback to the menu select resume normal boot, if you get a command prompt enter:
```
  startx    
```And follow prompts.

If the grub screen didn't appear and you end up at the ubuntu with the row of lights,
reboot and as your bios/setup screen disappears tap the shift key, this should get you to the grub menu .

I don't know exactly what 'Reboot' means. Is that the same as a Shut Down followed by Start?

I also don't know what 'grub screen' means.

---

### Post by jmfal on 2012-06-26
Reboot means  >>Restart

The grub screen lists the kernals installed and a recovery kernal for each one, plus memtest and possibly some partitions and windows if you have it installed.

When in the recovery kernal you have to use the arrows on your keyboard to move up and down and press enter key to make selection.

you may want to try and find it so you know how and update grub while you are there, it may fix the lag you are having at startup.

---

### Post by Penfold1971 on 2012-06-26
But what specifically do I do to Restart?

And what will the grub screen look like?

I'm really out of my depth with this setup at the moment.

---

### Post by jmfal on 2012-06-26
Restart =====restart your computer, I'll try to find a screen shot of grub,, maybe somebody will beat me to it.

---

### Post by mapes12 on 2012-06-26
Or you can use this really simple tool:-

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by IWantFroyo on 2012-06-26
Turn off your computer (cold shutdown (button) if necessary). Then hit the ESC button right after the manufacturer's screen (where it says the name of the company that either built the computer or the motherboard). This will take you to GRUB, which looks in general like [this]("http://1.bp.blogspot.com/-DAoIzD2ZBjM/TtZHYBNRP1I/AAAAAAAAFCs/nVg15g46Zno/grub2_picture.png").

Hit 'e' over the main option, and then add the following terms to the end of the file: pci=noacpi noapic

Good luck!

---

### Post by audiomick on 2012-06-26
But no-one has told you what GRUB is, have they? ;)

GRUB is a thing called a boot-loader. It is a piece of software that is loaded after the BIOS which directs the computer to where the Operating System is that it is supposed to start. 

On an Ubuntu install, if there is only one OS install on the machine, the settings default to not showing GRUB at boot up. It is running, but you don't see it, and mostly don't need to because you only have the one OS installed and therefore normally no need to choose.

If you had more than one OS installed, for instance a dual boot of Ubuntu and Windows, or several different Linux versions, you would always see GRUB at startup, allowing you to choose which OS install you want to boot into.

---

### Post by Penfold1971 on 2012-06-26
Thanks for all the replies.

I went to 'Shut Down ... ' (menu at top left of Desktop menu bar) and noticed from the dialog box that appeared that there was an option to Restart at bottom left.

That clears up my fog over 'Restart'.

I opted for Shut Down anyway and after a few minutes turned the computer back on. Everything proceeded in the correct fashion. I got the login screen requiring my password and got straight to the Desktop.

The hiccup of earlier this afternoon hasn't reappeared.

I can remember that just before the first warnings of errors appeared, I was exploring the System settings, and in particular Sound. It was after clicking the Test Sound button that things started to go wrong. It may or may not be relevant, but that was what I was doing.

---

### Post by Penfold1971 on 2012-06-26
Very odd. Everything has been working fine since I got the first login screen after the hiccup.

I'll designate this 'solved' for now.

Thanks for all the replies.

---

