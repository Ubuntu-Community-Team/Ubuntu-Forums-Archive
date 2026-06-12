---
title: "What makes ubuntu not so fast?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by cormano on 2008-05-26
Hello there. I've been running Ubuntu for years now, since 5.something. Im generally very pleased with the system, everything works, the forums are great, the repositories couldnt get any better, etc. But theres something ive been wondering for a while. What makes Ubuntu's gnome implementation slower and heavier on ram than other distros gnome implementation(PCLinuxOs for example) . Ill ellaborate: take ubuntu hardy heron, set it to use metacity, turn off unneeded services like cups(in my case), hplib, bluetooth, visual aids, etc. It still has about 100 processes running and around 200 mb of ram used right after boot. 
Now take PclOS2008 Gnome edition, without any tweaks, it has about 80 processes  and only about 110 mb of ram used, all acording to gnome-system-monitor and top. And the PclOS systems feel way more responsive too. PCLos is using metacity too, so thats not a wm issue.

I love ubuntu, its package system is much better, has a lot more software and its overall more polished, but that extra speed im missing pisses me off a bit.
All this is tested under the same hardware, and 3 different machines, a dothan laptop with 1GB ram, an athlon xp with 1.5 GB Ram, and a C2D e4300@3ghz with 2gb of Ram. Well, guess thats all, im just curious, hope someone knowledgeable can point some reasons for this. And sorry for the suboptimal english btw :D

---

### Post by cristo-father on 2008-05-26
I don't know the answer, but with window managers such as icewm you can just use less than 100mb from startup.It has awesome themes.

---

### Post by d.kusummmanth@gmail.com on 2008-05-26
Check out these links... [http://ubuntuforums.org/archive/index.php/t-213694.html]("http://ubuntuforums.org/archive/index.php/t-213694.html")
and[ When you can say that Gnome is slow/bloated]("http://adi.roiban.ro/?p=18")

I would advise u to shift over to Xubuntu, which will definitely make u happy with its speed improvement. Anyways, what u say is quite right.

But I've accepted this drawback, because it is compensated by other excellent improvements in Ubuntu like more User friendliness, More no of applications,etc.,

---

### Post by d.kusummmanth@gmail.com on 2008-05-26
one imp. reason for slowing down ur system could be Firefox, which is v.heavy on memory.

---

### Post by cormano on 2008-05-26
Thanks for all the replies. Im not really whinning about my system being unusable, not even close. Hardy Heron runs quite well on my dothan laptop, even at 800mhz. Its just that i wonder why such a difference exist between gnome running under 2 different distributions. As for Xfce, ive ran it in the past, its a nice piece of software, but i really like gnome, and the extra speed isnt that important for me, its just that im curious.

---

### Post by Bubba64 on 2008-05-26
> **cormano said:**
> Thanks for all the replies. Im not really whinning about my system being unusable, not even close. Hardy Heron runs quite well on my dothan laptop, even at 800mhz. Its just that i wonder why such a difference exist between gnome running under 2 different distributions. As for Xfce, ive ran it in the past, its a nice piece of software, but i really like gnome, and the extra speed isnt that important for me, its just that im curious.

I have a laptop that runs at 700Mhz and 256 ram and I notice a bit of a difference between it and the desk top which is 1.7 gig with the same 256 ram. I use the computers at school when I am forced to that run some windows version and they are slow to when their system has 4 times the speed of my 2700 Kb DSL.

---

### Post by robalcorn on 2008-05-26
> **cormano said:**
> Thanks for all the replies. Im not really whinning about my system being unusable, not even close. Hardy Heron runs quite well on my dothan laptop, even at 800mhz. Its just that i wonder why such a difference exist between gnome running under 2 different distributions. As for Xfce, ive ran it in the past, its a nice piece of software, but i really like gnome, and the extra speed isnt that important for me, its just that im curious.

I shadow your question I have never seen this before with other releases and other flavours of linux. I also have noticed many other comments about this for last few weeeks as well.My rig runs great but the memory usage is weird.

---

### Post by arcarsenal on 2008-05-26
Same here... it feels a little bogged down. Not too many complaints aside from that, though.

---

### Post by Paqman on 2008-05-26
I guess the way to answer your question would be to compare the differences in what processes are running by default.

---

### Post by robalcorn on 2008-05-26
> **Paqman said:**
> I guess the way to answer your question would be to compare the differences in what processes are running by default.

For me its just starting up ff3 b5 and disabling many of the "for me" unneeded services. But I can also sit back without surfing and watch irregular spikes in memory consumpution and hear hard drive working away with nothing relevant to cause it.

---

### Post by sam_delta on 2008-05-26
> **robalcorn said:**
> For me its just starting up ff3 b5 and disabling many of the "for me" unneeded services. But I can also sit back without surfing and watch irregular spikes in memory consumpution and hear hard drive working away with nothing relevant to cause it.
about the disk activity, ext3 file system once every some time (i duno how often) starts something called "journalling" which do something with your harddrive. (to keep data safe) so i guess its the ext3 journalling (which is safer for your data)

i duno if thats causing that disk activity . but thats my guess
sam

---

### Post by Paqman on 2008-05-27
Could be Tracker or Beagle indexing, a cron job or some other daemon. BOINC watches your keyboard and waits for you to be inactive a while before kicking in, for example.

---

### Post by FakeOutdoorsman on 2008-05-27
Why not try a custom install with the alternate installation disc?  Just install a command-line system and then build up from there.  You'll learn a lot about your system and get only what you want installed:

[Installation on Low Memory Systems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")
[Howto: Set up Hardy for speed, v1.0]("http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/")
[Lightweight Gnome]("http://ubuntuforums.org/showthread.php?t=298835")

---

### Post by dbera on 2008-05-27
Folkd... do some searching on the web please. All the Hardy slowness and disk access is due to Firefox-3 doing excessive fsync for its sqlite database.

Just do some web searches and you will find many people talking about it and even some workarounds. There is no beagle or tracker business here.

---

### Post by philinux on 2008-05-27
Turn those two "Tell me's off"

Hopefully RC1 will solve this.

---

### Post by sayakb on 2008-05-27
Well, what about my problem then?
I decided to bring back an old PC to life. Since it had XP, I never used it, and even decided to send it to junk. I tried puppy linux, but isn't that "too minimalistic"??
Anyway, I installed Xubuntu 7.10 on it. It already did have XP, so hence, I dual booted. Here's the config: Celeron 633MHz, 384MB SDRAM, 80GB IDE, Intel i810 mobo with onboard VGA (yeah, its an ooooold PC for sure!! ;))
Xubuntu was pretty slow. I posted a thread and I was suggested to use OpenBox ([http://ubuntuforums.org/showthread.php?t=807318](http://ubuntuforums.org/showthread.php?t=807318)). I customized it in my way. Now it runs only these:

[ATTACH]71786[/ATTACH]

And uses less than 80MB of RAM (usually ranges from 60-75MB)
Ofcourse, I can't use ROX (too minimalistic). I use ROX for desktop icons, thunar (, xfce-panel, just 2-3 applets and nothing more. Even after this, this all setup is slower than Windows XP Professional (AARGH..)
Ofcourse, i CANNOT use XP.. But what should I do to make this faster. I know this is an old PC, but how can such a lite setup be **slower** than XP on the same machine?? :mad:
:guitar::guitar::guitar:

---

### Post by Foxblood on 2008-06-09
> **Paqman said:**
> Could be Tracker or Beagle indexing, a cron job or some other daemon. BOINC watches your keyboard and waits for you to be inactive a while before kicking in, for example.


Well, I had quite the opposite experience with BOINC. On startup my CPU usage was maxed out. System monitor only confirmed what Conky had already told me - both CPU's at 100%. The only thing I had installed recently was BOINC. I removed it and now my CPU usage ticks over very nicely at around 3% each. Quite possibly I had it mis-configured. But this was after startup and BOINC was supposed to wait for idle time.

---

### Post by napzilla on 2008-06-18
Have you tried disabling the Compiz desktop effects? You can do this in a GUI by selecting System->Preferences->Appearance, and then selecting the 'Visual Effects' tag. Either Gutsy or Hardy started enabling some special effects by default, and I've found that they tend to eat up a lot of my memory and processor time. Switching the option to 'None' freed up a lot of resources. I use Metacity, so I felt that no effects would be in keeping with Metacity's reputation as the Cheerios of desktop managers.:)

---

