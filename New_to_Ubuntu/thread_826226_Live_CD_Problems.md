---
title: "Live CD Problems"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by mdvigi7536 on 2008-06-11
Hello.  Trying to run several Linux LiveCDs on an older computer.  I have burned the disc image properly and I have set the BIOS to go for the CD first.  Upon restart, I hear the CD drive making noise, but after a couple of minutes of nothing, it goes to Windows.  I know it's not the disc since it works in my computer, and I played a music CD in the drive when Windows came up, so I don't think it's the drive.  What gives?  This has happened on several distributions and I am just trying to get it to work so I can check it out.

Here's what I know about the computer:

It's an emachines computer, 733Mhz processor, 192MB of RAM, Philips CD-R drive.

I'd appreciate any advice.
--Mike

---

### Post by Lord Xeb on 2008-06-11
It isn't going to work.You need at least 284MB (I think) to have the LiveCD to even boot. You are going to have to use the alternate install which is text based or upgrade the amount of RAM.

---

### Post by Duck2006 on 2008-06-11
> It's an emachines computer, 733Mhz processor, 192MB of RAM, Philips CD-R drive.

You will have some problems trying to run Ubuntu, with that amount of ram. You will be better of trying puppy or DSL linux.

---

### Post by mdvigi7536 on 2008-06-11
Sorry, I should have been more specific!

I was trying to run xubuntu's live cd.  According to their website you need only 128 MB to run it and 192 to install it.  I have 192 and couldn't do either.

I also downloaded Puppy Linux--not that I know what it is, I just know it's really really small--and burnt the image, and got the same response.  Nothing for a few minutes, then windows.

---

### Post by RomeReactor on 2008-06-11
Hi. Have you tried the Xubuntu disc on another machine? It could be that it didn't burn correctly. If you still have the image and a spare blank CD, try burning it again at a lower speed.

---

### Post by kansasnoob on 2008-06-11
Even with Xubuntu you'll need the alternate CD which is "text based" install rather than graphic install.

[http://www.xubuntu.org/get#hardy](http://www.xubuntu.org/get#hardy)

Just choose your local, and then scroll down to where it says, "Alternate install CD".

---

### Post by mdvigi7536 on 2008-06-11
I thought it might have something to do with my laptop's burner too.  Burned the image at the slowest speed possible.  For my laptop, it was 10x.  No effect.

I have put all the CDs I burned into my laptop and they all work OK.

I am trying not to do the alternate install CD since I exceed the minimum requirements for Xubuntu's Live CD and I am just trying to try it out on this computer before I commit, something I understand can't be done on the alternate CD.  Plus, that "Puppy Linux" CD is supposed to work on the rock-bottom old computers and was also ignored.

What might be causing this computer to ignore all these bootable CDs?

---

### Post by RomeReactor on 2008-06-11
Did you burn the image in the laptop? maybe the burner is having trouble burning discs, but can read them. Can you move the image from your laptop to your PC and burn it there (at 4x if possible)? Also, did you check the md5 sum of the image?

---

### Post by miss.magenta on 2008-06-11
try a different brand of cd - some brands just don't play well with some hardware and, unfortunately, the only way to figure it out for yours is trial and error.

Last week at work I had to do a CentOS install for a new server, so I popped in the media that I've used many times before and the thing would not boot - it'd get past the raid setup, bios, but then just fail.  I went nuts for a little bit trying to figure it out, since I could boot to that disk in other machines...then I was reminded of this little issue, burned new cds on a different brand, and viola - installed on my merry way (as merry as I can be about redhat, which isn't very).

---

### Post by ugm6hr on 2008-06-11
Clearly there is a problem with booting from the CD drive on that machine.

Have you tried booting from any non-linux CDs?  You could try this: [http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm) if you haven't got a DOS / Windows CD.

---

