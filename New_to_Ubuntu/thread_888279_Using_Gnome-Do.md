---
title: "Using Gnome-Do"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by ingrid_ozikem on 2008-08-13
This looks like a great program but I can't understand its full functionality.

1. What are the possible operations one can do to an object such as a file? Can I define new operations, say Open with Mathematica?

2. Email -- if I type in an email address [email]etr@sds.com[/email] that is in my Thunderbird contact list, it brings up 'Email' operation but pressing return opens up Evolution (which I don't use).. how do I use Thunderbird with Gnome-Do? I don't see any plugins..

3. It find some files really quick but some files that exist, it doesn't find at all.. is this related to having Tracker on? Does Gnome-Do use that Tracker software?

Any other general help on Gnome-Do would be very helpful! I can't seem to do anything and all the websites talking about it are very vague..
my main question is how one defines new operations.

---

### Post by S.A.A on 2008-08-13
i think you need a plugin for a new operation like you said, and for email i suggest you make your thunderbird is the default email client and disable evolution plugin in GnomeDo.

finally, i think Gnome Do has it's own tracker "see the plugins".

---

### Post by ingrid_ozikem on 2008-08-13
Making Thunderbird the default client through System -> Pref. -> Pref. applications worked beautifully! Thanks a lot for that!

Will check out the tracker plugin.. it does say it has a 'locate' command.

---

### Post by appi2012 on 2008-08-13
locate works really well.

---

### Post by wd5gnr on 2008-08-14
Is anyone using this with KDE? It looks great, but many launches (e.g., anything with Google or the ssh plugin) give me odd xdg-open errors about "unexpected option". I do have xdg-open installed. But it looks like Do is passing it options (like -e or --lookup) in some way that xdg-open is reading them instead of the launched program.

Any ideas?

Update: Well I modified xdg-open to log the command line it is getting. Turns out define and ssh use gnome-specific programs I don't have. Wish the actions on Do were configurable. That may be the whole problem. Could write wrappers I guess.

---

