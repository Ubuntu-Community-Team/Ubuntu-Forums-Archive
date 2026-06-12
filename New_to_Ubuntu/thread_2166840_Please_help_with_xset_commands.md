---
title: "Please help with xset commands"
date: 2013-08-11
forum: New to Ubuntu
---

### Post by wt-pm66 on 2013-08-11
I am trying to adjust the speed of my trackball mouse, I have searched all over google, and several forums, the only thing I can find is to use the xset command. There are a lot of postings showing the general command to get the information, then they all say something like "to set speed 
   **mouse**   The   **m**  option  controls  the  mouse  parameters;  it  may  be
               abbreviated  to  ’m’.   The  parameters  for  the   mouse   are
               ‘acceleration’   and  ‘threshold’.   The  acceleration  can  be
               specified as an integer, or as a simple fraction.   The  mouse,
               or  whatever  pointer  the  machine  is  connected  to, will go
               ‘acceleration’  times  as  fast  when  it  travels  more   than
               ‘threshold’ pixels in a short time.  This way, the mouse can be
               used for precise alignment when it is moved slowly, yet it  can
               be set to travel across the screen in a flick of the wrist when
               desired.  One or both  parameters  for  the  **m**  option  can  be
               omitted,  but  if  only one is given, it will be interpreted as
               the acceleration.  If no parameters or the  flag  ’default’  is
               used, the system defaults will be set.

               If   the   ‘threshold’   parameter   is  provided  and  0,  the
               ‘acceleration’ parameter will be used in the exponent of a more
               natural  and continous formula, giving precise control for slow
               motion  but  big  reach  for  fast  motion,  and  a  progresive
               transition  for motions in between.  Recommended ‘acceleration’
               value in this case is 3/2 to 2, but not limited to that  range.


and "
$ xset m 3/2 0
"

However no matter how closely I try to follow these instructions, I either get an error msg "command not found", or nothing at all happens, except
what I just typed disappears and I'm back to the $ prompt. 
Also the instructions say to put the new xset values into a xinput(?) file, or edit the .xorfg(?) file, with no instructions on how to do either of 
these. 
I am at a total loss here, and I really need to adjust the sensitivity of my device. I have some medical problems which cause my hands to shake and 
this thing is so sensitive that it is hard to do any delicate operation, such as clicking on small boxes, resizing windows and such. A regular mouse 
hurts my  hand and arm, so I need the trackball because it is comfortable, but if I can't get this solved, I may have to go back to a mouse. 

Sorry for the long post but I wanted to get as much information as possible.

---

### Post by bsamim on 2013-08-11
Have you tried using the gui it seemed to do the trick for me. Just hit the windows key and type Mouse and choose the app and play with the settings there. If you must use xset yourself see below.

Check out the following. I think this should answer your question.

[https://wiki.archlinux.org/index.php/Mouse_acceleration](https://wiki.archlinux.org/index.php/Mouse_acceleration)

Also, the link at the top tells you to use the man xorg.conf which shows where you can put the xorg.conf file such that it will be looked in the following places for it.  So you can try copying one of the samples on the link site and using an editor make an xorg.conf file and drop it in one of the following locations and see if this helps.

  /etc/X11/<cmdline>           /usr/etc/X11/<cmdline>
           /etc/X11/$XORGCONFIG
           /usr/etc/X11/$XORGCONFIG
           /etc/X11/xorg.conf
           /etc/xorg.conf
           /usr/etc/X11/xorg.conf.<hostname>
           /usr/etc/X11/xorg.conf
           /usr/lib/X11/xorg.conf.<hostname>
           /usr/lib/X11/xorg.conf

---

