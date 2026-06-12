---
title: "HOWTO: write an awesome 3 configuration file"
date: 2008-08-03
forum: Outdated Tutorials &amp; Tips
---

### Post by shearn89 on 2008-08-03
[SIZE="4"]This howto aims to cover the basics of writing an awesome 3 configuration file in simple lua code, based on the example rc file. **[COLOR="Red"]IT DOES NOT COVER INSTALLING[/COLOR]**, as awesome 3 is still in development (the rc has only _just_ been released), and I'm running archlinux atm.[/SIZE] When awesome 3 has been released, and I've set up my ubuntu machine (I need one for some work), I'll redo my **old** awesome howto to cover installing awesome 3.

This guide **also assumes some knowledge of previous awesome versions**. It is in essence the few changes I made to convert my old awesomerc to the new lua syntax.

_Some info on this guide's syntax:_
1. **Bold is generally important, or the start of a new step.**
2. *Italic is code outside a "code" block.*
3. Blocked code is either terminal commands, or an extended rc file section.

[COLOR="SeaGreen"][SIZE="4"]_Contents_[/SIZE]
1. Set up
2. Open the rc file
3. Variables
4. "Floatings"
5. Appearance
6. Tags
7. Iconboxes
8. Widgets
9. Statusbars and showing widgets
10. Keybindings
11. Getting programs to open where you want them
12. Links
[/COLOR]

[SIZE="6"]_[COLOR="Blue"]THE GUIDE[/COLOR]_[/SIZE]
[COLOR="SeaGreen"]_**1. **_[/COLOR]**Firstly, make sure you have *wicked* installed.** This is what we will be using for some of the widgets you may currently use. If you use conky-cli for all your widgets, don't worry about this. I don't, and so I needed wicked.

**Start out** by copying the example file to your home directory. On my system this was achieved with:
```

cd ~
mkdir -p .config/awesome
cp /etc/xdg/awesome/rc.lua .config/awesome/rc.lua

```
This cd's to the home directory, creates the hidden config directory, and copies the example file. 

[COLOR="SeaGreen"]_**2. **_[/COLOR]**Open this file** with your favourite editor, however you like. The first thing to do is to include the wicked library right at the top. 
Add *require("wicked")* to the section at the top, under *awful* and *tabulous*.

[COLOR="SeaGreen"]_**3. **_[/COLOR]**Now add some variables** to make things easier. Under "variable definitions" I added:
```

terminal = "urxvt"
browser = "firefox3"
colorlight = "#4b7885"
colordark = "#223b56"

```
In the case of *terminal*, it was changed from xterm. The colours are simply how I do my themes - a light colour and a dark colour on a black background, with a cool wallpaper. If you want more/less colours, or no variables for the here at all, that's cool.

[COLOR="SeaGreen"]_**4. **_[/COLOR]**The next thing to note** is the *floatings* section. Programs added here are launched (generally, although at time of writing gedit is coming up tiled. hmmm.) floating on all tags. Things you want to appear on top of terminals/browser windows/etc on the tag you're working on are good things to add, just like the 2 examples *mplayer* and *pinentry*. I added gedit, and only that.

[COLOR="SeaGreen"]_**5. **_[/COLOR]**The Color and Appearance** settings are what used to be the *style* section in the old rc file. Adjust as appropriate.

[COLOR="SeaGreen"]_**6. **_[/COLOR]**Tags** is the next section. This is very important. If you read through this section in the rc file, you'll see that by default awesome gets the number of attached monitors (*screens*), and adds 9 tags to them. I changed this in my file to what I used to have in awesome 2.3 - 4 tags with names:
```

term = tag({ name = 'term', layout = 'tile' })
term.screen = 1
term.selected = true
net = tag({ name = 'net', layout = 'max' })
net.screen = 1
main = tag({ name = 'main', layout = 'max' })
main.screen = 1
float = tag({ name = 'float', layout = 'floating' })
float.screen = 1

```
These are written in the form:
*internalname = tag ({ name = "displayedname", layout = "layout" })*
Where *internalname* is the name for the tag when referenced in the rc file, and *displayedname* is the name shown on the screen. *Layout* is one of the layouts described in the section near the top of the file, just as in 2.3.
With all of the tags you [COLOR="Red"]must[/COLOR] add them to a screen (*term.screen = 1*), and you must *select* [COLOR="Red"]one to start on[/COLOR]. You should also note that screens start from 1, not 0.

[COLOR="SeaGreen"]_**7. **_[/COLOR]**Iconboxes** are accomplished as follows:
```

myiconbox = widget({ type = "textbox", name = "myiconbox", align = "left" })
myiconbox.text = "<bg image=\"/full/path/to/icon\" resize=\"true\"/>"

```

[COLOR="SeaGreen"]_**8. **_[/COLOR]**You can leave** the next few sections as they are, with the exception of maybe removing the *awesome version* textbox. We'll create our own.
**These go like this:**
```

internalname = widget ({ type = "textbox", name = "displayedname", align = "left/right" })
internalname.text = "some text"

```
This is where *wicked* comes in - it has some very useful built-in status functions designed for awesome. The ones I use are:
```

wicked.register(rootbox, 'fs', '  ${/ usep}%  ', 30)
wicked.register(homebox, 'fs', '  ${/home usep}%  ', 30)
wicked.register(mpdbox, 'mpd', '  $1  ')
wicked.register(clockbox, 'date', '  %H:%M  ')
wicked.register(linkbox, 'net', '  ${wlan0 rx} // ${wlan0 tx}  ')

```
These give me the used disk space as a percentage, the current mpd state, the time, and the up/down speeds of my network connection.
The other boxes I have run os functions to display things like battery status and connected network. These use *wicked*'s built in capability to call os functions, and allow me to get rid of the status script that I used in 2.3. The code for this is as follows:
```

wicked.register(internalname, 'function', function (widget, args)
   local filedescriptor = io.popen('os commmand')
   local value = filedescriptor:read()
   filedescriptor:close()
   return value
end, timebetweenupdates)

```
For more info on *wicked* have a look [here.]("http://awesome.naquadah.org/wiki/index.php?title=Wicked")
See my attached rc file at the end for the 2 I use.

[COLOR="SeaGreen"]_**9. **_[/COLOR]**Once we've created our widgets**, we need to create a statusbar or two, and add the widgets to them. I use 2; a top one for tags, widgets, and other things; and a bottom one for the tasklist and systemtray. If you look at the example rc file which you copied, it probably does something in a *for* loop to add a statusbar to each screen. I only use 1 monitor, so I changed it to this:
```

mystatusbartop = statusbar({ position = "top", name = "statustop", fg = fg_normal, bg = bg_normal })
mystatusbarbtm = statusbar({ position = "bottom", name = "statusbottom", fg = fg_normal, bg = bg_normal })

```
I then added all my widgets with the simple code (for each one)
```

mystatusbarname:widget_add(internalname)

```
Don't forget to put the statusbar onto a screen with *mystatusbarname.screen = 1*. Also don't forget that the tasklist, taglist, systemtray are all [COLOR="Red"]widgets[/COLOR], and needed to be added as such.


[COLOR="SeaGreen"]_**10. **_[/COLOR]**KEYBINDINGS.** Now the fun part you've all been waiting for. Keybindings in awesome 3 are nice and easy once you know how. Because you (possibly/probably) changed the tag names, you'll need to redo the *mod4 + number* hotkeys. These are the ones that let you use the numbers to refer to tags, allowing you to view/toggle/move clients and tags. There are 4 commands relevant for each tag - you can simply read them from the example file (inside the *for* loop), and adapt them, or you can copy and paste these ones, changing the *number *and *internalname*.
```

keybinding({ modkey }, "number", function () awful.tag.viewonly(internalname) end):add()
keybinding({ modkey, "Control" }, "number", function () internalname.selected = not internalname.selected end):add()
keybinding({ modkey, "Shift" }, "number", function () awful.client.movetotag(internalname) end):add()
keybinding({ modkey, "Control", "Shift" }, "number", function () awful.client.toggletag(internalname) end):add()

```
The other useful command is the *spawn* one, which launches programs. This is in the *Standard program* section, and is simply
```

keybinding({ modkey }, "yourkey", function () awful.spawn(terminal) end):add()

```
This is why we specified a *terminal* and *browser* variable, mostly for neatness. If you don't use a variable, [COLOR="Red"]you must put the program name in quotes[/COLOR], otherwise it won't work. You also need to check for conflicts in the shortcuts - the default ones seem to override any user-set ones. You can use this command in a terminal to scan through for the key you wish to check:
```

cat .config/awesome/rc.lua | grep \"key\"

```
where *key* is just the lower-case keyname, ie "o", "t", "p", etc.


[COLOR="SeaGreen"]_**11. **_[/COLOR]**Lastly, getting clients to open on tags.** This is done right at the end of the file, in the *Hooks* section. Under *function hook_manage(c)*, which is executed everytime a new client is spawned, just above *-- Honor size hints*, add this:
```

    function program(p)
        return c.class:lower():find(p)
    end
    if program("firefox") then
        awful.client.movetotag(internalname)
    end

```
This gets the class name in lower case, and if its a match, moves it to the tag. The class name can be found with *xprop | grep WM_CLASS* and a click on the relevant window.
I simply have one *if* statement for each program I wish to tag, however I'm sure there's a neater way of doing it with lists or whatever. At the mo, this works for me, so until I learn some more lua, I'll stick with this.



[COLOR="SeaGreen"]_**12. **_[/COLOR]Well, thats about it. If you get stuck, post here and i'll try and help out, but let me also point you towards some resources that I found very very helpful:
[The awesome wiki]("http://awesome.naquadah.org/wiki/index.php?title=Main_Page")
[The awesome wiki article on writing an rc.lua file]("http://awesome.naquadah.org/wiki/index.php?title=Awesome_3_configuration")
[The awesome wiki Wicked page]("http://awesome.naquadah.org/wiki/index.php?title=Wicked")
[Some example rc.lua files]("http://awesome.naquadah.org/wiki/index.php?title=Main_Page#User_configuration_files")

Basically, use the wiki!
Attached is my rc file for your viewing pleasure - everything works fine, including all my widgets, so if you get stuck it may well help.

Good Luck!

---

### Post by lightningdb on 2008-09-10
> Attached is my rc file for your viewing pleasure - everything works fine, including all my widgets, so if you get stuck it may well help.

Great guide!  I'm new to awesome, and wanted to dive right in the deep end with version 3.

I couldn't find your attached rc file though... I'm not super familiar with these message boards, so maybe I missed it, can you point me in the right direction?

---

### Post by kaiju on 2008-09-22
> **shearn89 said:**
> Programs added here are launched (generally, although at time of writing gedit is coming up tiled. hmmm.) floating on all tags.

as of rc4 or so, you can use ctrl+mod4+i to get the active window's class (the manpage says "Mod4 + Shift + i  Print the client class and instance", but for some reason it's ctrl and not shift for me).
i had a little sizing-trouble with vlc before i found out its class was not more not less than "." :)

---

### Post by kk0sse54 on 2008-10-21
Nice guide that helped get me started ,along with the awesome wiki, on using awesome3. Just wondering could you repost your rc.lua file?

---

### Post by shearn89 on 2008-12-14
hey all - just re-found this thread. I'll try and update it this week to cover any little changes in syntax etc, and post my latest rc.lua.

---

### Post by gladstone on 2009-01-02
> **shearn89 said:**
> hey all - just re-found this thread. I'll try and update it this week to cover any little changes in syntax etc, and post my latest rc.lua.

Yeah, unfortunately a lot of this stuff is already out-of-date for Awesome 3.1

Shame they keep breaking things ;)

---

### Post by kellemes on 2009-01-05
> **gladstone said:**
> Yeah, unfortunately a lot of this stuff is already out-of-date for Awesome 3.1

Shame they keep breaking things ;)

Well, the breaking of things makes the hole Awesome-experience fun. ;-)
Listen.. if it's a tiling wm you need and don't want to have the newest of features you shouldn't upgrade the package.
Awesome is moving, and it's moving fast, one reason why I use it.

---

### Post by shearn89 on 2009-01-14
I don't think i'll ever be able to keep up with number of updates - there seems to be a new rc out each week! I guess this will have to stay as a basic (slightly unhelpful) reference... :-(

---

### Post by Gigamo on 2009-01-15
> **shearn89 said:**
> I don't think i'll ever be able to keep up with number of updates - there seems to be a new rc out each week! I guess this will have to stay as a basic (slightly unhelpful) reference... :-(

Config files changes are not happening THAT often, imo, and it's only for the better. :)

Ofcourse if you're using git then you will have some more work ^^

---

### Post by hamzamusa on 2009-07-11
Hi
Thanks for the tutorials and the PPA reposatories , i was using Awesome 2 for quite sometime now , and now moved to Awesome 3 , however , there are issue in here i don't know if they are common or not :

1: playing around configuration won't take effects unless i logout/login again ! back to Awesome 2 all what i needed to do is to restart Awesome , not to logout to see changes taking effect !!!!

2: sometimes changing anything in the rc.lua file get me back to the defualt setting which in the /etc dir !

3: i select the theme i customize , which is unler .config/awesome/themes/mytheme/ but thats won't work , except for once which back also to the orginal setting !!!!

am using Awesome 3.3.1 

Any suggestions ?!

Best regards

---

### Post by shearn89 on 2009-07-11
Hey! wow, i'd kinda forgotten about this! Let me see if I can answer your questions:
> **hamzamusa said:**
> 
1: playing around configuration won't take effects unless i logout/login again ! back to Awesome 2 all what i needed to do is to restart Awesome , not to logout to see changes taking effect !!!!
There is a keyboard shortcut for awesome 3 - I think its something like mod+ctrl+r? Have a look in the rc.lua file. On my system I often have to hit it twice!

> **hamzamusa said:**
> 
2: sometimes changing anything in the rc.lua file get me back to the defualt setting which in the /etc dir ! That means that your rc.lua file has the wrong syntax. This, unfortunately, happens a LOT - the devs seem to change the syntax of the file at every release. I think there's a "check config file" option - try looking at the man pages for awesome (type "man awesome" in a terminal). Maybe its awesome -l /path/to/config/file.lua

> **hamzamusa said:**
> 
3: i select the theme i customize , which is unler .config/awesome/themes/mytheme/ but thats won't work , except for once which back also to the orginal setting !!!!

am using Awesome 3.3.1 
Best regards
Hmm. Did you use the full path to the theme? I wrote an up-to-date guide which is over at [my university's wiki]("http://compsoc.tardis.ed.ac.uk/wiki/AwesomeWM_guide"). Check the "Theme" section. If you post your theme's lua file I can try and see where its wrong?

---

### Post by hamzamusa on 2009-07-12
Hi shearn89
Thank you for thq quick reply , after i change back to version 3.1 its all working very well , don't know what`s the issue was , and it was working on arch very well .

just still stuck with one issue in the hand so far : Tags , can't define my tags . everytime i try to define my custom tags ( Common , Web , Chat , IRC , Design , Coding , Gamebox ) , seems i do that wrong , which back it to the old config at /etc/xdg/awesome/rc.lua . 

i tried it your way , however it does not work too .:( i hope you help me to know what`s missing :)

Update :
just Installed 3.3.1 now , seems it reads my themes very well , but still the tags issue :)

More Update :
Tried the Tags section in [http://compsoc.tardis.ed.ac.uk/wiki/AwesomeWM_guide](http://compsoc.tardis.ed.ac.uk/wiki/AwesomeWM_guide) and working perfectly ... 

THANK YOU
Best Regards

---

### Post by hamzamusa on 2009-07-12
Hey sorry for bothering more with Questions :

what if i want to change my keyboard layout ! from us english to another language ?

---

### Post by shearn89 on 2009-07-12
> **hamzamusa said:**
> Hi shearn89
Thank you for thq quick reply , after i change back to version 3.1 its all working very well , don't know what`s the issue was , and it was working on arch very well .

just still stuck with one issue in the hand so far : Tags , can't define my tags . everytime i try to define my custom tags ( Common , Web , Chat , IRC , Design , Coding , Gamebox ) , seems i do that wrong , which back it to the old config at /etc/xdg/awesome/rc.lua . 

i tried it your way , however it does not work too .:( i hope you help me to know what`s missing :)

Update :
just Installed 3.3.1 now , seems it reads my themes very well , but still the tags issue :)

More Update :
Tried the Tags section in [http://compsoc.tardis.ed.ac.uk/wiki/AwesomeWM_guide](http://compsoc.tardis.ed.ac.uk/wiki/AwesomeWM_guide) and working perfectly ... 

THANK YOU
Best Regards

good! no problem.

> **hamzamusa said:**
> Hey sorry for bothering more with Questions :

what if i want to change my keyboard layout ! from us english to another language ?

This'll be to do with xorg - are you on archlinux or ubuntu? [this]("http://wiki.archlinux.org/index.php/Xorg#Setting_non-us_keyboard_without_xorg.conf") should work for both!

---

### Post by V0rt3k on 2009-09-15
The tags doesn't work... Anyone who solved this?:(

---

