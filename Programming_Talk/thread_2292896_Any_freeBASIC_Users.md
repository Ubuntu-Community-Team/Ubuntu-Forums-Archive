---
title: "Any freeBASIC Users"
date: 2015-08-31
forum: Programming Talk
---

### Post by brian-mccumber on 2015-08-31
Hello I recently switched to Ubuntu and I found [freeBASIC]("http://www.freebasic.net") and installed it and have been playing with it a little and I like it, especially how easy it is to draw to a screen. I was wondering if there are any other freeBASIC users here? How easy did you find it to install it and what editor do you use to write bas and bi's? 

It was easy to install when I found the [fbwiki installation instructions]("http://www.freebasic.net/wiki/wikka.php?wakka=CompilerInstalling"). There is a whole list of apt-gets for other packages under the Debian\Ubuntu list in the Linux instructions but a couple were already installed and the rest installed easily using apt-get. I installed them in the order that they are in the list. I am using [Geany]("http://www.geany.org/") text editor and I have been able to compile the bas files and run them from the editor without any problems even when they use screen for graphics drawing and external files. 

I also found this [tutorial]("http://users.freebasic-portal.de/rdc/tutorials.html") and while it is missing the actual tutorial part it has all the game code set up in chapters with each chapter adding something to the game. The code is well documented and alot can be learned just by going through it. I compiled the final version and the game works and it is kind of fun if you like rogue-like rpg's with no sound. But hey it's source code, sound could be added.

Anyway, I guess this is mainly to see if we can get a discussion going about programming with freeBASIC on Ubuntu.

---

### Post by brian-mccumber on 2015-09-02
Well I was messing around with the freeBasic drawing and came up with this. It draws random circles in the display area and then connects them to a line from the center of the display area. I attatched a screenshot of it running, it keeps track of elapsed time and how many circles are drawn and updates the display every 100 circles.

```

screenres 640,480,32

dim as string key, msg
dim as integer x, y, r, g, b, strt, stp, counter, total

randomize timer    

strt=timer

draw string ( 10,  10), "Circles displayed: 0"
draw string (10,30), "Seconds elapsed: 0"

do
    x = rnd * 620 + 10
    y = rnd * 420 + 50
    r = rnd * 255 + 20
    g = rnd * 255 + 20
    b = rnd * 255 + 20
    circle(x,y), 10, rgb(r,g,b),,,,F
    line(320,240)-(x,y),rgb(r,g,b)
    sleep(50)
    counter=counter+1
    select case counter
        case 100                    
            total = total + counter            
            msg = "Circles displayed: " & total
            cls
            draw string (10,10), msg
            stp = timer
            draw string (10,30), "Seconds elapsed: " & stp - strt
            counter = 0
    end select
    key=inkey    
loop until key=chr(255,107)
end

```

[ATTACH=CONFIG]264180[/ATTACH]

---

