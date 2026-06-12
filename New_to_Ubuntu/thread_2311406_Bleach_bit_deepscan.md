---
title: "Bleach bit deepscan"
date: 2016-01-27
forum: New to Ubuntu
---

### Post by terry44 on 2016-01-27
I'm running a deepscan with bleach bit but even though I know this takes a long time no indication appears on screen to say how long it will take or if it's still running successfully. It's tempting to abandon it after several hours but could still be working ? Would the community oblige and give me the low down on this. Thank you Terry

---

### Post by Frogs Hair on 2016-01-27
Hello and Welcome

I've never had BB take more than a minute to finish the deepscan portion and a progress bar should appear next to active . I see no problem canceling the process if it's been hours. I exclude some actions under system that I'm not comfortable with  including ***memory*** and ***free disk space***. The later could take a very long time.

---

### Post by Dreamer Fithp Apprentice on 2016-01-27
It can easily take several hours if you have it set to wipe free space on a large partition.

The deep scan per se alone, no, not in my experience at least.

 If you did the wipe free space option and didn't mean to, or have changed your mind, you can kill it but it will leave a huge set of files behind that will take hours and hours to rm. It might even be easier in that case to copy your good data off that partition to somewhere else and then reformat it. If you decide to rm it instead it will bog down your system. I've been doing this off and on for quite a few hours now (days? sure seems like) now and even niced 19 it bogs down my system terribly.

If you didn't have that option set something has probably gone wrong unless you have a very unusual setup.

However, Bleachbit WILL often appear to have hung in the gui when it actually IS working. I always run it by starting it in a terminal so that I can tell the diference between the gui looking jammed or even blank even though it is chugging right along underneath and an actual hang. Also, it can tell you exactly WHAT is taking so long. You can also run it ENTIRELY in a terminal without the overhead of the gui at all, but that is another subject.

---

