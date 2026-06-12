---
title: "FLTK mouse troubles"
date: 2008-09-02
forum: Programming Talk
---

### Post by techmarks on 2008-09-02
I plot a function on the screen with OpenGL.
Then I'd like to grab it and rotate it with the mouse.

I can figure out the rotations, that's not the problem.
The trouble is with the grabbing the mouse events.

Now the troubles begin.

I thought the best way to do this is get the FL_PUSH event (left mouse button is clicked) and then the FL_DRAG event (mouse moved with button down) this works well, the problem is that when you resize the window, it generates a mouse down event!!! and that rotates the function while you are re-sizing the window (not good)

Then I tried grabbing the MOVE event (mouse moved with no button pressed) and just checking the event-state variable that the mouse is down.

To make this short the whole problem is that on the MOVE mouse event FLTK  will not even set the bitfields so you can know if the mouse button was down.  the MOVE events completely ignores the mouse buttons !!

It doesn't even set the bitfield shift states so you could know if any button were pressed during the MOVE event.

Very bad, Windows doesn't do it like that, I was hoping a way around this, any ideas??

I'm think I might have to give up on FLTK for now, really FLTK should not even be generating FL_PUSH (mouse down) just because you grabbed the window to move it. (maybe this is a problem with the window manager, I'm not sure.):confused:

---

### Post by WW on 2008-09-02
You might find some help here, but the experts are in the fltk.general forum; see the [FLTK Forums](http://www.fltk.org/newsgroups.php).

---

### Post by techmarks on 2008-09-02
Thanks I might have to try the experts on this one.

The simplest solutions would be to set the windows so they are not re-sizeable, and then the user just sets the window size at the creation of the plot.

But this seems like a limitation more than a solution.

If only FLTK would allow me to read the shift state bit fields on the MOVE event I think this work.

---

### Post by techmarks on 2008-09-03
I finally resolved the mouse events issue, it wasn't as serious as I feared.
So for the record here is my solution.

FLTK does keep information about the most recent event in static storage, until the next event processes.

So using the function "event_state" as follows worked;


First make sure the events captured belong to your window
and do the following just before your mouse handle function;


```

Fl::belowmouse(this);  //make sure the events belong to our window

```


Now you can do your OpenGL rotation matrix transforms;

```
if(   Fl::event_state(FL_BUTTON1)    )
{

...ok to procecess mouse related transforms...
(the left mouse button is pushed while we are inside the windows drawing area)

}
```

"event_state" is a bitfield of what shift states were on and what mouse buttons 
were held down during the most recent event, it's a small inline function so it's fast
and shouldn't affect performance much if at all.

We just check that it returned non-zero (if any of the passed bits are turned on).

Why do this if the button events FL_PUSHED and FL_DRAG only occurr when 
the mouse button is down anyhow?

The trouble is that FLTK will issue the FL_PUSHED event even when you 
push the mouse button on any window that is overlapping any area of the window you are
drawing into.

Also there is the complication that FLTK also registers FL_PUSHED when you grab on 
the windows border decoration to resize or move your window. 

But as you can see the solution is quite simple.

---

### Post by WW on 2008-09-03
Thanks for taking the time to report the solution!

---

