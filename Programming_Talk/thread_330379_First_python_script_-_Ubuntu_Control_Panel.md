---
title: "First python script - Ubuntu Control Panel"
date: 2007-01-03
forum: Programming Talk
---

### Post by Cirdan7 on 2007-01-03
Hello everyone, I'd thought I'd show off my first, biggest, and only python script. It is a control panel for Ubuntu. I was reading in the wiki that there is need for a Control Panel to keep all of the settings programs together. I decided that I wanted to write it. As my first python script I wrote a text-based version to get the concept down, i'll probably work on a GUI one soon. Tips would be great!

[Get the script here]("http://www.christiangaming.org/graphics/users/stormtrooper/ubuntucontrolpanel.py")

---

### Post by pmasiar on 2007-01-03
Without thinking too much about it (or even running it), just from surface:

1) First impression: Not bad for a first script. :-)
2) Missing docstrings, you may want to read coding standards of team who will integrate your script somewhere to Ubuntu, they may require them.
3) one-letter variable names are hard to search for. Minor detail, but sometimes might save you time to use ii, kk ect. Or even better: meaningful names.
k is key, l is label, i is in?
4) I would probably tried to avoid magical category numbers and related text strings, instead put menu in some dictionary. But it is possibly premature optimization, check how Ubuntu wants to do it for i18n (=internationalization) so it can be translated, if you want to learn the ropes to get it included.

Again, commenting on style only, without actualy trying to understand how it works. :-)

---

### Post by Lord Illidan on 2007-01-03
Not bad. Hardware doesn't work for me though.

Good luck upon the gui version, and keep it up.

Error for Hardware :

--Hardware--
Mouse
Removeable Drives and Media
Keyboard Shortcuts
Keyboard
Traceback (most recent call last):
  File "ubuntucontrolpanel.py", line 113, in ?
    main()
  File "ubuntucontrolpanel.py", line 110, in main
    menu.selectCategory()
  File "ubuntucontrolpanel.py", line 95, in selectCategory
    self.printMenu(3)
  File "ubuntucontrolpanel.py", line 78, in printMenu
    self.selectCategory()
  File "ubuntucontrolpanel.py", line 93, in selectCategory
    self.printMenu(2)
  File "ubuntucontrolpanel.py", line 51, in printMenu
    while i != "exit":
UnboundLocalError: local variable 'i' referenced before assignment

---

### Post by Cirdan7 on 2007-01-03
Ok, thanks for the input. I'll definitely work on it a bit more.

---

### Post by mallo on 2007-01-03
Nice ^_^.

I have a problem on Hardware too:

Mouse
Removeable Drives and Media
Keyboard Shortcuts
Keyboard
Traceback (most recent call last):
  File "ubuntucontrolpanel.py", line 113, in ?
    main()
  File "ubuntucontrolpanel.py", line 110, in main
    menu.selectCategory()
  File "ubuntucontrolpanel.py", line 93, in selectCategory
    self.printMenu(2) 
  File "ubuntucontrolpanel.py", line 51, in printMenu
    while i != "exit":
UnboundLocalError: local variable 'i' referenced before assignment


Try to build a GUI with zenity, it is very easy ;).

---

### Post by Lord Illidan on 2007-01-03
Or else try using PyGTK. I did some work on it in the holidays and it wasn't too hard.

BTW, are you a fan of LOTR, Cirdan7?

---

### Post by gpolo on 2007-01-03
of course everyone will have a problem with option 2, he forgot to add a line before the while in category 2.  i = self.getInput() at line 51, just a common mistake. keep the work going ;)

---

### Post by SuperMike on 2007-01-03
Download pgst from SourceForge.net, open it up, and learn how it works. I made it after seeing how RedHat made their Python control panel items. I used Glade-2 to draw the GUI and then used some tricks in Python to load the GUI and respond to signals from it.

Another approach:

Learn XUL from Mozilla and build a custom XUL chrome that you can load with a special command line option in Firefox. Have it connect back to a thin, embeddable web service on an alternate port like 26224. Thttpd is a good one. Have it use CGI to call either Perl, Python, or PHP. If you need a database and an ordinary CONF file won't work, then use SQLite because it's got a great license and is designed especially to be suitable as an embeddable standalone database for small projects.

---

### Post by Cirdan7 on 2007-01-03
> **Lord Illidan said:**
> Or else try using PyGTK. I did some work on it in the holidays and it wasn't too hard.

BTW, are you a fan of LOTR, Cirdan7?

Somewhat...I've only seen the movies. Long story short, I put my name into a LOTR name generator and this popped out. I did it because my last username was quite common.

As for the UI, I was planning on using pyGTK. Maby I'll look at the XUL thing if its not too complex.

---

