---
title: "wine + IE + COBOL"
date: 2006-04-09
forum: Programming Talk
---

### Post by LiquidFlame on 2006-04-09
hope i'm placing this in the right spot but anyways, not sure how many people out there can help me but this is my problem. i installed wine and works fine and i was able to get internet explorer up and running. My problem is for my COBOL programming class i need to use internet explorer because when i have to login to our mainframe it doesn't like firefox. So i tried opening up my link to under wine using IE6 but what happens is, i see the login screen for maybe 4 secs and then it just closes out on me. the editor that were using for my COBOL class is ROSCOE if that helps and the os that i'm running on my box is ubuntu. so if anyone has any idea how to let me access our mainframes that would be great cause i hate having to always go to the labs to work on my programs.

---

### Post by wmcbrine on 2006-04-09
Wow, that's a weird setup. I can't really help you with IE, but I'd suggest installing your own COBOL interpreter or compiler, developing locally, and only then testing on the mainframe. Check out this site:

[http://www.thefreecountry.com/compilers/cobol.shtml](http://www.thefreecountry.com/compilers/cobol.shtml)

Surprisingly, I find nothing in Synaptic.

Is the URL you need to access available to the outside world, so we could check it out?

Oh, BTW, have you tried the User Agent Switcher extension?

---

### Post by gord on 2006-04-10
[ie4linux](http://www.tatanka.com.br/ies4linux/) seems to be the most stable way of installing IE on linux, i used it the other day and havn't seen a problem. maybe try using that?

also if you use opera that can identify itself to the server as internet explorer if you want it to, so that will bypass the check your server has. but theres a chance it won't display/work right as most websites that block other browsers do so because they are too lazy to impliment the w3c standards that browsers are supposed to adhere to, and instead use ie's botched up standards.

---

### Post by Moonbuzz on 2006-04-27
The question here is whether you want a COBOL compiler for Linux, or whether you're trying to login to your mainframe.

If you're interested in a COBOL compiler, [TinyLinux]("http://tinylinux.org") is the best (free) option out there. For logging to your mainframe, I would suggest inquiring on a different method, assuming their site is IE only. It's worth checking whether you can telnet or have a similar terminal access. You'll be able to code and compile your files without needing the web interface.

---

