---
title: "Can't get Kubuntu 8.10 to work"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by itsStephen on 2008-11-01
I've been waiting so long for Kubuntu 8.10, I'm even going to build a new computer for it.

Thing is, I downloaded it earlier today to try it on the computers in the house have. Here's how it went

This one: Booted and desktop loaded as far as the cursor on a white background
Brother's: After the loading bar finished the screen went black. Then when you press the power button on the computer the ending screen thing that tells you to take the disc out came up.
Parents: Couldn't read the disc.

3 computers and no luck. This computer doesn't have enough ram anyway (256mb, 64 of it on graphics) but the other 2 should be able to run it. My brother has a Dell Inspiron 530 with an ATI Radeon HD 2400 pro. Hid (Dell) monitors light turns orange after the loading screen. We tried with my monitor but it still didn't work so I think it's the graphics card. I have a friend with the same card so I'll ask him to try it. My parents computer has always been picky with Linux but Kubuntu has always worked (and centOS).

What is wrong with it? I want to try it before I spend $400 AUD on a computer specially for it and it won't even work.

---

### Post by lH)4~mK0e on 2008-11-01
First, check the disc.  Run the CD media test (if it is still on the ubuntu cd) and make sure it passes.  It could just be a bad burn.  If it fails try burning the disc again.  Otherwise, try downloading Hardy (8.04 LTS) and see if you get the same results.  If you have the same issues, it could be a problem with your burner or discs (sometimes discs can be bad, an entire stack of discs can be bad).

---

### Post by itsStephen on 2008-11-01
> **miwarlock002 said:**
> First, check the disc.  Run the CD media test (if it is still on the ubuntu cd) and make sure it passes.  It could just be a bad burn.  If it fails try burning the disc again.  Otherwise, try downloading Hardy (8.04 LTS) and see if you get the same results.  If you have the same issues, it could be a problem with your burner or discs (sometimes discs can be bad, an entire stack of discs can be bad).

It passed. That was the second time I burned it. 8.04 did the same thing from memory.

I don't know if it's weird that the 2 computers I can get nothing on (this one will boot but doesn't have enough ram) both have Foxconn motherboards?

---

### Post by lH)4~mK0e on 2008-11-02
If all of these computers were custom built, then you may have to play around with the BIOS settings.  I know some of the older types of processors (Pentium II/III, AMD K62/Athlon/Duron/T-bird) and motherboards had to have PnP Operating System set to "Off."  Some motherboards still have issues with how the Linux Kernel handles ACPI.  So you may have to boot from the Live CD and hit F6 (I think whichever says More Options) and go to the end of the line with the "End" key or the arrow on the keyboard.  You might try adding this option at the END of the line by typing a Space and then:

```

acpi=off

```

Also, with a newer video card and sometimes with the HD Radeons, it is possible the Live CD doesn't know how to handle it.  If you can hit Ctrl + Alt + F1 and get to a virtual terminal that asks you to log in, it may just be using the wrong driver in the xorg.conf file.  You can log in using this virtual terminal and possibly fix this temporarily.  Just log in and issue this command:

```

sudo nano /etc/X11/xorg.conf

```

This will bring up an edit screen for your xorg.conf file.  Hit the PageDown key until you get to a section that says Section "Device" and look to see which driver is installed.  It will specifically say Driver.  Use your arrow keys to put your cursor to the right of the quotation mark on the left side.  Hit the delete key to remove the current text and add the text vesa to it so it looks similar to this.

```

Driver      "vesa"

```

Once you have done this hold down Ctrl and type the letter X to exit out.  It will ask you to save it, type Y then hit enter when it gives you the filename to overwrite.  You should now be back to the command prompt.  Issue this command:

```

sudo /etc/init.d/kdm restart

```

If this was causing the issue, then once it has restarted you should get video.  Try this with the Radeon HD card.  Also try the Memory tests included on Live CD for both Foxconn boards.

---

