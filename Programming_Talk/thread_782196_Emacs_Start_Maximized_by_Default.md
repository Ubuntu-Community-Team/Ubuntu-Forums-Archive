---
title: "Emacs: Start Maximized by Default?"
date: 2008-05-04
forum: Programming Talk
---

### Post by svk on 2008-05-04
How can I make emacs start maximized by default?  Is there anything I could do to .emacs?  By default, emacs starts up with a rather small window and it's a little annoying.

Thanks in advance.

---

### Post by LaRoza on 2008-05-04
man emacs:

```

--geometry geometry
               Set the Emacs window's width, height, and  position  as  speci-
               fied.   The geometry specification is in the standard X format;
               see X(1) for more information.  The width and height are speci-
               fied  in  characters;  the  default is 80 by 24.  See the Emacs
               manual, section "Options for Window  Size  and  Position",  for
               information on how window sizes interact with selecting or des-
               electing the tool bar and menu bar.

```

---

### Post by djs_uk on 2008-05-04
Within gnome/ubuntu, I find the --geometry option doesn't always give what I want.  It will only allow me to set the size/location to certain maximums only (maximums which don't match the height of my display).

Alternatively, for running emacs in full screen, just do the command :

*$ emacs -fs*

Or, for emacs in full height, do:

*$ emacs -fh*

Darren

---

### Post by svk on 2008-05-04
Thanks for the help.

I changed my .Xdefaults to make emacs start a bit bigger on start up, but it's still not ideal.  It is technically not "maximized", but simply "resized to fill the entire screen".  Call me obsessive-compulsive, but I'm somewhat bothered by this and will still hit "maximize".

Full screen is actually kind of cool and I'll certainly make use of it, especially as a way to force myself to not get sidetracked.  But for most purposes, I would definitely prefer just having it maximized.

Looks like compiz fusion might let me do what I want (I installed compizconfig-settings-manager).  There are lots of settings available, and they can be set to apply only to specific programs.  Awesome -- but I can't find a setting anywhere for starting a specific program maximized.  Fiddlesticks.

Looks like it's possible to do this in KDE.  I'm using Gnome.  More fiddlesticks.

If anyone has a solution, please post.  Meanwhile, I'll continue suffering from my obsessive compulsive disorder-induced paranoia that all windows must be maximized.

---

### Post by Tulth on 2008-08-11
Hey guys,

I ran into this emacs maximized problem as well on ubuntu 8.04.  the -fs option actually made it cover my desktop bars at the bottom and top of the screen, and fw and fh would not work together.  Posted below is the solution I arrived at for starting emacs maximized, just the way I wanted it:

```

(defun toggle-fullscreen ()
  (interactive)
  (x-send-client-message nil 0 nil "_NET_WM_STATE" 32
	    		 '(2 "_NET_WM_STATE_MAXIMIZED_VERT" 0))
  (x-send-client-message nil 0 nil "_NET_WM_STATE" 32
	    		 '(2 "_NET_WM_STATE_MAXIMIZED_HORZ" 0))
)
(toggle-fullscreen)

```

Just put it in your .emacs, and you should be set.  You should probably remove any other -fs/fh/fw command line arguments.

Hope this helps other emacs users on Hardy.

---

### Post by roelpeeters on 2008-10-07
Perfect! Thanks, just what I was looking for!

---

### Post by amacleod on 2008-11-11
Is there an X resource equivalent to the -fh or --fullheight switch?  I tried adding the following to my .Xresources:
> 
emacs.fullheight: true

but that did not achieve the desired effect.

I suppose I could put the elisp that sends X a maximize message in my .emacs, but that seems less clean, elegant, and easy to remember next time I'm setting it up.

---

### Post by amacleod on 2008-11-11
> **amacleod said:**
> Is there an X resource equivalent to the -fh or --fullheight switch?  I tried adding the following to my .Xresources:


Sorry.. I should have looked closer at the manpage for emacs before posting.  I found my own answer there:
> 
              fullscreen (class Fullscreen)
                      The  desired  fullscreen  size.  The value can be one of
                      fullboth, fullwidth, or fullheight, which correspond  to
                      the   command-line  options  ‘-fs’,  ‘-fw’,  and  ‘-fh’,
                      respectively.  Note that this  applies  to  the  initial
                      frame only.



---

### Post by amacleod on 2008-11-11
I noticed some very strange behavior now that I'm playing with Emacs in fullheight mode.  I'm using the GNOME desktop that comes with Ubuntu 8.04.1 LTS.  I've got two monitors which I'm using as a single desktop with Xinerama support.  When I added a panel to the right side of my right-hand screen, Emacs no longer respects the lower boundary set by the panel on the bottom of the screen (I start Emacs on the left-hand screen by default).  The moment I took away the vertical panel on the right, Emacs started fitting nicely between the horizontal top and bottom panels again.

Interesting thing about the top and bottom panels: the default panels supplied by GNOME only showed up on my left-hand screen, while the right-hand screen had none.  In that configuration, Emacs refused to start fullheight in the left-hand screen--it automatically jumped to the right where it had more room.  Adding blank/empty panels to the top and bottom of the right hand screen fixed this.

Anyway, I'm not sure what the cause of this is, but I figured I'd post about it here in case anyone else encountered similar problems.

---

### Post by unutbu on 2008-11-11
The devilspie package can help you control the window geometry (placement and size) for all your graphical apps. 

The beauty of devilspie is you don't have to learn a different trick, command or config file syntax to control the window geometry of each app. It is not a large package either.

Devilspie offers a consistent, lisp-like config language to handle all window geometry rules. 

For example, if you put this in ~/.devilspie/config.ds
```

( if 
  ( is ( application_name ) "emacs" )
  ( begin 
    ( geometry "831x1012+0+32" )
  )
)
```

then your emacs application will open with upper left corner at (0,32) and have width of 831 pixels height of 1012 pixels.

---

### Post by alienbrain on 2009-03-21
Ideally, you should configure this through your window manager.

[Devil's Pie]("http://burtonini.com/blog/computers/devilspie") is a "window-matching utility that gives great control over the placement and properties over windows in the X Window System"; It allows allows you to define rules for applications and apply them as they start. So:
```

sudo apt-get install devilspie

```

Now you should ```
man devilspie
``` on how to define those rules. Or if you are like me, then you can also use the nice [gDevilspie](http://code.google.com/p/gdevilspie/) to configure this in a flash using a nice GUI. You will need to add a rule for application "emacs", and in actions tick "maximize".

---

### Post by mltucker on 2009-04-11
Hello,

I'm hoping to do this without installing extra packages.  All the solutions so far (other than devil's pie) including -fh, -fs, and the toggle-fullscreen function aren't working for me since they all set the window height to be too large.  This makes it so that I have to maximize it or alt-drag and resize if I want to see the mode line at the bottom.  It is too large by default also.

This only happens with Emacs.  I am running the snapshot emacs with resolution 1024x600.  Any suggestions?

---

### Post by unutbu on 2009-04-11
mltucker, perhaps try this:

Edit or create ~/.Xdefaults

Put something like this in it:
```

Emacs.geometry: 80x54+0+30
```

Save the file. This should make emacs open a window which is 80 characters wide, 54 lines tall, and shifted 0 pixels to the right and 30 pixels down from the upper left corner. 

Then in a terminal run:
```

xrdb -merge ~/.Xdefaults 
```

Launch emacs.

---

### Post by mltucker on 2009-04-11
Hey unutbu,

Thanks.  That worked perfectly!

-Mark

---

### Post by jammrk on 2009-05-16
> **Tulth said:**
> Hey guys,

I ran into this emacs maximized problem as well on ubuntu 8.04.  the -fs option actually made it cover my desktop bars at the bottom and top of the screen, and fw and fh would not work together.  Posted below is the solution I arrived at for starting emacs maximized, just the way I wanted it:

```

(defun toggle-fullscreen ()
  (interactive)
  (x-send-client-message nil 0 nil "_NET_WM_STATE" 32
	    		 '(2 "_NET_WM_STATE_MAXIMIZED_VERT" 0))
  (x-send-client-message nil 0 nil "_NET_WM_STATE" 32
	    		 '(2 "_NET_WM_STATE_MAXIMIZED_HORZ" 0))
)
(toggle-fullscreen)

```



Exactly what i was looking for.  Placed it in my .emacs file and it worked perfectly.

---

### Post by SabreWolfy on 2012-02-20
> **amacleod said:**
> Is there an X resource equivalent to the -fh or --fullheight switch?  I tried adding the following to my .Xresources:

> 
emacs.fullheight: true


but that did not achieve the desired effect.

I suppose I could put the elisp that sends X a maximize message in my .emacs, but that seems less clean, elegant, and easy to remember next time I'm setting it up.

Look at the "Resources" and "Table of Resources" [here]("http://www.gnu.org/software/emacs/manual/html_node/emacs/X-Resources.html"). You need to add

> 
emacs.fullscreen: maximized


to ~/.Xresources, force a reload of the file with 'xrdb ~/.Xresources' and you're done. The "Table of Resources" shows the other fullscreen modes available. The "maximized" mode is the same as the command-line parameter "-mm".

---

