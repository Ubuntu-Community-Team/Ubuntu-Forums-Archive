---
title: "Python: Replacing strings in a file"
date: 2007-11-22
forum: Programming Talk
---

### Post by kwaanens on 2007-11-22
Hey there. I have no skills in Python, but I'm trying to crawl along with finding the tool for something simple.

I have a python script that generates a file with lines like this:
widget_colour=red
("widget_colour" only comes in one place.)

Now I want to replace "COLOUR" with "red" in another file.

I have narrowed it down to something like:
self.fh1 = self.fh1.replace('COLOUR', 'xxxxxxxxxxxx')

(Meaning that, that string replaces 'COLOUR' with 'xxxxxxxxxxx'. That has been tried and tested.)

What to put in in stead of the x-es?

I tried Googling all over the place, but it's hard when you don't know what you're looking for.

Thanks!

---

### Post by dwblas on 2007-11-22
Something like the following should work
```
line_in="widget_colour=red"
if "colour" in line_in:
   substrs=line_in.split("=")
   line_out = "some other stuff about colour=" + substrs[-1]
   self.fh1.write( "%s\n" % (line_out))
```

---

### Post by slavik on 2007-11-23
python implementation of sed?

---

### Post by LaRoza on 2007-11-23
> **slavik said:**
> python implementation of sed?

Perhaps there is more the app that requires more features, or the OP doesn't know sed.

---

### Post by kwaanens on 2007-11-23
Thanks for helping me out!

I was not being very clear in my attempt top explain what I was trying to do. (It's hard to explain this when I know to little about Python) At least the suggested lines do not work.

Anyway, my script is here: [http://pastebin.com/d3bab7979](http://pastebin.com/d3bab7979)

The first marked region is where the settings are recorded (works fine), the latter where the settings are collected.
widget_colour can be any of black, blue, red and grey, as seen in the options (and "widget_mode" can similarly be of any one listed value)

What I'm looking for, is the best way to apply the settings. (I could use the specific settings file generated at first marked region, because it seems that it's not possible to run more than one instance at the time anyway (hoping to change that as well, but that is probably more of a gtkmozembed-thing))

The script is ripped from another screenlet that does something similar, so there are probably some redundancies that can be removed, but I'll save those for later.

---

### Post by dwblas on 2007-11-23
For starters, here is some modified code. I think you want readlines instead of read on line 128.  read is generally used to read a specific number of bytes while readlines reads the entire file.  A print statement was added to show what was read.  Also, you want to consider breaking this up even further.  Adding options could become a separate function for example.  It's easier to understand and debug..```
#
                # make new html source from values in config settings
                self.fh = open(str(self.mypath)+'LastWidgetSource.html', 'r')   # declare LastWidgetSource.html as fh
                self.fh1_data = self.fh.readlines()                             # read fh and declare it as fh1
                self.fh.close()                                                 # we're done with fh, close it
                print self.fh1_data
#
                fh2 = open(str(self.mypath)+'gtoload.html', 'w')                # write file gtoload.html, declare it as fh2
                for line_in in self.fh1_data:
                   print "original line =", line_in
                   if 'USERNAME' in line_in:
                      line_in = line_in.replace('USERNAME',str(int(380*self.scale)))   # replace in fh1. what?
                   if 'COLOUR' in line_in:
                      line_in = line_in.replace('COLOUR', (self.widget_colour))     # replace in fh1. what?
                   if 'MODE' in line_in:
                      line_in = line_in.replace('MODE', (self.widget_mode))         # replace in fh1. what?
#
                   print "modified line =", line_in, "\n\n"
                   fh2.write(line_in)                                             # write fh1 into fh2
#
                fh2.close()                                                     # we're done with fh2, close it
```I don't know anything about screenlets, but generally you have to retrieve the selection with some sort of get statement which I don't see in your code.  But again, I am not familiar with screenlets.

---

### Post by kwaanens on 2007-11-23
I think there is a misunderstanding here, probably due to my poor explanation and/or understanding.

First off, replacing my lines with yours gets me:
 __init__
    fh2.write(self.fh1)                                             # write fh1 into fh2
TypeError: argument 1 must be string or read-only character buffer, not None

Second, these things
str(int(int(380)*self.scale))
 (self.widget_colour)
 (self.widget_mode)

from your quote are just jibberish I guess. That's only me fiddling around, so they at least won't do what I want.

The original code did read the entire text of LastWidgetSource.html (See attached file, renamed to txt)

To try to be clearer, I want this file read, the words USERNAME, COLOUR and MODE to be replaced by whatever is given in 
self.add_option(StringOption('Widget settings'......

Whether those values are taken from within the script or directly from a specified settings file is not *that* important, but I prefer the former.

---

### Post by dwblas on 2007-11-24
> First off, replacing my lines with yours gets me:
__init__
fh2.write(self.fh1) # write fh1 into fh2
TypeError: argument 1 must be string or read-only character buffer, not NoneNote that I was not writing self.fh1 to the second file, but taking each line/record in the list, which I named self.fh1_data to try to clarify.  You can not write an entire list to a file, which is what you were originally trying to do.  If you print self.fh1 or whatever it is named, you can see that it is a list.  Usually, you examine each record or line of the list, replace where appropriate, and then write that one line to the file.  The problem starts with trying to do too much at once.  Comment out the sections that you will test later with Python's  triple quotes """  

First, get the values for colour et al that you want to use and print them out to be sure that these are the variable names that you want and that they contain the correct vaules.  

Then, open the first file and write it's contents to the second file one line at a time, verifying the second file by veiwing it with a text processor.  

Then, test for the replacement conditions and replace, printing the contents before and after replacing (see my previous post) and write to the second file.  You can redirect the print output to a file or just output to a third file if the messages get too long.

As a general rule, in the beginning you want to write somewhere around  20 lines or one srceen and test, then move on to the next 20.

---

