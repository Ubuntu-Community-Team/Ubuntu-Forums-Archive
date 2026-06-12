---
title: "Monitors are cheap, can I add 4 Monitors with Ubuntu 14.04 ?"
date: 2015-01-04
forum: New to Ubuntu
---

### Post by cwmoser on 2015-01-04
I note that PC Monitors are cheap.
Can I add 4 Monitors to my Ubuntu 14.04?

I am currently running Dual Monitors with an nVidia GeForce Video Card.

What does it take to do this?  Anyone actually got it working?

Carl

---

### Post by TheFu on 2015-01-04
Updated: seems my knowledge is outdated thanks to display port (which I don't have).  Leaving it here for folks with older hardware.

I've seen 3 monitor setups - they use 2 video cards. My laptop supports 3 monitors with a single GPU (2 external connections and the built-in screen). For all external monitors, the cost issue seems to be mounting them in a useful way cheaply. Mounts seem to be 100$+.  My friend gave up and just put the 3x24 inch monitors across a huge desk, side-by-side.  You'll probably need to manually setup the xorg.conf file (he wrote part of X/Windows back in college at MIT, so not a big deal to him). I haven't had to do that with any dual monitor setup in years, but remember doing it for a control center setup for 400 UNIX workstations in the mid-1990s. Here's the redesigned setup: [http://www.nasaspaceflight.com/wp-content/uploads/2013/08/Z322.jpg](http://www.nasaspaceflight.com/wp-content/uploads/2013/08/Z322.jpg) for that team and the [older version I helped configure]("http://www.jsc.nasa.gov/history/jsc40/gallery/lores/S95-16439.jpg"). The worse part was that each video card had to run a separate X/Windows process - that means copy/paste between the monitors running on different cards didn''t work.  Perhaps a clipboard manager will handle that these days, but the normal select/paste method of X/Windows will not - which is a show-stopper for me.

There are companies who make single graphics cards that support 6+ monitors (VGA/HDMI ports), but the drivers are Widows only.

Whatever you do, your life will be much easier if identical GPUs are used. Do not mix nvidia and ATI.

---

### Post by DuckHook on 2015-01-04
I run 4 monitors on one GPU and can go up to 6 if I care to split my DisplayPort output using a splitter and active adapters. Newer monitors can avoid the cost of adapters by daisychaining their DisplayPorts (but you must make sure they are DP 1.2 standard and have 2 DisplayPorts), but I have ten-year old monitors picked up from an office clearance auction and they lack this capability. I can use either the open-source radeon driver or fglrx (both tested) on my ATI/AMD HIS HD 7950 card. It's easy and painless these days. I invested in a good GPU so that I wouldn't have to go the two card route, which I've heard is still fraught with pitfalls, although many people have reported success. I wouldn't know about that, since my GPU can be bought from eBay or Newegg for $120 these days, and I take the easy route because I no longer care to wrestle alligators on my production box.

The old issues with multiple monitor support have been largely laid to rest, thank goodness. The radeon driver has also come a long way. I understand that the same is true for Intel and nVidia, so there's no reason to hesitate.

---

### Post by TheFu on 2015-01-04
That 7950 card is impressive. 
Seems there are important caveats [http://www.techpowerup.com/forums/threads/three-monitors-on-an-ati-radeon-7950.205182/](http://www.techpowerup.com/forums/threads/three-monitors-on-an-ati-radeon-7950.205182/)

---

### Post by DuckHook on 2015-01-04
> **TheFu said:**
> ...Seems there are important caveats...Yes, very much so. You can't just plug in anything any which way and expect them all to work. My monitors are all identical, so that's one hurdle that I don't have to deal with. The card is a reference design, so it only has one DVI and one HDMI. Therefore each DP is connected via *passive* adapter to only one monitor, thus avoiding another hurdle. When doing these sorts of pushing-the-envelope type things, the usual KISS principle applies.

If I want to go to six monitors, I would have to buy two more *identical* monitors, two hubs/splitters (each driving three monitors), six *active* DP adapters and the DVI cables. The local computer store has priced out the hubs for me at $120 each, and the active adapters at $40. Therefore, the DP kit would end up costing me more than my monitors in total. This configuration would mean that I would have to abandon both the DVI and HDMI ports, as I will then have maxed out all available RAMDACs on the DP ports alone.

But I *would* have 6 monitors. <sigh> Oh well... Sometimes a guy has to practice some self-restraint.

---

### Post by cwmoser on 2015-01-04
Now I am wanting 4 separate desktops -- not 4 monitors chained together with the same desktop.

---

### Post by DuckHook on 2015-01-04
> **cwmoser said:**
> Now I am wanting 4 separate desktops -- not 4 monitors chained together with the same desktop.Yeh... It's a little bit like golf clubs: once you actually *get* the set for which you've pined away those many years, you immediately pine away for the next set up.:redface:

---

### Post by cwmoser on 2015-01-05
Yep, got dual Monitors at home now.  When I was working I had a quad Monitor setup - I liked a lot.
Helped a guy with a Windows virus issue with his home PC and he had 8 monitors - that was quite a setup.

---

### Post by TVTrukChik on 2015-01-06
I have a 4-monitor setup at work on 14.04.  I bought a single video card with 4 outputs:  2 HDMI, 1 DVI, and 1 DisplayPort.  I actually have them hooked up to 4 RF modulators, feeding a separate webpage to each of 4 digital channels on our in-house cable system.  It's kind of like an airport flight status display, but it's the status of our vehicles, microwave links, and remote cameras.  I'd have to take down one of the channels temporarily to get you the exact details of the card... it's a not-too-expensive NVidia or Radeon card, most likely Radeon.  Was super easy to set up.  If you want the exact video card details, I'll see if I can schedule a little "maintenance" time.  ;)

---

### Post by cwmoser on 2015-01-06
> **TVTrukChik said:**
> I have a 4-monitor setup at work on 14.04.  I bought a single video card with 4 outputs:  2 HDMI, 1 DVI, and 1 DisplayPort.  I actually have them hooked up to 4 RF modulators, feeding a separate webpage to each of 4 digital channels on our in-house cable system.  It's kind of like an airport flight status display, but it's the status of our vehicles, microwave links, and remote cameras.  I'd have to take down one of the channels temporarily to get you the exact details of the card... it's a not-too-expensive NVidia or Radeon card, most likely Radeon.  Was super easy to set up.  If you want the exact video card details, I'll see if I can schedule a little "maintenance" time.  ;)

"in-house cable system"?  Cool.  Can I ask you what modulators did you use to merge your signals in with the 
Cable Channels?  This is something I've been wanting to do for a long time.

Carl

---

### Post by TVTrukChik on 2015-01-06
> **cwmoser said:**
> "in-house cable system"?  Cool.  Can I ask you what modulators did you use to merge your signals in with the 
Cable Channels?  This is something I've been wanting to do for a long time.

Carl

They are Blonder-Tongue model HDE-2H/2S-QAM.  2 HDMI and 2 HDSDI inputs, can output 4 QAM channels into the space of 1 analog channel.  They're pretty pricey. 

--Donna

---

### Post by cwmoser on 2015-01-06
> **TVTrukChik said:**
> They are Blonder-Tongue model HDE-2H/2S-QAM.  2 HDMI and 2 HDSDI inputs, can output 4 QAM channels into the space of 1 analog channel.  They're pretty pricey. 

--Donna

Pretty pricey on Ebay too, ouch.
I have two Blonder Tongue modulators (AM-60-550B and BAVM-Z) that I use with
my antique Televisions.  But, they don't work by substituting Cable TV channels.

Carl

---

