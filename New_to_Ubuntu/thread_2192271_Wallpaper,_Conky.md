---
title: "Wallpaper, Conky"
date: 2013-12-07
forum: New to Ubuntu
---

### Post by Val87 on 2013-12-07
Hey.
I am Running Ubuntu 13.10 on an Acer Aspire 5750 i5 64bit with Intel Sandybridge graphics. 

I can across someones wallpaper:
I am interested in what is on the right? What is it, and how could i get that on my machine. I can see also Linux Backtrack, is it running at the same time? 
I know Compiz is the best way to improve visual, but are there other ways to make the desktop look cool? :) 
[ATTACH=CONFIG]248418[/ATTACH]

---

### Post by andrej1741 on 2013-12-07
[Conky]("http://en.wikipedia.org/wiki/Conky_%28software%29")?

---

### Post by QIII on 2013-12-07
conky, Lua ...

---

### Post by Val87 on 2013-12-07
Thanks, i installed it... but it is a simple monitor... In order to make it look "cool" apparently one has to learn some basic programming?

---

### Post by coldraven on 2013-12-07
I did this and it looks similar to your screenshot.
[http://xmodulo.com/2013/12/install-configure-conky-linux.html](http://xmodulo.com/2013/12/install-configure-conky-linux.html)

---

### Post by deadflowr on 2013-12-07
> **Valeri_Tarassov said:**
> Thanks, i installed it... but it is a simple monitor... In order to make it look "cool" apparently one has to learn some basic programming?

Are you meaning the initial conky after you just installed it?
Then yeah, it's a very generic conky script running.
Until you have your own .conkyrc file(with or without additional scripts like luas, templates, among other stuff) the conky program reads what can best be described as an example script.

A great place for help with learning conky would be the [conkysuperdupermegathread]("http://ubuntuforums.org/showthread.php?t=281865")

Here is also a nice little starting point
[https://help.ubuntu.com/community/SettingUpConky](https://help.ubuntu.com/community/SettingUpConky)

---

### Post by Val87 on 2013-12-07
Thanks, lovely people at ubuntu! :) I will try to set something up and let you know what happens! :))) Just hope i wont screwe anything up and wont have to reinstall! :)

---

### Post by deadflowr on 2013-12-07
> **Valeri_Tarassov said:**
> Thanks, lovely people at ubuntu! :) I will try to set something up and let you know what happens! :))) Just hope i wont screwe anything up and wont have to reinstall! :)

With conky, the worst thing you might have to do is reinstall conky.
It won't break your machine. Unless of course you decide to run a thousand conkys, fetching data all over the place, which seems unlikely.

The trick with conky is to use the terminal to make sure no errors crop up when it runs.
A good conky will load a few lines and then seemingly hang, which is is actually a good thing as long as the conky window you make you is on the screen.
If errors happen, then the terminal will keep running and adding new lines about the error(s).
If errors occur, you can hit ctrl + c to cancel it.
If ctrl + c doesn't work, an option is to right click on the terminal window and select either a new tab or new window and then run the kill command
```
killall conky
```
which will force the runaway conky session to die, in a sense.

Good Luck, anyway.

---

### Post by Val87 on 2013-12-07
Ok this is where i got.

[ATTACH=CONFIG]248413[/ATTACH]

But if you see the icons i have on the left, such as World of Tanks and SWTOR and a document, i cant click on any icons on the desktop any more. 
Can i do anything about that? I think this thread should be renamed as to concky theme. Plus it shows no IP address where the Wifi sign is. 
Anyone know what to do?

---

### Post by deadflowr on 2013-12-07
The icons are unclickable because conky is a window.
Transparent, perhaps, but a window running on top of the existing desktop nonetheless.
The icons are underneath the conky window.

If you want to click on the icons, you'll have to either place them on the screen where conky isn't set, or resize the conky layout.
Moving the icons is something you can do, if need be.
And resizing the conky layout is something we can help with, but we'd need to have the scripts to see and explain how to do it.

---

### Post by Val87 on 2013-12-07
And how do i supply you with the scripts?

---

### Post by Val87 on 2013-12-07
[B]Is this what you are looking for? It was in folder Scripts named "time"

[/B]use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 1
total_run_times 0
own_window no
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 250 5
maximum_width 500
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_left
gap_x 60
gap_y 300
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale yes
use_spacer yes




TEXT
${voffset 10}${color EAEAEA}${font GE Inspira:pixelsize=120}${time %H:%M}${font}${voffset -84}${offset 10}${color FFA300}${font GE Inspira:pixelsize=42}${time %d} ${voffset -15}${color EAEAEA}${font GE Inspira:pixelsize=22}${time  %B} ${time %Y}${font}${voffset 24}${font GE Inspira:pixelsize=58}${offset -148}${time %A}${font}
${voffset 1}${offset 12}${font Ubuntu:pixelsize=10}${color FFA300}HD ${offset 9}$color${fs_free /} / ${fs_size /}${offset 30}${color FFA300}RAM ${offset 9}$color$mem / $memmax${offset 30}${color FFA300}CPU ${offset 9}$color${cpu cpu0}%

---

### Post by deadflowr on 2013-12-07
You can open gedit and then file > open and then click on your user name in the top of the left pane.
Gedit defaults to open the recent, so you'll need to switch it to the username to navigate the home folder.
Then, right click on the open window which has the listing of you folders(like Downloads,Documents, etc,etc) and click on the line
show hidden files and folders. This will show all the files in the home folder, the conkyrc file has dot which means it hides normally.

Then when it opens slect edit and then slect all and then copy.
In the forums reply box (not the quick reply box) is a # symbol, this is the code tags.
click it and the code tags will appear in the dialog box.
right click and paste the paste what you copied in between the two code boxes [code]paste here[\code]
Then we can see the full script, if more is needed, we can ask and explain.
Most likely we will ask, as the layout you have most likely has a lua script or two.

Edited: So it seems you got the script in the above post.

So, it seems normal.
You can try to move it easily, by changing the gap_x line.
maybe try adding more, like change it from 60 to 100.
this will move it over to the right, I think.
might move it to the left, but that's the setting for were it is on the section of the screen it is in.
x= left/right
y = up/down.

---

### Post by Val87 on 2013-12-07
[COLOR=#333333][FONT=verdana]nano ~/.conkyrc command if ran in terminal opens also a information window where i can edit stuff, but i cant seem to able to copy the entire text from there, like in edit-select-all-copy. [/FONT][/COLOR]

---

### Post by Val87 on 2013-12-07
I understand that there is no way i can get those icons clickable? :( Why wouldn't they fix a bug like that? :(
Is it just the infinity theme bug, or is it overall for conky, maybe there is an alternative to conky?

---

### Post by deadflowr on 2013-12-07
> **Valeri_Tarassov said:**
> I understand that there is no way i can get those icons clickable? :( Why wouldn't they fix a bug like that? :(

Why is it a bug?
Open any other window and try to click the icons under it.

---

### Post by Val87 on 2013-12-07
Well i tried it. Icons don't click, ill just have to run them from unity dash. :)

---

### Post by DuckHook on 2013-12-07
Here is the principle that you need to understand: Everything that is painted on your screen is done by way of a window. Conky runs in a window. The global toolbar is a window. Your desktop itself is a window. They are special windows that are transparent, without the distraction of title bars and borders, etc. but they are still windows. Your desktop icons are on your desktop window. This is the first window that the system creates, so it lies at the very bottom of your collection of windows. If you then create a Conky window that is the same size as the desktop window, then even though the Conky window is transparent, has no borders, etc, the Conky window still completely covers up the desktop window and you can't get to any of the icons underneath.

The key is to make a Conky window that is *smaller* than the desktop window and then shove it against the right side of your screen or anyplace else where you won't be putting any icons. Your problem is a result of the fact that you've chosen a Conky scheme that looks pretty, but covers your whole desktop. If you want to fix this, simply choose a Conky script that is graphically smaller and leaves some empty desktop available. The internet is full of such scripts, all available for the cost of a download. Look especially at the megathread posted earlier.

---

### Post by coldraven on 2013-12-08
Look at my previous post, the conky script in that tutorial creates a window on the right side of the screen. I can click on the on the left three quarters of the desktop with no problem.

---

### Post by Val87 on 2013-12-08
Thanks guys, i will try all that. You have been super helpful.

---

