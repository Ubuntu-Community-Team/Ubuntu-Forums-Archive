---
title: "Problems with 12.04 server"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by ppoulsen2007 on 2012-05-25
Hi

Hope someone can help me with this problem I have... 

I just installed Ubuntu Server 12.04 on a Raid-1 made by 2 Intel 60GB SSD, with encrypted JVM. Installation went without problems, but when I rebooted the machine to start for the first time, I only get a black screen with a cursor and nothing more.

Can't seem to find anyone with this problem and I am new to Linux, very big Noob, so I hope someone can help me figur out this problem.

Please write what information you might need to help and a little help in how to get them. :-)

Thanks in advance
Peter

---

### Post by roelforg on 2012-05-25
Wait a few minutes (~10 should be enough) and see if it displays stuff then.
Because where normal ubuntu has a splash screen (the ubuntu logo with the dots), server has a black screen.

---

### Post by ppoulsen2007 on 2012-05-25
> **roelforg said:**
> Wait a few minutes (~10 should be enough) and see if it displays stuff then.
Because where normal ubuntu has a splash screen (the ubuntu logo with the dots), server has a black screen.

Unfortunately this isn't the problem, left it for 30 minutes and still the black screen with blinking cursor... Tried the 'e' and 'shift' to get Grub's attention, but no luck....

Anyone?

---

### Post by roelforg on 2012-05-25
> **ppoulsen2007 said:**
> Unfortunately this isn't the problem, left it for 30 minutes and still the black screen with blinking cursor... Tried the 'e' and 'shift' to get Grub's attention, but no luck....

Anyone?
Is there any hw activity?
Does the capslock blink?
If you press alt, does the capslock blink now?

---

### Post by ppoulsen2007 on 2012-05-25
> **roelforg said:**
> Is there any hw activity?
Does the capslock blink?
If you press alt, does the capslock blink now?

TURNS ON AND OF IF I press it, but no blinking if I press ALT. And system reachs to CTRL+ATL+DEL.....

---

### Post by roelforg on 2012-05-25
> **ppoulsen2007 said:**
> TURNS ON AND OF IF I press it, but no blinking if I press ALT. And system reachs to CTRL+ATL+DEL.....
I meant if it blinks on its own (that's the kernel's signal to say a kernel-panic happened).
Try waiting the 10 min and then press CTRL+ALT+F1 and (if that didn't work) ALT+F1
My server sometimes boots to tty7 (graphical) which doesn't work correctly in textmode on some systems.

---

### Post by ppoulsen2007 on 2012-05-25
> **roelforg said:**
> I meant if it blinks on its own (that's the kernel's signal to say a kernel-panic happened).
Try waiting the 10 min and then press CTRL+ALT+F1 and (if that didn't work) ALT+F1
My server sometimes boots to tty7 (graphical) which doesn't work correctly in textmode on some systems.

I just reinstalled without the encrypted LVM, but still the same problem... I booted with a Desktop CD, before I did the reinstall, and could see the SSD drive and all that was on them, and tried Boot-Repair, but that didn't work either.... 
I'm seriously considering a Windows server atm, and I hate Windows..... :-/

---

### Post by roelforg on 2012-05-25
> **ppoulsen2007 said:**
> I just reinstalled without the encrypted LVM, but still the same problem... I booted with a Desktop CD, before I did the reinstall, and could see the SSD drive and all that was on them, and tried Boot-Repair, but that didn't work either.... 
I'm seriously considering a Windows server atm, and I hate Windows..... :-/

Did you do as i asked?

---

### Post by ppoulsen2007 on 2012-05-25
Can it have something to do with the SSD Raid-1 array I'm running or the Intel Processor or? I'm grasping at air here, but am really lost....

---

### Post by ppoulsen2007 on 2012-05-25
> **roelforg said:**
> Did you do as i asked?

Yes, the machine makes little clicks, but nothing happens.

---

### Post by roelforg on 2012-05-25
> **ppoulsen2007 said:**
> Can it have something to do with the SSD Raid-1 array I'm running or the Intel Processor or? I'm grasping at air here, but am really lost....

It could, but the kernel didn't freeze because the capslock reacted ok and grub finished ok.

Still, do as i suggested and press those keys.
I really want to help you, but i can't if you won't cooperate.

---

### Post by ppoulsen2007 on 2012-05-25
> **roelforg said:**
> It could, but the kernel didn't freeze because the capslock reacted ok and grub finished ok.

Still, do as i suggested and press those keys.
I really want to help you, but i can't if you won't cooperate.

I did as you asked, and I really appriciate your help. :-)

Unfortunately, as I wrote in last post, the machine makes small clicks when I push the keys, but nothing happens. 

Why do you think Grub is working? Because shift and e key doesn't work?

---

### Post by roelforg on 2012-05-25
> **ppoulsen2007 said:**
> I did as you asked, and I really appriciate your help. :-)

Unfortunately, as I wrote in last post, the machine makes small clicks when I push the keys, but nothing happens. 

Why do you think Grub is working? Because shift and e key doesn't work?

The clicks are the sound of the keyboard.

Did grub show? (i assumed it did).

---

### Post by ppoulsen2007 on 2012-05-25
> **roelforg said:**
> The clicks are the sound of the keyboard.

Did grub show? (i assumed it did).

Nope straight to black screen with blinking cursor.

---

### Post by roelforg on 2012-05-25
> **ppoulsen2007 said:**
> Nope straight to black screen with blinking cursor.

Could you try to reinstall w/o raid?
By eliminating raid we can see if the problem is that or something else.

---

### Post by ppoulsen2007 on 2012-05-25
> **roelforg said:**
> Could you try to reinstall w/o raid?
By eliminating raid we can see if the problem is that or something else.

Yes then it works. :-D

---

