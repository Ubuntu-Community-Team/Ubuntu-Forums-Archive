---
title: "Platform programming basics"
date: 2006-06-06
forum: Programming Talk
---

### Post by Csabo on 2006-06-06
Hi all,

I'd like to understand the Linux platform a bit better. As a newbie, it's still not clear to me what I would be writing "programs for". Here's what I'm thinking: I want to write a new piece of software. Let's say it has a simple GUI, it can read an image as the input, process it and output something into a new textfile. Now, am I writing this for Linux, or Gnome, or Ubuntu, or Dapper? That is, will my software still work on Breezy? Will it work on Kubuntu or Xubuntu? Will it work on another distro?

Or is that determined by the way it is written?

This is what I would like to understand. I hope someone can clear it up for me a bit, and point me in the right direction for some documentation on Linux/Ubuntu programming best practices.

(An off-topic note: from my experience with other forums, I think it's not very useful to have a sticky topic with 200~some replies. Who is going to read that? It would be really great if the information from those two topics could be converted into a table, ie. what IDEs are available, where, pros/cons, etc.)

---

### Post by hod139 on 2006-06-06
Sounds like you might be interested in [freedesktop]("http://www.freedesktop.org/wiki/") if interoperability is a concern.

---

### Post by Csabo on 2006-06-07
Thanks for the link hod139. I read through it, but it didn't answer my questions. There's tons of links on the software page, but I don't know what those are or why I would need them.

I don't actually know if interoperability is a concern. Is it normally? How does this work? Do I have to pick Gnome or KDE or XFCE when I write software? I'm sure there must be lots of people on this forum who actually wrote software for Linux/Ubuntu, could someone explain this or point me in the right direction?

---

### Post by simplyw00x on 2006-06-07
You're programming for a toolkit. You have to pick one of those (although you can support multiple GUIs). Gnome's is GTK, KDE's is Qt, other DEs have different toolkits as well. Some are platform-agnostic like wxWidgets. GTK programs will run on KDE (if you install the libs) and Qt apps will run on Gnome (again, if you install the libs). GTK apps will also run on windows if you have the Windows GTK port installed.

I hope this clears things up a bit.

---

### Post by vayde on 2006-06-07
What is the relationship between the libs and the toolkit itself?  

For example, I believe there were apps loaded on my system that used Tk, but I still had to install Perl/Tk before I was able to write my own.

---

### Post by Csabo on 2006-06-07
simplyw00x, thanks for explaining that. Now I get it. I'm going to guess that it's common for most people to have both GTK and Qt installed, right? In that case, it's probably just user preference as to which one to use?

I looked at wxWidgets, and the fact that it works across so many platforms sounds really great. I'm wondering why wouldn't everyone use that? Can you maybe go into details a bit deeper on what are the pros/cons or impact of choosing a toolkit?

---

### Post by vayde on 2006-06-07
My personal experience:

GTK: Very pretty, good integration with gnome (duh)  very poorly documented, and in the case of the Perl bindings, rather verbose.

Qt: I never seriously looked into it, Trolltech's policies on using the toolkit seem like shades of microsoft.

Tk (Perl/Tk): Completely OO toolkit, very easy to write, there's even a book written on it.  Doesn't seem to support anitialiased fonts very well though.  (fonts are pretty jagged)  If anyone knows how to fix this I'll be forever grateful.

WxWidgets: Didn't look too closely, digging through the above 3 overwhelmed me at the time.

---

### Post by simplyw00x on 2006-06-07
I'd second vayde's impressions except:

GTK: Looks awesome, and is actually pretty easy, especially with glade

Qt: Looks pretty dire on GNOME. No stable implementation on windows.

Tk: No experience, no idea.

wxWidgets: Looks very good and works on windows as well.

I can personally reccommend a glade/GTK/python combo; cross-platform, fast, easy, doesn't need compiling.

---

### Post by vayde on 2006-06-07
[QUOTE=simplyw00x]GTK: Looks awesome, and is actually pretty easy, especially with glade
[/QUOTE]

Glade huh?  Ill look into it.  Thanks:D  (Though I tend to be a stone axe kind of guy: vim and chisel it out by hand)

---

### Post by red_Marvin on 2006-06-07
Just to hijack the thread a little: Does fluxbox use a special toolkit? Which?

---

### Post by LordHunter317 on 2006-06-07
[QUOTE=simplyw00x]I'd second vayde's impressions except:

GTK: Looks awesome, and is actually pretty easy, especially with glade[/quote]Except GLADE has tons of limitations you'll run up against.  In pratice, GLADE is less of an attraction in the end then it seems.  Go check to see how many GNOME apps actually use GLADE.  

> Qt: Looks pretty dire on GNOME.Sure, because GNOME doesn't use it.  THough you can run Qt apps, no problem. 

>  No stable implementation on windows.Uhh, no.  Qt has had a stable, functional Windows implementation before GTK+ did.  It wasn't free for a very long time, but that's another story.

---

### Post by Kimm on 2006-06-07
> 
GTK: Looks awesome, and is actually pretty easy, especially with glade

Qt: Looks pretty dire on GNOME. No stable implementation on windows.


I'll have to agree that GTK looks awesome if using the right theme (Ubuntulooks is great btw).

Qt has alot going for it. I never realy liked Qt3 but I find Qt4 to be a very reliable framework for GUI programming.

Note:
GTK can look just as pretty in KDE as it does in Gnome, same goes with Qt, just the other way around (they need theme managers however).
The thing is though, that they will look out of place!

I see Qt as a good choise for GUI programming, unless the target is specificly Gnome or XFCE. When KDE4 (uses Qt4) gets released, I think KDE will gain more ground than it allredy has (I know I'll switch), and then Qt skills are good to have :)

---

### Post by vayde on 2006-06-07
[QUOTE=Kimm]I see Qt as a good choise for GUI programming, unless the target is specificly Gnome or XFCE. When KDE4 (uses Qt4) gets released, I think KDE will gain more ground than it allredy has (I know I'll switch), and then Qt skills are good to have :)[/QUOTE]

You don't find the 'Do what you will with it, but if you want to be paid for what you create, cough up $3,000+' stance troublesome? No offense intended, Im curious as to your thoughts.

Writing software for free in your free time is great, and admirable, but sometimes it's nice to hone skills you can be paid to exercise.  (or am I missing something terribly fundamental about Qt's licensing?)

---

### Post by Kimm on 2006-06-08
vayde, Yes. If you want to be able to sell your work then GTK IS better than Qt.

However. I still wouldnt recommend GTK if the application is to be used in windows. There are themes that make it blend in somewhat, but it still looks somewhat out of place.

If Qt is not an option, I recommend wxWidgets.

---

### Post by simplyw00x on 2006-06-08
Gaim looks fine in windows, and it's GTK.

---

### Post by vayde on 2006-06-08
[QUOTE=Kimm]vayde, Yes. If you want to be able to sell your work then GTK IS better than Qt.

However. I still wouldnt recommend GTK if the application is to be used in windows. There are themes that make it blend in somewhat, but it still looks somewhat out of place.

If Qt is not an option, I recommend wxWidgets.[/QUOTE]

Fair enough.  I'm pretty happy with Tk.  It works fine in windows too, quick and easy to write. 

As a test, I wrote the same main window for an appliction in GTK and in Tk.  The GTK version was probably 30% more code to write, though it was pretty when done.

---

### Post by asimon on 2006-06-08
[QUOTE=red_Marvin]Just to hijack the thread a little: Does fluxbox use a special toolkit? Which?[/QUOTE]
No, Fluxbox uses the X11 library.

---

### Post by dpm on 2006-06-09
[quote=LordHunter317]Except GLADE has tons of limitations you'll run up against.  In pratice, GLADE is less of an attraction in the end then it seems. [/quote]

Which limitations has glade got?

---

