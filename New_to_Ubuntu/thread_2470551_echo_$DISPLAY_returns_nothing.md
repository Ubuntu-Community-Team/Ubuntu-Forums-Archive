---
title: "echo $DISPLAY returns nothing"
date: 2022-01-03
forum: New to Ubuntu
---

### Post by snadegg on 2022-01-03
This is a rabbit hole I fell into because I wanted to script a window switch in tmux.

I saw that the Ubuntu project had documentation on something called "xdotools." I gave it a try, but it always returned this:

Error: can't open display: (null)
Failed creating new xdo instance

So I found a few posts on stackexchange and one of the steps was to run "echo $DISPLAY" to find out what display to specify for xdotools, but it returned nothing.

I thought it was an issue with SSH but after troubleshooting for a while I plugged directly into the server and that didn't change anything.

I don't know where to go from here.
Thank you in advance!

---

### Post by Holger_Gehrke on 2022-01-03
xdotool is for controlling a X11 based GUI; tmux is a **t**erminal **mu**ltiple**x**er. Not the same thing at all, so this will not work. DISPLAY is a variable that should give the address and number of the active X11 display, usually something like ':0.0' (first display on the local machine (that's the nothing before the colon, if you're working remotely there might be the ip address of the machine doing the displaying before the colon).

You can control tmux from a shell running inside tmux by calling tmux with commands, for example 'tmux next-window' will switch to the next window and 'tmux select-pane -t +' will switch to the next pane. Read 'man tmux' for more details.

Holger

---

### Post by snadegg on 2022-01-03
That really helped clear things up.

I couldn't find any terminal commands for some window management stuff for tmux so I tried to automate input of the prefix and whatever key to tell it what to do. 

Thanks for telling me there's an easier way!

---

### Post by TheFu on 2022-01-04
DISPLAY is for X11.  So is xdotool.

I don't know if Wayland supports that or not.

If tmux is being run on a system running an X/Server with an active X/Session, then the DISPLAY should be set.  If there is no X/Server, then the DISPLAY should not be set.

X/Windows is a client/server architecture with the client being the remote system and the server being the system we sit behind. This is opposite for almost every other Client/Server architecture.

Anyway ... if you are using a desktop linux that has a GUI, then I'd suggest that you validate wither Xorg/X11 is being used with an X/Server or Wayland is being used.

There are pros and cons to using both Wayland or X11.  In theory, Wayland should be faster and more secure.  X11 should work with many more programs since lots of programs have not been ported to Wayland libraries/APIs and some take advantage of the xorg security problems to do some amazing things.

---

### Post by snadegg on 2022-01-04
I'm running Ubuntu without a GUI, I just didn't understand what X11 was. Thanks for the information!

---

### Post by TheFu on 2022-01-04
Please use the "Thread Tools" button near the top to mark this thread SOLVED to help the community out so people looking for and offering answers find what they seek.

---

