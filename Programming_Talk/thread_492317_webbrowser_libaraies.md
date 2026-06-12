---
title: "webbrowser libaraies"
date: 2007-07-04
forum: Programming Talk
---

### Post by hockey97 on 2007-07-04
Hi I am trying to make my own web browser and looking for web browser libaraies, ect.

I want or just need the  web control files, so I could get webpages to display.

Does anyone know where I could get some files or libaries that would give me most main functions,

of a web browser?

---

### Post by avik on 2007-07-04
You can use MozEmbed with one of the Gtk APIs to embed the Gecko engine (the engine behind Firefox), though I haven't found any thing related to C on that front.  However, I know [Ruby has it]("http://ruby-gnome2.sourceforge.jp/hiki.cgi?Gtk%3A%3AMozEmbed") and [so does Perl]("http://search.cpan.org/~tsch/Gtk2-MozEmbed-0.06/MozEmbed.pm").

Hope that helps.

---

### Post by hockey97 on 2007-07-04
Well I know C++ and c and python,  I am mostly advanced in c++  I know c++ the most so I am trying to make a web browser but don't want to make the engine, just want to make the user interface.

How do they make the engine?? I  would like to know becsue I am such a geek, I love to know how stuff works behind the scenes.

---

### Post by ankursethi on 2007-07-05
You have two very nice open source engines that you can use.

1. Gecko - used by Mozilla and several others. Written in C++. Almost standards compliant, has lots of plugins etc. and works on 90% of the sites now.

2. KHTML - used by Konqueror and Apple's Safari (it's the one from which WebKit has been forked). Fully standards compliant and, overall, nicer than Mozilla. Sadly, it doesn't have a browser to go with it that can be used by the average web surfer (Safari is useless and Konqueror is too intimidating). Also written in C++.

I suggest you go with KHTML. You must learn GUI programming under the Qt toolkit. I have no idea about embedding KHTML in your app, but a post to the KDE mailing list ought to sort that out. Try to find out how to make a KHTML browser that does NOT depend on the KDELibs, if possible. Otherwise, just go with Gecko. A Google search will help.

---

### Post by ButteBlues on 2007-07-05
Now that WebKit/WebCore (Safari's engine) is open source, go nab that. :)

It is the best rendering engine out there.

---

