---
title: "Ubuntu Server 16.04 Only boots thru recovery"
date: 2016-04-27
forum: New to Ubuntu
---

### Post by thaelina on 2016-04-27
So my googlefu has failed me and I can't seem to figure this out. I installed Ubuntu Server with just the default package and the server minimal package. 

Install goes off painlessly but when it restarted it just goes to a black screen with no flashing caret. If I force a restart Crtl+Alt+Del it will restart and throw up the restarting splash screen. 
If I press DEL while its up it will show me a bunch of text real quick that I presume is shutdown steps since its unmounting stuff.

Now when I bring GRUB up on the startup and use the recovery mode, it loads just fine and I can proceed with the startup from there. 
Using the resume option in recovery it will load into the shell just fine and I can login as I expect. I tried running dpkg and fsck and ecenn updated GRUB and nothing changes for a normal startup.

So it sounds then like its a graphics driver issue which my googlefu also agrees with. I think it's curious that I don't have a discrete card, I'm using the on-board intel graphics. 
I had a Win7 install on the box prior that worked perfectly fine. I mean it may still be a graphics issue but I seriously doubt that. But then again I'm not 100% on that.

I'm not sure what is going on here, anyone have any ideas?

A side note, booting the 16.04 desktop live from USB works fine, installing the desktop instead of the server gives me the same black screen.

Parts:
[URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16813157271"]ASRock Z68 Extreme3 Gen3
[/URL][Intel Core i7-3770K Ivy Bridge]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819116501")[URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16813157271"]
[/URL]

---

### Post by DuckHook on 2016-04-27
Welcome to the forums, thaelina.

Though you are posting in the *New to Ubuntu* area, you sound like a seasoned user. Assuming this is so, I shall dispense with finicky detail and get to the point.

The usual procedure with black screen is to edit grub and add the nomodeset switch. Have you tried this? Since you can boot into recovery, it is possible to use an editor to try that first. Tell us how it goes.

---

### Post by thaelina on 2016-04-28
Okay so first, thanks! I'm actually super new to linux altogether, Ive just been what I would consider a power user of computers (namely windows) for years. And my googlefu is strong. 
So I went ahead and added the nomodeset switch and it booted wonderfully. Thanks for the tip, not sure why I didn't try that yet.
Went ahead and set it in /etc/default/grub as well and all is good. Removed quiet splash while I was in there too, I like seeing the scrolling lines.
Thanks for the quick reply! Had to go to work.

EDIT: Set to solved.

---

### Post by DuckHook on 2016-04-28
For someone "super new" to Linux your self sufficiency is impressive. Glad you worked it out. Good luck and happy Ubuntu-ing!

---

