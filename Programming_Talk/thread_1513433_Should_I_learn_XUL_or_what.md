---
title: "Should I learn XUL or what?"
date: 2010-06-19
forum: Programming Talk
---

### Post by Nonno Bassotto on 2010-06-19
I'm familiar with web programming, both client and server side, and I'd like to expand a bit my knowledge in order to be able to write some desktop programs. Python with PyGTK and Glade seems one of the most viable ways.

My problem is that I'm not really familiar with the desktop way of managing widgets. On the web you tipically describe the elements on the page with a markup language, usually some version of HTML, and when an event is fired you modify the elements with Javascript. As far as I understand, in a typical desktop programs, widgets have their own life, sending signals to each other and reacting to signals with callbacks. This is very far from the grounds I'm familiar with, so I'm trying to understand if there is a way to use the web paradigm in a desktop program.

I'm mostly attracted by XUL, which seems exactly what I'm looking for. The problem is that the [documentation]("https://developer.mozilla.org/en/XUL") I can find about XUL seems a bit outdated. Is learning XUL a good idea? Or is it becoming already an old technology?

What are the alternatives? For the most simple applications, where the widgets are only slightly modified, there are some [easy]("http://buc.billeragroup.net/") [tools]("http://autoglade.sourceforge.net/"), but what about a more complex program?

---

### Post by soltanis on 2010-06-19
I prefer wxWidgets myself. GUI programming is indeed not that easy, which is one of the reasons I like to stay out of it. IMHO this is why web applications are the new rage, because they're easier to build and maintain, easier to deploy, and easier for a user to get along with (no installation, just go to a website).

---

### Post by wmcbrine on 2010-06-19
You should definitely learn XUL... if you want to write Firefox extensions.

Glade is pretty easy to use, and so is PyGTK, IMHO.

---

### Post by Nonno Bassotto on 2010-06-19
Both answers seem to miss my point. First, let me remark that XUL is [not only]("https://developer.mozilla.org/en/XULRunner") for Firefox extensions, and [several programs]("https://developer.mozilla.org/en/XULRunner_Hall_of_Fame") (including Firefox itself) have been based on it. My doubt is more about the fact that I don't see much documentation around, hence I'm not sure whether this technology will be useful some time from now or it is already ageing.

That said, I know there are several options if I want to do standard GUI programming. As I have said, should I do so, I have already resolved to learn PyGTK. The point is that all standard widget libraries are more or less based on the paradigm that widgets communicate between them using signals. So every widget is an object with lots of methods. This adds a further complication with respect to what I know now, and I'm not sure I want to learn this at the moment.

Instead I'd like to be able to describe widgets via a markup language (these will be static) and alter them based on events. If I understand correctly, XUL based applications work this way. Are there any other options to do things this way? Is XUL good to develop applications with? Can I expect to be still using it a few years from now?

---

### Post by loell on 2010-06-19
not sure about XUL, but lately I'm rooting on [PyJama]("http://pyjs.org/")s for web and desktop UI.

---

### Post by nrs on 2010-06-20
Ugh. It's bad enough Firefox uses XUL. You don't need to be using it too. If I understand you correctly, you're looking for something like:
```
<?xml version="1.0"?>
<interface>
  <requires lib="gtk+" version="2.16"/>
  <!-- interface-naming-policy project-wide -->
  <object class="GtkWindow" id="window1">
    <child>
      <object class="GtkButton" id="button1">
        <property name="label" translatable="yes">button</property>
        <property name="visible">True</property>
        <property name="can_focus">True</property>
        <property name="receives_default">True</property>
      </object>
    </child>
  </object>
</interface>

```You can write it yourself but most people just use Glade or something like it. GTK+ is great for GNOME but I'd seriously consider using Qt if you want to write cross-platform applications.

---

### Post by JwB Zoofware on 2010-06-20
You can write a GUI in XAML using pure XML markup afaik which is pretty simple, though obviously its only for Windows and you won't be able to achieve much without a C# backend.

Other than that I don't really think there's anything else out there even remotely similar to what you're looking for.

Glade and Gtk are probably the best way to go... I always thought GUI programming was well beyond my skill level, but stick at it, read some books and just try things and it'll become second nature :)

---

### Post by Nonno Bassotto on 2010-06-20
@loell: Pyjamas seems interesting, although I can't find the documentation for Pyjamas desktop.

@nrs: I know glade stores its files in XML. But say you have a menu which must be grayed out if a box is ticked. How do you do that in PyGTK? I want to be able to have a function which reacts to the click event of the box and modifies the DOM accordingly. I'm quite sure this is not the way PyGTK interactions work.

---

### Post by loell on 2010-06-20
yeah, the wiki is currently a mess,it still is on its early stage, I guess.
and oh you could also do glade later on with this.

[http://sourceforge.net/projects/pyjsglade/](http://sourceforge.net/projects/pyjsglade/)

---

### Post by simeon87 on 2010-06-20
> **Nonno Bassotto said:**
> @nrs: I know glade stores its files in XML. But say you have a menu which must be grayed out if a box is ticked. How do you do that in PyGTK? I want to be able to have a function which reacts to the click event of the box and modifies the DOM accordingly. I'm quite sure this is not the way PyGTK interactions work.

The XML file is only a description of the GUI, the interaction needs to be coded in Python itself. In there, you would code what happens when the user clicks on something, etc.

---

### Post by louis--taylor on 2010-06-20
> not sure about XUL, but lately I'm rooting on [PyJama]("http://pyjs.org/")s for web and desktop UI.

Hoho! I know the brother of the main developer of this...

> I know glade stores its files in XML. But say you have a menu  which must be grayed out if a box is ticked. How do you do that in  PyGTK? I want to be able to have a function which reacts to the click  event of the box and modifies the DOM accordingly. I'm quite sure this  is not the way PyGTK interactions work.

Essentially, glade replaces writing the GUI in python/c/whatever and stores it in XML. When you want to use the widgets, you get them from the xml file, and use them inside the program like normal widgets. The only difference between writing a GUI in pure code and with glade is speed.

---

