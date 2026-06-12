---
title: "[SOLVED] Gnusolfege not working"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by benevolent on 2008-05-22
Hello... 

I have [this programm](http://www.solfege.org/) installed, and it's not working at hardy (at gutsy it was 100% ok!)


I want this for my music theory practice (I don't want to install similar windows programm under wine since there are equally effective free programs)


this is the output error, but i cannot figure out what it needs


> Checking for gtkhtml2... ok
warning: invalid directory in path: /home/dimitris/lessonfiles
Solfege will use fakesynth
/usr/share/solfege/src/mainwin.py:436: GtkWarning: Refusing to add non-unique action '_Rhythm' to action group 'NotExit'
  self.m_action_groups['NotExit'].add_actions(actions)

Traceback (most recent call last):
  File "/usr/bin/solfege", line 77, in <module>
    src.mainwin.start_app(os.path.join(prefix, "share", "solfege"))
  File "/usr/share/solfege/src/mainwin.py", line 802, in start_app
    w.post_constructor()
  File "/usr/share/solfege/src/mainwin.py", line 640, in post_constructor
    self.m_app.display_sound_init_error_message(self.m_app.m_sound_init_exception)
  File "/usr/share/solfege/src/app.py", line 158, in display_sound_init_error_message
    self.m_ui.display_exception_message(e)
  File "/usr/share/solfege/src/mainwin.py", line 497, in display_exception_message
    sourcefile, lineno, func, code = traceback.extract_tb(sys.exc_info()[2])[0]
IndexError: list index out of range


Thx in advance

---

### Post by nowshining on 2008-05-22
have u tried going to the main website and seeing if they have an update? or u could file a launchpad bug report. either that or it's trying to add itself to a group which doesn't exist. Alas have u installed all updates?

---

### Post by benevolent on 2008-05-22
Hm... Indeed there was an update!!! I download it and now its working ;-)


Thank you very much!!!

---

### Post by bluefrog on 2008-05-22
you could install from the source code. I just tried the development release and it's working alright

---

