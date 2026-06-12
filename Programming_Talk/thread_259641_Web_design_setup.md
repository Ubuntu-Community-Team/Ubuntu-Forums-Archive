---
title: "Web design setup"
date: 2006-09-17
forum: Programming Talk
---

### Post by music_man on 2006-09-17
Hi

Just thought I'd share how I do web design on Ubuntu. Perhaps people could provide some better alternatives.

For a localhost server I use XAMPP (Lampp) running. This provides me with PHP and MYSQL.

For graphics design I use Inkscape and GIMP.

For coding I use Quanta Plus.

---

### Post by tminuszero on 2006-09-17
Why do you use XAMPP instead of the regular apache/php/perl/mysql packages? Just wondering. Is it the control panel?

---

### Post by music_man on 2006-09-17
It is easy to startup. I just open terminal and type in:

/opt/lampp/lampp start

and it goes.

---

### Post by tminuszero on 2006-09-18
I don't understand - why don't you just leave it running, and only restart it when necessary? I have a development server with multiple virtualhosts, but on my desktop I have apache2 running with php/mysql, all standard packages. I've never had to start them, as they start during boot.

Do you find it easier to manage several virtualhosts with XAMPP?

---

### Post by X.Cyclop on 2006-09-18
If you install AMP (Apache + MySQL + PHP/Perl/Python) from Ubuntu (like me) repos, they will run at startup as services.

To make it with Xampp:
[GNOME] System > Preferences > Sessions > Startup Programs [tab] > Add and type **/opt/lampp/lampp start**.

I have Xampp just for learning some bash scripts.:biggrin: 

I use gedit, sometimes nano.:biggrin: 

:wink:

---

