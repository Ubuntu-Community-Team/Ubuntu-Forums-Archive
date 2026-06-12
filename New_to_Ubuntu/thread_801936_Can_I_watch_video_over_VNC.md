---
title: "Can I watch video over VNC?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Twizzle on 2008-05-21
I have managed to set up a server using Ubuntu 8.04, with a CCTV camera connected to it via a Hauppauge PVR 150 card, and can connect to it using PalmVNC from my Palm TX, but when I launch mplayer on the server, the video only shows as a black box on the palm. I know that the video works normally because I plugged my monito into the server and all was fine.

Is it possible to view video over the vnc system? I am doing this all over my home netwwork so speed should not really be an issue.

---

### Post by .nedberg on 2008-05-21
Just did a test with VLC on my Mythbuntu server. I could watch video just fine (no sound though). I had a problem with mplayer, it did not want to play the files at all.

Don't know about palmVNC, but at least it is possible!

---

### Post by MaindotC on 2008-05-21
I've tried watching youtube and stuff over VNC and it's just very slow.  Sometimes when I was trying to take a screen shot of video that was playing through realplayer, it would be a black screen - dunno why it does that but it may be realplayer codec video.

---

### Post by Twizzle on 2008-05-24
Hmm, I have had a play around and using mplayer or Videolan I can play any film on my server but it just shows as a blue or black screen on the PC / Palm when connecting using vnc.

I guess there is a setting somewhere to allow a higher data throughput?

Any one point me in the right direction.

---

### Post by Twizzle on 2008-05-25
Im now using vnc4server on the server and xvnc4viewer on the main pc. I have set all the settings on the viewer to max but can't find anyway to change settings for the viewer.

When accessing the server, it feels very responsive and has full colour etc but I still can't watch any video through the vnc viewer.

Does anyone know if there are settings I can use, or should I be using a different vnc server?

---

### Post by Inxsible on 2008-05-25
I used to watch video over NX - no sound again-  and it was pretty fast too. I know its not VNC, but NX gives a better remote desktop experience. You might wanna try it out, although I am not sure if your palm would support NX.

---

### Post by Twizzle on 2008-05-25
Thanks for the suggestion.

It does look good but I need the palm facility to work really so will continue trying with vnc for now :)

---

### Post by _sAm_ on 2008-05-25
What about opening it with ssh? I just tried to open Firefox via ssh on my LAN and it works very good(playing both music and youtube).

---

### Post by Twizzle on 2008-05-25
Sounds like something I could try, thing is I have no idea what SSH is. Will do some digging, but is there something I need to install on my server / PC first or does Ubuntu come with it pre installed?

---

### Post by Twizzle on 2008-05-25
OK got ssh working but it just gives me a command prompt. Is there any way of having a graphical interface like x?

---

### Post by Twizzle on 2008-05-25
SSH is now fully working on my server and PC, and I managed to figure out how to use graphical programs so I can view mplayer etc from my server on my PC.

The only thing I can't do now is view video on my palm from my server. I guess SSH for palm does not have that functionality, and I will have to look for an alternative method to remote monitor my CCTV.

---

### Post by rolltidega on 2009-06-22
Twizzle, can you tell me how you got this to work?  I am trying to do the same thing to view video.  Thanks....

---

### Post by StygianAgenda on 2010-08-24
@Twizzle > The problem with SSH on PalmOS (any build prior to Palm WebOS) is that the SSH clients for that platform do not have a way to hand the remote GUI apps off to an X-Windows Server.

There's not a perfect answer to this, but there are some workable solutions.  

On Ubuntu, I use XDMCP + vnc4server, setup in a way so that the XDMCP service is pushing thru VNC to give each connection an isolated desktop session with their own login screen.  Now, I use this primarily with Tunnelier (portable SSH tunneling app; win32) combined with UltraVNC viewer.  I'm able to store the pair on a flash drive for use in Windows, or Linux via WINE.  on my iPhone, I use iTeleport (formerly known as Jaadu VNC) combined with PPTP-VPN.  The effect is the same, either way.  A remote desktop is delivered to the VNC client with it's own GDM session, separate from the local console session.  There are tons of HowTo's for setting this up that can be found via a Google search, so I won't repeat them here.  Just search "XDMCP + VNC" and your distro-name (example: "XDMCP + VNC Ubuntu").

If memory serves, I used 'PalmVNC' for my last PalmOS system (a Sony Clié UX-50), but I was using that long before I found out about XDMCP+VNC.

Now, as far as video thruput... The Windows solution I use (Tunnelier + UltraVNC) works pretty well.  Over my Gbit LAN, it's nearly flawless (the flaws that *do* exist, are due to RFB being a weak protocol for streamed video), and it's watchable over a remote connection from my work, but I have to reduce the colors to 256 for the framerate to keep up.  Otherwise, I'll get about 3 frames-per-sec at best, losing any non-shown frames (they simply don't display) from VLC or Media Player Classic HC.

On my iPhone, unfortunately, I haven't yet figured out how I need to tune it's settings to get remote video to display properly.  It may be simply a matter of changing the video players themselves to use something other than the default overlay plane, such as Direct-X rendering or OpenGL rendering in the case of Linux.

Anyways, I hope this is helpful, or atleast informative.  Best of luck m8.

---

