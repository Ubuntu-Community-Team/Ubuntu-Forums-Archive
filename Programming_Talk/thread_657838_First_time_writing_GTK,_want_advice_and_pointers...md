---
title: "First time writing GTK, want advice and pointers..."
date: 2008-01-04
forum: Programming Talk
---

### Post by smartboyathome on 2008-01-04
I am wanting to write a GUI for my script in GTK, but don't know where to begin. I would like it to pop up a window which has the instructions for using it, which asks me for the file I want to encode, what I want it to be saved as, and then a button to push to encode it. I would like the encode and decode boxes to have buttons on the side which would pop up a new window and allow me to navigate to the files/folders where I want to save it (for the encode box, I would like it to be kinda like the open box in many gtk programs, and for the decode box I would like it to be like the save box in many gtk programs). Thanks to everyone who helps.

PS: Script can be found in [this topic]("http://ubuntuforums.org/showthread.php?t=650008") (post #6).

---

### Post by ZuLuuuuuu on 2008-01-04
You can begin by reading GTK+ tutorial:

[http://www.gtk.org/tutorial](http://www.gtk.org/tutorial)

After a few days from beginning you will be able to do simple GUI programs with GTK. And you can ask your question here and there:

[http://www.gtkforums.com](http://www.gtkforums.com)

---

### Post by smartboyathome on 2008-01-04
Thanks, ZuLu, I will look at those.

---

### Post by MicahCarrick on 2008-01-04
Here's my 2 cents...

First, work through a bit of the above mentioned tutorial and read about GTK so that you understand the theory of a "main loop", Widgets as objects (Object Oriented Programming), and "signals".

Once you have the basics, you may want to switch to using Glade to build your interface. Here's my tutorial on the subject: [GTK+ and Glade3 GUI Programming Tutorial - Part 1]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

Then you can pick a programming language to implement your glade file. Most people opt for Python or C. The above tutorial works through both of those languages.

Spend the time to understand how the GTK manual is layed out. It will be your best friend. In my own experience, I learned 80% of what I know about GTK through the manual as I worked out projects. Install the program devhelp and the corresponding docs so you can search through the manuals on your computer:

yum install devhelp libgtk2.0-doc

And some of my favorite resources for GTK are the GTK+ Forums ([http://www.gtkforums.com](http://www.gtkforums.com)), the GTK+ mailing list, #gtk IRC channel, and the GNOME development pages ([http://library.gnome.org/devel/](http://library.gnome.org/devel/))

---

### Post by smartboyathome on 2008-01-18
I made the GUI for my encoder based on your tutorial MicahCarrick, but I can't figure out what to do next (ie, how to start coding) the my converter in PyGTK. I tried converting my .glade file to .xml like you said to do to your tutorial glade file, but it had an error and won't convert it. The error was:
```
  File "/usr/bin/gtk-builder-convert", line 470, in _convert_dialog_response
    if (node.tagName == 'object' and
AttributeError: Document instance has no attribute 'tagName'
```
I would like to start programming this, but don't know how.

Also, when I open the file in Glade, it doesn't show, and I have to make the whole thing over again to make changes. Is there a way around this? Thanks for everyone's help.

Smartboy

---

### Post by smartboyathome on 2008-01-20
bump

please help, I would like to learn PyGTK so I can put this together.

---

### Post by fissy on 2008-01-20
You might find it easier to use zenity in your script rather than writing a C program to run a single shell command. [zenity]("http://man.cx/zenity") displays gtk widgets (like a file chooser) from shell commands.

e.g.

```

#!/bin/sh

inputfile = $(zenity  --title="Select a file to encode" --file-selection)

outputfile = $(zenity --title="Choose output file" --file-selection)

mencoder $inputfile -ovc lavc -oac mp3lame -lameopts cbr:br=128 -ffourcc XVID -lavcopts vcodec=mpeg4:vbitrate=256 -vf scale=220:176,crop=220:176 -ofps 15 -o $outputfile >/dev/null 2>/dev/null | zenity --progress --pulsate

zenity --text-info "finished"

```

I'm not at a linux box right now so i can't test this.

Fissy

---

### Post by smartboyathome on 2008-01-20
That doesn't work unfortunately, since the input file cannot be found (though I chose it from the file chooser), and the output file cannot be chosen since it doesn't exist.

---

### Post by majormar on 2008-01-24
I am also getting this exact error. If I use the -w option I can get the output file to generate, but without "window" object descriptions. Any pointers to a solutions are appreciated. Here is the exact error I am getting.

 gtk-builder-convert ffmpeggui.glade ffmpeggui.xml
Traceback (most recent call last):
  File "/usr/bin/gtk-builder-convert", line 690, in <module>
    sys.exit(main(sys.argv))
  File "/usr/bin/gtk-builder-convert", line 678, in main
    conv.parse_file(input_filename)
  File "/usr/bin/gtk-builder-convert", line 147, in parse_file
    self._parse()
  File "/usr/bin/gtk-builder-convert", line 223, in _parse
    self._convert(node.getAttribute("class"), node)
  File "/usr/bin/gtk-builder-convert", line 249, in _convert
    self._default_widget_converter(node)
  File "/usr/bin/gtk-builder-convert", line 266, in _default_widget_converter
    self._convert_dialog_response(node, object_id, response)
  File "/usr/bin/gtk-builder-convert", line 470, in _convert_dialog_response
    if (node.tagName == 'object' and
AttributeError: Document instance has no attribute 'tagName'

---

### Post by psychicdragon on 2008-01-24
I've never used GtkBuilder before. Iwasn't even aware that it was in Gtk yet. But, I can provide an example of and PyGtk app that uses libglade.

```
#!/usr/bin/env python
 
import gtk, gtk.glade
 
class MyApp:
  def __init__(self):
    self.widgets = gtk.glade.XML("my_glade_file.glade") 
    dic = {"on_window_destroy" : gtk.main_quit}
    self.widgets.signal_autoconnect(dic)
    self.widgets.get_widget("window").show()
 
if __name__ == "__main__":
  app = MyApp()
  gtk.main()
```

---

### Post by fissy on 2008-01-25
> **smartboyathome said:**
> That doesn't work unfortunately, since the input file cannot be found (though I chose it from the file chooser), and the output file cannot be chosen since it doesn't exist.

Well I did say I couldn't test it ;-)

The code below works, but the output file is hard coded to "output", though you can change the directory. There's also no error checking at all.

fissy

```

#!/bin/sh

inputfile=$(zenity  --title="Select a file to encode" --file-selection)
outputdir=$(zenity --title="Choose output directory" --file-selection \
        --directory)

mencoder $inputfile -ovc lavc -oac mp3lame -lameopts cbr:br=128 \
        -ffourcc XVID -lavcopts vcodec=mpeg4:vbitrate=256 \
        -vf scale=220:176,crop=220:176 -ofps 15 -o `echo $outputdir"/output"` \
        | zenity --progress --pulsate --auto-kill --auto-close

zenity --info --text "finished"


```

---

### Post by DugDra on 2008-01-27
Regarding:
gtk-builder-convert",
AttributeError: Document instance has no attribute 'tagName'

I also had this problem. The minimum example.glade file that I found with this problem was a top level window with a container and a button. 

I'm very new to GTK programing, I may not have a file or something else I need for  gtk-builder-convert to work correctly.  I was able to convert several other x.glade  files successfully.
Doug

---

### Post by MicahCarrick on 2008-01-27
GtkBuilder is a relatively new replacement for libGlade. If you find it easier to use Glade until you get a handle of things, they are very similar and you should be able to easily make the migration down the road.

If you want to send me your .glade file which you are trying to convert and the python code you're using to display it, shoot it to my email address and I'll figure it out and let you know.

---

### Post by dmrlook on 2008-01-31
Hey Folks - any luck with the error "AttributeError: Document instance has no attribute 'tagName'".  I just ran into it as well last night as I was following the tutorial.  If I delete the button, all works well and my program runs. Once I add back the button, I can't convert the glade file to an xml file due to the error.

Any help would be appreciated.

Thanks,!

---

### Post by ad_267 on 2008-02-03
I had the same problem converting glade files to xml. I found the answer here: [http://bugzilla.gnome.org/show_bug.cgi?id=496344](http://bugzilla.gnome.org/show_bug.cgi?id=496344)

To fix it open up the glade file in a text editor and remove the line <property name="response_id">0</property> under the widgets with class="GtkButton"

Edit: Micah, I've been reading through your tutorials and have found them very helpful thanks! I have a very small amount of experience programming in C and VisualBasic and I'm looking forward to reading the rest of your tutorial on programming the text editor with Glade3 and C/Python.

---

### Post by marf88 on 2008-02-03
Micah just wanted to say awesome tutorial, keep up the great work.

I was playin around with your tutorial and I ran into this problem as well. I posted comment about it but now I realize the solution posted here.

---

