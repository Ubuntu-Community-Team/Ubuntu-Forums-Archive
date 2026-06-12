---
title: "gtk+ or qt"
date: 2008-01-26
forum: Programming Talk
---

### Post by cjnkns on 2008-01-26
I am a bit new to this so if I say something stupid ---- sorry.

I am trying to get started learning programming under linux. 
I know a bit of Ruby so figured that would be a good place to start.
So I started going through the Ruby/GTK+ tutorial.

But, I cam across QtRuby also. So from what I understand Gnome is developed using GTK+ and Kde developed using QT right?

Is one more superior than the other? Or is this question similar to the old Gnome vs Kde questions people ask.

I have read different threads that say gtk+ isn't as well maintained or not implemented as well as qt.. .anyone here have any thoughts?

---

### Post by runemaste644 on 2008-01-26
I prefer qt because it has a handy GUI. May i suggest adding a poll to your thread and see what others think?

---

### Post by LaRoza on 2008-01-26
> **runemaste644 said:**
> I prefer qt because it has a handy GUI. May i suggest adding a poll to your thread and see what others think?

Use whatever you want.

> 
Is one more superior than the other? Or is this question similar to the old Gnome vs Kde questions people ask.

No. And Yes.

---

### Post by Auria on 2008-01-26
Gnome (and XFCE i think?): gtk
KDE: Qt

---

### Post by lnostdal on 2008-01-26
I use GTK+ for development because, well, I know GTK+.

I use both GTK+ and QT applications, even though I have a Gnome desktop. It doesn't matter IMHO -- I pick the best application regardless of what GUI toolkit/library it uses. I think most people do this.

Try both and decide yourself.

---

### Post by Majorix on 2008-01-26
Well I would go with gtk+ because you have to pay to qt if you want to go commercial. I don't like limitations. And since you are asking for what we use for Linux (and not cross-platform) I can safely recommend gtk+.

---

### Post by maddog39 on 2008-01-26
> **Majorix said:**
> Well I would go with gtk+ because you have to pay to qt if you want to go commercial. I don't like limitations. And since you are asking for what we use for Linux (and not cross-platform) I can safely recommend gtk+.
Although they are both equally just as crossplatform, however Qt is easier to cross compile and get working than Gtk is. I have to say though, I mostly use Gtk but I bought C++ Programming with Qt4 and I have to say that Qt has some very reboust APIs that are very helpful with alot of things. So just think about what your going to do with your application and compare the pros and cons.

---

### Post by LaRoza on 2008-01-26
I would also like the point out that wxWidgets is very good also.

---

### Post by MicahCarrick on 2008-01-26
Neither is "superior" to the other. They have differences that may be important to you. I'm a GTK+ fan myself.

Being a new programmer, read up a bit on Qt, GTK+ and wxWidgets and think about what you want to achieve. If they all seem equally suited for your needs--just pick one. You could always switch later if you find it limiting. For just about every feature that people will say makes one advantageous over the others there is likely a trade off elsewhere.

I have only done very little things with Qt myself--primarily because I prefer GNOME. I use GTK+ in C, Python, and Ruby for both Linux and Windows applications. So I could talk all day about how great GTK+ is, but somebody else could come along do the same about Qt, wxWidgets, Java, etc.

---

### Post by EXCiD3 on 2008-01-26
I have found that Qt is my favorite. It has much more than just a GUI library and therefore my applications become cross compatible extermely easily.

---

### Post by Majorix on 2008-01-26
> **maddog39 said:**
> Although they are both equally just as crossplatform, however Qt is easier to cross compile and get working than Gtk is. I have to say though, I mostly use Gtk but I bought C++ Programming with Qt4 and I have to say that Qt has some very reboust APIs that are very helpful with alot of things. So just think about what your going to do with your application and compare the pros and cons.

It's not totally about being cross-platform with this. I am talking about licensing issues, and if you ask me, a license is one of the sh!ttiest thing that happened to the computers; and therefore I would say "Stay away from QT as long as you can.".

---

### Post by LaRoza on 2008-01-26
> **Majorix said:**
> It's not totally about being cross-platform with this. I am talking about licensing issues, and if you ask me, a license is one of the sh!ttiest thing that happened to the computers; and therefore I would say "Stay away from QT as long as you can.".
> 
Qt Open Source Edition Licensing

The Qt Open Source Edition is available to the Open Source community under Trolltech's Dual Licensing Model. The Open Source Edition of Qt and Qt Jambi is freely available for the development of Open Source software governed by the GNU General Public License (GPL). If you want to do proprietary, commercial development you need to purchase a Qt Commercial Edition.


QT has several licenses. If you make Open Source Software, you can use the Open Source Edition for free in your programs.

---

### Post by Majorix on 2008-01-26
Sadly, for us software devs, open-source is mainly a hobby, except for a few really dedicated and nice people. I, for one; as a software engineering student, want to make money out of programming, and as such I have to think of these details.

QT is crossed out in my list for now, until maybe one day they give up on their licensing policies :)

---

### Post by LaRoza on 2008-01-26
> **Majorix said:**
> Sadly, for us software devs, open-source is mainly a hobby, except for a few really dedicated and nice people. I, for one; as a software engineering student, want to make money out of programming, and as such I have to think of these details.

QT is crossed out in my list for now, until maybe one day they give up on their licensing policies :)

Hobbies are fun :)

As a student, and future employee, I bet you won't be making software that is sold. It will likely be used for internal use.

I don't use QT either, but not because of the license.

---

### Post by Majorix on 2008-01-26
> **LaRoza said:**
> Hobbies are fun :)

As a student, and future employee, I bet you won't be making software that is sold. It will likely be used for internal use.

I don't use QT either, but not because of the license.

Internal use for what? Commercial needs... You have to pay them (even if that will be your boss paying, you yourself can become the boss one day too) for that kind of use. And your boss maybe won't want to pay when there are free (as in "comes with no license" and costs no money) toolkits.

---

### Post by LaRoza on 2008-01-26
> **Majorix said:**
> Internal use for what? Commercial needs... You have to pay them (even if that will be your boss paying, you yourself can become the boss one day too) for that kind of use. And your boss maybe won't want to pay when there are free (as in "comes with no license" and costs no money) toolkits.

Most programmers write software for companies. True, it isn't open source, but it isn't being sold either.

You'll find out when you get there :)

---

### Post by bruce89 on 2008-01-27
I am a bit suspcious of the fact that QT is more than just a widget toolkit. It's as if you are locked into the whole QSomething world.

---

### Post by LaRoza on 2008-01-27
> **bruce89 said:**
> I am a bit suspcious of the fact that QT is more than just a widget toolkit. It's as if you are locked into the whole QSomething world.

It works and people like it.

---

### Post by bruce89 on 2008-01-27
> **LaRoza said:**
> It works and people like it.

Fair enough.

---

### Post by LaRoza on 2008-01-27
> **bruce89 said:**
> Fair enough.

I am not a QT fan myself either, but it is just an option, and free to use and distribute.

---

### Post by bruce89 on 2008-01-27
I now regets saying anything now, I've only minimal GTK+ experience.

I suppose if you like everything (databases, UI, XML) to be done with a single API, QT's a good choice. I just think it's a bit restrictive (licence wise), and a bit lock-iny.

---

### Post by LaRoza on 2008-01-27
> **bruce89 said:**
> I now regets saying anything now, I've only minimal GTK+ experience.

I suppose if you like everything (databases, UI, XML) to be done with a single API, QT's a good choice. I just think it's a bit restrictive (licence wise), and a bit lock-iny.

(Don't be intimidated that I am a mod, I mark it when I am modding with red text)

I don't like QT for that either. Technically, it is a good toolkit, but not idealistically. I prefer completely free when I can.

I just didn't want a flame war to develop. I am sure no one here wanted that either.

---

