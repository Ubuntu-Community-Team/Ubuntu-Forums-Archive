---
title: "ow to change default DVD program in hardy?!"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Afkpuz on 2008-04-26
Hello.  In gutsy, it used to be easy to change your default dvd programs.  System>Preferences>Removable Drives and media.  However, Hardy no longer has this option and as we all know, totem is a worthless dvd played that can't even play dvds.  So, where/how can I change my player to VLC?  I know the command that I would paste into the gutsy section, but where has that field gone?  Thanks

---

### Post by mc4man on 2008-04-26
there have been several ways since beta, atm you'll probably be good with this method
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)   about 1/2 way down. When it comes to replacing wxvlc %F I'd just use vlc %m, personally i think it's a mistake to have vlc default to deinterlacing, the rest, ie. open with fullscreen, volume can be permanently set in preferences if desired, and deinterlacing can be enabled when needed at runtime

edit : can only vouch for method linked in post #3

---

### Post by bluehue on 2008-04-26
This is the method I just used: [http://ubuntuforums.org/showpost.php?p=4580595&postcount=8](http://ubuntuforums.org/showpost.php?p=4580595&postcount=8)

Worked like a charm. All dvds now autoplay with vlc. :)

---

### Post by mc4man on 2008-04-26
> This is the method I just used
That's what i used back in beta and while i haven't tried the above posted method I suggested it because it looks ok and seems somewhat simpler. (other than the vout-filter silliness)

Edit @ bluehue - glad it worked for you - I've had no issues with that method - just watch out for vlc update (not very likely till possibly 9.0)

---

### Post by bluehue on 2008-04-26
> **mc4man said:**
> That's what i used back in beta and while i haven't tried the above posted method I suggested it because it looks ok and seems somewhat simpler. (other than the vout-filter silliness)
I didn't realize you're the same person that suggested the fix in the link I posted :) As mentioned, there are many ways of fixing the issue, and I figured you're method would work despite it being for beta releases (and it did). But yeah, the OP should follow the link you posted, as it refers to a more simpler solution.

---

