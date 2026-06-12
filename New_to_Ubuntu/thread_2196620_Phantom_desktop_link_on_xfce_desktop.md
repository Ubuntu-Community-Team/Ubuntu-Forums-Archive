---
title: "Phantom desktop link on xfce desktop"
date: 2013-12-30
forum: New to Ubuntu
---

### Post by mlnease on 2013-12-30
Hello,

This is a really trivial annoyance but I'd be glad to resolve it.

On my xfce desktop, there's a little blank square at the top left (barely visible in the attached screenshot).  If I have an open window that overlaps that spot (as I usually do), it takes a little square bite out of the corner of that window.  If I right-click on the square, it reveals itself to be a link to the desktop itself.  All 'Default Icons' are unchecked in 'Desktop Settings'.

Can anyone please advise me as to exactly what this is and how I can get rid of it?

Thanks very much in advance.

---

### Post by Toz on 2013-12-30
Here is one way that might help to identify it. Open a terminal window and run the following command:
```
ps -A | grep $(xprop _NET_WM_PID | cut -d' ' -f3)
```
...then click on the square.

Assuming its an X11 window, this command will grab the pid of the window using xprop and pull out the associated application process info using ps.

---

### Post by mlnease on 2013-12-30
> **Toz said:**
> Here is one way that might help to identify it. Open a terminal window and run the following command:
```
ps -A | grep $(xprop _NET_WM_PID | cut -d' ' -f3)
```
...then click on the square.

Assuming its an X11 window, this command will grab the pid of the window using xprop and pull out the associated application process info using ps.

Great, thanks--here's the terminal output:  ```
10752 ?        00:00:00 xfce4-terminal
```

Afraid it doesn't mean much to me, though.  I guess that xprop has identified the process id of 'the phantom' as 10752, correct?

Thanks very much for your quick response.

---

### Post by Toz on 2013-12-30
> **mlnease said:**
> I guess that xprop has identified the process id of 'the phantom' as 10752, correct?.
Yes. Interesting that it looks like that though. Do you have any active xfce4-terminal windows open?

What does the following return:
```
pstree 10752
```

---

### Post by mlnease on 2013-12-30
> **Toz said:**
> Yes. Interesting that it looks like that though. Do you have any active xfce4-terminal windows open?

I did, yes--had to to run the code, right?  Or have I misunderstood?

> **Toz said:**
> What does the following return:
```
pstree 10752
```

```
pstree 10752
``` returned nothing.

Thanks for the follow-up.

Sorry!

---

### Post by Toz on 2013-12-30
Try the two commands together:
```
pstree $(ps -A | grep $(xprop _NET_WM_PID | cut -d' ' -f3) | cut -d' ' -f2)
```

If its just an errant terminal window, you can kill it using:
```
xkill
```
...and clicking on it.

---

### Post by mlnease on 2013-12-30
> **Toz said:**
> Try the two commands together:
```
pstree $(ps -A | grep $(xprop _NET_WM_PID | cut -d' ' -f3) | cut -d' ' -f2)
```

Output:  ```
No such user name: ?
```

If its just an errant terminal window, you can kill it using:
```
xkill
```
...and clicking on it.

I've tried xkill--causes a screen flash, then back to square one.

Thanks again!

---

### Post by Toz on 2013-12-30
Can you just post back the complete results of:
```
xprop
```
...after clicking on that square?

---

### Post by mlnease on 2013-12-30
> **Toz said:**
> Can you just post back the complete results of:
```
xprop
```
...after clicking on that square?

Gladly:

```
mn@mn-OptiPlex-745:~$ xprop
_NET_WM_ICON_GEOMETRY(CARDINAL) = 601, 994, 200, 30
_NET_FRAME_EXTENTS(CARDINAL) = 1, 1, 24, 1
_NET_WM_ALLOWED_ACTIONS(ATOM) = _NET_WM_ACTION_CLOSE, _NET_WM_ACTION_ABOVE, _NET_WM_ACTION_BELOW, _NET_WM_ACTION_FULLSCREEN, _NET_WM_ACTION_MOVE, _NET_WM_ACTION_RESIZE, _NET_WM_ACTION_MAXIMIZE_HORZ, _NET_WM_ACTION_MAXIMIZE_VERT, _NET_WM_ACTION_SHADE, _NET_WM_ACTION_MINIMIZE, _NET_WM_ACTION_CHANGE_DESKTOP, _NET_WM_ACTION_STICK
WM_STATE(WM_STATE):
        window state: Normal
        icon window: 0x0
_NET_WM_DESKTOP(CARDINAL) = 0
_WIN_WORKSPACE(CARDINAL) = 0
_WIN_STATE(CARDINAL) = 0
_NET_WM_STATE(ATOM) = 
WM_HINTS(WM_HINTS):
        Client accepts input or input focus: True
        Initial state is Normal State.
        bitmap id # to use for icon: 0x4000018
        bitmap id # of mask for icon: 0x400001b
        window id # of group leader: 0x4000001
XdndAware(ATOM) = BITMAP
_MOTIF_DRAG_RECEIVER_INFO(_MOTIF_DRAG_RECEIVER_INFO) = 0x6c, 0x0, 0x5, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x10, 0x0, 0x0, 0x0
_NET_WM_ICON(CARDINAL) =     Icon (48 x 48):
                                                    
                                                    
                                                    
                                                    
                                                    
                                                    
                                                    
      &#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;  
     &#9617;                                            &#9617; 
     &#9617;                                            &#9617; 
     &#9617;                                            &#9617; 
     &#9617;   &#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;   &#9617; 
     &#9617;   &#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9617;&#9617;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;   &#9617; 
     &#9617;   &#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;   &#9617; 
     &#9617;   &#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9619;   &#9617; 
     &#9617;   &#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9619;   &#9617; 
     &#9617;   &#9618;&#9618;&#9618;&#9618;&#9618;&#9617;&#9617;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9619;   &#9617; 
     &#9617;   &#9618;&#9618;&#9618;&#9618;&#9617;   &#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9619;   &#9617; 
     &#9617;   &#9618;&#9618;&#9618;&#9618;&#9617;    &#9617;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9619;&#9619;&#9618;&#9619;   &#9617; 
     &#9617;   &#9618;&#9618;&#9618;&#9618;&#9618;&#9618;    &#9617;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9619;&#9619;&#9619;&#9619;&#9618;&#9619;   &#9617; 
     &#9617;   &#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9617;   &#9617;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9618;&#9619;   &#9617; 
     &#9617;   &#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;    &#9617;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9618;&#9619;   &#9617; 
     &#9617;   &#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;    &#9617;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9618;&#9619;   &#9617; 
     &#9617;   &#9618;&#9618;&#9618;&#9618;&#9618;&#9618;    &#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9618;&#9619;   &#9617; 
     &#9617;   &#9619;&#9618;&#9618;&#9618;&#9617;    &#9618;&#9619;&#9618;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;   &#9617; 
     &#9617;   &#9619;&#9618;&#9618;&#9618;&#9617;  &#9617;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;   &#9617; 
     &#9617;   &#9619;&#9619;&#9619;&#9619;&#9619;&#9617;&#9617;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;   &#9617; 
     &#9617;   &#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;        &#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;   &#9617; 
     &#9618;   &#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;        &#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;   &#9618; 
     &#9618;   &#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;   &#9618; 
     &#9618; &#9617;&#9617;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9617;&#9617; &#9618; 
     &#9618; &#9617;&#9617;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9617;&#9617; &#9618; 
     &#9618; &#9617;&#9617;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9617;&#9617; &#9618; 
     &#9618; &#9617;&#9617;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9617;&#9617; &#9618; 
     &#9618; &#9617;&#9617;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9617;&#9617; &#9618; 
     &#9618; &#9617;&#9617;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9617;&#9617; &#9618; 
     &#9618; &#9617;&#9617;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9617;&#9617; &#9618; 
     &#9618; &#9617;&#9617;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9617;&#9617; &#9618; 
     &#9618; &#9617;&#9617;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9617;&#9617; &#9618; 
     &#9618; &#9617;&#9617;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9617;&#9617; &#9618; 
     &#9618;&#9617;&#9617;&#9617;&#9619;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9619;&#9617;&#9617;&#9617;&#9618; 
     &#9618;&#9617;&#9617;                                        &#9617;&#9617;&#9618; 
     &#9618;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9618; 
     &#9618;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9618; 
      &#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;  
                                                    
                                                    
                                                    


_NET_STARTUP_ID(UTF8_STRING) = "xfce4-panel/xfce4-terminal/2212-45-mn-OptiPlex-745_TIME42450716"
WM_WINDOW_ROLE(STRING) = "Terminal-0x22662838-12211-1388449549"
_NET_WM_SYNC_REQUEST_COUNTER(CARDINAL) = 67108870
_NET_WM_WINDOW_TYPE(ATOM) = _NET_WM_WINDOW_TYPE_NORMAL
_NET_WM_USER_TIME_WINDOW(WINDOW): window id # 0x4000005
WM_CLIENT_LEADER(WINDOW): window id # 0x4000001
_NET_WM_PID(CARDINAL) = 12211
WM_LOCALE_NAME(STRING) = "en_US.UTF-8"
WM_CLIENT_MACHINE(STRING) = "mn-OptiPlex-745"
WM_NORMAL_HINTS(WM_SIZE_HINTS):
        user specified size: 1 by 577321696
        program specified minimum size: 49 by 57
        program specified resize increment: 8 by 17
        program specified base size: 17 by 23
        window gravity: NorthWest
WM_PROTOCOLS(ATOM): protocols  WM_DELETE_WINDOW, WM_TAKE_FOCUS, _NET_WM_PING, _NET_WM_SYNC_REQUEST
WM_CLASS(STRING) = "xfce4-terminal", "Xfce4-terminal"
WM_ICON_NAME(STRING) = "Terminal - mn@mn-OptiPlex-745: ~"
_NET_WM_ICON_NAME(UTF8_STRING) = "Terminal - mn@mn-OptiPlex-745: ~"
WM_NAME(STRING) = "Terminal - mn@mn-OptiPlex-745: ~"
_NET_WM_NAME(UTF8_STRING) = "Terminal - mn@mn-OptiPlex-745: ~"
mn@mn-OptiPlex-745:~$ 


```

---

### Post by Toz on 2013-12-30
Okay, now its not the terminal there anymore - must be something else.

What video card do you have?
```
lspci -k | grep -iA2 VGA
```

Can you try turning off the composting (Settings Manager -> Window Manager Tweaks -> Compositor) and see if it disappears. If so, does it re-appear when you enable compositing.

Does is show up right after a reboot/login?

Do you have any java applications running:
```
ps -ef | grep java
```

---

### Post by mlnease on 2013-12-30
> **Toz said:**
> Okay, now its not the terminal there anymore - must be something else.

What video card do you have?
```
lspci -k | grep -iA2 VGA
```

```
mn@mn-OptiPlex-745:~$ lspci -k | grep -iA2 VGA
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
    Subsystem: Dell Device 01da
    Kernel modules: i915
mn@mn-OptiPlex-745:~$
``` 

Can you try turning off the composting (Settings Manager -> Window Manager Tweaks -> Compositor) and see if it disappears. 

It did!

> **Toz said:**
> If so, does it re-appear when you enable compositing.

It did not!

> **Toz said:**
> Does is show up right after a reboot/login?

> **Toz said:**
> Do you have any java applications running:
```
ps -ef | grep java
```

Yes:

```
mn@mn-OptiPlex-745:~$ ps -ef | grep java
root      2458  2309  0 Dec29 ?        00:00:38 java -jar /usr/share/java/ipblockUI.jar
mn       12316 12213  0 16:36 pts/0    00:00:00 grep --color=auto java
mn@mn-OptiPlex-745:~$ 
```

I haven't yet rebooted (in order not to interrupt this exchange), but the problem appears solved--thanks a million!  Should it reappear after reboot, I'll let you know but I should be able to troubleshoot it thanks to your invaluable advice.

Thanks again and

Happy New Year!

---

### Post by Toz on 2013-12-30
Glad to hear its gone. I believe that its the java application that's leaving the remnant there.

---

### Post by mlnease on 2013-12-30
> **Toz said:**
> Glad to hear its gone. I believe that its the java application that's leaving the remnant there.

I'll remember that--and Settings Manager > Window Manager Tweaks > Compositor.

I realize I'm asking for trouble using Java, but I'm addicted to a crossword puzzle that depends on it.

Can't thank you enough for your time and perseverance.

Cheers,

mn

p.s.  Toz, apparently your surmise was correct--the problem returned on reboot, and disappeared with ```
sudo killall java
```  

Cool.  Thanks again.  I'll just have to remember to kill Java when I'm not using it.

---

