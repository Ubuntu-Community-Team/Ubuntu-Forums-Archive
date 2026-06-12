---
title: "Router 2nd Reboot Access Denied"
date: 2013-10-02
forum: New to Ubuntu
---

### Post by Kompftputer on 2013-10-02
I am using the internet now. If I reboot my router, I cannot connect unless I reboot it a second time. I can only connect every second reboot. Please help me to solve this. Something is wrong because I can connect to the internet so why only every second time? Windows can connect every time, why can't linux or is it just Ubuntus fault? I can't even connect through Terminal using "[COLOR=#333333][FONT=monospace]telnet" commands.[/FONT][/COLOR]

---

### Post by grahammechanical on 2013-10-02
The router is a separate item of equipment from your computer. If there is a hardware fault in the router it is nothing to do with Ubuntu. But if you switch the router Off and then On then Ubuntu will be disconnected from the router and then it will take Ubuntu some moments to reconnect to the router even if we are using a cable to connect the computer to the router. It stands to reason that if the OS is not connected to the router then you will not be able to use terminal commands either.

It could also be that Ubuntu is not set to automatically connect to the router. Have you thought of that? Are you getting any messages from Ubuntu on this subject? Ubuntu tries to connect to the router while Ubuntu is loading itself. So that we are connected by the time we get to the login screen. If we boot Ubuntu before the router has had time to make its own connection to the ISP then Ubuntu may give us some kind of not connected message.

---

### Post by Kompftputer on 2013-10-02
Every 2nd reboot: I wait for all the router's lights to turn on (signalling internet connection) and Ubuntu has 3/4 bars (wifi) but telnet commands fail and web browsers also fail.

MS Windows always connects successfully.

---

