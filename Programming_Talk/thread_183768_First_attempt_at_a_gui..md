---
title: "First attempt at a gui."
date: 2006-05-28
forum: Programming Talk
---

### Post by Engnome on 2006-05-28
I've made a few perl cli programs and now I'd like to have a go at some gui programming. I've stumbled upon glade wich I must say is a really nice app. After a hole day googling around for guides/tutorial/examples (havent found that much though.](*,) ) Ive found how to do it (in theory) The problem is that there seems to be three ways to generate perl code with glade:

1: choose perl when saving but I dont have that option for some reason. (maybe they have taken that away as 3 seems to be the preferred way.)

2: Use perl2gtk to generate perl code from the xml file. When trying to use this I get errors :( attached the log file. 

3 Dont generate perl gui code but instead call the xml file from the perl script.

I'd like to get 1 or 2 working as I want to learn how perl gtk gui stuff works "behind the scenes" I cant read that xml file. 

Hopefully I have been clear explaining what Im trying to achieve, but feel free suggesting other ways or ide's. Maybe gtk isn't the best? It seems kinda nice though.

I'll be very happy/grateful with ANY input here, saw a similar thread (pretty old though) with zero replies :(

---

### Post by psychicdragon on 2006-05-29
The prefered way to make use of Glade is to use libglade, ie. load the widgets directly from the XML file. Take a look at this page from the gtk2-perl documentation: [Gtk2::GladeXML]("http://gtk2-perl.sourceforge.net/doc/pod/Gtk2/GladeXML.html")

After the widgets are loaded from the Glade file, you can still modify, delete and add new widgets.

---

### Post by Engnome on 2006-05-29
[QUOTE=psychicdragon]The prefered way to make use of Glade is to use libglade, ie. load the widgets directly from the XML file.[/URL]
[/QUOTE]

No? well I guess I'll do it the hard way then :???: Found a great tutorial for it.
That way I'll really learn it :D.  And I wont be like the ppl in my class that insisted on using wysiwug html editors and the when we were supposed to add php they were like wtf? we have to MANUALLY change the code?

btw did you read my post or did you come to the glade part and then just posted about Glade::XML ?Im gonna check it out later but wanna learn the basics first. Therefore I wanted some example perl code of what my gui would look like.

---

### Post by psychicdragon on 2006-05-29
I read your entire post. :rolleyes: 

I think it is a good idea to try creating the UI from scratch if you've never used Gtk+ before. Checking the class listing repeatedly is probably the best way to learn about all the widgets and their methods. 

Once you think you've got the hang of it though, there's really no point in not using Glade IMO. It saves you time, and your keeps your code from getting cluttered.

Good luck.

---

### Post by Engnome on 2006-05-29
OK thanks alot for the comments psychicdragon. :KS 

I've been sitting all day and got some basic stuff working. I am creating one of my favorite learn-yourself-app, the guess what number I'm thinking on program (80% done) Its surprisingly simple when you really get into it, why have I waited so long with gui apps? Going to move onto glade and the XML method later.

---

