---
title: "[gvim] How can I get GVIM to always start in a maximized window?"
date: 2007-03-11
forum: Programming Talk
---

### Post by shawnhcorey on 2007-03-11
Hi,

I'm using GNOME. I want to know if there is a command I can add to my ~/.gvimrc that will always start gvim in a maximzed window.

shc

---

### Post by Mr. C. on 2007-03-11
VIM FAQ Entry 31.15:

```
31.15. How do I change the location and size of a GUI Vim window?

You can use the "winpos" command to change the Vim window position. To
change the size of the window, you can modify the "lines" and "columns"
options.

For example, the following commands will position the GUI Vim window at the
X,Y co-ordinates 50,50 and set the number of lines to 50 and the number of
columsn to 80.

    :winpos 50 50
    :set lines=50
    :set columns=80

The arguments to the 'winpos' command specify the pixel co-ordinates of the
Vim window. The 'lines' and 'columns' options specify the number of lines
and characters to use for the height and the width of the window
respectively.

For more information, read

    :help 31.4
    :help :winpos
    :help 'lines'
    :help 'columns'
    :help GUIEnter
```

---

### Post by shawnhcorey on 2007-03-12
That's not quite what I asked. That sets the window to a predetermined size. I want it maximized.

I was thinking something like this but :simalt does work in the current version.

```
:autocmd GUIEnter * simalt <F10>
```

---

### Post by Mr. C. on 2007-03-12
Perhaps you overlooked the help information I presented to you:

:help 'lines'

```
'lines'                 number  (default 24 or terminal height)
                        global
        Number of lines of the Vim window.                               
        Normally you don't need to set this.  It is done automatically by the
        terminal initialization code.  Also see |posix-screen-size|.     
        When Vim is running in the GUI or in a resizable window, setting this
        option will cause the window size to be changed.  When you only want
        to use the size for the GUI, put the command in your |gvimrc| file.
        Vim limits the number of lines to what fits on the screen.  You can
        use this command to get the tallest window possible: >
                :set lines=999
```

MrC

---

### Post by shawnhcorey on 2007-03-13
Perhaps you overlooked the help information on columns.

:help 'columns'

```
'columns' 'co'		number	(default 80 or terminal width)
			global
			{not in Vi}
	Number of columns of the screen.  Normally this is set by the terminal
	initialization and does not have to be set by hand.  Also see
	|posix-screen-size|.
	When Vim is running in the GUI or in a resizable window, setting this
	option will cause the window size to be changed.  When you only want
	to use the size for the GUI, put the command in your |gvimrc| file.
	When you set this option and Vim is unable to change the physical
	number of columns of the display, the display may be messed up.
	Minimum value is 12, maximum value is 10000.

```

That part about the display being messed up concerns me.

---

### Post by Mr. C. on 2007-03-13
> **shawnhcorey said:**
> Perhaps you overlooked the help information on columns.If this was directed at me, no, I certainly did not. I gave the link in my first post.

> **shawnhcorey said:**
> 
That part about the display being messed up concerns me.
There is no harm in trying it.

You can also set properties for the various GUI launchers, like the Terminal (Accessories).  Check out: 

```
man gnome-terminal
```

and you will see a --geometry switch.  You use this to specify windows sizes and positions.  Here's what geometry looks like:

```
GEOMETRY SPECIFICATIONS
       One of the advantages of using window systems instead of hardwired ter-
       minals is that applications don't have to be restricted to a particular
       size or location on the screen.  Although the layout of  windows  on  a
       display  is  controlled  by the window manager that the user is running
       (described below), most X programs accept a command  line  argument  of
       the  form  -geometry WIDTHxHEIGHT+XOFF+YOFF (where WIDTH, HEIGHT, XOFF,
       and YOFF are numbers) for specifying a preferred size and location  for
       this application's main window.

       The  WIDTH  and  HEIGHT parts of the geometry specification are usually
       measured in either pixels or characters, depending on the  application.
       The  XOFF and YOFF parts are measured in pixels and are used to specify
       the distance of the window from the left or right and  top  and  bottom
       edges  of the screen, respectively.  Both types of offsets are measured
       from the indicated edge of the screen to the corresponding edge of  the
       window.  The X offset may be specified in the following ways:

       +XOFF   The left edge of the window is to be placed XOFF pixels in from
               the left edge of the screen (i.e., the X coordinate of the win-
               dow's  origin  will  be  XOFF).  XOFF may be negative, in which
               case the window's left edge will be off the screen.

       -XOFF   The right edge of the window is to be  placed  XOFF  pixels  in
               from  the  right  edge of the screen.  XOFF may be negative, in
               which case the window's right edge will be off the screen.

       The Y offset has similar meanings:

       +YOFF   The top edge of the window is to be YOFF pixels below  the  top
               edge of the screen (i.e., the Y coordinate of the window's ori-
               gin will be YOFF).  YOFF may be negative,  in  which  case  the
               window's top edge will be off the screen.

       -YOFF   The  bottom  edge  of the window is to be YOFF pixels above the
               bottom edge of the screen.  YOFF may be negative, in which case
               the window's bottom edge will be off the screen.

       Offsets  must  be  given  as pairs; in other words, in order to specify
       either XOFF or YOFF both must be present.  Windows can be placed in the
       four corners of the screen using the following specifications:

       +0+0    upper left hand corner.

       -0+0    upper right hand corner.

       -0-0    lower right hand corner.

       +0-0    lower left hand corner.

       In the following examples, a terminal emulator is placed in roughly the
       center of the screen and a load average monitor, mailbox, and clock are
       placed in the upper right hand corner:

           xterm -fn 6x10 -geometry 80x24+30+200 &
           xclock -geometry 48x48-0+0 &
           xload -geometry 48x48-96+0 &
           xbiff -geometry 48x48-48+0 &
```

MrC

---

### Post by wdw443 on 2007-12-27
> **shawnhcorey said:**
> Hi,

I'm using GNOME. I want to know if there is a command I can add to my ~/.gvimrc that will always start gvim in a maximzed window.

shc

I let my gvim start maximaized with "devilspie". This means that you should install "devilspie" first.(sudo apt-get install devilspie)
Then touch the config file "gvim.ds" in ~/.devilspie/, (if ~/.devilspie does not exist, just make it). Following is what looks like in gvim.ds.
*$cat /home/me/.devilspie/gvim.ds* 
[B](if
        (contains(window_name) "Vim")
        (fullscreen)
)[/B]

Now start devilspie,
$devilspie &
After that you can start your GVim in full screen, I hope it works!:)

---

### Post by LorisB on 2008-05-28
> **wdw443 said:**
> I let my gvim start maximaized with "devilspie". This means that you should install "devilspie" first.(sudo apt-get install devilspie)
Then touch the config file "gvim.ds" in ~/.devilspie/, (if ~/.devilspie does not exist, just make it). Following is what looks like in gvim.ds.
*$cat /home/me/.devilspie/gvim.ds* 
[B](if
        (contains(window_name) "Vim")
        (fullscreen)
)[/B]

Now start devilspie,
$devilspie &
After that you can start your GVim in full screen, I hope it works!:)

That works for me, thanks ! I replaced fullscreen with maximize, because I don't want the window title to go away.

---

### Post by Amy lsdell on 2009-06-03
The original question was "How can I get GVIM to always start in a maximized window?".

The solution: add 2 lines in profile, "set winheight=999", and "set winwidth=999", that's all.

Why are we getting all these garbage unrelated responses?

Do not answer the question if you don't know the answer.

Do not answer the question if you do not want to read the question.

Do not reply to any question just to show off your fixed area of expertise.

No wonder Unixes were unable to dent garbage OS like Microsoft's.

---

### Post by Mr. C. on 2009-06-03
> **Amy lsdell said:**
> The original question was "How can I get GVIM to always start in a maximized window?".

The solution: add 2 lines in profile, "set winheight=999", and "set winwidth=999", that's all.



Curious, as these are vim FUNCTIONS, which RETURN values, and are used as follows:
```

  :echo "The current window has " . winheight(0) . " lines."

```

Your "solution" **does not** work in my gvim.


> **Amy lsdell said:**
> 
Why are we getting all these garbage unrelated responses?


There is nothing unrelated at all about the posts.  They are all possible answers, or helpful to others.
> **Amy lsdell said:**
> 
Do not answer the question if you don't know the answer.

Do not answer the question if you do not want to read the question.

Do not reply to any question just to show off your fixed area of expertise.

Let's add some others:

Do not chastise people who take the time to help out.

Do not answer two year old threads.

Do not assume what others have and have not read.

Do not assume your interpretation is correct.

Do not assume there is only one answer - yours.

Do not assume others desire to remain ignorant or lack desire to learn.

Do not stray from a thread's topic by adding your own digs under the guise of being helpful.

> **Amy lsdell said:**
> 
No wonder Unixes were unable to dent garbage OS like Microsoft's.

Yup, you've nailed the root cause.  Now go pat yourself on the back and take a hike.

---

### Post by hessiess on 2009-06-03
Use a tiling WM :)

---

### Post by SilverWave on 2010-02-23
> > E.g In ~/.bashrc:
> 
> alias gvim="gvim -geom 80x30"

My setting is:
alias gvim="gvim -geom 210x50"

Cheers.

---

### Post by jack_the_lad on 2011-04-29
the easiest way to do this in ubuntu is via ccsm.

launch terminal and type

```
ccsm
```

then navigate to window management and enable window rules.

under window rules put "class=Gvim" in maximized column.


gvim should now start maximized.

---

### Post by leondz on 2011-12-04
Thanks jack_the_lad, this works very well (on 10.10 as well as 11.x) - much better than the lines=999 columns=999, which doesn't always open gvim on the same workspace as it was invoked.

---

