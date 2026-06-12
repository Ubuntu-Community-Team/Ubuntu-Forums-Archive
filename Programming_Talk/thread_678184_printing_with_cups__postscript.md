---
title: "printing with cups / postscript"
date: 2008-01-25
forum: Programming Talk
---

### Post by KPexEA on 2008-01-25
I am converting an app written in c++ from windows to linux. The linux version of the app is generating a postscript file and then sending it to the printer using Cups. It seems to be working fine except for if I print any accented characters then they are not printing correctly.

I'm not sure if the problem is text encoding or perhaps the font I am using is different on the printer than the one I have on the computer ( I am using Arial, and the printer I am using is a HP Laserjet 3700 )

The possible solutions that I have thought of so far are:

1) Embed the true type font directly into the postScript file, is this is the correct solutions, then does anyone have any sample code for doing this?

2) Or perhaps it is an encoding issue and I need to have some sort of encoding commands in the PostScipt file?

Any help would be greatly appreciated,
Thanks
Kevin

---

