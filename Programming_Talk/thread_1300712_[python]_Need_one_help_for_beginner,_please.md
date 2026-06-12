---
title: "[python] Need one help for beginner, please"
date: 2009-10-25
forum: Programming Talk
---

### Post by baskar007 on 2009-10-25
i am new to python, when the below code will read a data form remote host.

when i run this code with out gtk, its works perfectly. but struck when i add gtk UI to this code.

struck at "s.h.endheaders()"
 
```

import gtk,httplib,threading

class html(threading.Thread):
    def __init__(s,url):
        threading.Thread.__init__(s)
        s.url=url
        s.host='softwareroxer.110mb.com'
    
    def run(s):
        s.h = httplib.HTTPConnection(s.host)
        print "Sending Request..."
        s.h.putrequest('GET',remote)
        s.h.putheader('Accept', '*/*')
        print "request_complete"
        s.h.endheaders()
        print "headers end"
        print "Reciving response..."
        r = s.h.getresponse()

def start(data1=None,data2=None):
    html=html('http://softwareroxer.110mb.com/index.html')
    html.start()

def windo():
    win=gtk.Window()
    win.connect("destroy", gtk.main_quit)
    button=gtk.Button("Click Me!")
    button.connect("clicked",start,None)
    win.add(button)
    button.show()
    win.show()

windo()
gtk.main()

```

please help me friends.

---

### Post by Can+~ on 2009-10-25
You're new to python and you're already using threads, httplib and a graphic toolkit?

[PHP]Traceback (most recent call last):
  File "asdf.py", line 21, in start
    html=html('http://softwareroxer.110mb.com/index.html')
UnboundLocalError: local variable 'html' referenced before assignment[/PHP]

You cannot use the same name twice:

[PHP]html=html()[/PHP]

change the name, something like "htmlThreadHandler"

Here:

[PHP]s.h.putrequest('GET',remote)[/PHP]

The variable "remote" is not declared anywhere [Read the doc]("http://docs.python.org/library/httplib.html#httplib.HTTPConnection.putrequest"). I guess you wanted a string:

[PHP]s.h.putrequest('GET','remote')[/PHP]

---

### Post by fiddler616 on 2009-10-25
[QUOTE=baskar007]i am new to python[/QUOTE]
Announcement, everybody: I have started learning Python next month, any competency I may show is purely coincidental, and any tutorials I recommend are for us mortals.

---

### Post by baskar007 on 2009-10-25
> **Can+~ said:**
> You're new to python and you're already using threads, httplib and a graphic toolkit?

[PHP]Traceback (most recent call last):
  File "asdf.py", line 21, in start
    html=html('http://softwareroxer.110mb.com/index.html')
UnboundLocalError: local variable 'html' referenced before assignment[/PHP]

You cannot use the same name twice:

[PHP]html=html()[/PHP]

change the name, something like "htmlThreadHandler"

Here:

[PHP]s.h.putrequest('GET',remote)[/PHP]

The variable "remote" is not declared anywhere [Read the doc]("http://docs.python.org/library/httplib.html#httplib.HTTPConnection.putrequest"). I guess you wanted a string:

[PHP]s.h.putrequest('GET','remote')[/PHP]

well, i am not so new to Python already i have designed apps for mobile phones. actually i should say i am new to PyGTK and Linux.

Thank you for this  i did mistake on remote. 
and sorry for those mistakes like html=html blah-blah

Here is the actual code:
[PHP]
import gtk,httplib,threading

class app(threading.Thread):
    def __init__(s,url):
        s.url=url
    def run(s):
        s.h = httplib.HTTPConnection(s.url)
        print "Sending Request..."
        s.h.putrequest('GET',remote)
        s.h.putheader('Accept', '*/*')
        print "requsted"
        s.h.endheaders()
        print "Reciving response..."
        r = s.h.getresponse()
        ecode,ereason=r.status, r.reason
        print ecode,ereason

def start(data=None,url):
    App=app(url)
    App.start()
    print "Thread started"

def ui():
    url="http://ubuntuforums.org/images/misc/ubuntulogo.png"
    window=gtk.Window()
    w.connect('destroy',gtk.main_quit,None)
    b=gtk.Button('Button')
    b.connect('clicked',start,url)
    w.add()
    w.show_all()
    gtk.main()
[/PHP]

i want to start a thread when i clicked on button. yes of course this will start a thread, but thread struck's after some time.

the code will continue after the window closed.


i can't figure out what is the problem?

please helpme.

---

### Post by bonefry on 2009-10-25
Buddy, before anyone can help you, you've got to post the right code.

Don't post code that throws a syntax error when your described problem is not a syntax error.

And what does "struck" mean anyway?
The interface hangs? You can't close the window? The window closes but the process doesn't terminate?

---

### Post by baskar007 on 2009-10-26
> **bonefry said:**
> Buddy, before anyone can help you, you've got to post the right code.

Don't post code that throws a syntax error when your described problem is not a syntax error.

And what does "struck" mean anyway?
The interface hangs? You can't close the window? The window closes but the process doesn't terminate?
sorry,
struck, i mean thread hangs after some time(1sec).
i don't want to close the window,i just start a thread when i click on button.

please sorry for the above code.

---

### Post by baskar007 on 2009-10-26
i just founded a solution for my problem [here]("http://faq.pygtk.org/index.py?req=show&file=faq20.006.htp")

solution is calling gobject.threads_init() at start.

```
import gtk,threading.thread,gobjects
gobject.threads_init()
#here your other codes class
```

---

