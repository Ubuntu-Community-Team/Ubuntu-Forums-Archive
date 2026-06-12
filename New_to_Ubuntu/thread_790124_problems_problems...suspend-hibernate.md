---
title: "problems problems...suspend-hibernate"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by lunaluna on 2008-05-11
suspend-hibernate don't wok although the procedure starts i end up with the screensaver(?)(it used to work,dont know what happened)
i really need those 2 to work...

and the panels it takes some time to "refresh" and firefox sometimes doesn't appear on the panel(minimize) but i can see the space from it there...

---

### Post by kestrel1 on 2008-05-11
What version of Ubuntu are you using?

---

### Post by lunaluna on 2008-05-11
> **kestrel1 said:**
> What version of Ubuntu are you using?

8.04 heron

---

### Post by lunaluna on 2008-05-11
bump

---

### Post by Joeb454 on 2008-05-11
No need to bump that soon :) As a general rule in the Forums - bump **at most** once every 24 hours.

Anyway, that said, you need an equal amount of Swap as your RAM, so if you have 2GB RAM, you will need 2GB Swap to suspend.

Hibernate I'm not so sure, though I do know that Suspend/Hibernate support in linux is still a little...poor ;) Though I hear there are improvements in some of the newer kernels.

---

### Post by lunaluna on 2008-05-11
in the start it worked for me without problems but not now...

---

### Post by kestrel1 on 2008-05-11
What Graphics Card do you have? If you have an Nvidia card I have heard that the restricted drivers can cause problems. I have an Nvidia card, with the restricted drivers running & when I tried to hibernate the system didn't, it just shutdown & had problems restarting. I don't tend to use hibernate, I was just testing it.

---

### Post by lunaluna on 2008-05-11
> **kestrel1 said:**
> What Graphics Card do you have? If you have an Nvidia card I have heard that the restricted drivers can cause problems. I have an Nvidia card, with the restricted drivers running & when I tried to hibernate the system didn't, it just shutdown & had problems restarting. I don't tend to use hibernate, I was just testing it.

nope its ati...

---

### Post by kestrel1 on 2008-05-11
OK, that's that theory out of the window then. :lolflag:
Have you installed any updates since it was working or changed anything on the system?

---

### Post by lunaluna on 2008-05-11
> **kestrel1 said:**
> OK, that's that theory out of the window then. :lolflag:
Have you installed any updates since it was working or changed anything on the system?

i havent really made any significant changes-unless desktop effects is one..-so i guess it could be...
tried it without them and although it showed somekind of error during the process it did it...

---

### Post by kestrel1 on 2008-05-11
So removing the desktop effects helped? but you still get an error.
What is the error message?

---

### Post by lunaluna on 2008-05-11
> **kestrel1 said:**
> So removing the desktop effects helped? but you still get an error.
What is the error message?

the "error" screen was really quick but from what i remember i saw 
...fglrx:KCL_enable_pat. ERROR ... already configured..(from the third-last line)
i thought this was the important one...

---

### Post by ninjashoes on 2008-05-12
When I first upgraded at first I would get the blinking black sceen of death then my monitor wouldnt turn on. I got those two problems fixed but theres one more thing thats bugging me when I resume from suspend I lose my internet connection. I tried all the fixes on here and with google that I could but I can't get it working yet.

---

### Post by dfour on 2008-05-12
suspend/hibernate has never worked for me for ubuntu.  Doesn't matter if it's on any one of my 4 different desktops or laptops I use.

---

