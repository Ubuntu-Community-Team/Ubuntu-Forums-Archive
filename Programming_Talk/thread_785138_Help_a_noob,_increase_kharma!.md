---
title: "Help a noob, increase kharma!"
date: 2008-05-07
forum: Programming Talk
---

### Post by xer0kill on 2008-05-07
I am not a programmer. At all. I'm turning to you guys for help because I cannot seem to find an application that fits my needs. It's VERY simple and I know it would be a breeze for someone who knows anything at all.

Here's what I'm looking for: An application that I can have running in a corner of the screen. Basically it's got an adjustable number of different colored squares (I'm thinking three squares by three squares). Each square has a programmable text "title" on it as well as a numerical value. Left clicking on the square increases the value by 1, right clicking decreases the value by one. I'd also like a button I could press that would copy all the values to the clipboard in a list format with line breaks between each item (Variable1: value, Variable2: value, etc)

Any of you guys know of an existing application that can do this? I am thinking it could be done in python fairly easily. I looked at some beginner's tutorials but I'm too stupid/don't have the time right now to learn it all from the beginning (I'm a graphics guy). Anybody have some links that could tell me what I need to know to build something like this quickly? This application could end up saving me tons of time every day.

Thanks in advance!

---

### Post by samjh on 2008-05-07
Are you asking us to make one for you? ;)

I don't know of any existing program like that.

---

### Post by pmasiar on 2008-05-07
GUI apps are not trivial, but maybe you will find a volunteer. Better try to hang around and suggest this when someone will ask what to program. 

EasyGUI is the simplest GUi for Python. Another option might be pygame.

BTW it is [http://en.wikipedia.org/wiki/Karma](http://en.wikipedia.org/wiki/Karma) not kharma :-)

---

### Post by RIchard James13 on 2008-05-07
What on earth is that program for? That is not just a question of curiosity it is a question that might help someone give you a solution.

Such an application sounds very trivial for me to make, I'm wondering if there is any hard part to it?

---

### Post by b1g4L on 2008-05-07
Seems easy enough to do. What's the purpose of this program?

---

### Post by xer0kill on 2008-05-07
> **RIchard James13 said:**
> What on earth is that program for? That is not just a question of curiosity it is a question that might help someone give you a solution.

Such an application sounds very trivial for me to make, I'm wondering if there is any hard part to it?

The app would be for keeping track of what I accomplish while I'm working. My employer is now wanting me to give numbers for basically everything I do in a given day. For example, number of questions I answered, number of blogs I read, number of blogs I post, number of comments I post on other blogs. Right now, my method is not very efficient. The best way of doing things with the tools I have right now would seem to be to keep my spreadsheet open and "above all" on all desktops. It's still a pain cause every time I do some task I've got to click on the spreadsheet and type in a number. It really bogs me down, especially if I'm answering a question every minute or two.

If anyone has any alternative ideas to accomplish what I need, I'm all ears. I'm not looking to get anybody to do free work for me! If possible, I'm looking for the simplest solution, something that I could accomplish myself. The "click boxes" idea seems like the best for me right now: one simple click to show that I completed something (with the right click being in case I accidentally click on the wrong box and need to change it back).

Of course, if anybody is bored and wants to code something up to help get me started, I wouldn't object :D. I do want to learn python, but right now I'm working 40 hours a week as well as watching my kids 45-50 hours a week and I just don't have the time to set aside to start from the beginning. I often get ideas for productivity apps, and it would be nice to be able to actually work on them.

---

### Post by pmasiar on 2008-05-07
Simple shell program, can be run in a small window
[php]
actions = dict(a='answer', p='blog post', r='read')
counts = {}
prompt = ''.join( aa for aa in actions)

while 1:
    print 'next action:'
    for aa in actions:
        print aa, actions[aa]
    new = raw_input('enter one of ' + prompt + ': ')
    if new not in actions:
        print '************\nwrong action:', new, "\n************"
        continue
    try:
        counts[new] += 1
    except:
        counts[new] = 1
    
    print "activity so far:\n========="
    for aa in counts:
        print actions[aa], ":",counts[aa]

    print "==========\n\nctrl-c for quit"

[/php]

Enjoy!

---

### Post by xer0kill on 2008-05-07
Thanks pmasiar! I'll give that a shot this evening and let you know how it works for me.

---

### Post by stevescripts on 2008-05-07
Oh well, having a few minutes to kill, this pm - a really simple gui hack

```

#! /usr/bin/tclsh

package require Tk

foreach i {1 2 3} {
	grid [label .$i -text 0 -width 5 -relief groove -bd 2] -row 0 -column [expr $i - 1]
}

foreach i {4 5 6} {
	grid [label .$i -text 0 -width 5 -relief groove -bd 2] -row 1 -column [expr $i - 4]
}

foreach i {7 8 9} {
	grid [label .$i -text 0 -width 5 -relief groove -bd 2] -row 2 -column [expr $i - 7]
}

wm title . Q

proc plust {widget} {
        set res [$widget cget -text]
        set res [expr {$res + 1}]     
        $widget configure -text $res
}

proc minust {widget} {
        set res [$widget cget -text]
        set res [expr {$res - 1}]
        $widget configure -text $res
}

bind . <1> {plust %W}
bind . <3> {minust %W}


```

Left click to increment - right click to decrement ...

Seeing as how you are a graphics person ... if you will come up with 9 small images/and or bitmaps - I will add them to the widgets for you.

Come up with a list of the nine things you really want to track, and I will
add a menu to the app, and save things in a text file for you.

Nothing like a little diversion on a humpday sfternoon (wednesday, for any of you not familiar with that americanism ... ;) )

copy the script into a text editor - save it as q.tcl - chmod +x and play ...

Steve

---

### Post by xer0kill on 2008-05-07
Nice one Steve! Graphical even. Tcl, eh? I haven't ever heard of that, but it sounds like just the language for me to accomplish some of the simple ideas I have in a quick amount of time. Thanks man, I'll test that out tonight as well.

---

### Post by stevescripts on 2008-05-07
FWIW, tcl and tk are more widely in use than it may be suspected.  Often hidden deeply under the covers.

Glad to be of a little help.

Steve

---

### Post by Mr.Macdonald on 2008-05-07
If Java is good ill make you a decent .jar you could run

---

### Post by smartbei on 2008-05-08
Here is a version in Python that supports everything I believe... Had some fun with this. Copying to the clipboard was probably the most difficult part.

You will need to install the packages python-tk (for the gui) and xsel (for the clipboard manipulation):
```

sudo aptitude install xsel python-tk

```

Save the attached file, and run:
```

chmod +x square.py

```
to make it executable.
And then you can run with "./square.py <width you want it> <height you want it>"

For a 3 rows by 4 columns app, run "./square.py 4 3"

---

