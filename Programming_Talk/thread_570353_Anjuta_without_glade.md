---
title: "Anjuta without glade?"
date: 2007-10-08
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2007-10-08
Hello I want to make a C++ GTK program in Anjuta without using glade. Is this possible in Anjuta? If yes, how to I start?

---

### Post by Yz85Racer on 2007-10-08
Use SciTE.

---

### Post by ryno519 on 2007-10-08
> **SledgeHammer_999 said:**
> Hello I want to make a C++ GTK program in Anjuta without using glade. Is this possible in Anjuta? If yes, how to I start?

Make a generic C++ project and just link to the gtkmm library.

[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03.html)

---

### Post by SledgeHammer_999 on 2007-10-08
> **ryno519 said:**
> Make a generic C++ project and just link to the gtkmm library.

[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03.html)

thanks. Well, I was thinking about that but I wanted to confirm it.

---

### Post by SledgeHammer_999 on 2007-10-08
One more question: How do I tell Anjuta where to look for the "gtkmm.h" header?

---

### Post by ryno519 on 2007-10-08
> **SledgeHammer_999 said:**
> One more question: How do I tell Anjuta where to look for the "gtkmm.h" header?

I've always had trouble getting Anjuta to do that. I always end up editing the configuration files by hand.

---

### Post by SledgeHammer_999 on 2007-10-08
ok. Well I know that my "gtkmm.h" is here "/usr/include/gtkmm-2.4". Can you tell what changes should I do and in what files?(as you understand I am not a pro)

thanks you.

---

### Post by slavik on 2007-10-08
change the include line for the project.

---

### Post by SledgeHammer_999 on 2007-10-09
well I put this in the include line "/usr/include/gtkmm-2.4" but when trying to build the project the compiler cannot find <gtkmm.h> although it is in "/usr/include/gtkmm-2.4/gtkmm.h". Is my include line right?

---

### Post by SledgeHammer_999 on 2007-10-09
FINALLY I FOUND A SOLUTION.
(this was hard to figure out)
I'll post a howto as soon as I can.

---

