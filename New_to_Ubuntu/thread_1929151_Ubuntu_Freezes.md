---
title: "Ubuntu Freezes"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by topdog2009 on 2012-02-21
Hi guys
 Ubuntu 11.10 freezes after entering  password (get red Ubuntu screen). When first installed (fairly recently)  it appeared to work OK. Not used for some time though.

Dual boot machine Windows 7 and Ubuntu. Plenty of RAM available.  Replies on other threads indicate indicate going to Grub menu ...HOW??

Also reference found to boot repair but if system is frozen how do I get it?

Brian

---

### Post by bogan on 2012-02-21
Hi!,[B] topdog2009,
[/B]
To get the Grub boot menu to show: Press 'Shift' key during initial boot period.

I Posted in the other Thread you posted to: >  **Re: Ubuntu freezing at login upon reboot.**             
                                                                In the grub menu, select the Ubuntu entry you want and press 'e' to get to the edit screen.

Move the cursor to the Linux boot line, where it says 'ro quiet splash'  and alter it to: 'ro --verbose text'; then press 'Ctrl+x' to boot.

If you get it wrong, 'Esc' will take you back to the menu, or Ctrl+c  will give a grub prompt with limited commands available, see text at  bottom of grub menu screen.

If all is well you will get a tty log-in prompt, if not press  Ctrl+Alt+F1 or F2; Ctrl+Alt+F7 will take you to what should be the  graphics screen.

Log-in and enter password and you will get a Terminal prompt. Enter      

     ```
sudo service lightdm start
``` to get to the full GUI screen.Please Post details of your computer including the Video card make and model;.

Chao!,** bogan**.

---

### Post by topdog2009 on 2012-02-22
This was the grub menu

setparams 'Ubuntu,with Linux3.0.0-15-generic'

set gfxpayload=$1linux-gfx-mode
insmod part - msdos
insmod ntfs
set root = '(hd0,msdos2)'
search --no-floppy--fs-uuid--set=rootD048BA6748BA4BCA
loopback loop0 /ubuntu/disks/root.disk
set root =(loop0)
linux /boot/vmlinuz -3.0.0-15-generic root=uuid=D048BA6748BA4BCA loop=/ubuntu/discs/root.disk [COLOR=Navy]_ro quite splash_[/COLOR] vt.ha\ndoff=7
initrd /boot/initrd.img-3.0.0-15-generic.

I replaced the underlined blue print above with ro -- verbose.txt

Pressed Ctrl +x to reboot.

Screen went blank - nothing worked (Esc, CTRL C) had to turn machine off.

I have a Toshiba Satellite  C655D video card is AMD Radeon HD 6250 Graphics

Brian

---

### Post by wildmanne39 on 2012-02-22
Hi, give this a try:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

### Post by bogan on 2012-02-23
Hi!,** topdog2009**,

You Posted:>  linux /boot/vmlinuz -3.0.0-15-generic root=uuid=D048BA6748BA4BCA loop=/ubuntu/discs/root.disk [COLOR=Navy]_ro quite splash_[/COLOR] vt.ha\ndoff=7
initrd /boot/initrd.img-3.0.0-15-generic.

I replaced the underlined blue print above with ro -- verbose.txt The original "quite splash" should in any case be "quiet splash".

What you changed it to should be: " --verbose text" not "--verbose.txt".

or " nomodset  --verbose text"

Chao!, **boga**n.

---

### Post by topdog2009 on 2012-02-23
hi Bogan

That fixed it - thanks.

Are they still racing at Brands Hatch (going back 50 years)

Brian

---

