---
title: "Where to start with python?"
date: 2005-06-19
forum: Programming Talk
---

### Post by sapo on 2005-06-19
Hi, i would like to start programing python, mainly for making guis for some apps that doesnt have it..

So i think that i ll need python and GTK, but i dont know from where to start..

I m programming php for food, and programmed pascal and clipper for a long time.. so i m not a newbie in programing..

If someone knows a good tutorial or a good documentation regardin gtk + python i would apreciate it...

And please, i cant stand those "hello world" apps, i want to start making something.. like a simple app that when i click in a button runs one command and when i click in another runs another...

And a good editor would be fine too, i use gedit to code php and i m fine with plain text.. i prefer to type than to click in buttons to make code for me  ](*,) 

thanx :)

---

### Post by Moobert on 2005-06-19
your need gtk, pygtk and maybe glade if you want code produced for you

Two good articles on python gui programing:

[http://www.linuxjournal.com/article/6586](http://www.linuxjournal.com/article/6586)

[http://www.oreillynet.com/pub/wlg/6340](http://www.oreillynet.com/pub/wlg/6340)

Good example:

[http://primates.ximian.com/~sandino/python-glade/](http://primates.ximian.com/~sandino/python-glade/)

gui creation without glade, (just coding):

[http://www.pygtk.org/pygtk2tutorial/index.html](http://www.pygtk.org/pygtk2tutorial/index.html)

---

### Post by sapo on 2005-06-19
[QUOTE=Moobert]your need gtk, pygtk and maybe glade if you want code produced for you

Two good articles on python gui programing:

[http://www.linuxjournal.com/article/6586](http://www.linuxjournal.com/article/6586)

[http://www.oreillynet.com/pub/wlg/6340](http://www.oreillynet.com/pub/wlg/6340)

Good example:

[http://primates.ximian.com/~sandino/python-glade/](http://primates.ximian.com/~sandino/python-glade/)

gui creation without glade, (just coding):

[http://www.pygtk.org/pygtk2tutorial/index.html](http://www.pygtk.org/pygtk2tutorial/index.html)[/QUOTE]

thanx a lot.. i will take a look.. and maybe i ll try glade too, but i m not a fan of those kind of gui creators.. i m accostumed to raw coding :)

btw there are some good examples in these website.. thanx a lot.. and if someone knows some more examples, please post it  :grin:

---

### Post by dannyp on 2005-06-19
I would recommend wxPython for GUI programming. IMO it is easier to use than pyGTK.

---

### Post by sapo on 2005-06-19
[QUOTE=dannyp]I would recommend wxPython for GUI programming. IMO it is easier to use than pyGTK.[/QUOTE]


Do you know any tutorial or any website where i can read about wxPython? 

thanx :)

---

### Post by Moobert on 2005-06-19
[QUOTE=sapo]Do you know any tutorial or any website where i can read about wxPython? 

thanx :)[/QUOTE]

[http://wiki.wxpython.org/](http://wiki.wxpython.org/)

seems good :)

pyQt seems worth looking into too, qt-designer being the gui builder.

---

### Post by sapo on 2005-06-20
thanx guys.. btw wich is better for me to start? wxpython or python + gtk?

i m a little lost  ](*,)

---

### Post by Quest-Master on 2005-06-20
[QUOTE=sapo]thanx guys.. btw wich is better for me to start? wxpython or python + gtk?

i m a little lost  ](*,)[/QUOTE]
 Python + wxPython, definitely.

---

### Post by nobodysbusiness on 2005-06-21
I'm using Python and wxPython for my app. I haven't worked with PyGTK, so I can't comment on how difficult it is, but wxPython works well and gives apps a native look and feel. I recommend using wxGlade as a GUI designer and Eclipse with the PyDev plugin for coding. I've tried several different IDE's and GUI designers, and this is the combination that I like the best (that I've found so far, anyway).

---

### Post by jdong on 2005-06-21
[QUOTE=sapo]
And a good editor would be fine too, i use gedit to code php and i m fine with plain text.. i prefer to type than to click in buttons to make code for me  ](*,) 

thanx :)[/QUOTE]

DrPython, in Backports, is a great editor for Python. Using plugins available from drpython.sf.net, you can get autocomplete.

No good GUI builders, though... you'll have to get the hang of doing so by hand. I don't know how much easier glade makes it.

---

### Post by sapo on 2005-06-21
my friend told me about this book:

[http://byteofpython.info/](http://byteofpython.info/)

I think that its very easy and interesting.. i m starting with it.. then i ll go with wxpython maybe...

thanx for helping  :grin:

---

### Post by jdong on 2005-06-21
I highly recommend WxPython, and the WxWindows/WxWidgets system in general. No matter what language you use with the WxWidgets system, you get beautiful, native-looking apps on all supported platforms. VERY VERY nice :)

One thing I liked about Python as a beginner was its ease. I started learning Python while running Fedora, which half the admin tools and the whole installer was written in Python. Python is very interactive source-wise. It's EASY to play around with snippets of code, or change bits here and there to see what they do. The interactive Python shell is your friend :) So's dir() and help()

A couple quick "Getting Started" 2-page tutorials and a Firefox bookmark on Python docs should be all you need to get very productive in the language. May I suggest O'Rielly books like "Python Cookbook" or "Learning Python"?

I recommend Python Cookbook a lot more if you're a learn-by-examples type. It's designed for older 2.x releases, but all the information still holds pertinent. It has SOO many examples that you can ALWAYS find some snippet to apply to your program.

---

### Post by sapo on 2005-06-22
[QUOTE=jdong]I recommend Python Cookbook a lot more if you're a learn-by-examples type. It's designed for older 2.x releases, but all the information still holds pertinent. It has SOO many examples that you can ALWAYS find some snippet to apply to your program.[/QUOTE]

thanx.. i preffer learning this way.. i hate reading explanations.. i learn more looking at codes... i ll give it try.. thank you!

---

### Post by sapo on 2005-06-22
yo lads.. thanks for all the help.. i m already starting to make some noob scripts with python...

Can somebody post a good python forum, i love to ask noob questions in forums  :roll:

Today i ll finish the first book [http://byteofpython.info](http://byteofpython.info)

And tomorrow i m planning to start with wxpython, and maybe start my first app, today i stayed programing those kind of "Hello word" stuff, but i think that python is very very easy.. i ve learned php in 2 weeks, from nothing till making a website with admin panel, news posting, image upload etc... 

And i think that python will be quicker than it  :grin:

---

### Post by christooss on 2005-06-22
I think book at followed llink is the best for lurning pyhon

[http://greenteapress.com/thinkpython/](http://greenteapress.com/thinkpython/)

When you will get better start lurning dive in to python. It can be found on goolge and on your home machine

---

### Post by jdong on 2005-06-22
[QUOTE=sapo]yo lads.. thanks for all the help.. i m already starting to make some noob scripts with python..[/QUOTE]

Sounds like me... Backports is 90% automated now, thanks to Python: [http://ubuntubackports.org/ubp/projects/ubp-tools/ubp-build/ubp-build.py](http://ubuntubackports.org/ubp/projects/ubp-tools/ubp-build/ubp-build.py)

---

### Post by sapo on 2005-06-22
[QUOTE=jdong]Sounds like me... Backports is 90% automated now, thanks to Python: [http://ubuntubackports.org/ubp/projects/ubp-tools/ubp-build/ubp-build.py](http://ubuntubackports.org/ubp/projects/ubp-tools/ubp-build/ubp-build.py)[/QUOTE]

nice.. i ll print this script to read in the bathroom. i m sure i ll learn a lot.. yes i read source code while sitting in the throne  :roll:

edit: nice script.. hum.. that "os.something" functions.. are a kind of class to handle shell stuff? i m a little interested in making some stuff that will need a lot of interaction with shell, wget, etc etc  :grin:

---

### Post by jdong on 2005-06-22
os.system() executes the given command using your default shell. I use this as a replacement for shellscript-style programming for Python. Many of these can be re-coded in native python via the APT Python libraries, but I like the os.system() method better.

The other os functions are for looking for files, manipulating folders, etc. There are specific nt,mac,and posix modules with specific versions of these functions, but the os platform-independent generics are suitable for my purposes.



All-in-all, this script took about 2-3 hours of an afternoon, from the #! statement to automatic backports. THAT'S why I love Python :)

---

### Post by Quest-Master on 2005-06-22
[QUOTE=jdong]os.system() executes the given command using your default shell. I use this as a replacement for shellscript-style programming for Python. Many of these can be re-coded in native python via the APT Python libraries, but I like the os.system() method better.

The other os functions are for looking for files, manipulating folders, etc. There are specific nt,mac,and posix modules with specific versions of these functions, but the os platform-independent generics are suitable for my purposes.



All-in-all, this script took about 2-3 hours of an afternoon, from the #! statement to automatic backports. THAT'S why I love Python :)[/QUOTE]
 Personally I prefer os.popen("command") and its .read() properties.. it just gives you a lot more flexibility over what you're doing. :)

---

### Post by jdong on 2005-06-22
[QUOTE=Quest-Master]Personally I prefer os.popen("command") and its .read() properties.. it just gives you a lot more flexibility over what you're doing. :)[/QUOTE]

Yeah; when I actually need interaction with the command, I'd use popen... When I just want it to run (I know whether or not it worked -- if there ain't no debs around after the packaging process, it didn't work very well, did it? ;)), system() is my friend.

---

### Post by sapo on 2005-06-23
yo lads.. i m a little confused with the lists, tuples and dicts stuff..

i m a php programmer and in php we have arrays and vars... 

lists seems to me like arrays, tuples is saying here that are imutable strings.. is it constants?

and wth is this dict stuff? looks like an array, but seems diferent... someone could help understand this stuff?

thanx a lot  :grin:

---

### Post by Quest-Master on 2005-06-23
Well, this is basically what a dictionary does simply.

qm = ["hair":"black", "skin":"brown", "height":"tall"]
print "QM's hair color is " + qm["hair"]
print "QM's skin color is " + qm["skin"]
print "QM is pretty " + qm["height"] + ", I guess."

Of course, instead of using hair, skin, and height, you could use black, brown, and tall. These can become very very useful later on when programming large-scale apps. :)

---

### Post by jdong on 2005-06-23
[QUOTE=sapo]
lists seems to me like arrays, tuples is saying here that are imutable strings.. is it constants?

and wth is this dict stuff? looks like an array, but seems diferent... someone could help understand this stuff?

thanx a lot  :grin:[/QUOTE]

tuples are the basic sequential collection structure: like C arrays. They are unchangeable once they're made... So sort of like immutable strings. You can't insert/remove items from a tuple. They have to be remade from scratch.

Lists are like PHP arrays...

Dictionaries are like arrays, but indexed with arbitrary objects as opposed to integers.

---

### Post by pdpi on 2005-06-23
Personally, I just started learning Python myself. Since I have some 10 years worth of programming experience (pretty decent for a 22 year old :D), and considering I wanted to start doing some GUI programming either way, I just skimmed through some of the more popular Python tutorials (dive into python and the "official" tutorial), and keep them in a background browser tab while going through the PyGTK tutorial, which reads easily enough for me to spend more time implementing (and changing) the examples myself rather than reading through the presented code. It's that simple. So, if people are saying that wxWidgets are even easier... well... the code probably writes itself ;)

regarding the dictionaries, a dictionary is a hash table, en.wikipedia.org/wiki/Hash_table for a good description. If you want the short version, it's simply a way of changing arbitraty immutable objects ("keys") into numbers, and associating other objects ("values") to the table, using the key's hash as the position of an array (the internal representation of the hash table) to insert itself into. If you think carefully about it, and about the  way collisions (multiples keys mapping to the same number) are handled, it works much in the same way as a dictionary (so for those complaining about it, it actually IS a pretty good metaphor)

---

### Post by christooss on 2005-06-23
which pyGTK tutorial are you using. And What is "offical" tutorial?

---

### Post by sapo on 2005-06-23
hum.. i think i understand..

but in what ocassion to use dicts and lists? i m used to php so i just use arrays...

and another question.. can i have one dict inside another?

thanx guys for helping.. i m already doing some code  :grin:

---

### Post by jdong on 2005-06-23
[QUOTE=sapo]hum.. i think i understand..

but in what ocassion to use dicts and lists? i m used to php so i just use arrays...

and another question.. can i have one dict inside another?

thanx guys for helping.. i m already doing some code  :grin:[/QUOTE]

Lists are used whenever you need to add/remove items from the array during runtime. For example, if you're making an address book program that users can actively add/remove names from, you'd want to use lists. Otherwise, each add/remove operation with tuples means re-making the WHOLE ARRAY AGAIN (ouch).

Dicts are used when the particular data is best referenced by something other than numbers. For example, a list that relates name to phone number. You can do it like this:
addrbook={ "John Doe": "123-456-7890", "Bob Python":"321-654-0987"}

Then, refer to addrbook["John Doe"] to find the phone number for John Doe.


Another more interesting use is to mimick the select-case/switch structure. For example, in C:
```

switch(input_char)
{
    case 'Y':
           action1();
     case 'N':
            action2();
     default:
            action3();
}

```

In Python, functions are just a data type that supports the () "call" operators. In other words, you can assign functions to variables. So:

```

action_dict={ 'Y': action1, 'N': action2}
try:
  action_dict[input_char]();
except KeyError:
  action3()

```

It does the same thing. You're using a dictionary (specialized list) of functions.

---

### Post by sapo on 2005-06-23
thanx jdong.. now things are clearer...

i was trying that wxglade now.. but i dont like gui designers.. i think i ll learn wxPython and code it by hand.. the wxglade just messed up all the code  ](*,)

---

### Post by pdpi on 2005-06-23
[QUOTE=christooss]which pyGTK tutorial are you using. And What is "offical" tutorial?[/QUOTE]
 I'm using this tutorial: file:///usr/share/doc/python-gtk2-tutorial :)

it's on synaptic under a similar name, and can probably be found elsewhere easily. By "official" tutorial, I mean the tutorial that's on the python.org website

---

### Post by sapo on 2005-06-24
Hi fellows... i need to help..

I have learned a lot of things in the command line.. but now i ll try some gui stuff...

And i m trying to do a script to convert mp3 to ogg, mpc to mp3, and vice versa, the command line isnt the problem.. i already know how to do it...

but i m completely lost with the gui..  ](*,) 

the first thig:

I tried to make a button so the user can browse a folder... but i dont know how to do it. and i didnt find anything about... anyone could help me?

thanx  :grin:

---

### Post by sapo on 2005-06-24
thats me again hehe i ve found this:

[http://wxwidgets.org/manuals/2.5.3/wx_wxfiledialog.html#wxfiledialogctor](http://wxwidgets.org/manuals/2.5.3/wx_wxfiledialog.html#wxfiledialogctor)

I think that it is what i need.. anyone have some example code or something? cause i didnt manage how to make it work  ](*,)

---

### Post by sapo on 2005-06-24
Now the file stuff is working.. but i want to make an output terminal to write the terminal output in a text object... anyone could help me? i ve read a lot of stuff in the manual but i cant figure out how to do it.. my app is starting to gain some form  :grin:

---

### Post by jdong on 2005-06-24
find the textbox and start appending to it? ;)

---

### Post by crashtest on 2005-06-24
[QUOTE=sapo]
I tried to make a button so the user can browse a folder... but i dont know how to do it. and i didnt find anything about... anyone could help me?

thanx  :grin:[/QUOTE]

The absolute easiest method for doing gui can be found here:
[Easygui](http://www.ferg.org/easygui/) 

This will get beginners (like me) doing gui stuff in about 5 minutes.  Later on when I am more advanced I plan to learn Tkinter or wxPython.

---

### Post by sapo on 2005-06-24
[QUOTE=jdong]find the textbox and start appending to it? ;)[/QUOTE]

but how do i append the terminal output??  :-? 

i m appending vars and all that stuff.. but how do i get the terminal output and append to the textbox?

thanx for helping :)

my little program is already working.. i ll post the code later.. just have to fix some bugs..

---

### Post by christooss on 2005-06-24
I m really looking forward to see you program. Why I am new to programing and since I m lurning python as my first program language its very good to see useful programs not programs like hello world.

---

### Post by sapo on 2005-06-24
[QUOTE=christooss]I m really looking forward to see you program. Why I am new to programing and since I m lurning python as my first program language its very good to see useful programs not programs like hello world.[/QUOTE]

i ll post it soon.. but first i need to make some stuff.. and google isnt helping me  ](*,) 

the program is already working.. but the code is so freaking dirty.. i m ashamed of posting it.. i ll clean it up first and comment it  :grin:

---

### Post by christooss on 2005-06-24
You can send it to me through Privete Message

I want dirty code :)

---

### Post by sapo on 2005-06-24
[QUOTE=christooss]You can send it to me through Privete Message

I want dirty code :)[/QUOTE]

ok ok you win, but first let me comment it.. so you will understand better ;)

i m still stuck with the output stuff.. i cant make the terminal output to the textbox.. please some expert help me :(

---

### Post by sapo on 2005-06-24
The code is attached.. just take a look.. but i didnt clean it up it.. so its  VERY dirty..

The program is "working" you can select a folder and the bitrate.. then the program will create a converted_files folder inside the selected folder.. and encode the mp3 files using lame.

I ll try to make it convert a lot of audio formats like, mp3, ogg, mpc, wav, etc.. and i have to think about the id3 stuff and a tool to rename the files.. btw.. it will take some time...

but feel free to try it out  :grin: 

and i need help especially in this part:

```

                output = "\nConverting File: %s" % (i)
                self.text_output.AppendText(output)
                process = None
                status = "Please wait, encoding File %s" % (i)
                self.SetStatusText(status)
                #Exect the lame Command
	        pid = wxExecute(lame, wxEXEC_SYNC, process)
	        output = "\nFile Encoding Done!!"
                self.text_output.AppendText(output)
                status = "%s encoded sucessfully!!" % (i)
                self.SetStatusText(status)

```

I want the text_output text filed to output the terminal stream.. but i didnt managed how to do it.. plese.. any help is welcome..

---

### Post by christooss on 2005-06-24
How can one use this program without wx installed.

Why am I asking that?

If I make program and distribute it I want that user could start program with simple python my_program.py without first installing wxlibs.

Is that possible?

---

### Post by christooss on 2005-06-24
I get this error

> Traceback (most recent call last):
  File "converter.py", line 194, in ?
    app = MyApp(0)
  File "/usr/lib/python2.4/site-packages/wxPython/wx.py", line 1951, in __init__    _wxStart(self.OnInit)
  File "converter.py", line 187, in OnInit
    frame = main_frame(NULL, -1, "Music Converter")
  File "converter.py", line 25, in __init__
    self.__do_layout()
  File "converter.py", line 69, in __do_layout
    grid_sizer_2.Add(self.text_input, 0, wxEXPAND|wxFIXED_MINSIZE, 0)
NameError: global name 'wxFIXED_MINSIZE' is not defined


---

### Post by jdong on 2005-06-24
wrap the wx import statements with a try/except block.

```

try:
  import wx
except ImportError:
  print "Dude... you don't have wxpython..."

```

---

### Post by sapo on 2005-06-24
[QUOTE=jdong]wrap the wx import statements with a try/except block.

```

try:
  import wx
except ImportError:
  print "Dude... you don't have wxpython..."

```[/QUOTE]


thanx i ll do it :)

jdong, could you help me you the terminal output stuff? i ve spent a lot of time trying to make that work withou sucess :(

---

### Post by sapo on 2005-06-24
[QUOTE=christooss]How can one use this program without wx installed.

Why am I asking that?

If I make program and distribute it I want that user could start program with simple python my_program.py without first installing wxlibs.

Is that possible?[/QUOTE]

hum.. i could just make the gui outside the main program... i think i m gonna do it.. but first i want to make it a graphical tool that can be usefull for something :p

---

### Post by sapo on 2005-06-24
[QUOTE=christooss]I get this error[/QUOTE]

hum.. whats your wxPython version?

here everything is working...

btw.. i ll think about making the program and the gui in separate files.. i think that it should work better.. but i want to learn how to make the gui.. the terminal stuff isnt that difficult  :-P

And here a screenshot with everything running:

[[IMG]http://img148.echo.cx/img148/8568/screenshot26wa.th.jpg[/IMG]](http://img148.echo.cx/my.php?image=screenshot26wa.jpg)

Man.. i ve spent all the afternoon trying to make the terminal output appear in the textbox.. look the lame output in the terminal.. i want that to appear in the text box.. but i dont know how  ](*,)

---

### Post by psychicdragon on 2005-06-25
To capture the terminal output you can do something like this.
```
import commands
terminal_out = commands.getstatusoutput('your command here')
```
Took me quite a while to figure that out. I assume you've been trying to use os.system(command) right?

---

### Post by sapo on 2005-06-25
[QUOTE=psychicdragon]To capture the terminal output you can do something like this.
```
import commands
terminal_out = commands.getstatusoutput('your command here')
```
Took me quite a while to figure that out. I assume you've been trying to use os.system(command) right?[/QUOTE]

Man.. i love you  :grin:  that worked...

But now i got another problem.. while the program is encoding.. it seens like crashed... everything freezes.. i need a way to run that command in the background  ](*,)

---

### Post by dcraven on 2005-06-25
This code is what I do in a pygtk program I have. You can probably adapt it to your toolkit of choice.

```

def run(self, command):
	child_e, child_o = os.popen4(command)
	while 1:
		data_o = child_o.readline()
		self.textbuffer.insert(self.textbuffer.get_end_iter(), data_o)
		self.textview.scroll_to_mark(self.textbuffer.get_insert(), 0)
		while gtk.events_pending():
			gtk.main_iteration(False)

```

Hope that helps.
~djc

---

### Post by sapo on 2005-06-25
[QUOTE=dcraven]This code is what I do in a pygtk program I have. You can probably adapt it to your toolkit of choice.

```

def run(self, command):
	child_e, child_o = os.popen4(command)
	while 1:
		data_o = child_o.readline()
		self.textbuffer.insert(self.textbuffer.get_end_iter(), data_o)
		self.textview.scroll_to_mark(self.textbuffer.get_insert(), 0)
		while gtk.events_pending():
			gtk.main_iteration(False)

```

Hope that helps.
~djc[/QUOTE]

it didnt worked.. crashed the app  ](*,) 

i was looking at another wxPython app and to show the output in the terminal was used this:

```

    def OnIdle( self, evt ):
        # If processing hasn't been started/enabled, do nothing
        if not self.running:
            return

        # If no process is currently executing, start the next
        # one in the queue.
        if self.process is None:
            self.StartNextProcess()

        # If a process is currently running, get its output and
        # print it to the command window
        if self.process is not None and self.pid != 0:
            stream = self.process.GetInputStream()
            if stream.CanRead():
                self.txtOut.AppendText( stream.read() )
            
    # ==========================================================
    # Start the next process in the queue
    # ==========================================================
    def StartNextProcess( self ):
        # If there is a command in the queue
        if len( self.strCmdQueue ) > 0:
            self.strCurCmd = self.strCmdQueue.pop( 0 )
            # Show the command that is being executed,
            # and the number remaining in queue
            self.txtCurCmd.SetValue( self.strCurCmd )
            self.txtOut.AppendText( "Running command: %s\n" % self.strCurCmd )
            # Start the process running
            self.process = wxProcess( self )
            self.process.Redirect()
            self.pid = wxExecute( self.strCurCmd, wxEXEC_ASYNC, self.process )
            self.lblQueue.SetLabel( "Commands left to run: %d" % len( self.strCmdQueue ) )

```

This code is from tovid, i ve tried to understand it but i cant manage how to put it to work.. i undestood what it does.. but even copying the whole functions it still didnt work  ](*,)

---

### Post by Quest-Master on 2005-06-25
lol.. you can do a simple os.popen("terminal command here").read() to get terminal output.. very easy. :)

---

### Post by sapo on 2005-06-25
[QUOTE=Quest-Master]lol.. you can do a simple os.popen("terminal command here").read() to get terminal output.. very easy. :)[/QUOTE]

thats not easy

an mp3 can take 10 minutes to encode... my app stays frozen from 10 minutes..  ](*,) 

i want a better feedback for users.. i m making it by hand without the terminal output  :|

---

### Post by Quest-Master on 2005-06-25
EDIT: Never mind this, I was getting an error with your program, but it appeared that an old Warty installation of wxGTK was messing things up.. hehe.

---

### Post by jdong on 2005-06-25
[QUOTE=sapo]thats not easy

an mp3 can take 10 minutes to encode... my app stays frozen from 10 minutes..  ](*,) 

i want a better feedback for users.. i m making it by hand without the terminal output  :|[/QUOTE]

You'd need to use threads...

---

### Post by sapo on 2005-06-25
[QUOTE=jdong]You'd need to use threads...[/QUOTE]

Where do i find some info about it?

thanx

---

### Post by christooss on 2005-06-25
Where can I lurn more about python and XML

A link to one big cool tutorial would be fine :-D

---

### Post by christooss on 2005-06-25
Sorry to bother you again but I am unable to find wxdemos

---

### Post by sapo on 2005-06-25
[QUOTE=christooss]Where can I lurn more about python and XML

A link to one big cool tutorial would be fine :-D[/QUOTE]

this interests me too  :grin: 

[QUOTE=christooss]Sorry to bother you again but I am unable to find wxdemos[/QUOTE]

wxdemos??? :?

---

### Post by Quest-Master on 2005-06-25
christooss: Search for SAX and DOM with Python. Learn to use them, and you're set.

---

### Post by christooss on 2005-06-25
Hm do I have to intal pyxml for sax or dom work? Probably yes

/edit It is a YES but witch package do I have to install pyxml comes with defalult ubuntu installation?

---

### Post by sapo on 2005-06-26
hi fellows... please somebody could teste the 0.0.0.0.0.1/2 version of my program? hehe

it is working, but its still simple, just rename the attached file to .py  :roll: 

It already can:

Converts ogg to mp3 and mp3 to ogg, you just have to select the folder where the files are.

And it converts even if you have mp3 and ogg files in the same folder.. it will convert everything to the selected format.

it requires:
wxPython, lame, vorbis-tools

please somebody test it and post a feedback.. the terminal output i made by hand cause i didnt managed how to get the terminal output.. btw.. i m working on it..

The major problem is that the app cant copy the id3 tag to the file.. so **you are gonna lose the id3 in the new file**

If somebody have time and interest feel free to comment if something is wrong in my code.

thanx

---

### Post by christooss on 2005-06-26
I still get errors

> Traceback (most recent call last):
  File "converter2.py", line 314, in ?
    app = MyApp(0)
  File "/usr/lib/python2.4/site-packages/wxPython/wx.py", line 1951, in __init__    _wxStart(self.OnInit)
  File "converter2.py", line 307, in OnInit
    frame = main_frame(NULL, -1, "Music Converter")
  File "converter2.py", line 26, in __init__
    self.__do_layout()
  File "converter2.py", line 70, in __do_layout
    grid_sizer_2.Add(self.text_input, 0, wxEXPAND|wxFIXED_MINSIZE, 0)
NameError: global name 'wxFIXED_MINSIZE' is not defined


---

### Post by sapo on 2005-06-26
[QUOTE=christooss]I still get errors[/QUOTE]


it seens to be something with your wxPython.. i tried to remove this thing that is giving you erros.. but the layout just messed up..  ](*,) 

btw here another version with some corrected bugs:

[http://xgn.no-ip.org:1000/downloads/converter.py](http://xgn.no-ip.org:1000/downloads/converter.py)

---

### Post by christooss on 2005-06-26
I got a little question

How to put raw_input to the list

number = raw_input(Write a number: )

How can I now add number to list?

---

### Post by sapo on 2005-06-26
[QUOTE=christooss]I got a little question

How to put raw_input to the list

number = raw_input(Write a number: )

How can I now add number to list?[/QUOTE]


list.append(number)

you mean add a number to a list right?

---

### Post by christooss on 2005-06-26
Yes I already solved this
```

b = []
n = 0
while n < 15:
        t = raw_input('We will add this to the list ')
        if len(t) == 0:
                break
        b.append(t)
        n = n + 1
```


of course you can increase n but 15 suits me
Thanks anyway

---

### Post by christooss on 2005-06-29
For me wxpython is history. Why beacause there is no good tutorial about this. Im moving to pygtk. I think I will manage to lurn quicker.

I hope this odisey will end with successes. Maybe I will than come back to wxpython. Maybe

---

### Post by Quest-Master on 2005-06-29
[QUOTE=christooss]For me wxpython is history. Why beacause there is no good tutorial about this. Im moving to pygtk. I think I will manage to lurn quicker.

I hope this odisey will end with successes. Maybe I will than come back to wxpython. Maybe[/QUOTE]
 
Hehe, in time you'll learn that using wx you'd probably code more than a third less than what you would with PyGTK.

---

### Post by christooss on 2005-06-29
Hm ok maybe thats true but... For begginer its easyer to start with planty of help.

---

### Post by sapo on 2005-06-29
[QUOTE=Quest-Master]Hehe, in time you'll learn that using wx you'd probably code more than a third less than what you would with PyGTK.[/QUOTE]

thats true!

The official documentarion sux... and we cant find almost anything about it.. btw i ve managed how to do some simple things with it.. 

But still i cant find a way to use threadings properly with wxPython  ](*,)

---

### Post by christooss on 2005-06-30
I find pyGTK + Glade + simplegladeapp.py far more easier to use than wxpython and boaconstructor.

And I would recommend this combination to every newbie to python and to programing.

---

### Post by Quest-Master on 2005-06-30
Use wxGlade instead of Boa.

I find it interesting that people actually like pyGTK more than wxPython. Never seen it before. :o

---

### Post by sapo on 2005-06-30
[QUOTE=Quest-Master]Use wxGlade instead of Boa.

I find it interesting that people actually like pyGTK more than wxPython. Never seen it before. :o[/QUOTE]

thats what i m using.. but theres inst some good tutorials about wxPython.. and the official documentation is a little difficult to understand  ](*,)

---

### Post by JuanC on 2005-07-01
Why not using PyQT?

With the Qt 4 release , QT library is open source in all OS.
[http://www.trolltech.com/newsroom/announcements/00000209.html](http://www.trolltech.com/newsroom/announcements/00000209.html)

---

### Post by christooss on 2005-07-01
Guys I am learning programing. For now I will stick to my pygtk combination and become a hell of a programer :)

in autum I will have to start learning Java. Its the only language that they use at my colleage.

---

### Post by python_guy on 2005-07-05
I think GUI is python's weak point (so the same for some script language)

1. I used glade and pygtk on windows (small programs for company). it depend on the gtk library and libglade. At that time, dropline ceasted their version for better compatibility and the other runtime doesn't have libglade. I ran in serious troubles.

(Windows users should be happier now, they have the gustin's pygtk, the official runtime from glade for win and documents from pygtk.doc)

2. I tried to switch my project to wxpython, I installed wxPython and it really take time and patient trying the compile options. The API wasn't fixed and people who use unicode have to use 2.5.x development branch, When a different sub-sub version is used, the program would behave funny.
(The API is fixed/locked in 2.6)

3. pygtk is doing ok in linux, wxPython could also work with py2exe. However, they have their problems, I realized that java is better for cross platform gui programming

However, I don't know Java and I found out that doing web programming is actually much easier. I used a less productive method. I use mod_python directly with apache. I didn't know how mod_python work and resetted apache infinity times just for terminated my buggy python program. The result seems OK, I can add small programs to the company's intranet. It has shortages but it is relatively easy.

I wished I know the existence of httpserver modules, zope, plone, cherrypy and cheetah. I wasted some time, but it seems that web programming is the way to go. I think bundle the program with intergrated server would work for small office. (Example, moin moin desktop ver)

---

### Post by thierryl on 2006-11-23
Ok, I searched for a thread on this specifically but all i got was this thread on python.

Has anyone found an easy way to install PyXML on Ubuntu? So far I havent found any packages for it and .gz won't run under 'python setup.py install' etc.

Would really like if someone had a link to a repository on this... 

:)

Thanks
T.

p.s. and yes I unpacked the .gz first... lol...

---

### Post by daubers on 2007-05-16
> **jdong said:**
> You'd need to use threads...

I'm also trying to do this but haven't found anything on doing it..... is there an example somewhere that I could follow fairly easily?

---

