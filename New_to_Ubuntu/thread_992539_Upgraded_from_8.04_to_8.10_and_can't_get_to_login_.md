---
title: "Upgraded from 8.04 to 8.10 and can't get to login screen"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by amyg on 2008-11-24
I am currently browsing other topics, so I apologize if this had been covered.  I haven't found anything relavant using the search engine.

Prior to any install (like when I moved up to 8.04) it always logs me in in low graphics until I get my NVidia card updated.  So when it came up with a low graphics message I wasn't concerned.

These are the options it gives me after clicking ok from reading all the NVidia errors : 

[LIST]
[*]Run Ubuntu in low graphics mode
[*]Reconfigure Graphics
[*]Troubleshoot the error
[/LIST]

I've tried to just use the enter in with low graphics option (as I have in the past), however it blacks out to a screen.  I cannot type, click, do anything.  The only option I have is to reboot, which of course puts me in the same boat.  If someone could help me troubleshoot this (or point me to where I can read about it in more detail) I would be much obliged.

I have also dug around a little in the other two options (which have other lists in which I can go into more detail about), but I cannot find anything that my 'skill level' feels comfortable with until I am more sure about what I am doing.

I am currently posting from my husbands computer as I cannot log in, I will check back as soon as I can, so I apologize for any slow responses.

Thank you to anyone that takes the time to read and respond.  I will continue my own research and hopefully come across the answer =)

edit: and after digging i managed to find a way in.  sorry for taking up space!  i didn't think it'd be that easy =)

---

### Post by cmnorton on 2008-11-25
You may have to boot into recovery mode; run dpkg-reconfigure xserver-xorg; answer all questions taking the default answer; but specify the vesa instead of nvdia driver. 

This should let you configure well above the low graphics option and use your system normally.

---

