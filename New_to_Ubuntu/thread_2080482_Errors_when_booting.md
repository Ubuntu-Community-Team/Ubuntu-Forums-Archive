---
title: "Errors when booting"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by Alan Bradley on 2012-11-04
When I boot up I get a screen flashes during boot up that looks like errors. It flashes pretty fast and I cant read all it. But everything seems to boot fine and there are no problems that I can tell.

Is there a way to pause this screen so I can read the errors? Is this normal? Or is something not installed correctly?

---

### Post by grahammechanical on 2012-11-04
First, if everything boots fine what are you worried about?

Second, what you think are error messages are most probably system messages. I say most probably because I am not seeing your screen, am I?

Third, the boot manager has its own video settings that are basic so that it runs on every video card. At some point the boot manager hands over control to the Xserver, which is the application that sits between the OS and the video card in Linux. The Xserver will have its own default settings and at some point it will read the optimum video settings from the monitor and switch to those as well as activating and making use of the video driver that the OS has chosen for your particular video card.

So, you see it is a complicated business. And it has to be like this because of the great variation of hardware that people like us are installing Linux on.

Regards.

---

### Post by ibjsb4 on 2012-11-04
Open nautilus and go to your filesystem then navigate to /var/log/boot and see if the error message shows up there.

---

### Post by Alan Bradley on 2012-11-11
Thanks for the explanation. I was just concerned that something could go wrong at a later time. But I guess your right, if it aint broke then don't fix it.

---

### Post by Alan Bradley on 2012-11-11
@ibjsb4

Thanks for the answer. I checked and there was nothing there. So I guess everything is okay.

---

### Post by Bashing-om on 2012-11-11
Alan, It's me again ....

If you have made any edits to grub's kernel boot line you may have enabled boot messages upon booting ??? -> But I agree ---if it ain't broke, don't fix it !

Then again -> if it ain't broke, you have not tweaked it enough !

[INDENT]my pennies worth <== BDQ

[/INDENT]

---

