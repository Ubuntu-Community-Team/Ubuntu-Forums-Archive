---
title: "X11 click jitter"
date: 2011-01-20
forum: Programming Talk
---

### Post by ian.macky on 2011-01-20
An X11 question: often when clicking the mouse there is often unintentional small movement-- a pixel or two-- which jitter is then interpreted as dragging the mouse-- but it's intended by the user to be just a click.  This is a problem.

Naive solution is to treat 1 or 2 (or some small N) pixel drags (with button(s) down) as a click, but when *actually* dragging, this gets in the way, since dragging the mouse is just a long sequence of many small drags.

I can't distinguish between an unintentional small drag which was meant to be a click and an intentional small drag which is part of a long drag.

Any suggestions??  --ian

---

### Post by worksofcraft on 2011-01-20
> **ian.macky said:**
> An X11 question: often when clicking the mouse there is often unintentional small movement-- a pixel or two-- which jitter is then interpreted as dragging the mouse-- but it's intended by the user to be just a click.  This is a problem.

Naive solution is to treat 1 or 2 (or some small N) pixel drags (with button(s) down) as a click, but when *actually* dragging, this gets in the way, since dragging the mouse is just a long sequence of many small drags.

I can't distinguish between an unintentional small drag which was meant to be a click and an intentional small drag which is part of a long drag.

Any suggestions??  --ian
I have never noticed this and I think perhaps it is a problem with your mouse, however I can understand how it might happen so can you not simply use time and positions from when your mouse button actually changes state?

---

### Post by ajgreeny on 2011-01-20
From the System ->Preferences ->Mouse  Help button:-
> Sensitivity

Use the slider to specify how sensitive your mouse pointer is to movements of your mouse.so reduce the sensitivity to help your problem.

Trial and error, I think.

---

### Post by ian.macky on 2011-01-20
An X11 question: often when clicking the mouse there is often unintentional small movement-- a pixel or two-- which jitter is then interpreted as dragging the mouse-- but it's intended by the user to be just a click.  This is a problem.

Naive solution is to treat 1 or 2 (or some small N) pixel drags (with button(s) down) as a click, but when *actually* dragging, this gets in the way, since dragging the mouse is just a long sequence of many small drags.

I can't distinguish between an unintentional small drag which was meant to be a click and an intentional small drag which is part of a long drag.

Any suggestions??  --ian

---

### Post by ian.macky on 2011-01-20
Sorry for the duplicate posts-- I kept getting 502's back and was retrying.  Is there any way to remove the duplicates?

Hmm, did not think it might be a problem with the mouse.  What sensitivity adjustments can be made in X?  All I know of are the acceleration parameters which xset fiddles.

[ajgreeny]("http://ubuntuforums.org/member.php?u=27747") refers to some menu somewhere, System->Preferences->Mouse Help button; no idea where that's supposed to be, or what control underlies it.

I run twm with xterms, no fancy candy coatings.  My event loop is not too complicated (this is a portable application, not specific to X11):

```

    for (;;)
    {
        ev->type = PAT_GUI_EVENT_NONE;
        XSync(xd, 0);
        XNextEvent(xd, &x_event);

        switch (x_event.type)
        {
...various irrelevant cases removed...

            case ButtonPress:
                ev->type = PAT_GUI_EVENT_BUTTONS;
                ev->buttons = old_buttons | pat_x11_map_button(x_event.xbutton.button);
                break;

            case ButtonRelease:
                ev->type = PAT_GUI_EVENT_BUTTONS;
                ev->buttons =
                    old_buttons & ~pat_x11_map_button(x_event.xbutton.button);
                break;

            case MotionNotify:
                if (dvd->xptr_x < 0)
                {
                    ev->type= PAT_GUI_EVENT_PTR_ABS;
                    ev->xd = PAT_X11_X(x_event.xmotion.x);
                    ev->yd = PAT_X11_Y(x_event.xmotion.y);
                }
                else
                {
                    ev->type = PAT_GUI_EVENT_PTR_REL;
                    ev->xd = x_event.xmotion.x - dvd->xptr_x;
                    ev->yd = dvd->xptr_y - x_event.xmotion.y;
                }
                dvd->xptr_x = x_event.xmotion.x;
                dvd->xptr_y = x_event.xmotion.y;
                pat_x11_combine_motion(dev, ev);
                break;

            default:
                break;
        }
        if (ev->type != PAT_GUI_EVENT_NONE)
            return TRUE;
    }
}

/* merge consecutive motion events */

PAT_PRIVATE void
pat_x11_combine_motion(patdev *dev, patgev *ev)
{
    pat_x11_data *dvd = dev->data;
    Display *xd = dvd->xd;

    XEvent x_event;
    int n;

    for (n = XPending(xd); n-- > 0; )
    {
        XPeekEvent(xd, &x_event);
        if (x_event.type != MotionNotify)
            break;
        XNextEvent(xd, &x_event);
        ev->xd += (x_event.xmotion.x - dvd->xptr_x);
        ev->yd += (dvd->xptr_y - x_event.xmotion.y);
        dvd->xptr_x = x_event.xmotion.x;
        dvd->xptr_y = x_event.xmotion.y;
    }
}

```

---

### Post by ajgreeny on 2011-01-21
The suggestion I gave you was for gnome;  sorry if that is not of use, but I wrongly assumed that you were on a standard ubuntu setup.

---

### Post by Arndt on 2011-01-21
> **ajgreeny said:**
> The suggestion I gave you was for gnome;  sorry if that is not of use, but I wrongly assumed that you were on a standard ubuntu setup.

The program which is called by the mentioned menu sequence is gnome-mouse-properties, so if you have gnome installed, it is available.

It seems to do other things than 'xset'. There may be a command line tool for what gnome-mouse-properties does, but I don't know it.

---

