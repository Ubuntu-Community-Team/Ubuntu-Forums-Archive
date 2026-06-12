---
title: "Trouble Finding Utility to Capture Windows"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by bobsmith2 on 2008-09-17
As a very new Linux user, I have found many replacement programs for the ones I was using in XP, but I'm not finding many utilities. The first thing I'm looking for is a window capture utility that performs auto-scroll... something like the "Screengrab!" extension in Firefox, or "Snag-it" in Windows. Is there a program that will capture the ENTIRE window (auto-scroll) - not just the visible portion? I found one (can't recall the name) that creates movies, but all I want is a simple program that will capture entire screens. Does that exist? Thanks.

---

### Post by compnut41 on 2008-09-17
Applications --> Accessories --> Take Screenshot is what you are looking for. If you want to edit the pictures you take use Gimp. These are both built in so have fun.

Ps. What do you use to do the movies

---

### Post by starcannon on 2008-09-17
Your _Prt Scrn_ Button will do this as well. If you want a particular window then with that window on top Alt+_Prt Scrn_ will grab the window in focus and only the window in focus.

The screen shot utility that compnut41 suggested is nice as well, it even lets you set a timer, and choose with window decorations or with out etc...

If you would like to record a movie of your desktop:
{System>Administration>Synaptic Package Manager}
Search:
```
recordmydesktop
```mark for installation
Search:
```
gtk-recordmydesktop
```Then go to {Applications>Sound & Video>gtk-recordMyDesktop}

or alternately you can install those 2 applications with a single command:
{Applications>Accessories>Terminal}
```
sudo apt-get install recordmydesktop gtk-recordmydesktop
```
Enjoy.

---

### Post by bobsmith2 on 2008-09-17
> **compnut41 said:**
> Applications --> Accessories --> Take Screenshot is what you are looking for. If you want to edit the pictures you take use Gimp. These are both built in so have fun.

Ps. What do you use to do the movies

Thanks compnut41, but that utility won't capture the entire window - only the visible part. I don't recall the name of the movie app I tripped on, but it was far more involved than I needed. I just need a simple screen capture that will get the entire window.

---

### Post by bobsmith2 on 2008-09-17
> **starcannon said:**
> Your _Prt Scrn_ Button will do this as well. If you want a particular window then with that window on top Alt+_Prt Scrn_ will grab the window in focus and only the window in focus.

The screen shot utility that compnut41 suggested is nice as well, it even lets you set a timer, and choose with window decorations or with out etc...

Enjoy.

Thanks starcannon, but neither of those will capture the entire window - only the visible area.

---

### Post by leef on 2008-09-17
This is a rather round about way of doing what you want but in firefox you could try;

File > Print > PDF > Print

Then convert to png with imagemagick;

convert input.pdf output.png

hope that helped

---

### Post by starcannon on 2008-09-17
Oh I feel stupid, I now see what your trying to do, my bad. Gee wiz, hmm let me dig around and see if we can find an app for your particular need.

bobsmith2[I] [SIZE=1]you have a non standard something happening there, both of those options let me grab either then entire desktop or a particular windows depending on which options I choose when I take my screen cap. 

gonna need some more information to help solve this one I think.[/SIZE] [/I]

---

### Post by starcannon on 2008-09-18
xvidcap may do it. Its a command line utility though.

```
sudo apt-get install xvidcap
```

then:
```
man xvidcap
```

and quick reference:
```
xvidcap --help
```

GL wish I knew more on this subject, but that about taps me out.

---

### Post by Dill on 2008-09-18
Someone mentioned *imagemagick* earlier, and that contains a tool called *import* which may do the job for you. Try installing the imagemagick suite and reading the man page on import

```
sudo apt-get install imagemagick
man import
```

Also, here is an excellent guide on taking screenshots in Linux-- some of the options have been mentioned, some take screenshots of the entire screen (not what you want), and some will do your exact bidding.

[http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux](http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux)

Cheers, 
Dylan

---

### Post by starcannon on 2008-09-18
nice link Dill. Thanks

---

### Post by bobsmith2 on 2008-09-18
Thanks very much to everyone who replied. I spent quite a long time trying out many of the recommendations here as well as those in the excellent guide mentioned by Dill. Perhaps I'm missing something, but I can't find anything that will do what I need. The guide was excellent. It contains a number of ways to obtain screen-shots, but as far as I can tell, they all pretty much do the same three things:

1) capture the screen
2) capture the portion of a window that is visible on the screen
3) capture a section of the visible screen

They are all limited to capturing the portion of the window that is visible on the screen; they can't capture the area of the window that scrolls off the screen. 

Xvidcap would probably do the job, but I don't want to make a movie of me scrolling through a long window, I just want to grab a single .png file screen-shot that I can later load into an image viewer, scroll through, and read. Snag-It and a bunch of other open-source apps available for the Windows OS do this. Screengrab is a small (44K) extension that does this in Firefox. But I can't locate anything that will do this (outside of Firefox) within the Linux OS.

Again, thanks for the help, and if anyone knows of anything that will capture the entire window (including the part that scrolls off the screen), and that will save it in a single image file, please let me know.

---

### Post by Dill on 2008-09-18
I couldn't find any way to easily take a screenshot of a window that resides in two separate workspaces. BUT, there are some workarounds, and you can try to see which one suits your fancy...

1.) If you don't mind moving the window into a single workspace temporarily (and if it will fit), you can use *wmctrl* to "activate" this window (which will move it into your active workspace), and then use import to take a screenshot. So your code may look something like...

```
sudo apt-get install wmctrl
wmctrl -l
```

... which will list your open windows. NB: if you want to get solely a list of windows (and not the window ID and other such stuff wmctrl prints out), try this:

```
wmctrl -l | awk '{ for (i = 4;i <= NF;i++) printf "%s ",$i; print ""}'

```

Once you know the name of the window of which you'd like to take a screenshot, you can use wmctrl again to activate the window and use import to take a screenshot

```
wmctrl -a name_of_window
window_id=`wmctrl -l | grep name_of_window | awk '{print $1}'
import -window $window_id foo.jpg
```

2.) I also played around with another tool from the *imagemagick* suite: *montage*. Montage allows you to combine two images into one. So, I had a window that resided in two separate workspaces, and first, I took a screenshot in one workspace...

```
wmctrl -l | awk '{ for (i = 4;i <= NF;i++) printf "%s ",$i; print ""}'
window_id=`wmctrl -l | grep name_of_window | awk '{print $1}'
import -window $window_id foo.png
```

This took a picture of half of the window. Then, I switched workspaces (to where the other half of the picture was) by executing Ctrl-Alt-left-arrow or Ctrl-Alt-right-arrow (I only have two workspaces). Wash, rince, repeat in the other workspace...

```
window_id=`wmctrl -l | grep name_of_window | awk '{print $1}'
import -window $window_id foo2.png
```

Note that I named this output file foo2.png. Now, execute this command...

```
montage -adjoin -geometry +0+0 foo.png foo2.png combined_picture.png

```

And it joins the two half-pictures into one! I've attached the remnants of the surgery, as well... doesn't look half bad.

Anyway, it would be great if there was a way to automate all of this into a shell script. Unfortunately, I couldn't find a way to switch workspaces automatically via the command line, and had to use the Ctrl-Alt-left-arrow/right-arrow method, instead. 

Normally, it seems, you should be able to switch workspaces using wmctrl (reference [http://reachbeyondgrasp.blogspot.com/2008/01/wrapping-workspaces-in-gnome.html](http://reachbeyondgrasp.blogspot.com/2008/01/wrapping-workspaces-in-gnome.html)). However, *compiz* seems to reject the idea of workspaces and joins all of your workspaces into one large desktop (reference [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/153322](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/153322)). And since compiz comes pre-packaged on Hardy Heron installations, it looks like scripting the switching of workspaces is going to be difficult.

I hope I was lucid enough to give you some insight into this issue, and I wish you good luck! I'm off to the Outback for a week, but I'll see if I can look into it some more when I get back.

Cheers, 
Dylan

---

