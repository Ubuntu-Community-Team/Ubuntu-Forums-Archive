---
title: "Ubuntu Installed but......"
date: 2014-05-25
forum: New to Ubuntu
---

### Post by gordon99 on 2014-05-25
I have just installed Ubuntu 14.04 as an additional OS to Windows 7. At the completion of the install it asked if I wanted to re-start. I thought I should remove the USB flash drive from which I did the installation before re-starting and as I did a chain of writing came up with words like panic. Nothing would work so I switched off the Notebook and, with some trepidation, switched back on. A screen with about 5 or so boot options came up in the Ubuntu colour. I left it to boot up without changing the selection and it booted into Ubuntu much to my relief. I then logged off and shut down. On switching back on the boot option screen re-appeared and this time I selected Windows 7 which booted up as normal so it seemed.
I am anxious to know what happened when I removed the flash stick to cause the black and white screen to appear with the worrying script.
Is there likely to be corruption of the installation or is this something which frequently occurs with no adverse outcome?
One other question. The options I get to boot up include, amongst other things,  Windows boot loader. Why is that? I expected just to see Ubuntu and Windows 7 as the options. Are there any checks or tests I should make to satisfy myself that all is well?

---

### Post by sammiev on 2014-05-25
Looks good. You will notice options like Advance Boot and Windows Recovery and maybe Hp or Dell or whatever Recovery or Tools. Those options are for when things go wrong or if you do a little extra testing.

---

### Post by whitesmith on 2014-05-25
I believe this is what happened. You made a mistake in removing the USB drive before Ubuntu finished its shut-down process, which caused a kernel panic -- essentially the equivalent of Windows' BSOD. Since the machine booted normally afterwards it appears no permanent harm was done. The Windows boot loader is a normal part of installation, since it provides for the contingencies **sammiev** mentioned.. Don't worry! All is well provided Ubuntu boots without error. Regards.

---

### Post by Unanimated on 2014-05-26
> **whitesmith said:**
> I believe this is what happened. You made a mistake in removing the USB drive before Ubuntu finished its shut-down process, which caused a kernel panic -- essentially the equivalent of Windows' BSOD. Since the machine booted normally afterwards it appears no permanent harm was done. The Windows boot loader is a normal part of installation, since it provides for the contingencies **sammiev** mentioned.. Don't worry! All is well provided Ubuntu boots without error. Regards.

Adding on to this, you caused a kernel panic within the live CD session that the installer uses - which was all cleared when you restarted the computer and the RAM was reset, so there's nothing to worry about.

---

### Post by gordon99 on 2014-05-26
Many thanks for the re-assurance. The screen at switch on has two memory test options. I have run both, though they seem similar tests, may even be identical. Am waiting for the second one to complete. The first test (which made no mention of consol in the title) took about 30 minutes. The second test, which included consol, seems as if it will also take about 30 minutes. 
The second test has now finished as I write on an Ipad. Both tests gave a Pass. I will now get to know Ubuntu and no doubt will be back with more questions.

---

### Post by mastablasta on 2014-05-26
those tests didn't help you figure out anything but the fact you have a working RAM modules :P

[https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest)

---

