---
title: "starts to load (little orange thing going back and forth) then freezes"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by sniperhunter on 2008-06-02
okay, Im a dual boot. computer stats:
   gigabyte k8u motherboard socket 754
   AMD atholon 64 processor 2.2 ghz
   visiontek ATI radeon x1300 512 mb AGP 8x video card.
   1 gig ram.
   MS XP pro and Ububntu.
   19` samsung 906bw screen

xp was installed first (i recently converted to linux and dual boot- yea for me!) on my C drive (IDE) I installed ubuntu on my F drive (sata) anyway- the marvelous 6.0 version of linux configured the grub/dual boot menu for me! such wonders i had not expected:guitar:

I then upgrade using some code in the Alt+F2 command to 8.06- whatever the newest one is.

upgrade successful it reboot, i login to 8,00 and immediately attempt to enable desktop effects. it gives me a box about "enabling 3d effects, ati video card, changes in effect after reboot" - i clicked "Okay" and reboot- it sounded like the thing to do! anyway, it reboot. 
  I got to that lovely black screen with UBUNTU" at the top and a little orange bar that goes back and forth.- it stopped, tried to go to the next screen  and the screen stays blank.  not blank like it does when it has no input- and it says "please connect something" this time, my screen regognizes some input- but it just wont show it. (i.e if i hit source on my screen - it flickers between analog and dvi- and reverts to analog- on my screen that means something is there)
so, any advice on how to satisfy ubuntu?
p.s im gnomish not kde

---

### Post by Quintin Riis on 2008-06-03
Can you get to a virtual terminal with CTRL+ALT+F1 ?

---

### Post by canthus13 on 2008-06-03
You may need to play with the boot options a little bit. -nolapic and -noapic might help. You can add these at boot time in the Grub menu like this:
> 
    * Press 'e' to start editing.
    * Scroll down to the "kernel..." line. The is the line that tells Grub which kernel to boot with and the parameters to be passed to the kernel when it boots are placed at the end of this line.
    * Press 'e' again to edit this line.
    * Move to the end of the line. You will see any existing parameters and can add other new parameters to the end.
    * Parameters are separated by spaces and are mostly either a single word (e.g. nolapic), or an equation (e.g. acpi=off).
    * Once you have added the parameter to the end of the line, press Enter to accept the editing.
    * Then press 'b' to boot using that kernel and those parameters.

If they work, you can edit /boot/grub/menu.lst and add the options to the appropriate line.

--Me

---

