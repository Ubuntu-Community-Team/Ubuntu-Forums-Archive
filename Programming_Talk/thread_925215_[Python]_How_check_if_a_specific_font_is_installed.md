---
title: "[Python] How check if a specific font is installed?"
date: 2008-09-20
forum: Programming Talk
---

### Post by gomputor on 2008-09-20
Hello everybody.
I'm working on a little app written with PyGtk, something like a text
editor and what i want to do is to set a default font for the editor
(no need to answer this, I aleady know how to do it) and check if that
specific font is installed in the user's system. If not then to set a
secondary font. So how can I check if the font I want is installed?
I did a search but found nothing to help me.

Another question I have (and I don't know if I should post it in a
separate thread), is how to get the encoding a text file is written?
(like if it's windows-1252 or utf-8 or whatever.)
I know how to decode it if I already know it's encoding, and decode it
in the encoding I want, but how to check what's the encoding of the file
if I don't know it before hand?
And of course I mean how to check them programmatically :)

Thank you in advance.
(I'm working on Ubuntu 8.04, Python 2.5.2, PyGTK 2.12.1)

---

### Post by pmasiar on 2008-09-20
I don't know GTK, but my hunch is (as other systems do it) that you specify list of fonts, from specific to more generic, to some standard guaranteed to be present, and GUI has a way to walk down the list and pick first match.

You cannot be sure which encoding is used - you can only make unreliable guess. Encoding must be provided by the author.

---

### Post by gomputor on 2008-09-21
Ok guys and gals, after 3 days of beating my head, googling a lot, reading the docs and searching in various forums, I finally found the answer for the font part of my thread.
As I'm pretty new to Ubuntu and PyGtk (nearly 2 months, after 10 years working with Windows), from what I read I came to the conclusion that Gtk+ (and PyGtk) use pango to handle the fonts of the system and all the applications (if gnome is used of course, and please correct me if I'm wrong).
So I started to read more carefully the pango documentation, and there was the answer. And it's a very very simple one I might say.
So here it is if someone is interested:
[PHP]
# The get_pango_context() method returns the pango.Context with
# the appropriate colormap, font description and base direction
# for the selected widget (text_view in our case, assuming
# text_view is a gtk.TextView)

context = text_view.get_pango_context()

# list_families() returns a tuple containing a set of the fonts
# that pango can use with the selected widget

fonts = context.list_families()

# so we iterate in the font tuple
for font in fonts:
    # if our font is found (get_name returns a string)
    if font.get_name() == 'Terminus':
        # set that font for our text_view and break the loop
        text_view.modify_font(pango.FontDescription('Terminus 8'))
        break
    else:
        # else set our second choice font
        text_view.modify_font(pango.FontDescription('DejaVu Sans Mono 8'))
[/PHP]
Pretty simple and straightforwarded after all, eh?
And of course you must import pango to use it.

Now as for the encoding question.... well I didn't find anything yet, but
I got hope :)

---

### Post by unutbu on 2008-09-21
gomputor, thanks for the default font setting code.

Regarding encoding, pmasiar already gave the answer:
Abandon hope all ye who enter here

The computer only sees a file composed of 0's and 1's. How it chooses to convert blocks of 0's and 1's into characters is an arbitrary choice. The underlying data (0's and 1's) give no indication what character encoding to use.

From Mark Pilgrim's "Dive Into Python" ([http://diveintopython.org/xml_processing/unicode.html):](http://diveintopython.org/xml_processing/unicode.html):)
> 
Exchanging documents between systems was difficult because **there was no way for a computer to tell for certain which character encoding scheme the document author had used**; the computer only saw numbers, and the numbers could mean different things.
Now, if you had a dictionary, I suppose you could guess/test various encodings and calculate how many words are recognized in each encoding and then select the encoding which contains the most recognized words...

---

### Post by gomputor on 2008-09-21
First of all thanks for the replies. :)
Yeah, I finally found out that looking to find the encoding inside some info that this file may have (like [encoding=this]), is absolutely useless. No such info there.
So I figured out to use something like this below:
[PHP]

import sys

# gather the encodings I thing that the file may be encoded inside a tuple
encodings = ('windows-1253', 'iso-8859-7', 'whatever codec....')

try:
    f = open(filename, 'r').read()
except Exception, e:
    print e                          #just to check if it's an IOError or what
    sys.exit(1)

for enc in encodings:
    try:
        # try to decode the file with the first encoding from the tuple.
        # if it succeeds then it will reach break, so we will be out
        # of the loop (something we want on success)
        data = f.decode(enc)
        print 'succeded enc= ', enc  # just for debbuging purposes
        break
    except Exception, e:
        # if the first encoding fail, then with the continue
        # keyword will start again with the second encoding from
        # the tuple an so on.... until it succeeds.
        print e                      # just for debbuging purposes (and not only)
        continue
        
# ............
# now do something with data, like encode it in utf-8
# or whatever encoding you want, or just view it.....
# ...........

[/PHP]

If anyone has a better idea then I'll be very happy to see it! :)

---

