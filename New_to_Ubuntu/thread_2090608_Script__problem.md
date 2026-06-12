---
title: "Script  problem"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by rusty_jones on 2012-12-02
I ran this code and that is all i got in terminal.


```
&#9492;&#9472;&#9472;> conky -c /home/rusty/conky_baseball
Conky: desktop window (e00029) is subwindow of root window (10e)
Conky: window type - override
Conky: drawing to created window (0x2000001)
Conky: drawing to double buffer
```

This is my conky

```
# Conky settings #
background no
update_interval 300 #Update interval in seconds, it's up to you.

# --- Window Layout & Options --- #
own_window yes
own_window_transparent yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
use_xft yes
alignment top_right
gap_x 1300 
gap_y 35
# --- Colours, Sizes, Fonts & Margins --- #
minimum_size 1600 1600 #these may not need to be this big but it doesn't really matter
maximum_width 450 #this should be right if you use the same data I do.
stippled_borders 3
border_inner_margin 9
border_width 9
default_color grey

draw_outline no
draw_borders no
#font Monospace:size=8:weight=bold
uppercase no
draw_shades no

TEXT
${color CA1F2C}${font freemono:size=10}Philadelphia Phillies ${hr 2}
${color FFFFFF}${font freemono:size=8}${exec ~/.conky/baseball/Phillies_results.py}
#${color CA1F2C}${font freemono:size=10}Today's Games ${hr 2}
#${color FFFFFF}${font freemono:size=8}${exec ~/.conky/baseball/scores.py}
#${color CA1F2C}${font freemono:size=10}MLB Standings ${hr 2}
#${color CA1F2C}${font freemono:size=9} Wild Card ${hr 1}
#${color FFFFFF}${font freemono:size=8}${exec ~/.conky/baseball/standings_wild.py}
#${color CA1F2C}${font freemono:size=9} American League ${hr 1}
#${color FFFFFF}${font freemono:size=8}${exec ~/.conky/baseball/standings_al.py}
#${color CA1F2C}${font freemono:size=9} National League ${hr 1}
#${color FFFFFF}${font freemono:size=8}${exec ~/.conky/baseball/standings_nl.py}
```

Anyone have any idea's why it just stops there?

---

### Post by Toz on 2012-12-02
> **rusty_jones said:**
> I ran this code and that is all i got in terminal.


```
&#9492;&#9472;&#9472;> conky -c /home/rusty/conky_baseball
Conky: desktop window (e00029) is subwindow of root window (10e)
Conky: window type - override
Conky: drawing to created window (0x2000001)
Conky: drawing to double buffer
```
This is normal.

> This is my conky

```
# Conky settings #
background no
update_interval 300 #Update interval in seconds, it's up to you.

# --- Window Layout & Options --- #
own_window yes
own_window_transparent yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
use_xft yes
alignment top_right
gap_x 1300 
gap_y 35
# --- Colours, Sizes, Fonts & Margins --- #
minimum_size 1600 1600 #these may not need to be this big but it doesn't really matter
maximum_width 450 #this should be right if you use the same data I do.
stippled_borders 3
border_inner_margin 9
border_width 9
default_color grey

draw_outline no
draw_borders no
#font Monospace:size=8:weight=bold
uppercase no
draw_shades no

TEXT
${color CA1F2C}${font freemono:size=10}Philadelphia Phillies ${hr 2}
${color FFFFFF}${font freemono:size=8}${exec ~/.conky/baseball/Phillies_results.py}
#${color CA1F2C}${font freemono:size=10}Today's Games ${hr 2}
#${color FFFFFF}${font freemono:size=8}${exec ~/.conky/baseball/scores.py}
#${color CA1F2C}${font freemono:size=10}MLB Standings ${hr 2}
#${color CA1F2C}${font freemono:size=9} Wild Card ${hr 1}
#${color FFFFFF}${font freemono:size=8}${exec ~/.conky/baseball/standings_wild.py}
#${color CA1F2C}${font freemono:size=9} American League ${hr 1}
#${color FFFFFF}${font freemono:size=8}${exec ~/.conky/baseball/standings_al.py}
#${color CA1F2C}${font freemono:size=9} National League ${hr 1}
#${color FFFFFF}${font freemono:size=8}${exec ~/.conky/baseball/standings_nl.py}
```

Anyone have any idea's why it just stops there?
What do these files/scripts do/supposed to do:
- ~/.conky/baseball/Phillies_results.py
- ~/.conky/baseball/scores.py
- ~/.conky/baseball/standings_wild.py
- ~/.conky/baseball/standings_al.py
- ~/.conky/baseball/standings_nl.py

On my system, this script just displays a red line. Of course, I don't have those files. Perhaps you can post the content of one of those files.

---

### Post by rusty_jones on 2012-12-02
here are two of the files that's called in the script.

Phillies_results.py

```
#!/usr/bin/env python
import os
results = "lynx -nonumbers -nolist -dump http://m.4info.com/search?searchQuery=Philadelphia+Phillies | egrep -i -B2 -A8 'Status'"
cmd = os.popen("lynx -nonumbers -dump %s" % results)
output = cmd.read()
cmd.close()
print output
```

standings_nl.py

```
#!/usr/bin/env python
import os
filename = "http://scores.espn.go.com/mlb/standings | egrep -A19 'National League'"
cmd = os.popen("lynx -nonumbers -dump %s" % filename)
output = cmd.read()
cmd.close()
print output
```

---

### Post by Toz on 2012-12-03
I just realized that only the line that runs the Phillies_results.py script is uncommented. When you go to the web page referenced in that script ([http://m.4info.com/search?searchQuery=Philadelphia+Phillies]("http://m.4info.com/search?searchQuery=Philadelphia+Phillies")), you get:
> MLB coverage will resume in March.

If you uncomment the line with the standings_nl.py script, it will display the standings.

Note, you need to have lynx installed for these scripts to work.

---

### Post by rusty_jones on 2012-12-03
If you run ```
standings.py
``` you should get this printout, which another got.

[HTML][]("http://ompldr.org/vZ2ptZw")[/HTML]

All I get is 
```
&#9492;&#9472;&#9472;> conky -c /home/rusty/conky_baseball &
[1] 3837
Conky: desktop window (e00029) is subwindow of root window (10e)
Conky: window type - override
Conky: drawing to created window (0x2e00001)
Conky: drawing to double buffer

```

I've run all the scripts one at a time and none of then get past this point.

---

### Post by Toz on 2012-12-03
Try running the script independent of conky:
```
~/.conky/baseball/standings_nl.py
```

Do you get a listing of the standings to display? If not, check that the files are marked executable.

---

