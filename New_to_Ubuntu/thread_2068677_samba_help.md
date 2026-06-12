---
title: "samba help"
date: 2012-10-09
forum: New to Ubuntu
---

### Post by oldwindows geek on 2012-10-09
Hello, had to do a new install of my Ubuntu after an update caused my system to crash,currently running 10.04 Lts, tried 12.04 Lts but could not get things working, so I decide to try 10.04 again get it up and running then upgrade, currently running 1 Ubuntu machine on a home network and 2 windows xp's, my printer is attached to a windows xp and shared, but I am unable to see that xp machine in samba, worked before , but not now(?), need help getting it to work again, or may have to return to a window machine. the Ubuntu machine keeps appearing in my network workgroups folder in Ubuntu:confused:

---

### Post by audiomick on 2012-10-09
> **oldwindows geek said:**
> the Ubuntu machine keeps appearing in my network workgroups folder in Ubuntu:confused:

Yeah, that is correct. It does that. Nothing to worry about.

I don't want to offer any guesses about the printer, I'm afraid. I'm not too sure about that.

---

### Post by critin on 2012-10-09
> **oldwindows geek said:**
> ,currently running 10.04 Lts,  1 Ubuntu machine on a home network and 2 windows xp's, 

my printer is attached to a windows xp and shared, but I am unable to see that xp machine in samba

 the Ubuntu machine keeps appearing in my network workgroups folder in Ubuntu:confused:

Not sure what is meant by 'unable to see in Samba'.    You won't.  Do you mean it isn't seen in the file manager Network?   

Ubuntu is a part of your workgroup, yes?  It will show.  It's okay.

Basic Problem is:  Your xp printer machine will not show in network.    Do the other xp machines show up on all machines?   Does ubuntu show on all xp machines?

XP lan works a little differently than Win7 network as it's much easier (for me).  Go into windows and set up the network again.  Be sure the internet is connected to all machines first, and the printer is connected & turned on.  You know the drill.  lol

 You don't have to actually change anything when setting up the network again  if the workgroup name hasn't changed, you're just running it again so it will catch the new ubuntu.  Restart all machines and it should show up on all.  Be sure everything you want to share in 10.04 has the right permissions before restarting.

The printer machine should now show in ubuntu.  

When I configure Samba I don't require passwords.

---

