---
title: "[SOLVED] Noob needs help with conky settings"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by I wanted to leave on 2008-09-20
I managed to install conky and copy a script to conkyrc and run it. 
See screenshot
But it seems I have a conflict with compiz when I restart Ubuntu.
Instead of displaying as in the screenshot, it appears/disappears as do my panels, open gnome windows etc
How do I fix this?


Please provide complete answers for a noob thanks

---

### Post by Dr Small on 2008-09-20
Please re-explain the problem again.

---

### Post by I wanted to leave on 2008-09-20
That was quick, thanks.
Ok you can see it works in the screenshot if I load conky after a reboot via the terminal. But when I go to sessions and add conky to start on boot, and then reboot the desktop, I get a flashing on and off of conky, my panels, and any open gnome windows etc. 
It seems like a conflict with compiz? 
Hope Ive explained it better

---

### Post by mc4100 on 2008-09-20
Could you post the contents of:
```
cat ~/.conkyrc
```
Only post the stuff before TEXT.

Edit: also, if you "killall conky" after login, and then launch it again "conky", do you still have the same issues?

---

### Post by I wanted to leave on 2008-09-20
Output

bra10n@bra10n-desktop:~$ cat ~/.conkyrc
background yes
use_xft yes
xftfont Bitstream Vera Sans:size=7
xftalpha 0.8
update_interval 3
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline yes
stippled_borders no
border_margin 0
border_width 1
default_color white
default_shade_color black
alignment bottom_left
minimum_size 1262
gap_x 26
gap_y 26
use_spacer none

no_buffers yes
uppercase yes

---

### Post by treehouse on 2008-09-20
What command are you using to execute conky at startup?

---

### Post by mc4100 on 2008-09-20
This should fix your problem:
[list]
[*]Remove conky from Sessions.
[*]Create a new text file in gedit:
```

#!/bin/bash
sleep 30
conky &
exit 0

```
[*]Save this as, say, ".conky-delay.sh".
[*]Make it executable.
[*]Add this to Sessions.
[/list]

---

### Post by I wanted to leave on 2008-09-20
No if I load it via the terminal after the desktop starts all is good as per the screenshot.

---

### Post by I wanted to leave on 2008-09-20
> **treehouse said:**
> What command are you using to execute conky at startup?

conky
conky

Is this right?

---

### Post by mc4100 on 2008-09-20
The problem is you need to wait until compiz is loaded, which means adding:
```
conky
```
To the start-up programs isn't enough when using compiz -- see my previous post on how to fix this.

---

### Post by I wanted to leave on 2008-09-20
> **mc4100 said:**
> This should fix your problem:
[list]
[*]Remove conky from Sessions.
[*]Create a new text file in gedit:
```

#!/bin/bash
sleep 30
conky &
exit 0

```
[*]Save this as, say, ".conky-delay.sh".
[*]Make it executable.
[*]Add this to Sessions.
[/list]

thanks but could you explain this more for a noob

---

### Post by treehouse on 2008-09-20
> **mc4100 said:**
> This should fix your problem:
[list]
[*]Remove conky from Sessions.
[*]Create a new text file in gedit:
```

#!/bin/bash
sleep 30
conky &
exit 0

```
[*]Save this as, say, ".conky-delay.sh".
[*]Make it executable.
[*]Add this to Sessions.
[/list]


Do this thing ^

If for some reason it doesn't load correctly change the line 'conky &' to 'conky -c ~/.conkyrc &' replacing '~/.conkyrc' with the location of your config file if it isn't in the home directory.

---

### Post by mc4100 on 2008-09-20
[list]
[*]Remove conky from System -> Preferences -> Sessions, so it doesn't start when you log in:
Select the one that says conky, and click remove. Close the window when you're done.
[*]Create a new text file in gedit:
In Applications -> Accessories -> Text Editor, paste the following into the window:
```

#!/bin/bash
sleep 30
conky &
exit 0

```
[*]File -> "Save as", and copy/paste ".conky-delay.sh" into the "name".
[*]Click "Save". Close the window when you're done.
[*]Click Places -> Home Folder
[*]Press CTRL+H, look for ".conky-delay.sh"
[*]Right-click it, go to Properties, and then the permissions tab, in the file browser, and make it executable.
[*]Add this (".conky-delay.sh") to System -> Preferences -> Sessions:
Name: Conky
Command: 
```
~/.conky-delay.sh
```
[*]Log Out, and then back in, waiting 30 seconds, to test if it's working.
[/list]
Is this better? I can provide complete step-by-step on clicking one thing after another with screenshots, if this isn't enough.

---

### Post by mc4100 on 2008-09-20
I've update the above post but as treehouse suggests, if: 
```
#!/bin/bash
sleep 30
conky &
exit 0
``` Doesn't work, try replacing it with:
```
#!/bin/bash
sleep 30
conky -c ~/.conkyrc &
exit 0
```

---

### Post by I wanted to leave on 2008-09-20
> **mc4100 said:**
> [list]
[*]Remove conky from System -> Preferences -> Sessions, so it doesn't start when you log in:
Select the one that says conky, and click remove. Close the window when you're done.
[*]Create a new text file in gedit:
In Applications -> Accessories -> Text Editor, paste the following into the window:
```

#!/bin/bash
sleep 30
conky &
exit 0

```
[*]File -> "Save as", and copy/paste ".conky-delay.sh" into the "name".
[*]Click "Save". Close the window when you're done.
[*]Click Places -> Home Folder
[*]Press CTRL+H, look for ".conky-delay.sh"
[*]Right-click it, go to Properties, and then the permissions tab, in the file browser, and make it executable.
[*]Add this (".conky-delay.sh") to System -> Preferences -> Sessions:
Name: Conky
Command: 
```
~/.conky-delay.sh
```
[*]Log Out, and then back in, waiting 30 seconds, to test if it's working.
[/list]
Is this better? I can provide complete step-by-step on clicking one thing after another with screenshots, if this isn't enough.

Cheers mc4100 all fixed. None more surprised than both of us!
Thanks for your help & patience

---

### Post by mc4100 on 2008-09-20
You're very welcome; and should make the tread as "solved", in thread tools, since your problem is fixed, and it helps other users find useful posts.

---

### Post by Dr Small on 2008-09-20
> **mc4100 said:**
> I can provide complete step-by-step on clicking one thing after another with screenshots, if this isn't enough.

For this reason, it is generally easier to just explain a few commands to run, and be done with it.

---

### Post by mc4100 on 2008-09-20
> **Dr Small said:**
> For this reason, it is generally easier to just explain a few commands to run, and be done with it.
I'll admit, it could have been done quicker with a few ""touch"'s here, and some "echo"'s there, (throw in some "chmod"s for good measure),  but it's good to explain things properly so people can get a feel for how they can configure their system graphically, then progressing onto learning the Command Line.
At which point, it shall be, Lesson One: Shell Scripts. ;)

---

### Post by I wanted to leave on 2008-09-20
Explanations were fine :KS
I'm just a noob

---

