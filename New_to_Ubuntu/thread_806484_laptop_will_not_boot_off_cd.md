---
title: "laptop will not boot off cd"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by golgo13 on 2008-05-25
I want to resize my ubuntu partition/ try puppy linux but in both cases my laptop will not boot off the ubuntu/ puppy live cd respectively
the cd drive works fine and because it happens with both distros I know its not the cd disk either
i have changed the bios setting to boot from cd so I don't know why this is not happening
any ideas?

---

### Post by hyper_ch on 2008-05-25
during boot you might need to press a button (F7 or F8 or F10 or F12) through which you can select what to boot from...

---

### Post by Bubba64 on 2008-05-25
> **hyper_ch said:**
> during boot you might need to press a button (F7 or F8 or F10 or F12) through which you can select what to boot from...

That is the answer, your screen at start up will tell which f# for bios it goes by fast so act quick. Mine is F12

---

### Post by hyper_ch on 2008-05-25
I'm not talking about bios here... some bioses do have a key for selecting startup device upon boot.

---

### Post by Bubba64 on 2008-05-25
> **hyper_ch said:**
> I'm not talking about bios here... some bioses do have a key for selecting startup device upon boot.

You are correct sir it is called temporary boot device, on my computers, my bad.

---

### Post by golgo13 on 2008-05-25
I tried the F12 boot start up device selector and bios settings boot selector before I made the OP but both did not work
I just end up on the ubuntu screen whatever so my question is what is preventing the boot from cd selection 'sticking'?

---

### Post by Joeb454 on 2008-05-25
Try hitting F2 or Del while the computer is booting (literally like 1 second after pressing the power button ;)) And change the boot device priority in your bios :)

---

### Post by KingTermite on 2008-05-25
I don't get it. O.P. said he changed boot order in bios and everybody is trying to tell him how to change the boot order in the BIOS. O.P. already did that according to first post.

Are you CD you created is bootable?

How about this...try to disable any other boot devices in the BIOS so it ONLY boots from CD/DVD and see what it says.

---

### Post by bubba_169 on 2008-05-25
Are you sure you didnt just copy the iso file to the cd instead of burning the image? What software did you use to burn the cd?

---

### Post by Bubba64 on 2008-05-25
> **golgo13 said:**
> I want to resize my ubuntu partition/ try puppy linux but in both cases my laptop will not boot off the ubuntu/ puppy live cd respectively
the cd drive works fine and because it happens with both distros I know its not the cd disk either
i have changed the bios setting to boot from cd so I don't know why this is not happening
any ideas?

How did you change bios to read from a CD. Also have you had the computer read the CD to make sure there are no errors.

---

### Post by Raccoon1400 on 2008-05-25
> **golgo13 said:**
> I tried the F12 boot start up device selector and bios settings boot selector before I made the OP but both did not work
I just end up on the ubuntu screen whatever so my question is what is preventing the boot from cd selection 'sticking'?

You sure you are saving the setting in BIOS?

---

### Post by golgo13 on 2008-05-26
ok this is the current situation:
I erased the cd and reburned the puppy linux image to check I had done it correctly
I ran puppylinux on my 128MB RAM desktop (which has the hard drive removed!) to check the cd and it worked fine so the problem cannot be the cd itself
and as the image was burnt with the drive I want to boot from (on my laptop) then I am assuming that the drive itself is OK too
I checked I was saving the BIOS settings and that the boot from cd option was at the top (I also disabled the other boot priorities just to make sure)
This resulted in getting to the preboot screen which was as far as it went (with both puppy and ubuntu)
Cannot think what is stopping it booting from the cd then...?!
any other ideas?

---

