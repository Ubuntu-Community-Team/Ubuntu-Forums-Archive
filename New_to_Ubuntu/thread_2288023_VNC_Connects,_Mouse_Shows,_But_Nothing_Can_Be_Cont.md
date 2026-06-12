---
title: "VNC Connects, Mouse Shows, But Nothing Can Be Controlled"
date: 2015-07-23
forum: New to Ubuntu
---

### Post by iden2 on 2015-07-23
I have an Xubuntu server running vino to which I connect using Remmina using VNC protocol.  When I connect I can see everything that was on the screen when I was last sitting in front of the computer but I can't type or choose anything with the mouse. The mouse appears to move around on the screen but it can not interact with anything on the screen. I have ssh access and can run commands on the command line that way but I can not physically get to the machine to make any adjustments right now. What do I not know? I am using Mint 17 to run the Remmina VNC connection. What can be done from an ssh shell to fix this issue?

---

### Post by steeldriver on 2015-07-23
It sounds like vino-server is configured in view-only mode, but I don't know how you'd confirm or modify that on Xubuntu - does

```

DISPLAY=:0 vino-preferences

```

(from a terminal) exist/work? I've always used x11vnc for desktop sharing on non-gnome systems

---

### Post by iden2 on 2015-07-24
Thanks for that idea. There is another point I should have mentioned. I was able to successfully connect and control the machine from a Lubuntu 14 install on a netbook in the same house as the server as well as using that machine via a cellphone hotspot connection to test whether it would work from outside the LAN. Running the command from the terminal you suggested results in no reaction and no return prompt from the server machine (oh well).

---

