---
title: "Python: I just don't get it."
date: 2010-08-28
forum: Programming Talk
---

### Post by kalaharix on 2010-08-28
I am trying to understand Python. I really am.

When I complain on this forum that Python is not integrated well enough with the graphical environment, I am told that it makes sense to separate the design of the gui from the design of the logic.

Yet when I start following gui creation in Python using wxPython, I end up with a hopelessly un-readable mess of integrated gui-creation and program-logic.

Here is the Python code for a commonly used tutorial example which demonstrates interoperability between widgets:

```
#!/usr/bin/python

# communicate.py

import wx

class LeftPanel(wx.Panel):
    def __init__(self, parent, id):
        wx.Panel.__init__(self, parent, id, style=wx.BORDER_SUNKEN)

        self.text = parent.GetParent().rightPanel.text

        button1 = wx.Button(self, -1, '+', (10, 10))
        button2 = wx.Button(self, -1, '-', (10, 60))

        self.Bind(wx.EVT_BUTTON, self.OnPlus, id=button1.GetId())
        self.Bind(wx.EVT_BUTTON, self.OnMinus, id=button2.GetId())

    def OnPlus(self, event):
        value = int(self.text.GetLabel())
        value = value + 1
        self.text.SetLabel(str(value))

    def OnMinus(self, event):
        value = int(self.text.GetLabel())
        value = value - 1
        self.text.SetLabel(str(value))


class RightPanel(wx.Panel):
    def __init__(self, parent, id):
        wx.Panel.__init__(self, parent, id, style=wx.BORDER_SUNKEN)
        self.text = wx.StaticText(self, -1, '0', (40, 60))


class Communicate(wx.Frame):
    def __init__(self, parent, id, title):
        wx.Frame.__init__(self, parent, id, title, size=(280, 200))

        panel = wx.Panel(self, -1)
        self.rightPanel = RightPanel(panel, -1)

        leftPanel = LeftPanel(panel, -1)

        hbox = wx.BoxSizer()
        hbox.Add(leftPanel, 1, wx.EXPAND | wx.ALL, 5)
        hbox.Add(self.rightPanel, 1, wx.EXPAND | wx.ALL, 5)

        panel.SetSizer(hbox) 
        self.Centre()
        self.Show(True)

app = wx.App()
Communicate(None, -1, 'widgets communicate')
app.MainLoop
```

Here is the exactly the same functionality using the same GTK+ but in Gambas:

```
' Gambas class file
'-------------------------------------
PUBLIC SUB Form_Open()
  ME.Center
END
'-------------------------------------
PUBLIC SUB btnAdd_Click()
  showResult(1)
END
'-------------------------------------
PUBLIC SUB btnSubtract_click()
  showResult(-1)
END
'-------------------------------------
PUBLIC SUB showResult(iChange AS Integer)
  lblResult.text = Str(Val(lblResult.text) + iChange)
END
'-------------------------------------
```

Now answer honestly: which one would you rather have to maintain and modify in six months time?

---

### Post by Bachstelze on 2010-08-28
The Python one, because I don't now anything about Gambas. ;)  The bottom-line is: use what works best for you.  If you prefer Gambas, use Gambas.  It's that simple.

---

### Post by juancarlospaco on 2010-08-28
I dont like Wx :)

---

### Post by ssam on 2010-08-28
have you tried using glade?

its you draw the interface. then the code just needs to hookup to the signals that the interface generates.

---

### Post by worksofcraft on 2010-08-28
Yes I also highly recommend Glade. You can use it with C and C++ and many other languages.

It is an interactive rapid application development tool that generates an XML file that defines the GUI you want.

Here is a sample of loading the GUI and connecting the signals in a Python application:

```

		# slurp the GUI from the XML created with Glade
		wTree = gtk.Builder()
		wTree.add_from_file("/usr/share/speaknumber/speaknumber.glade")

		# connect all the signals to a function in our code
		dic = { 
			"on_button1_clicked" : self.on_speak
		}
		
		wTree.connect_signals(dic)

```

---

### Post by JK3mp on 2010-08-28
> **juancarlospaco said:**
> I dont like Wx :)

I +1 this. lol

---

### Post by maximinus_uk on 2010-08-29
That Python one is much easier to maintain - I can read the code, whereas that Gambas one just looks like magic, for example:

```
showResult(1)
showResult(-1)

```

Not obvious on first reading what&#347; going on here at all.

---

### Post by kalaharix on 2010-08-29
"Not obvious on first reading what&#347; going on here at all."

Sorry, don't buy that one at all. It's exactly the same construct as:
```
Communicate(None, -1, 'widgets communicate')
```

i.e. the use of a program-defined function.

---

### Post by maximinus_uk on 2010-08-29
> **kalaharix said:**
> "Not obvious on first reading what&#347; going on here at all."

Sorry, don't buy that one at all. It's exactly the same construct as:
```
Communicate(None, -1, 'widgets communicate')
```

i.e. the use of a program-defined function.

No, not the same. For this:

```
Communicate(None, -1, 'widgets communicate')
```

I can read the code for the Communicate class right above this code. Now let's look at what I said I couldn't understand more specifically:

```
showResult(-1)
```

OK so this seems to some function to display something. But why that -1? And what does it display? Where? Ergo, I find this code hard to understand.

Now be honest I neither know wxWindows or GAMBAS but, *just by looking at the 2 sources you provided*, the longer one is much easier to understand.

---

### Post by nvteighen on 2010-08-29
Please, don't blame the language for this. You'd be doing this mistake was it in C, C++, Python, Perl, Forth or Smalltalk-80... and using a text interface. Gambas or VB forgive you because of how they work.

The best way to code stuff, specially when learning, is to first code something like a "library": functions that do what you want, regardless of the interface. Python is specially good for this because you can use the interactive interpreter as "testing interface". Then, when that works, create the UI... Think of it as a user that enters the functions in the correct order like they were commands in the shell.

If done right, UI code will depend on the implementation code but implementation code will be independent of the UI.

---

### Post by kalaharix on 2010-08-29
maximinus_uk: "I can read the code for the Communicate class right above this code. Now let's look at what I said I couldn't understand more specifically:"

erm.. the function showResult is below the code rather than above. Would it help you if I put it above? :)

nvteighen: "Please, don't blame the language for this."

I couldn't agree more and think this applies to Gambas as well. My code sample is as independent of the UI as any Python-Glade version would be.

---

### Post by Wybiral on 2010-08-29
The point here is, the wx library has nothing to do with python as a language. If you want a "showResult" function in python, write it. If you're trying to "get" python, learn the actual language. You can't just compare it to parts you're already familiar with from other languages and say you don't get it.

---

### Post by Dies on 2010-08-29
No one cares about Gambas and at this point probably no one ever will. Get over it.

---

### Post by Zugzwang on 2010-08-29
> **Dies said:**
> No one cares about Gambas and at this point probably no one ever will. Get over it.

What kind of comment is this? To sum up the thread, the OP complained that the "GUI code" in a typical Python program clutters up the "application logic", which does not seem to be the case with Gambas so he/she asks why this is the case in such a high-level language like Python. This is a totally valid question! In the course of this thread, there have been two answers:

[LIST=1]
[*]Using glade, this GUI code disappears, so the application in Python will be much more tidy. 
[*]Python is a general-purpose language, so from a language-design point of view, it wouldn't make too much sense to integrate the GUI stuff too tightly into the language.
[/LIST]

These are valid answers to a perfectly valid question. So, to sum it up, you *can* have this nice separation in Python as well (by using glade), but the language does not force you to do so. Thus you have to know about this possibility and then you can program GUI with python "fine again". So what does this have to do with someone caring about Gambas and getting over something?

---

### Post by Dies on 2010-08-29
> **Zugzwang said:**
> What kind of comment is this? To sum up the thread, the OP complained that the "GUI code" in a typical Python program clutters up the "application logic", which does not seem to be the case with Gambas so he/she asks why this is the case in such a high-level language like Python. This is a totally valid question! In the course of this thread, there have been two answers:

[LIST=1]
[*]Using glade, this GUI code disappears, so the application in Python will be much more tidy. 
[*]Python is a general-purpose language, so from a language-design point of view, it wouldn't make too much sense to integrate the GUI stuff too tightly into the language.
[/LIST]

These are valid answers to a perfectly valid question. So, to sum it up, you *can* have this nice separation in Python as well (by using glade), but the language does not force you to do so. Thus you have to know about this possibility and then you can program GUI with python "fine again". So what does this have to do with someone caring about Gambas and getting over something?

No, if you actually pay attention the whole "course" of this thread amounts to nothing more than a thinly veiled "Gambas > Python".

This is evident right from the start and probably why the first comment is spot on with "Use whatever you like".


And no, I don't see it as a valid question or concern. For the most part, I don't think it matters much which language you use to program an application, only how you design it. There is either separation between the UI and the logic or there isn't.

---

### Post by worseisworser on 2010-08-29
> **Dies said:**
> And no, I don't see it as a valid question or concern. For the most part, I don't think it matters much which language you use to program an application, only how you design it. There is either separation between the UI and the logic or there isn't.

Interesting. How do you design something in a particular way when there is no language support for implementing the design you happen to have in mind?

There certainly is a significant jump in what you can express or design in, say, a low-level simple language like ASM to languages like Lisp, Haskell, C#, Python or Java, no?

Language matters a lot IMHO.

---

### Post by Dies on 2010-08-29
> **worseisworser said:**
> Interesting. How do you design something in a particular way when there is no language support for implementing the design you happen to have in mind?

There certainly is a significant jump in what you can express or design in, say, a low-level simple language like ASM to languages like Lisp, Haskell, C#, Python or Java, no?

Language matters a lot IMHO.

We're obviously talking about high level languages here. Not sure why you would even bring ASM into the mix... I guess you missed where I said "For the most part", huh?

In any case, if someone was honestly interested in how, or the best way, to accomplish something in any particular language, then they would, or at least should, just ask that without pointing out that "insert your favorite language here" is so much better, easier, faster, etc... every chance they get.

Can we at least agree on that?

.

---

### Post by worseisworser on 2010-08-29
> **Dies said:**
> We're obviously talking about high level languages here. Not sure why you would even bring ASM into the mix...

Because it is an obvious example which pretty much anyone can see.


> **Dies said:**
> I guess you missed where I said "For the most part", huh?

I saw it, but I do not agree with it. I.e., what I said applies not only in the lower-level vs. higher-level language case, but also in the high-level vs. other high-level language case.

Perhaps one can think of the scenario as one with branches; a tree, i.e., not just a single root with one branch moving towards "high level language".

And indeed if one is to look at the Wikipedia page about programming paradigms one will see that they make up a tree of categories and sub-categories: [http://en.wikipedia.org/wiki/Programming_paradigm](http://en.wikipedia.org/wiki/Programming_paradigm) (right hand side).


> **Dies said:**
> In any case, if someone was honestly interested in how, or the best way, to accomplish something in any particular language, then they would, or at least should, just ask that without pointing out that "insert your favorite language here" is so much better, easier, faster, etc... every chance they get.

Can we at least agree on that?

I'm not sure I understand what is being said here, but I don't think pointing out that <some other language/environment> might be more suitable than the one some person is currently using is a bad idea in general when done with some care. Perhaps this is why we are using Linux?

---

### Post by Dies on 2010-08-29
> **worseisworser said:**
> Because it is an obvious example which pretty much anyone can see.

Maybe obvious but also irrelevant...

> **worseisworser said:**
> 
I saw it, but I do not agree with it. I.e., what I said applies not only in the lower-level vs. higher-level language case, but also in the high-level vs. other high-level language case.

Perhaps one can think of the scenario as one with branches; a tree, i.e., not just a single root with one branch moving towards "high level language".

And indeed if one is to look at the Wikipedia page about programming paradigms one will see that they make up a tree of categories and sub-categories: [http://en.wikipedia.org/wiki/Programming_paradigm](http://en.wikipedia.org/wiki/Programming_paradigm) (right hand side).

I don't see where you are going with this, most of the high level languages which are currently in use, and by that I mean widely adopted, just in case you misinterpret currently in use, have a lot of libraries written for them.

The fact that so many libraries are written for them, implies if not proves that separation of UI and logic is possible.

> **worseisworser said:**
> 
I'm not sure I understand what is being said here, but I don't think pointing out that <some other language/environment> might be more suitable than the one some person is currently using. Perhaps this is why we are using Linux?

I on the other hand am sure I have no idea what you're *trying* to say there.

---

### Post by worseisworser on 2010-08-29
> **Dies said:**
> Maybe obvious but also irrelevant...

Not if you had understood my next paragraph.


> **Dies said:**
> I don't see where you are going with this, most of the high level languages which are currently in use, and by that I mean widely adopted, just in case you misinterpret currently in use, have a lot of libraries written for them.


I'm not talking about libraries; I'm talking about language or languages.

..and support for e.g. programming paradigms tends to be a language issue; not a library one.


> **Dies said:**
> The fact that so many libraries are written for them, implies if not proves that separation of UI and logic is possible.

I'm talking about your previous generalization; not this, and again not libraries.


> **Dies said:**
> I on the other hand am sure I have no idea what you're *trying* to say there.

I edited my post as part of a sentence went missing when copy/pasting, but never mind; I do not think I care to talk about this with you as you seem petty and annoyed while not really understanding what I'm saying anyway.

---

### Post by Dies on 2010-08-29
> **worseisworser said:**
> 
I edited my post as part of a sentence went missing when copy/pasting, but never mind; I do not think I care to talk about this with you as you seem petty and annoyed while not really understanding what I'm saying anyway.

Yeah, you're right, I am petty the one.

I mean it's not like you took something way out of context and then declined to even meet me halfway, right?

---

### Post by slooksterpsv on 2010-08-29
Maintain and Modify 6 months down the road?
Python

I've used Gambas and am learning it, same with Python, but I'd rather learn gtk python or wx python where I have a more finite control over it than Gambas. Plus python is way extensible as there are tons of additional libraries that can be installed and configured with it.

If you're lost on how to make the interface, try Glade, Glade is amazing and simple to use (just remember you have to use Sizers in order to set objects on the window, 1 sizer space for 1 object that's for Wx Widgets).

---

### Post by kalaharix on 2010-08-30
Thank you Zugzwang for you support and summary. I think it is spot on. I think the point I am trying to make is that oft-repeated mantra that Python 'encourages' good programming while generic BASIC like languages do not is nonsense. As most seem to agree in the this thread: it is just as possible to write appalling code in Python. Conversely (I would contend) it is possible to write good code in Gambas.

Dies: "No one cares about Gambas and at this point probably no one ever will. Get over it."
Apart from being childish, this response is symptomatic of the inherent problem with the Python Mafia. Python is better supported but only because it is cross-platform. If it was Linux only (like Gambas) then it would be in exactly the same boat. I am afraid Python is hanging on M$'s coat-tails to get the acceptance it has.

If you want to be truly depressed go and have a look at the "Linux Market Share" article on linuxjournal.com. Ask yourself how much of the problem is due to Linux users with an attitude like yours.

Gambas, with a bit less condescension from the community, has the ability to bring huge rafts of casual users into Linux. That just cannot be a bad thing.

You are right in one thing though: In my heart I have to admit, my original post was about Gambas :redface:. I don't see it (in your words) as Gambas > Python. More like Gambas =  Python. Or should it be Python == Gambas :)

---

### Post by Dies on 2010-08-30
> **kalaharix said:**
> 
Dies: "No one cares about Gambas and at this point probably no one ever will. Get over it."
Apart from being childish, this response is symptomatic of the inherent problem with the Python Mafia.

Python mafia? I think you're confused, sure I like Python, it's nice, but I could care less if others don't.

Also, you could have just as easily started a thread about Gambas, what you like about it and why you feel people should prefer it, rather than one that bashes a popular language in an attempt to prop up another. :wink:

> **kalaharix said:**
> 
Gambas, with a bit less condescension from the community, has the ability to bring huge rafts of casual users into Linux. That just cannot be a bad thing.

If you really want Gambas to be recognized, or at least get people to take notice, there's no need to talk about it, all you need to do is program a "killer app" using Gambas. Till you, or someone else does that it's all just talk.

> **kalaharix said:**
> 
You are right in one thing though: In my heart I have to admit, my original post was about Gambas :redface:. I don't see it (in your words) as Gambas > Python. More like Gambas =  Python. Or should it be Python == Gambas :)

:)

---

### Post by Reiger on 2010-08-30
I think the issue here really was the particular GUI toolkit. For starters the “Python” idiomatic toolkit is Tk, and not the abstracted-toolkit-on-top-of-a-toolkit that is Wx (on Linux, using Wx is a convoluted way of using GTK; and on Windows it is a convoluted way of using Microsoft UI toolkit-of-the-day...). 

So I'd expect that the Tk toolkit has much better Pythonic interfaces to code as you would expect from Python and not using all sorts of obscure magical C++ style bitmask operations that Wx needs. 

As for a third contender apart from GTK, consider Qt. PyQt bindings are rumoured to be quite good (a proper Python interface rather than C code with Python syntax that some libraries are), and Qt really nice so you might want to check it out.

---

