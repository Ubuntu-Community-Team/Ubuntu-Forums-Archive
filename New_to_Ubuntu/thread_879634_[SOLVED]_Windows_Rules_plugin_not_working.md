---
title: "[SOLVED] Windows Rules plugin not working"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by wariskampar on 2008-08-04
I set a rule for Conky using CCSM Windows Rules Plugin. Whenever I 'Show Desktop' or minimize all opened windows, Conky will stay on top (un-minimizeable). However, this is not happening. It seem like this plugin is not working. Am I alone with this problem. If not, how do I solve it? Thanks

---

### Post by wariskampar on 2008-08-04
Can somebody help me with this problem

---

### Post by estyles on 2008-08-04
Make sure that the regexp plugin is enabled.  I had a problem that Window Rules didn't seem to be doing anything at all, and the problem was that the regexp plugin was disabled.

---

### Post by kk0sse54 on 2008-08-04
What exactly were you trying to accomplish with Window's Rule? If you were just trying to embed conky into your desktop then you just need to edit your .conyrc other wise you can use Window's Rule to embed such things as your terminal into your desktop as long as you use compiz of course.

---

### Post by kk0sse54 on 2008-08-04
If you have trouble editing your .conkyrc use the one from this thread [http://ubuntuforums.org/showthread.php?t=205865&highlight=conky](http://ubuntuforums.org/showthread.php?t=205865&highlight=conky) although the thread is old the config file should still work

---

### Post by wariskampar on 2008-08-04
I do not want conky to disappear whenever I click on "Show Desktop" icon. @estyles; how do you enable regexp plugin. I could not find it. Embbed conky in Desktop?

---

### Post by estyles on 2008-08-04
> **wariskampar said:**
> I do not want conky to disappear whenever I click on "Show Desktop" icon. @estyles; how do you enable regexp plugin. I could not find it. Embbed conky in Desktop?

Yeah, I didn't need to use compiz window rules to keep conky from minimizing.  I'll have to take a look at my .conkyrc file when I get home and see if I can figure out why.

As far as compiz - I'm pretty sure that the regexp plugin is under Utility.  Again, will have to check it out when I get home to be sure.

---

### Post by wariskampar on 2008-08-04
It is not so in my case. Conky will always minimize when I 'Show Desktop'. Btw, here is my conky global config. One more thing, just found out that Windows Rules plugin was ok, only the minimize rules do not works. 

```
# set to yes if you want Conky to be forked in the background
background yes

# Draw borders around text
draw_borders no
draw_graph_borders no

update_interval 1.0

text_buffer_size 1024

double_buffer yes
own_window yes
own_window_transparent yes

# If own_window is yes, you may use type normal, desktop or override
#own_window_type normal

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

use_xft yes
xftfont Liberation Sans:size=8
#xftfont Trebuchet MS:size=10

# Text alpha when using Xft
xftalpha 0.9

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
#total_run_times 0

maximum_width 205
default_color white
#alignment top_right
alignment bottom_right

uppercase no
```

---

### Post by estyles on 2008-08-04
I think you should set "own_window_type desktop".  Or possibly override.  (note that the line that says "own_window_type normal" is commented out, because normal is the default.  Uncomment it, and try changing normal to desktop.)

---

### Post by wariskampar on 2008-08-04
not working. if I change it to desktop, everytime ,i launch conky, my system will automatically log out (luckily i set my conky_start.sh for 15 sec, otherwise, I would not be able to log in into my desktop again:)). change it back to normal does not yield anything either. hmmm...what it should be then?....

---

### Post by estyles on 2008-08-04
> if I change it to desktop, everytime ,i launch conky, my system will automatically log out

well, that certainly shouldn't happen - yeah, good thing you set the sleep command in your .sh file.  I'm somewhat stumped.  I'll post tonight after I check my .conkyrc file at home.

---

### Post by wariskampar on 2008-08-04
I figured it out. @estyles, somehow, you were right,but instead of desktop, I change it to override. That solve my problem. Thanks

---

### Post by estyles on 2008-08-05
> **wariskampar said:**
> I figured it out. @estyles, somehow, you were right,but instead of desktop, I change it to override. That solve my problem. Thanks

Cool.  Yeah, like I said, it's supposed to be either "desktop" or "override".  I guess it was override.  The plugin I was talking about in compiz, btw, is "Regex Matching" under utility.  It's one of those things that should just always be on - allowing it to be turned off as a plugin breaks a bunch of the other operations of compiz...  which seems silly to me.

---

