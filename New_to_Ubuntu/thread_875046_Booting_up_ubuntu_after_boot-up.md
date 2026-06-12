---
title: "Booting up ubuntu after boot-up"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by napsta on 2008-07-30
I just installed ubuntu onto a second hard drive, but when I turn on my computer it doen't show a dual boot were I have the choice between window  (what my family uses) and ubuntu (what I want to use) . How can I make it so that when my computer boots-up it will give me the choise of windows or ubuntu?

---

### Post by Xerp on 2008-07-30
Perhaps you need to set your BIOS to boot from the second drive, which I assume is where you also installed GRUB?

---

### Post by napsta on 2008-07-30
well I'm sort-of a nerd in training so....I have no clue

---

### Post by philinux on 2008-07-30
Open a terminal from accessories menu.

Copy and paste the following code.

```
cat /boot/grub/menu.lst
```

Post the resulting output.
Dont forget to highlight this text and click the code icon (#). This make it more readable.

---

### Post by napsta on 2008-07-30
in windows or ubuntu?

---

### Post by tonez2600 on 2008-07-30
When you first turn on your computer there will be a screen that comes up for a couple seconds that says something about hit F12, Del, or F5,(or something like that) to enter setup. You will need to press that button to get in to the BIOS for you system. Once there there should be a option to select where you want the system to boot from. But seeing as how you said you put the Ubuntu install on one hard drive and you XP is on another, I am willing to bet that grub installed itself on the second drive, and does not realize that XP exists. You might have to reconfigure grub so it knows XP is there. I was just reading something about reconfiguring grub let me see if i can find it.

---

### Post by original_jamingrit on 2008-07-30
You can change your BIOS at boot-up.  When you start up, you should see a screen flash to tell you what key to press before going into setup or use the BIOS menu.  It flashes by quickly, so this may take a couple of tries to spot it.  When you figure it out, poweroff.  And then, power back on, quickly tapping or pressing that key.  This should bring you into the BIOS menu.  From there, you can set which hard drive to boot first.  Then Save and Exit.

It complicates things because BIOS menus may vary, so if you get into the BIOS menu and don't understand how to change the bootable drive, don't.  Just reboot and post here again for more info.

---

### Post by philinux on 2008-07-30
> **napsta said:**
> in windows or ubuntu?

Ubuntu.

I assume this is whats booting now? Or is it just windows?

---

### Post by napsta on 2008-07-30
well my internet only works in windows right now so that's what I'm on but I'm trying to see if when I boot-on if I can pick which drive I want to use

---

### Post by napsta on 2008-07-30
mybad I think I said this wrong let me reformat the question 

I have two hard drives #1 is windows, #2 is ubuntu
The computer boots on the first hard drive but I can't boot on number #2 I need someone to help step by step on how I can get the start-up screen to show a choice betwen #1 and #2

---

### Post by philinux on 2008-07-30
> **napsta said:**
> mybad I think I said this wrong let me reformat the question 

I have two hard drives #1 is windows, #2 is ubuntu
The computer boots on the first hard drive but I can't boot on number #2 I need someone to help step by step on how I can get the start-up screen to show a choice betwen #1 and #2

Ok.

When it boots do you see anything on screen regarding grub. Or does windows just boot.

---

### Post by napsta on 2008-07-30
for 5 seconds then it just boots straight to windows

---

### Post by Lexicon101 on 2008-07-30
go to this site: [Super Grub Disk: Download]("http://www.supergrubdisk.org/index.php?pid=5") Download it from mirror #0 (1 is down..)
Burn it to a disk, then restart your computer, using others' suggestions about entering the setup screen, but with this suggestion, to have your computer boot from CD.

BEFORE DOING SO: Go to this website to find the fix to your problem.. it will probably be installing GRUB to the master boot record of the first harddisk in your system.
Alternately, you could set up the motherboard to boot the drive with linux in it, because it should have GRUB already set up, and all you'd have to do is add windows into the boot sequence. that way your windows boot record would be safe, and your linux boot record would do all the work.

EDIT: That wasn't supposed to be a smiley face.

---

### Post by philinux on 2008-07-31
> **napsta said:**
> for 5 seconds then it just boots straight to windows


When grub appears be quick and press the esc key. You can then use the up down arrow keys to select Ubuntu.

---

