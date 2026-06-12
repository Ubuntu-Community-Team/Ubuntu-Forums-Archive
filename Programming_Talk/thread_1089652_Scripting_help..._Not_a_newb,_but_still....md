---
title: "Scripting help...? Not a newb, but still..."
date: 2009-03-07
forum: Programming Talk
---

### Post by jwinchester1 on 2009-03-07
Hey all,

 I've mostly browsed, finding all I need in the forums, but, inevitably, I have a question (hopefully) can help me out with. I'm runnin 8.04 on two machines. Laptop - client and Server. I FINALLY figured out X forwarding (though only gn-apps work??), with Nautilus and gnome-panel, cool so far...

 So, my question is: I have NO experience w/ scripts, even tho I know how *necessary* they are sometimes. I know to make them executable, etc. Just not... the syntax?

 I'm trying to first login to my server:

```
ssh -X jamesw@localhost
```

THEN - anyway to enter pword automatically? So, I'm not prompted each time? My current 'script' ssh's in, but prompts for authentication - any way to do this automatically?

Enter ```
xinit
```

Third, and forth (sorry :( ) is getting $james: nautilus to run (showing errors if any) and gnome-panel (ditto).

There might more programs I want load auto- So, could someone help? Figure it's easy (besides the possible pword thing), just couldn't figure out how to pause. SSH - Pword - nautius - g-p, etc.

Any suggestions? Thanks for the help!

Jwinchester1

---

### Post by jwinchester1 on 2009-03-09
Bump.

Somebody? I get it to the pword prompt in SSH, then have to enter THAT manually - and everything else :(

I've tried $xinit | sudo nautilus

but it quickly asked for pword then ran the xinit script, ignoring nautilus!

What do I do??

Thx all,

J

---

### Post by jwinchester1 on 2009-03-09
Wow. Reading up, I didn't realize now *deep* scripting can get. I always thought it was basically just LIKE the command line - su and u get a password prompt (unless editing the sudoers file, which I'm not too willing).

But once I get the hang of it... oh yeah! And, if I'm not mistaken cron can run the scripts too - for maintenance, damage, control ;), etc

So... I guess if you'll just 'teach this man to fish...' (trite, I know) and point me @ some good reference material for scripting. Just a bash tutorial right?

Oh... one more thing :) I finally got my n800 to tunnel into my server - w/ X forwarding everything works great so far - and w/ 32gigs of space, u CAN'T go wrong :P

Thx all,

Nd

---

### Post by albandy on 2009-03-09
you can do autologin with ssh using public and private keys.
See this guide:

[http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)

---

### Post by escapee on 2009-03-09
I'm not much help to your auto-login script (for that I'd have to recommend using keys instead of passwords as albandy has), but once you're logged in have you tried initially launching "gnome-session"?  It'll generate an entire session of gnome for you, giving gnome-panels and Nautilus.

---

