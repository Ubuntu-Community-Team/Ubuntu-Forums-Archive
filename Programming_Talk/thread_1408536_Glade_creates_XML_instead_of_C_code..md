---
title: "Glade creates XML instead of C code."
date: 2010-02-16
forum: Programming Talk
---

### Post by n97ua on 2010-02-16
Kind of new to Ubuntu and started looking at Glade to assist in writting GUI of my first application for GNOME to be compiled in C.

I took me a while to learn Glade only to discover it wrote XML and not C or C++ as I had been lead to believe.  Apparently XML is better in many ways except I want nothng to do with runtime GUI creation from outside sources like XML.  

Moving runtime sources to a TEXT file is both sloppy and non-secure in the real world.  Not to speak of execution time.  I am not looking for why anyone would prefer their program to be manipulated by an outside text file at run time.  Or how robust an XML design or format is.  Nor its portability to other languages. ie: ( Micro-junk Windows )

I came to Ubuntu to get away from that environment and see no reason to write software for an ( MS ) platform.   ( EVER ! )   To me Ubuntu has been a very welcome OS.  I want to develop my own Linux code for the Gnome desktop, and I want it to be just that.  A program.  Not code that requires a corresponding text file to run at runtime.

Given this background, the question is this.  [COLOR="DarkRed"]**Is there an application that will assist in writting the GUI portion of a Linux Gnome environment like GTK+ which outputs C or C++ code ?**[/COLOR]

Any help would rock... And keep the Ubuntu world creating great programs.

---

### Post by Joeb454 on 2010-02-16
Thread moved to Programming Talk :)

---

### Post by pbrane on 2010-02-16
The older version of glade would write C/C++ code for the GUI. You really don't want that. I use Glade 3.6.7 and GtkBuilder. I mainly write using C++ so the API I am using is Gtkmm. The GtkBuilder class is called Gtk::Builder. You can access your glade XML file and interact with the widgets using the Gtk::Builder classes. I don't think you will find any speed issue with the GUI being in an XML file. The entire file can be loaded and parsed at startup. Also many programs use "outside" files for resources and configuration. I don't think that is a problem. In *nix these files can be placed in system directories that are not accessible by the normal user.

However if you wish to hardcode the GUI then that is entirely possible. You can't use glade to do that. I don't know of any other program that will allow you to create a Gtk GUI and output the code for you.

If you really want something like that then your best bet is to get an older version of glade and try that. Caveat: Gtk has gone through many changes and you won't be able to take advantage of the newer features. And some features have been deprecated.

In case you haven't already seen this:
[http://library.gnome.org/devel/gtk/stable/]("http://library.gnome.org/devel/gtk/stable/")

---

### Post by diesch on 2010-02-16
It shouldn't be that hard to write a program that reads Glade's XML files and creates C code from them.

[http://freshmeat.net/search/?q=glade&section=projects](http://freshmeat.net/search/?q=glade&section=projects) find some such projects but I guess they don't work with Glade-3.

---

### Post by nrs on 2010-02-16
>   A program.  Not code that requires a corresponding text file to run at  runtime.
Whatever you do, *don't* look in /etc. There is no security risk. If you want this you're going to have to use an older version of glade. It was ditched for a reason.

---

### Post by Milliways on 2010-02-16
I recently taught myself to use glade and gtk+ (also coming from Windows)

The following is very helpful:-

[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)

The only thing I initially found confusing is the reference to gtk-builder-convert
This is no longer necessary if you select your glade project preferences as GtkBuilder.

If you have not used gtk+ before it is worthwhile to do some simple examples constructing widgets from code first.

PS There is no security risk if you install the glade file in /use/local/share/ along with your program.

PPS IF you really don't want to do this you can include the xml as a string in your program and load this into GtkBuilder

---

### Post by matthew.ball on 2010-02-17
wxFormBuilder will give you C++ code. Works fairly well (I haven't found any issues, though I have really only created some basic forms).

I would strongly recommend wxWidgets though - it is a fairly robust framework allowing you to write cross-platform applications which have a native look.

Don't know if you're interested in C++ or want to stick primarily to C. There is probably a C binding available for wxWidgets, but I've not searched.

---

### Post by n97ua on 2010-02-17
**WOW** - You have all helped a great deal.  Everyone in their own way.  This is by far the very best thing **Ubuntu** offers.  Very nice people all offering their help.  I am fond of a program always having within it,  the complete program.  Makes for an easy install and there is never a chance of a deleted or misplaced component.  

I understand the reasons for doing XML.  Sure... ** But that was not the point.**  I want to create one file.  One program written in C or C++ that within it, containes tight fast conmpact code with the knowledge, that it will never have to depend on an XML text file to run.

To this I want to thank all of you for the various solutions you have all provided.  Again I cannot thank you all enough...    **Ubuntu Rocks **!  I cannot think of any OS better then Ubuntu...  I worked with DOS and hated Windows.  I loved Unix and I love Linux even better.  I would never go back to MS Windows for any reason.  Even if they fix it, which I believe is impossible.  Thank you everyone...  You are what makes **Ubuntu** such a great OS.  

I have helped others out here too.  I think its my duty to return these favors. After all, its what make Ubuntu the best OS in the entire world.  All of you are what makes Ubuntu such a thrill to use. 

I was an Assembler programer for the 8088 chip a long time ago.  Tight fast and complete have always been important to me.  I can give users one file and within it is all they need.  

Certainly external data is a different thing but when that data or lack there of, can cause my program to halt or crash then this is a different thing.  Again my thanks...  :P

8-)

---

### Post by wmcbrine on 2010-02-17
There are no standalone program files -- do an "ldd progname" and look at all the external libraries it links to. Of course you could build it static (which I don't recommend), but even then, you'd still need a kernel, an X server, etc. (Even in DOS, this was true -- you couldn't run your EXE or COM file without IO.SYS, MSDOS.SYS, and COMMAND.COM, or whatever they were called. It was a simpler environment, but there were still dependencies.)

Relying on a text file will not make it slow, either. Reading text files is trivial compared to actually building the GUI. And it's not going to be constantly rereading the file -- that should happen just once, at startup.

But of course, if you want, you can include the XML into the program as a string, and initialize from that instead of an external file.

I was actually kind of annoyed by the code generator -> XML generator switch myself, but not for any of the reasons you mentioned -- it just seemed like more work.

---

### Post by CptPicard on 2010-02-18
A lot of it has been said already but I feel compelled to point out how just wrong your assumptions are... it is important to understand early on that when you're learning something new, such as application programming for Linux in this case, having wrong assumptions about what is appropriate will be damaging your progress. You'll just hit your head against a wall until you learn you were wrong, and that the other people are doing things in a certain way for a reason.

Now, if you really had a proper, specific reason for not wanting to use XML data files, it would be different, but it just seems like a sweeping prejudice...

> 
Moving runtime sources to a TEXT file is both sloppy and non-secure in the real world. 

How? Even if there were a way to "break into" the XML (and in that case, replacing the binary would be an even more dangerous option), there are no "runtime sources" involved in the XML file -- it is a well-formed description of GUI structure, but it does not represent generally executable code.

> 
 Not to speak of execution time.

Ever tried? It's loaded once, and the GUI objects are created into RAM. After that, there is no difference -- GUI code is not intense, so any benefits you'd get from compilation are not noticeable.

> 
  I am not looking for why anyone would prefer their program to be manipulated by an outside text file at run time.  Or how robust an XML design or format is.  Nor its portability to other languages.

That is, "I am a beginner at this but I am *not* looking to learn why things are done the way they are, I just want to hold onto my preconceptions... please don't inform me" :)

> I want to develop my own Linux code for the Gnome desktop, and I want it to be just that.  A program.  Not code that requires a corresponding text file to run at runtime.

I'm willing to bet it would be hard to find any other  Gnome desktop program like that, so why would you want to actively break the model, considering that I honestly don't think you have the ability to make that sort of a technical call yet?


> **n97ua said:**
>  I am fond of a program always having within it,  the complete program.  Makes for an easy install and there is never a chance of a deleted or misplaced component.

I would suggest you learn about the Debian "apt" packaging system. Makes for really easy installs, without the horrible requirement of creating monster-binaries that you'll have to manually manage and that will each contain their own versions of whatever.

> One program written in C or C++ that within it, containes tight fast conmpact code with the knowledge, that it will never have to depend on an XML text file to run.

Any code that actually has any bearing on execution speed in your binary is typically somewhere else than in the GUI part, and as has been said, the XML itself does not influence any of that.

> 
I was an Assembler programer for the 8088 chip a long time ago.  Tight fast and complete have always been important to me.  I can give users one file and within it is all they need.

Ok, figures. ;) The low-level guys tend to have a kind of "can't see the forest for the trees" kind of mentality. I can also give users one file and within it is all they need -- a .deb package. It also fetches dependencies, installs and configures everything...

> 
Certainly external data is a different thing but when that data or lack there of, can cause my program to halt or crash then this is a different thing.

It is much more likely that a hardcoded GUI crashes your program as it is fully executable code. The XML parser can be made separately robust, and the XML file itself isn't "code", so it can't crash in that sense.

I actually am not sure if there is some sort of included scripting for GUI functionality in Gnome GUIs, but at least as long as it's strictly XML, it won't/can't crash anything.

---

### Post by Jonas thomas on 2010-02-18
I feel like a fence sitter here. I can sort see all points here.
I dabbled in Glade at Blade a while back and I sort of bugged me it had a text file instead of C++.  Still, Cptpicard makes excellent points.
However, wound't it make sense to have a glade configuration file as XML in development but an then when it's production, have an option obfuscate the file somehow for those who don't want there XML so easily manipulated?

---

### Post by CptPicard on 2010-02-18
Well, this is an operating system with an open source ethos, so having the GUI design (which tends to be intellectually trivial anyway) as readable text shouldn't be too shocking... :)

---

### Post by Jonas thomas on 2010-02-18
> **CptPicard said:**
> Well, this is an operating system with an open source ethos, so having the GUI design (which tends to be intellectually trivial anyway) as readable text shouldn't be too shocking... :)

I played briefly with glade, was impressed and disappointed at the same time.  Your point if valid.   But.... say for example a small company who might want to use oss tools ,might not use glade.  I just see viewable XML config file as something that might restrict wider use outside of the pure open source applications.
OTH.. I suppose as the other poster pointed out, this file could be place the file where access could be retricted if required.

---

### Post by Tibuda on 2010-02-18
You can use [gtk_builder_add_from_string]("http://library.gnome.org/devel/gtk/unstable/GtkBuilder.html#gtk-builder-add-from-string") instead of gtk_builder_add_from_file, and embed the XML file in your C code.

---

### Post by n97ua on 2010-02-18
**Yes...** This is also a great idea.  The from string would also solve it.  I like all the solutions provided.  Right now I am working on the **wxFormBuilder** suggestion and I like that a great deal more then glade at this point.

So if you guys want a real solution this one looks like a winner.  I consider this question resolved at this point.  It seems like the question was heading down a bad path where no Ubuntu has gone before.  

Certainly the great percentage of you guys out there have provided a great deal of help, and I cannot stress how great that is.  :P

---

### Post by wmcbrine on 2010-02-18
> **Jonas thomas said:**
> But.... say for example a small company who might want to use oss tools, might not use glade.I'm trying to imagine why the Glade developers should care about that, but I can't.

---

### Post by matthew.ball on 2010-02-18
> **n97ua said:**
> **Yes...** This is also a great idea.  The from string would also solve it.  I like all the solutions provided.  Right now I am working on the **wxFormBuilder** suggestion and I like that a great deal more then glade at this point.

So if you guys want a real solution this one looks like a winner.  I consider this question resolved at this point.  It seems like the question was heading down a bad path where no Ubuntu has gone before.  

Certainly the great percentage of you guys out there have provided a great deal of help, and I cannot stress how great that is.  :P
You may come up with an issue here.

In your original post you said you wouldn't want to develop for Windows under any circumstance. Using wxWidgets it's highly likely your code will just compile on Windows with no change to the code base.

Just find it slightly amusing :p

---

### Post by nrs on 2010-02-18
> **Jonas thomas said:**
> I feel like a fence sitter here. I can sort see all points here.
I dabbled in Glade at Blade a while back and I sort of bugged me it had a text file instead of C++.  Still, Cptpicard makes excellent points.
However, wound't it make sense to have a glade configuration file as XML in development but an then when it's production, have an option obfuscate the file somehow for those who don't want there XML so easily manipulated?

> **Jonas thomas said:**
> I played briefly with glade, was impressed  and disappointed at the same time.  Your point if valid.   But.... say  for example a small company who might want to use oss tools ,might not  use glade.  I just see viewable XML config file as something that might  restrict wider use outside of the pure open source applications.
OTH.. I suppose as the other poster pointed out, this file could be  place the file where access could be retricted if required.

Honestly, what have you people got to hide? :P There is no "code" in the XML file, there is no information in there that couldn't be gained from looking at a screenshot of your application, it just describes the widget layout. It's not that different from HTML. Has "View Page Source" harmed corporate uptake of the web? 

"Normal" users can't play with the file, since it's generally placed in /usr (At least when installed through a package manager). Even if they could though, what's the big deal? They can find a way to crash the application? They could crash the application by messing with data you view as legitimate, maybe by screwing with save data as an example. Which makes about as much sense.

---

### Post by Jonas thomas on 2010-02-19
can we just change the subject..
so Nrs... how's those olympics going??

---

### Post by Tibuda on 2010-02-19
> **wmcbrine said:**
> I'm trying to imagine why the Glade developers should care about that, but I can't.

I can think of a reason: Get support from ISVs!

---

### Post by Jonas thomas on 2010-02-19
> **danielrmt said:**
> I can think of a reason: Get support from ISVs!

I did a little googling on ISV and Glade.  I ran across and interesting(for me a least)white paper.  
[http://www.mono-project.com/Mono,_a_technical_whitepaper]("http://www.mono-project.com/Mono,_a_technical_whitepaper")

---

### Post by billy8 on 2012-09-06
Searching for the same thing and got here. Lots of replies are nice but some are representing many things that are going wrong in Linux today, e.g., more and more narrow-minded ipeople are taking control and posing their will on the Linux world that was supposed to be all about open and option (not just free). It's sad. 

I hope the Glade team or someone else (if someone wants to form a team please count me in) someday gives us an option to generate C code directly. There are many good reasons for that. You'd know some if you have ever done serious programming.

---

### Post by diesch on 2012-09-06
I don't know any reason why one could possible want Glade to create C code instead of XML. 

But if you really need that it shouldn't be hard to hard a small tool that creates C from the XML file.

---

### Post by SledgeHammer_999 on 2012-09-07
Just write the GUI code by hand it's not that difficult. Also you could compile the XML file as a resource INTO your binary so you won't have an extra file to distribute.

---

