---
title: "Grub Rescue on Dell Inspiron 6000"
date: 2014-06-03
forum: New to Ubuntu
---

### Post by cameron10 on 2014-06-03
This is an old thread - I hope someone can still take time to help me...

I've been using Ubuntu exclusively on my Dell Inspiron 6000 laptop since 2011... I upgraded ubuntu to 13.4 last year and everything was fine...

I haven't used the laptop much year, but the times I did, it was crashing pretty easily especially after a mega update last week...

Now I'm in grub rescue limbo. I did an ls prompt and was returned (hd0) (hd0,msdos5) (hd0,msdos1). I was going to try just load the new 14.4 version via usb (i downloaded the iso on another computer) and when I plug in the usb, I also get (hd1) and (hd1,msdos1) as options when I prompt ls - more on that later.

I tried ls (hd0,1)/ in all sorts of permutations and I only get the unknown filesystem message.  I scoured the threads all day and tried most everything (I'm actually downloading a boot repair iso as I type...) with no dice... I cannot find the iso files anywhere.

I have gone into my BIOS and messed around to load an OS from a USB, and tried the F12 Boot Menu... everything always brings me back to the error: unknown filesystem. grub rescue>

Am I missing something stupidly simple? How can I really tell if my HDD is totally corrupt?

---

### Post by oldfred on 2014-06-03
Moved to your own thread. That was a tutorial, and old, but still valid for BIOS type installs.

Best to see details of your install. Post link from a BootInfo report:

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by cameron10 on 2014-06-04
Thanks for moving my post!

One element I was missing was an iso installer, so I downloaded a copy of UNetbootin and burned a copy of boot-repair-disc-64bit... Using my F12 Boot Menu I actually got a page other than the grub rescue prompt, but unfortunately I was informed that the kernel requires an x86-64 CPU but I only have an i686...

I looked in my BIOS to enable Virtualization, but I cannot find it as an option - it's possible my hardware does not support it...

I am going to try locate a 32bit version of boot-repair-disc and try again, but my hopes are not high...

I had also downloaded a 32bit version of Ubuntu 14.04 (which I had not previously burned with UNetbootin) that I may try and start from scratch...

I had previously transferred all my important data from my Dell so I'm not worried about recovery at this point, I just want a useable laptop (specifically to start learning linux as I have barely scratched below the Ubuntu GUI...)

---

### Post by cameron10 on 2014-06-04
Boot-Repair-Disc FTW!

---

