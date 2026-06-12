---
title: "Python code completion"
date: 2008-12-28
forum: Programming Talk
---

### Post by pokerbirch on 2008-12-28
I'm new to Python and have mostly programmed under Windows with Visual Studio. Now since moving to Linux, my blinkers have been lifted, so i'm now more inclined to use dedicated tools for the job in hand.

What i'm looking for is a Python editor/ide/whatever with the best code completion and call tips. Having tried just about everything in the repos, i seem to be going round in circles. These are my findings...i'd LIKE to be disproved:
[LIST]
[*]Geany is nice but there's no code completion for Python.
[*]Gedit is also nice and has some plugins for Python, but code completion is poor.
[*]SPE, IPython and BOA have reasonable code completion but only in the Shell.
[*]IDLE also has Shell based code completion but looks pretty crap on Ubuntu.
[*]Vim and Emacs. WHY? Jesus, i never realised that a simple text editor could be made so difficult to use!
[*]I've also tried DrPython, Eric4, Pida, PyPe and Eclipse/PyDev. The main let downs were lack of (or poor) code completion/call tips.
[/LIST]

My reasons for not wanting the Shell style editors is because it runs my code real-time and that's no good when you're trying to write classes, functions, timed code, etc, etc. But perhaps i have misunderstand the whole Python and Shell thing...i'm assuming that the sole purpose of a Shell is for quick n' dirty code testing?

The one i haven't mentioned is Editra...and that's because it is the one i am currently using. What i'd *like* to see, is my available options every time i press '.' or '(' or 'ctrl+space'...but in reality i know that this is no simple task for a language like Python. I do know that Editra executes the code in order to find code completions and the developer has 'perfect' code completion at the top of his 'to do' list.

So yeah, what i'm asking is: are there any editors/ide's that have BETTER code completion than Editra?

---

### Post by kaivalagi on 2008-12-28
I too have had most experience with VS, due to work...

I use PyDev with Eclipse for my fun coding, and the code completion can be annoyingly ****...i.e. just when you want help none is available

I tend to have a browser window open to python docs where I look up libraries etc for help as and when

I'll be keeping an eye on your thread with curiosity...good code completion would be a nice luxury

---

### Post by CptPicard on 2008-12-28
Eclipse + PyDev is the best I've used.

When it comes to code completion with Python, you have to understand that you can't deduce types from Python all the time statically simply by studying source, because the types are not declared but exist only at runtime. So theoretically speaking this makes Python type resolution necessarily Turing-complete, because you must run any algorithm you have to know what types are present at runtime.

Then again, duck typing reduces greatly the number of actual types you must deal with, so the general unavailability of code completion is not such a huge issue as it would be in static-typed languages like Java.

---

### Post by kjohansen on 2008-12-28
I used WingIDE, to get full code completion it is not free but I like it and its code completion keeps getting better with each update...

---

### Post by ApostleofJesus on 2008-12-28
If you don't mind, consider buying Wing IDE. I have long been using 101 free version (No code completion) and Bought Personal Edition. I enjoy code completion now :)

---

### Post by imdano on 2008-12-28
If you work an open source project written in Python you can get the professional version of WingIDE for free.  I've been very happy with it.  The code completion works great, as do the other neat features (debugger, source browser, integration with pylint and pychecker, lots of other good stuff).

---

### Post by pokerbirch on 2008-12-28
When i tried Eclipse + PyDev, it didn't seem to offer me anything more than Editra did...so i couldn't see much point in having a fat Java app and JVM when a 7Mb package could do the same. Mind you, i've learnt a lot more Python since i did that about a week ago. :)

I quite like Editra. You can tell that the developer is a Python coder. The simple things like block (un)commenting, customizable syntax colouring + layout + views + etc, python plugins, 'run' button/key, etc, etc all make coding enjoyable. There's even a HTML generator which creates a web page with your code all nicely coloured to match your syntax settings.

I've just been playing around with some http code and there are a couple of areas where Editra code completion fails. Here's the code:

[PHP]
import urllib2
import gzip
from cStringIO import StringIO # cStringIO faster than StringIO

USER_AGENT = 'Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.0.5) Gecko/2008121622 Ubuntu/8.10 (intrepid) Firefox/3.0.5'

# build http req
debug = urllib2.HTTPHandler(debuglevel = 0) # 1 = on, 0 = off
req = urllib2.build_opener(debug)
req.addheaders = [('Accept-Encoding', 'gzip'),
                  ('User-Agent', USER_AGENT)]
# send http request
try:
    resp = req.open('http://www.whatismyip.com')
    # get response headers
    resp_headers = resp.info()
    # check if gzipped
    resp_encoding = resp_headers.getheaders('Content-Encoding')
    if resp_encoding == ['gzip']:
        # decompress response
        buf = StringIO(resp.read())
        gz = gzip.GzipFile(fileobj = buf)
        html = gz.read()
        print(html)
    else:
        # data not compressed
        html = resp.read()
        print(html)
except:
    print('HTTP ERROR')
[/PHP]

Details of code completion (roughly in line order):
[LIST]
[*]typing 'urllib2.' shows correct completions throughout the document and typing '(' shows correct call tips for every function.
[*]typing 'req.' doesn't include 'addheaders' as an option on the first call. Once it has been used once, it becomes available for the rest of the document. Call tips are not shown.
[*]again, when typing 'req.', 'open' is not included in the list of completions. Unlike 'addheaders' above, this never gets added, even after you've used it. No call tips.
[*]typing 'resp.' shows no completions at all. This remains for the entire life of the 'resp' object. No call tips.
[*]typing 'resp_headers.' shows no completions at all. This remains for the entire life of the 'resp_headers' object. No call tips.
[*]typing 'gzip.' correctly shows all completions.
[*]typing 'gzip.GzipFile(' shows correct call tips.
[*]typing 'gz.' correctly shows all completions.
[*]typing 'gz.read(' shows correct call tips.
[/LIST]
I've probably missed a couple, but you get the general idea. I'm wondering if you guys could be kind enough to try this code in your editors of choice and report your findings? I'm particularly interested in seeing how PyDev and WingIDE compare to Editra's code completion.

---

### Post by imdano on 2008-12-28
The results in WingIDE are the same, except for "req." always showing addheaders as a code completion option.  I think the cases where you don't see completions means the type of the variable is ambiguous or not clearly defined in the current or imported modules.

However, you can tell WingIDE how to treat variables it can't figure out using the assert keyword.  For example:
[php]class TestDialog(gtk.Dialog):
    def __init__(self):
        gtk.Dialog.__init__(self)

test = TestDialog()[/php]Referencing test.vbox, which is of type gtk.VBox, does not show any code completion options in WingIDE.  However, doing this:
[php]class TestDialog(gtk.Dialog):
    def __init__(self):
        gtk.Dialog.__init__(self)
        assert(isinstance(self.vbox, gtk.VBox))

test = TestDialog()[/php]Will cause the code completion to show up correctly.  This may be the case in other editors, too, so try it out.

---

