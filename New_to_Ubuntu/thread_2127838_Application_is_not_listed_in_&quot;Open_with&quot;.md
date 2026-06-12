---
title: "Application is not listed in &quot;Open with&quot;, how to add executable?"
date: 2013-03-21
forum: New to Ubuntu
---

### Post by kramer65 on 2013-03-21
Hello,

I've got some Python scripts which I want to open with Spyder (my favorite python IDE). The problem is that when I click "open with" or properties > "open with", I don't see Spyder listed as being installed. I do know where the executable is (/usr/bin/spyder) but I also don't see a way to add an executable.

Does anybody know how I can manage to open .py files in Spyder by double-clicking them?

---

### Post by vasa1 on 2014-03-14
Bumping before this is buried ;)

Would the answer be to create a .desktop file with *Exec=/usr/bin/spyder*?

Or, more generally, is a .desktop file essential for any application to be available as an option in "Open with ..."?

---

### Post by mc4man on 2014-03-14
> **vasa1 said:**
> 
Or, more generally, is a .desktop file essential for any application to be available as an option in "Open with ..."?

At least in Gnome it is the only way, whether gnome2 or 3. In gnome3 one would also want to add a <space> %<letter> to end of the Exec= line, U u F f are valid choices.

---

### Post by vasa1 on 2014-03-14
> **mc4man said:**
> At least in Gnome it is the only way, whether gnome2 or 3. In gnome3 one would also want to add a <space> %<letter> to end of the Exec= line, U u F f are valid choices.
True! I've mostly seen %U.

---

