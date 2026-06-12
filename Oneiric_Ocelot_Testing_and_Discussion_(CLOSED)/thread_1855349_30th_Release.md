---
title: "30th Release"
date: 2011-10-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Quarkrad on 2011-10-06
newbie - I've just built a system based on  11.10 and it working well.  If I leave it as it is and continue with all the updates will it be the same as the formal release on the 30th or should I re-install?  Thanks.

---

### Post by Quackers on 2011-10-06
A fully updated 11-10 should be the same as the new release. But that doesn't stop some of us doing a fresh install anyway :-)

---

### Post by jerrylamos on 2011-10-06
The semi "Official" answer they give us is that updates will keep you current.

Any number of us have found that multiple updates like the one I'm doing now will get the system somewhat garbled if not dead.

Because of "dead" possibility I have a couple or three or four partitions with Ocelot, Narwhal, ... running.  A few 10 GB partitions on a 250 GB hard drive leaves space for a hardly ever used Windoze 7 (for when I pass this pc on).

After the severalth update with new kernels the space taken by this update is about 1 GB larger than it was as a new install a few weeks ago.  Time to re-install. I do use Synaptic to remove old kernels but even that doesn't buy back all the old space.

Did I mention I'm running a USB hard drive right now on an Acer Aspire netbook?  Nice and responsive.  I'm retired, I also test on a tower and a notebook....I had a left over 2.5" hard drive from a laptop so with a new USB case $10 to $20 great for testing.    

You choose your own.  I think on a release in development a new install every so often cleans things up.

Now a couple days before a release the daily build can be almost the same as the release code.  Maybe.

Jerry

---

### Post by thatguruguy on 2011-10-06
> **jerrylamos said:**
> I had a left over 2.5" hard drive from a laptop so with a new USB case $10 to $20 great for testing. 

That's exactly what I do; I put the betas on an external hard drive and test from there. That way, I can just scrub it off and re-install as many times as I want if I get significant breakage.

The release candidate rolls out today.  There shouldn't be many changes between now and the full release date, which is the 13th (not the 30th).

---

### Post by jerrylamos on 2011-10-07
> **thatguruguy said:**
> That's exactly what I do; I put the betas on an external hard drive and test from there. That way, I can just scrub it off and re-install as many times as I want if I get significant breakage.


I've been starting on the next Ubuntu even before Alpha.  Early in the game, maybe even months later, Grub boot can get screwed up. That makes recovery a bit! troublesome.

With this setup using an external USB hard drive as bios default boot (if plugged in), Grub is set to update the external USB hard drive and leave the main hard drive alone.  Hopefully. 

I can even try the USB hard drive on my netbook (this one), notebook, and tower.  Ubuntu Grub does get a bit upset at seeing a different hard drive as /dev/sdb so I do a sudo update-grub as soon as I can get a successful boot.

Have fun.

Jerry

---

### Post by sgage on 2011-10-07
> **Quarkrad said:**
> newbie - I've just built a system based on  11.10 and it working well.  If I leave it as it is and continue with all the updates will it be the same as the formal release on the 30th or should I re-install?  Thanks.

I typically just keep updating right through the final release, and don't worry about it if everything's working. You should end up with the same bits.

I will download a copy of the official iso just to have, but won't reinstall unless something goes wrong.

BTW, the formal release date is Oct. 13, less than a week away!

---

