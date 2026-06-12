---
title: "Fresh Kubuntu install hangs at boot time"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by doctorbighands on 2011-11-01
Just installed Kubuntu 11.10 amd64 on my desktop machine. Md5sum of my downloaded iso checked out. Install appeared to go fine. I rebooted after installation was complete, got to the login screen, entered credentials, and then it hung on the "hard drive" logo (as in, wouldn't boot further, and stuck cursor). 

I hit CTRL-ALT-F3, logged in, and ran updates, thinking maybe something was out of sorts. Rebooted after updates, same story - still hung at KDE boot screen with the "hard drive" logo.

I tried switching to KDE because Oneiric+Unity is an unstable, buggy, messy, user-unfriendly disaster. Now, after jumping ship to something else, I can't even get my machine to boot properly.

What gives? I'm sure it's something simple, but I don't know where to go from here.

Thanks!

EDIT: I'm 99% sure it isn't a hardware issue. All hardware is nearly brand new, HDD and RAM diagnostics check out, and the machine worked fine right up until I upgraded to Oneiric. Just in case, though, here's the basic configuration:

Core i5-760 CPU
16GB RAM
60GB SSD (boot/OS device)
750GB HDD (/home)
ATI Radeon HD 5570 PCI-e GPU

---

### Post by doctorbighands on 2011-11-01
Problem seems to be solved, for now. All that remains is to figure out exactly what the problem was!

Let me explain:

After letting it sit at the "hung" boot screen for awhile, it eventually tried to give me a desktop, but it was going reeeeeeeeally slowly. So, I figured maybe it was a hardware conflict after all. I tried two things at once: Drop to a shell prompt and install the fglrx driver (that process went fine), then unplugged all of my USB peripherals. Rebooted, and it's running like a champ!

Either the graphics driver was causing the problem (which I don't think is likely), or one of my USB devices was. The only ones left that I haven't troubleshot are an external HDD and a MagicJack that's meant to be used in a Windows VM in VirtualBox. I'm leaning toward the MagicJack, although it's worked fine before and I'm not sure what it would be doing to cause problems.

Anyway, problem seems to be solved, and it looks like I can chalk it up to a hardware conflict of some kind. Maybe that'll help someone in the future...who knows?

---

