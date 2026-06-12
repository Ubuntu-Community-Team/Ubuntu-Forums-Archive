---
title: "In Screen Saver, when I move Mouse to get to desktop the screen scrambles ..."
date: 2022-11-08
forum: New to Ubuntu
---

### Post by cwmoser on 2022-11-08
In Screen Saver, when I move Mouse to get to desktop the screen scrambles ... I have to mouse click on the Desktop to unscramble the screen.
Not a show stopper, just annoying.

Got any ideas as to the cause?
I am using Compiz and a Radeon video card.

---

### Post by MAFoElffen on 2022-11-09
Which video driver? What is the AMD Radeon GPU model?

---

### Post by cwmoser on 2022-11-09
I have an AMC Radeon HD 6570 video card.  
1GB Ram PCI-e DDR3
1920 x 1080

The screen scramble seems to occur ever other wake up from screen saver which is a blank screen.

---

### Post by MAFoElffen on 2022-11-13
Whenever I see a post on the screen not right after coming back from a screensaver, or from sleep, I have to suspect one of two things, either the video driver or the ACPI energy saver settings, whereas BIOS versions of some machine fall in there on the later.

If you ran the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info"), it would provide information on the Video hardware and the video driver, as well as the Machine and BIOS version. Please post the URL of where it uploads the report to a pastebin.

---

