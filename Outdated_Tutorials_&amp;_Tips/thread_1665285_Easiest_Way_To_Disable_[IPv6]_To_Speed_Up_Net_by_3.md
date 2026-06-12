---
title: "Easiest Way To Disable [IPv6] To Speed Up Net by 3x- Begginers"
date: 2011-01-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Bazzi313 on 2011-01-12
Hey this is how to disable ipv6, which will increase internet speed for most users

First We Must Find out if your Internet does or does not use IPv6: Simply go to this page 

[SIZE=5]Do You Used Ipv6[/SIZE]

[http://ip-lookup.net/](http://ip-lookup.net/)
And go Under the Conversions Tab, and it will tell you

So If You Have ipv4 Read on if not forget this.

[SIZE=5][COLOR=Black]How to Disable[/COLOR][/SIZE]

A simple and graceful way of disabling IPv6 is to use [sysctl]("http://en.wikipedia.org/wiki/Sysctl") to modify kernel parameters at runtime. ( Might Sound Complicated I'll explain it dw. )
 
[LIST]
[*]Add the following parameter and setting  **net.ipv6.conf.all.disable_ipv6 = 1** to [COLOR=#005500][FONT=monospace]/etc/sysctl.conf[/FONT][/COLOR] [COLOR=SeaGreen]directory[/COLOR]:
[/LIST]
 
[COLOR=Red]*So Basically , type:* [COLOR=Black]**sudo gedit /etc/sysctl.conf**[/COLOR][/COLOR][COLOR=Red] in terminal  [/COLOR][COLOR=Red][COLOR=PaleGreen]_[COLOR=SeaGreen]( to access the file because u cant edit files in etc, unless accessed through terminal)[/COLOR] _[/COLOR]add [COLOR=Black]net.ipv6.conf.all.disable_ipv6 = 1[/COLOR] to the bottom of the pad, no #.[/COLOR] if there is a # just go to the line under.

Then Reboot, and type in terminal [B]
ip a | grep inet6[/B] in terminal

If nothing happens then it has worked

THEN CHECK SCREEN SHOT IF YOURS IS LIKE SCREEN SHOT IT WORKED!!

Please comment on results

---

