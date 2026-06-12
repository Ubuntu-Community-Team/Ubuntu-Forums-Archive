---
title: "libsensors don't registered?"
date: 2008-11-11
forum: Programming Talk
---

### Post by MeduZa on 2008-11-11
Hello, I'm working on a project that need to access libsensors, I have the library installed (libsesors headers too) my program compiles if I use -lsensors in the command line.

[COLOR="Red"]Now the problem:[/COLOR]
I'm working with Anjuta, I use several libraries in my project, including libsensors, when I try to add the libraries, the Anjuta way:
project > properties > packages > add package > [LIST]
all the libraries appear in the list, except libsensors, I have been searching on line for a solution and found nothing
The library is there because when I use with command line -lsensors everything goes well, but I cannot find it in the Anjuta library list, is it not registered in the system? How can I fix it? because I'd like to compile without the need to add -lsensor by myself.
I have the same problem with -ldl (linking library but in this case I don't know the library name) but i think it has the same problem the other one has (not in the list)
Thanks.

---

### Post by MeduZa on 2008-11-13
no one?

---

### Post by MeduZa on 2008-12-01
up
-.-

---

### Post by Zugzwang on 2008-12-01
Never used Ajunta, but Googling yielded: [http://anjuta.sourceforge.net/documentations/subpage/documents/C/anjuta-build-tutorial/c808.html]("http://anjuta.sourceforge.net/documentations/subpage/documents/C/anjuta-build-tutorial/c808.html"), see 4.1.3

Summary: If your library isn't in the list, then you have to add it manually!

---

### Post by MeduZa on 2008-12-02
> **Zugzwang said:**
> Never used Ajunta, but Googling yielded: [http://anjuta.sourceforge.net/documentations/subpage/documents/C/anjuta-build-tutorial/c808.html]("http://anjuta.sourceforge.net/documentations/subpage/documents/C/anjuta-build-tutorial/c808.html"), see 4.1.3

Summary: If your library isn't in the list, then you have to add it manually!

thanks men I will read that!!

---

### Post by mdurham on 2008-12-02
A simple way of reading the sensors is:
> system("sensors > afile.txt");
and parse afile.txt
At least that what I did.
Cheers, Mike

---

### Post by MeduZa on 2008-12-05
> **mdurham said:**
> A simple way of reading the sensors is:

and parse afile.txt
At least that what I did.
Cheers, Mike

I'm working on c++, that let me access libraries to get information on the system.

I don't like to parce txts xD I like to access libraries like the real programs do.

Like I see, libsensors is not a dpk-config librarie and that why anjuta can't see that library

---

