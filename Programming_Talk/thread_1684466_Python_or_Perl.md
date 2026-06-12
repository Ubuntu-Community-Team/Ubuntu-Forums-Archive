---
title: "Python or Perl?"
date: 2011-02-09
forum: Programming Talk
---

### Post by ~Middle on 2011-02-09
I am considering learning either Python or Perl, but i want to ask a few questions first:
 
What will be best to learn in terms of developinbg software for Ubuntu?
 
Which language is easier? (I think perl)
 
Is Perl/Python visual or only CL?
 
Is there a point learning Perl if i am fluent with Bash?
 
What applications can i use Python/Perl for? (I.e. is one good for x or y only..)
 
Thanks a lot!

---

### Post by llanitedave on 2011-02-09
Most people think Python is easier to learn than Perl.  Python has a GUI packaged with the language, Tkinter, so its not strictly command line if you don't want it to be.  There are other easily available UI packages for it as well. You can use tk with Perl to create GUIs also.

Both languages are very high-level, have tons of libraries, and there's not much that either can't do -- although each seems to have its niche, there's a huge amount of overlap.

Python comes with Ubuntu, and Perl has an Ubuntu-supported version as well.

My preference to recommend would be Python -- simply because I like it, and it is easy to learn and powerful.

Others might feel differently.

---

### Post by cipherboy_loc on 2011-02-09
1) What will be best to lear in terms of developing software for Ubuntu?
It depends on what you want to do. If you want to create a cool new Web server in Perl, go a head. But if you want to develop a GUI in Perl, go dunk you head in Python. ;)  There are a lot more GUI Applications written in Python rather than Perl because Perl was never meant to be a GUI-oriented language.

2) Which language is easier?
Once you learn one language, it is easy to pick up another. If you don't already know a language, I would go for Python, because you end up typing less characters.  ;)

3) Is Perl/Python visual or only CL?
Both of the languages (as pointed out earlier) are both GUI and CL, it just depends on how easy you want it to be. Personally I would write GUIs in Python due to the support for multiple toolkits (GTK, QT, etc). But remember, you need to walk (CLI) before you can fly (GUI).

4) Is there a point of learning Perl if I am fluent with Bash?
Yes, and no. While they each incorporate most of the same elements (Regular Expressions, looping, methods, etc), there are some things that, while you can do in Bash, you can do more easily in Perl.  Most of the things that are hard in Bash are complex things, but you can do anything in just about any language.

5) What applications can I use Python/Perl for? (I.e. is one good for x or y only..)
I cannot name some good examples, but for GUIs I would use Python, for servers and clients I would use Perl, and for the web I would use either Perl or Python.




Cipherboy

---

### Post by juancarlospaco on 2011-02-09
python

*antigravity powah!*

---

### Post by ~Middle on 2011-02-09
Thanks a lot for the responses they have been very useful!

I have a few perl and python scripts, that are just script.pl/,py files, are these ow level, as they are jsut made with a text editor (Like bash) or they the standard way of making programs? I would prefer not to have to install a graphical developers pack for either language, as i like my command line!

After having a look at what some perl scripts can do i am beginning to favour it, but the complications of making GUI's (Which i would rarely do - but would like the possibility to expand to) is a tad off putting.

At the moment, i am pretty 'fluent' in Bash and Pascal, pretty low level i know, but it has given me a good start!

Thanks a lot!

---

### Post by nvteighen on 2011-02-09
> **~Middle said:**
> 
I have a few perl and python scripts, that are just script.pl/,py files, are these ow level, as they are jsut made with a text editor (Like bash) or they the standard way of making programs? I would prefer not to have to install a graphical developers pack for either language, as i like my command line!


You can write them in any text editor of your choice and run them in the Terminal with no problems at all. :)

> 
After having a look at what some perl scripts can do i am beginning to favour it, but the complications of making GUI's (Which i would rarely do - but would like the possibility to expand to) is a tad off putting.


Well, GUIs are hard to write manually. Even simple ones can be a bit frustrating; but it's completely possible. So, most people use some GUI designer to create the layout (usually saved in an XML-based format) and code the logic elsewhere, using the GUI designer's library to load the GUI.

---

### Post by ~Middle on 2011-02-09
So is either perl or pythons GUI designer preferable?

And another odd question, i aspire to become a network pentester, and one thing that i wish to do in the future is learn how to write exploits, would you have any idea which language is more commonly used for this? 

I have seen many perl exploits but few python ones, however my knowledge is rather limited there...

Thanks a lot!

---

### Post by MadCow108 on 2011-02-09
> **~Middle said:**
> So is either perl or pythons GUI designer preferable?

And another odd question, i aspire to become a network pentester, and one thing that i wish to do in the future is learn how to write exploits, would you have any idea which language is more commonly used for this? 

I have seen many perl exploits but few python ones, however my knowledge is rather limited there...

Thanks a lot!

gui designers are not language dependent. They depend on the toolkit (e.g. Qt, Gtk, WxWidgets, tkinter, ...). Some may even be toolkit independent
there are libraries for the most important toolkits in both perl and python.

If you chose python check out the ipython shell. Its an excellent tool for command line development (and scientific computing ;) )

---

### Post by ~Middle on 2011-02-09
Awesome, thanks a lot for your help guys!

I think that i may do like a week of python and a week of perl then decide, but this has definitely, helped me decide that this is the path i want to go down!

---

### Post by shawnhcorey on 2011-02-09
> **~Middle said:**
> So is either perl or pythons GUI designer preferable?

For Perl, I suggest you consider [Glade]("http://glade.gnome.org/"), a User Interface Designer.  For it, you'll also need the Perl modules, [Gtk2]("http://search.cpan.org/~tsch/Gtk2-1.222/Gtk2.pm") and [Gtk2::Glade]("http://search.cpan.org/~tsch/Gtk2-GladeXML-1.007/GladeXML.pm").  This allows the application to use the Glade XML file directly.

---

### Post by ~Middle on 2011-02-09
Just edited a python script, and noticed that everything HAS to be indented perfectly, is it this finickity with everything or just indentation?

I do like indenting, but it is a pain in the *** when you are just trying to quickly debug something, so i was just wondering if python is like that with everything?

---

### Post by Simian Man on 2011-02-09
> **~Middle said:**
> Just edited a python script, and noticed that everything HAS to be indented perfectly, is it this finickity with everything or just indentation?

No, just indentation.  You should set up your editor to indent automatically if it doesn't already.  That makes it much easier :).

---

### Post by trent.josephsen on 2011-02-09
> **~Middle said:**
> I do like indenting, but it is a pain in the *** when you are just trying to quickly debug something

This is strange to me because I find that incorrect indentation makes debugging three times as hard as it should be.  I knew people in my early CS classes who would write C++ or Java code in a jumbled mess and come back to indent it later.  Not only did they introduce more bugs, but they wrote generally sloppier and less well-structured code than people who took care to make it clean from the start and keep it clean while editing.

Sloppy indentation is symptomatic of sloppy thinking.  If you don't have that kind of attention to detail, it's the *first* thing you need to cultivate if you want to be a successful programmer.

---

### Post by ~Middle on 2011-02-09
Ah no, you see i indent everything first time, but wehn i come to debugging, and i want to try like 10 different things to see which is the issue, it is nice to be just able to through some lines in quickly without worrying about where they are!

Thanks for the responses guys!

Oh and is gedit a suitable editor? And can i set that up to auto indent?

---

### Post by shawnhcorey on 2011-02-09
> **~Middle said:**
> Just edited a python script, and noticed that everything HAS to be indented perfectly, is it this finickity with everything or just indentation?

If you think it's bad now, wait until you have to maintain code that has seen 20 or 30 people before you, each with a different number of spaces for indentation.  :)

---

### Post by ssam on 2011-02-09
> **shawnhcorey said:**
> If you think it's bad now, wait until you have to maintain code that has seen 20 or 30 people before you, each with a different number of spaces for indentation.  :)

as long as you all use tabs its fine (then you can each set you editor to show a tab as however many spaces you like) :-)

---

### Post by shawnhcorey on 2011-02-09
> **ssam said:**
> as long as you all use tabs its fine (then you can each set you editor to show a tab as however many spaces you like) :-)

Key word being "all".  The problem is that different people have different ideas on what is the proper indentation.  Even those Style Guidelines that are Permanent Forever and Ever get changed every 2-3 years.  And the problem gets worst when you have to integrate outside code.

---

### Post by LemursDontExist on 2011-02-10
> **~Middle said:**
> Ah no, you see i indent everything first time, but wehn i come to debugging, and i want to try like 10 different things to see which is the issue, it is nice to be just able to through some lines in quickly without worrying about where they are!

Thanks for the responses guys!

Oh and is gedit a suitable editor? And can i set that up to auto indent?

gedit is a good editor, and it can autoindent - I think it should be turned on be default, but you can set it under Edit -> Preferences -> Editor, in any case.  I would actually recommend setting the editor to insert spaces instead of tabs (4 spaces is standard) - if you have both tabs and spaces in your document it can cause problems so it's safest just not to use tabs at all.  (The [python style quide]("http://www.python.org/dev/peps/pep-0008/") suggests this).

If you want a slightly more feature rich but still lightweight nd easy to use editor, you might check out Geany - I find it's a good compromise between features and bloat.

---

### Post by kurum! on 2011-02-10
> **~Middle said:**
> I am considering learning either Python or Perl, 
I suggest neither. Learn Ruby instead. It has the best of both Python and Perl.

---

### Post by rcktsingh on 2011-07-14
How about this: In python, you don't have to put semicolon at the end of a line. that saves a lot of space and time and stupid errors. :lolflag:

---

### Post by cgroza on 2011-07-14
> **shawnhcorey said:**
> If you think it's bad now, wait until you have to maintain code that has seen 20 or 30 people before you, each with a different number of spaces for indentation.  :)
Hmm, in emacs, all I have to do to fix that is C-x h TAB and it gets the indentation right in the whole file. :D

---

### Post by uRock on 2011-07-14
NecroThread Closed.

---

