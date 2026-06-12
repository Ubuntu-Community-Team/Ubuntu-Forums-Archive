---
title: "Xubuntu/Ubuntu iinstallation feezes on a HP Celeron?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by lupita sosa on 2008-06-25
Hello Ubuntu Community ;D

This computer originally run on Windows XP, but no matter what anti virus we used, it was always plagued with Trojans D:

So m y son recommended me to use Ubuntu,but since the computer is pretty low at RAM we we have chosen to use Xubuntu instead.

The problem is that the installation freezes

When we run Xubuntu from the live CD to install it from there, it runs so painfully slow that it takes it several minutes just to move the mouse, and clicking on the install button is so slow that it eventually freezes the computer.

And if attempt to install it from windows, (after putting the --skipmemorycheck to the WUBI installer), it installs it, but when i reboot and it gets to the desktop, where its suppossed to install the OS and make the partitions, etc. It freezes...
no dialog box or installation process or whatsoever appears, it stays there with only the desktop image until it freezes.

So it never gets installed
i'm on puppy Linux, but i don't really like it..

The specs are:

40 gb Hard drive
2.8 ghz Intel Celeron processor
32 mb video Card
248 mb ram

Do you think it could be that it's a Celeron processor? it runs fine, but you can notice that it's not good for some applications...

Any help on installing and running Ubuntu, Xubuntu or some other Linux or things like that OS that are easier to use and more Ubuntu like than puppy linux would be greatly appreaciated

Thanks :D

---

### Post by phidia on 2008-06-25
The amount of ram you have should be enough for xubuntu. I really don't think it's the processor either. The clock speed of the cpu is more then adequate. The [xubuntu webpage]("http://www.xubuntu.org/get") does recommend 256MB ram for running once installed
A couple of things to try would be the alternate install cd-that requires less memory for installation. I would check that the iso images you have/get are ok-run md5sum on them from puppy if need be.
A couple of other distros you might try are [Zenwalk]("http://www.zenwalk.org/") & [Dreamlinux]("http://www.dreamlinux.com.br/").
Both of those use the xfce DE and IMO they are less resource intensive.

---

### Post by dominiquec on 2008-06-25
I have had the same problem occur to me on a 240MB RAM Thinkpad.  It takes a while to load the LiveCD, and sometimes it just hangs during the installation.  Once you get past it, though, it works okay (not great because it's slow, but okay).

To get through the installation, I recommend you use the Alternate install disk.  This dispenses with the LiveCD functionality.

---

### Post by dominiquec on 2008-06-25
By the way, I am using a minimalist version of Ubuntu on my Thinkpad now.  Not sure if it's up to your tastes (no sound) but since all I use it for is browsing and writing, it works okay for me.

My experinces at [http://ubuntuliving.blogspot.com/2008/06/minimalist-ubuntu.html](http://ubuntuliving.blogspot.com/2008/06/minimalist-ubuntu.html)

---

### Post by luisito on 2008-06-25
I cannot be because it is a Celeron. I am currently writing this post on a Celeron of 800Mhz with 384Mb of ram. It runs fine even though it is an arcaic processor. I don't know how installation would go because I did it a while ago in Feisty and then I updated to hardy online.

---

### Post by growingneeds on 2008-09-21
On my IBM Celeron D, I had difficulty installing Ubuntu Live CD. The install came through after using the Alternate CD. However, I am currently using the Xubuntu Alternate CD. The installation no longer hangs (compared to the Live CD), and the desktop is able to handle most tasks reasonably (no doubt slow at times).

I would highly recommend getting the Xubuntu Alternate CD for Celeron installations.

---

### Post by andersja on 2009-10-06
Related question: how well does a Celeron M fare with Ubuntu karmic and today's apps (Skype video conferencing etc) - is it anywhere near comparable to the Intel Atom, and does it still work fine? See also: [http://ubuntuforums.org/showthread.php?t=1283176](http://ubuntuforums.org/showthread.php?t=1283176)

---

### Post by Bartender on 2009-10-06
You cannot use the LiveCD.  You have to use the alternate-install CD.  You end up with the same operating system at the end, it's just that the alt-install CD doesn't need as much RAM as the LIveCD does.

If you can scrounge up more RAM for that PC, get it to at least 512, you'll notice a HUGE difference.

The Celeron processor is PLENTY fast enuf for Ubuntu or Xubuntu or Kubuntu.  It's just the RAM that's killing you.  I have a test PC running a 1GHz Pentium III and it's fairly responsive.  But it has about 700+MB RAM.

---

### Post by andersja on 2009-10-07
Thanks, Bartender

I'll head to crucial.com and pick up a spare 512Mb stick to get up to 768Mb. It was the processor capacity I was more worried about, as swapping / upgrading a laptop processor would be nigh on impossible. Thanks again for sharing!

---

### Post by 3rdalbum on 2009-10-07
Yep, definitely the amount of RAM. You can either upgrade the RAM or install using the "Alternate CD", because there's not enough RAM to run the live CD system AND the installer program :-)

---

### Post by Bartender on 2009-10-07
andersja -
I was responding to the original poster with the 2.8 MHz Celeron.  But it sounds like you're in the same boat as far as RAM.

Just so we're clear - there are two issues when we're dealing with a low-RAM PC.  

The first issue is just getting the CD to install.  The LiveCD requires more RAM while it's doing its thing than the alt-install CD, so using the alt-install CD is the typical path.  If you had a LiveCD and a friend who was willing to loan you a stick of compatible RAM, you could bump up your RAM just long enough to install using the LiveCD, then remove the RAM and give it back! :)

The second issue is how are you going to feel about a sluggish PC day in and day out.  Yeah, Ubuntu will run on 256 RAM, but the experience is so much nicer with at least 512.

---

