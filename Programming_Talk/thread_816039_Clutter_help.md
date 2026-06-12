---
title: "Clutter help"
date: 2008-06-02
forum: Programming Talk
---

### Post by | MM | on 2008-06-02
**Warning: I am pretty much a total noob at writing python, well code in general...**


Hi,

I've been fooling around with clutter for the last few hours and I've come across a problem with Behaviours that i cannot figure out.

So i have a custom clutter 'widget' which is of the type <DropShadowImage object at 0x9fc820 (ClutterGroup at 0xbee840)>.  Its basically a clutter.Group with a couple of textures:
```
w = DropShadowImage("/media/sdb5/My Pictures/Evil/DSC04684.JPG", shad_width=25, shad_opacity=0.5)
stage.add(w)
``` 

I connect my widget to an event (mouse click) which calls the following code:
```
def smooth_scale(action, event, widget):
	if event.button == 1 and event.click_count == 2:
		timeline = clutter.Timeline(25, 150)
		timeline.set_loop(False)
		
		alpha = clutter.Alpha(timeline, clutter.smoothstep_inc_func)

		s_behaviour = clutter.BehaviourScale(0.7, 0.7, 0.2, 0.2, alpha=alpha)
		s_behaviour.apply(widget)
		
		timeline.start()
		print widget, widget.get_scale()
```

Now i can get this to work when i create the timeline, alpha and s_behaviour in main() and just do timeline.start() in a seperate function called if an event occurs.  but i cannot get it to work when i move all of the behaviour stuff out into its own function.  I do not get any errors either.  What am i doing wrong? :confused:

I've attached my complete code as well if that helps.

I am off to bed then have uni, so it'll probably be a day before i check back.

Cheers for any help, 
Matt

---

### Post by | MM | on 2008-06-09
Well i solved this a while ago.  You have to make the following globals or create the animation in a seperate class:

```
timeline = clutter.Timeline(25, 150)
timeline.set_loop(False)
		
alpha = clutter.Alpha(timeline, clutter.smoothstep_inc_func)
s_behaviour = clutter.BehaviourScale(0.7, 0.7, 0.2, 0.2, alpha=alpha)
```

---

