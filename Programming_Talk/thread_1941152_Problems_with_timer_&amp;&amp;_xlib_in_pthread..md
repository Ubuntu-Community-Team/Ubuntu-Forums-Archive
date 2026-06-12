---
title: "Problems with timer &amp;&amp; xlib in pthread."
date: 2012-03-15
forum: Programming Talk
---

### Post by CynicRus on 2012-03-15
Good day, gentlemen.There appears to be the next race. There is a timer routine and routine creates a window using xlib, which displays the countdown timer. When both are performed in the routine flow of main - all work out fine, but - I need to scatter them to different threads. Of course using pthread. So - when you try to do it - catch inexplicable Interrupted system call. More precisely - is understandable. In general - decorated with a timer on the form and executed in the thread - everything is fine, everything works. Form of stuffing in a separate thread: Interrupted system call.
The timer is connected with the form as follows:
```
void timer_init()
{
    signal(SIGALRM, &timer_callback);
    struct timeval interval = { 1, 0 };
    struct timeval value = { 1, 0 };    struct itimerval timerval;
    timerval.it_interval = interval;
    timerval.it_value = value;
    setitimer(ITIMER_REAL, &timerval, 0);
}
void timer_callback(int sign)
{
    if (timer_value > 0)
    {
        timer_value--;
    }
    window_repaint_send();
}

```event processing for window:
```

void window_loop()
{
    int ret;
    XEvent event;
    for (;;)
    {
        XNextEvent(display, &event);
        switch (event.type)
        {
        case Expose:
        {
            window_repaint();
            break;
        }
        case ResizeRequest:
        {
            XResizeRequestEvent *resize = (XResizeRequestEvent *) &event;            window_width = resize->width;
            window_height = resize->height;
            break;
        }
        default:
        {
            break;
        }
        }
    }
}
void window_repaint_send()
{
    XExposeEvent expose = { Expose, 0, 1, display, window, 0, 0, window_width, window_height, 0 };
    XSendEvent(display, window, 0, ExposureMask, (XEvent *) &expose);
    XFlush(display);
}
void window_repaint()
{
    XClearArea(display, window, 0, 0, window_width, window_height, 0);

    XFontStruct *font = XLoadQueryFont(display, "10x20");
    if (!font)
    {
        exit(EXIT_FAILURE);
    }

    GC gc = XCreateGC(display, window, 0, NULL);
    XSetFont(display, gc, font->fid);
    char timer_message[100];
    timer_str(timer_message);
    int timer_message_pos_x = window_width / 2 - XTextWidth(font, timer_message, strlen(timer_message)) / 2;
    int timer_message_pos_y = window_height / 2 ;
    XDrawString(display, window, gc, timer_message_pos_x, timer_message_pos_y, timer_message, strlen(timer_message));
    char attention_message[100];
    if (timer_get_message(attention_message))
    {
        int attention_message_pos_x = window_width / 2 - XTextWidth(font, attention_message, strlen(attention_message)) / 2;
        int attention_message_pos_y = window_height / 2 + 30;
        XDrawString(display,  window, gc, attention_message_pos_x, attention_message_pos_y,  attention_message, strlen(attention_message));
    }
    XFreeGC(display, gc);
}


```I suspect that the problem is in the depths of window_loop, when referring to the timer, and a corresponding call window_repaint_send window_repaint. I tried a mutex lock repaint, but somehow it did not bring dividends. And therefore I ask your advice.

PS:Sorry for bad English, it is not my native language. But, I tried)

---

### Post by CynicRus on 2012-03-16
And hello again, appears defeating last problem with XLockDisplay, XUnlockDisplay. The timer works off jauntily, the window cheerfully drawn. But I made a mistake somewhere, and - only work flows.
[http://hpaste.org/65381](http://hpaste.org/65381)
Socket - create, listen. But - do not accept the second application - to connect them - and all. In this state they can run forever. In what may be plugging?

---

