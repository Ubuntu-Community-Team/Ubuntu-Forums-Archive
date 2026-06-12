---
title: "Partial open-source - worth it?"
date: 2008-05-30
forum: Programming Talk
---

### Post by Vadi on 2008-05-30
Hi all,

One of the programs I'm developing is text-only right now, and I'm looking to make it a GUI to manage it easier. 

Now, the program itself isn't open-source, for several reasons a) Back when I started on it, I really didn't know that much / care about opensource, b) in the small field that it's used, it has became extremely popular, and while there are free / open-source programs available, they fall behind mine quite a bit (poorly, if at all, supported, maintained, and worse program logic, with the last two points being *very* important), and c) I sell it, and while it's just a hobby for me, it did pay for my serval laptop and a couple of courses at my uni.

I did have the idea of making the gui for it open-source though. Like, why not? The most important of the program is it's logic, maintenance, and support, which won't be affected by this. The only prob is that due to the design, the gui will need to be built-in to the program, so at best I can create separate source files and distribute those, while making some functions that are used inside the system "blank". 

Is this worth it though? And what license can I go by - I don't think gpl would allow this "mix".

---

### Post by pmasiar on 2008-05-31
I think you need professional advice from a good lawyer if you want to make free GUI tightly integrated with proprietary source, release GUI but keep part of sources locked.

What you can do, is to make API to your program, and then use it from your GUI as a library. Distribute library as separate binary-only file, that would be more kosher IMHO.

---

### Post by Vadi on 2008-05-31
Okay, I'll look into that.

---

### Post by winch on 2008-05-31
> **Vadi said:**
> The only prob is that due to the design, the gui will need to be built-in to the program, so at best I can create separate source files and distribute those, while making some functions that are used inside the system "blank".

If nobody can build the source but you what is the point in making it open source?

---

### Post by Vadi on 2008-05-31
They'll be able to, if I manage to split this as a library. Though, yeah, there isn't much point in open-sourcing that I see now.

---

