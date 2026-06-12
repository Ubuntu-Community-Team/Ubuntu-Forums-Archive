---
title: "Patch ?"
date: 2012-07-13
forum: New to Ubuntu
---

### Post by Lupajz on 2012-07-13
Hey I have a question.

> [http://www.mail-archive.com/platform-driver-x86@vger.kernel.org/msg03451.html](http://www.mail-archive.com/platform-driver-x86@vger.kernel.org/msg03451.html) 
[http://www.mail-archive.com/platform-driver-x86@vger.kernel.org/msg03452.html](http://www.mail-archive.com/platform-driver-x86@vger.kernel.org/msg03452.html) 
[http://www.mail-archive.com/platform-driver-x86@vger.kernel.org/msg03453.html](http://www.mail-archive.com/platform-driver-x86@vger.kernel.org/msg03453.html) 

I found this emails with a patch files ready signed to be released :P But I want them now. Is there any way I could put them into my kernel that I am running atm ? (3.4.4)

---

### Post by Cheesehead on 2012-07-13
If you already know how to compile a kernel, yes.

If you want to learn, see [https://help.ubuntu.com/community/Kernel/Compile/](https://help.ubuntu.com/community/Kernel/Compile/) . It is probably not worthwhile for those patches. However, when the patched are added AND when the Ubuntu Kernel Team bumps the kernel to that version, please help test it!

Ubuntu Kernel Team bumps are reported in the Ubuntu Weekly News, on [http://planet.ubuntu.com](http://planet.ubuntu.com) , and other places.

**Tip**: Try it in a VM first. Your first few tries compiling a kernel are likely to tie up your sytem for hours and VERY likely to break your system.
**Tip**: Get kernel patches and discussion from the source at kernel.org instead of that unauthorized reprinter.

Download the source code
Prepare your config file
Apply the patches
Compile
Install

---

### Post by Cheesemill on 2012-07-13
If you can wait then these patches will be incorporated into the 12.04 kernel that is in the repositories

Just keep updating your system and you will get them eventually (or you could compile a custom kernel as outlined in the above post).

---

### Post by Lupajz on 2012-07-14
@Cheesemill - yep sure I will eventualy update my kernel, but at those messages I think there was mentioned that it will be avaliable only from version 3.6 ? So it will be som time :) 

@Sure I will help test it, as it is pretty important update for me :)I know something about compiling kernel but I am not sure about making an patch file from those emails :( 
Any help at this point ? How should those files look like ??

---

