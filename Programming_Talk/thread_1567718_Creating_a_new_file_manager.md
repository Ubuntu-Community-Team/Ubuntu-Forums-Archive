---
title: "Creating a new file manager"
date: 2010-09-04
forum: Programming Talk
---

### Post by lunamystry on 2010-09-04
I have an idea for a file manager. I posted it here: [http://lunamsytry.wordpress.com/]("http://lunamsytry.wordpress.com/"). I think it is totally possible. I am currently creating a game as a university project. So I have some knowledge C++.

I would like comments and suggestions and possible problems with creating something like this. 

Thanks

---

### Post by dv3500ea on 2010-09-04
I think this is a really good idea. I am not very good at file management and tend to forget where I put things and which of the various hierarchy structures I am using. I also get into a conundrum of which folder to put my files in when they would be suitable for more than one folder. I think using tags would make life easier.

I am actually working on a tag based file manager: [https://launchpad.net/tagfm]("https://launchpad.net/tagfm").

I am still working out how to use all of the development tools at the moment and haven't yet documented my project (I plan to do this this weekend). Basically, I have a database storing the tag information of files. Instead of the concept on a working directory, I have the two lists of tags; included and excluded tags which are used to filter and search files. I am also making my API usable on any language by using socket programming with HTTP and JSON.

I am a long way off creating a GUI (I am not good at GUI programming), but I have attached the mockup I made when I started the project.

---

### Post by SledgeHammer_999 on 2010-09-04
I think your ideas are really similar to the way Gnome 3 is going. There are 2 particular applications developed there that seek to "revolutionalize" the way file tracking works. Basically they want to monitor and log the user's habits and then present this info in a meaningful way. I can't remember now what the names of the applications were, but if you search about Gnome 3 I am sure they will come up pretty soon.

---

### Post by dv3500ea on 2010-09-04
> **SledgeHammer_999 said:**
> I think your ideas are really similar to the way Gnome 3 is going. There are 2 particular applications developed there that seek to "revolutionalize" the way file tracking works. Basically they want to monitor and log the user's habits and then present this info in a meaningful way. I can't remember now what the names of the applications were, but if you search about Gnome 3 I am sure they will come up pretty soon.

I think your thinking of [Zeitgeist]("http://zeitgeist-project.com/").

This provides a history based approach with advanced features like what files you were last using when you were doing some other task. I am thinking of more of a categorisation approach to file management. I might use zeitgeist as an extension to my 'autotag' mechanism at some point in the future.

---

### Post by SledgeHammer_999 on 2010-09-04
Yeap, Zeitgeist.


Although for me Zeitgeist and your approaches are uninteresting. I am used to the way things work now and I know what my filesystem and file-layout looks like. But others might find it useful, especially people who like to throw everything at one place and not care about it later(or organize it).

To the OP. Since you know C++ and since, I assume, you use Gnome don't forget the existance of [Gtkmm](www.gtkmm.org).

---

### Post by lunamystry on 2010-09-04
> **SledgeHammer_999 said:**
> Yeap, Zeitgeist.


Although for me Zeitgeist and your approaches are uninteresting. I am used to the way things work now and I know what my filesystem and file-layout looks like. But others might find it useful, especially people who like to throw everything at one place and not care about it later(or organize it).

To the OP. Since you know C++ and since, I assume, you use Gnome don't forget the existance of [Gtkmm](www.gtkmm.org).

I am hoping to also use it on with KDE because I kinda like KDE over gnome and I like Ubuntu over KDE and right now Kubuntu doesn't feel like Ubuntu with KDE. I am hoping one day it will and I will move back to KDE.

edit:
So I was thinking QT4. I saw how Clementine looks on both Kubuntu and Ubuntu. They looked better that gtk apps (which are cross platform). I think apps that use KDE specific things like Amarok and Okular don't look as good but I could just avoid KDE libraries in qt4.

---

### Post by lunamystry on 2010-09-04
> **dv3500ea said:**
> I think this is a really good idea. I am not very good at file management and tend to forget where I put things and which of the various hierarchy structures I am using. I also get into a conundrum of which folder to put my files in when they would be suitable for more than one folder. I think using tags would make life easier.

I am actually working on a tag based file manager: [https://launchpad.net/tagfm]("https://launchpad.net/tagfm").

I am still working out how to use all of the development tools at the moment and haven't yet documented my project (I plan to do this this weekend). Basically, I have a database storing the tag information of files. Instead of the concept on a working directory, I have the two lists of tags; included and excluded tags which are used to filter and search files. I am also making my API usable on any language by using socket programming with HTTP and JSON.

I am a long way off creating a GUI (I am not good at GUI programming), but I have attached the mockup I made when I started the project.

That sounds real cool. I will check it out. I was going to work on this later in the year after all the hectic stuff with vasity were done. I think now I will either help out with your project or find something else.

---

### Post by SledgeHammer_999 on 2010-09-04
> **lunamystry said:**
> I am hoping to also use it on with KDE because I kinda like KDE over gnome and I like Ubuntu over KDE and right now Kubuntu doesn't feel like Ubuntu with KDE. I am hoping one day it will and I will move back to KDE.

edit:
So I was thinking QT4. I saw how Clementine looks on both Kubuntu and Ubuntu. They looked better that gtk apps (which are cross platform). I think apps that use KDE specific things like Amarok and Okular don't look as good but I could just avoid KDE libraries in qt4.

OK. As long as you don't use KDE or GNOME specific API then you app will work great in either of them, no matter if you've written it in Qt or Gtk+.

---

