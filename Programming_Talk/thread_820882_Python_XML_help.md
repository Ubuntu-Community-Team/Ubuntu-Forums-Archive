---
title: "Python XML help"
date: 2008-06-06
forum: Programming Talk
---

### Post by dbbolton on 2008-06-06
I have an XML file containing this:

```

        <entry name="font" mtime="1211869682" type="string">
                <stringvalue>FONTNAME</stringvalue>
        </entry>

```

How can I get python to get the line in the middle and make it a string? I know how to get a line containing a search string, but the problem is that the "stringvalue" element appears in the file several times, and "FONTNAME" changes. The only string that could be used to find this is "font", but it occurs in the line before the line I want. Any suggestions?

---

### Post by [h2o] on 2008-06-06
> **dbbolton said:**
> I have an XML file containing this:

```

        <entry name="font" mtime="1211869682" type="string">
                <stringvalue>FONTNAME</stringvalue>
        </entry>

```

How can I get python to get the line in the middle and make it a string? I know how to get a line containing a search string, but the problem is that the "stringvalue" element appears in the file several times, and "FONTNAME" changes. The only string that could be used to find this is "font", but it occurs in the line before the line I want. Any suggestions?

Take a look at one of the xml parsers that are shipped with python. I have only tried "minidom" ([http://docs.python.org/lib/module-xml.dom.minidom.html](http://docs.python.org/lib/module-xml.dom.minidom.html)) but it works nicely.

Or you could iterate through the lines and find all lines that contain the '<entry name="font"' string and then extract the value from the next line:

```

extract_data = False
for line in lines:
 if line.index('<entry name="font"') >= 0:
  extract_data = True
 elif extract_data:
  # Extract the data from the tagusing split or whatever
  # Then use the data in some way...
  extract_data = False

```

---

### Post by pmasiar on 2008-06-06
Do you have just this small snippet, or is is part of big file?

Small texts with fixed structure you can split on text literals, bigger/flexible XML files are much harder. Don't try to parse big XML using re. Use ElementTree; or BeautifulSoup for HTML.

---

### Post by nick_h on 2008-06-06
You could use the [expat](http://www.python.org/doc/current/lib/module-xml.parsers.expat.html) XML parser.

Here is a modified version of the example code:
```
import pyexpat

# 3 handler functions
def start_element(name, attrs):
    print 'Start element:', name, attrs
def end_element(name):
    print 'End element:', name
def char_data(data):
    print 'Character data:', repr(data)

p = pyexpat.ParserCreate()

p.StartElementHandler = start_element
p.EndElementHandler = end_element
p.CharacterDataHandler = char_data

p.Parse("""<?xml version="1.0"?>
<entry name="font" mtime="1211869682" type="string">
<stringvalue>FONTNAME</stringvalue>
</entry>""", 1)
```

---

### Post by dbbolton on 2008-06-06
> **'[h2o] said:**
> Take a look at one of the xml parsers that are shipped with python. I have only tried "minidom" ([http://docs.python.org/lib/module-xml.dom.minidom.html](http://docs.python.org/lib/module-xml.dom.minidom.html)) but it works nicely.

Or you could iterate through the lines and find all lines that contain the '<entry name="font"' string and then extract the value from the next line:

```

extract_data = False
for line in lines:
 if line.index('<entry name="font"') >= 0:
  extract_data = True
 elif extract_data:
  # Extract the data from the tagusing split or whatever
  # Then use the data in some way...
  extract_data = False

```

Here is what I've tried:
```

if exists(os.path.expanduser("~/.gconf/apps/gnome-terminal/profiles/Default/%25gconf.xml")):
     extract_data = False
     for line in open(os.path.expanduser("~/.gconf/apps/gnome-terminal/profiles/Default/%25gconf.xml")):
          if line.index('<entry name="font"') >= 0:
               extract_data = True
          elif extract_data:
               termfont = line
               break
else:
    termfont = "fghsrtfyhfgh"

```

term font ends up as "fghsrtfyhfgh". What did I do wrong?

> **pmasiar said:**
> Do you have just this small snippet, or is is part of big file?

Small texts with fixed structure you can split on text literals, bigger/flexible XML files are much harder. Don't try to parse big XML using re. Use ElementTree; or BeautifulSoup for HTML.

It is a large gconf XML file.

---

### Post by days_of_ruin on 2008-06-06
What exactly are you trying to do?
I have been working with gconf files lately and I used the python
gconf module.
```
>>>import gconf
>>>c = gconf.client_get_default()
>>> c.get_value("/desktop/gnome/interface/font_name")
'Liberation Sans 10'

```

---

### Post by dbbolton on 2008-06-06
> **days_of_ruin said:**
> What exactly are you trying to do?
I have been working with gconf files lately and I used the python
gconf module.
```
>>>import gconf
>>>c = gconf.client_get_default()
>>> c.get_value("/desktop/gnome/interface/font_name")
'Liberation Sans 10'

```
That is exactly what I want to do! I wasnt aware of the gconf module. Thank you very much :guitar:

---

### Post by pmasiar on 2008-06-06
import gconf.... reminds me about this cartoon:

[http://imgs.xkcd.com/comics/new_pet.png](http://imgs.xkcd.com/comics/new_pet.png)

---

### Post by LaRoza on 2008-06-06
> **pmasiar said:**
> import gconf.... reminds me about this cartoon:


I thought it was a joke myself...

---

### Post by days_of_ruin on 2008-06-06
> **LaRoza said:**
> I thought it was a joke myself...
Huh?What about that cartoon isn't a joke?

---

### Post by nick_h on 2008-06-07
> import gconf.... reminds me about this cartoon:
which reminded me of this one:

[http://imgs.xkcd.com/comics/python.png](http://imgs.xkcd.com/comics/python.png)

---

### Post by pmasiar on 2008-06-07
> **days_of_ruin said:**
> Huh?What about that cartoon isn't a joke?

joke candidate was not the cartoon, but "import gconf". Looked really close to linked cartoons. Possibly you may want to upgrade your sense of humor :-)

---

### Post by LaRoza on 2008-06-07
> **days_of_ruin said:**
> Huh?What about that cartoon isn't a joke?

I thought the initial "import gconf" was a parody on that.

---

### Post by days_of_ruin on 2008-06-08
> **pmasiar said:**
> joke candidate was not the cartoon, but "import gconf". Looked really close to linked cartoons. Possibly you may want to upgrade your sense of humor :-)

I wasn't making a joke when I posted "import gconf".
Considering that "gconf" isn't an english word or anything I don't see
how that is comparable to "import soul".

---

### Post by LaRoza on 2008-06-08
> **days_of_ruin said:**
> I wasn't making a joke when I posted "import gconf".
Considering that "gconf" isn't an english word or anything I don't see
how that is comparable to "import soul".

Well, someone says they want to use Python to edit gconf, and it just so happens to have a module named "gconf" that is easily imported.

It is the same principle.

---

### Post by Wybiral on 2008-06-08
> **days_of_ruin said:**
> I wasn't making a joke when I posted "import gconf".
Considering that "gconf" isn't an english word or anything I don't see
how that is comparable to "import soul".

Well, it's funny because it's a cliché for Python.

Person #1 "I'm trying to write *thing* in python"

Person #2 "Oh, don't waste your time, just use: import *thing*"

Happens all the time :)

---

### Post by pmasiar on 2008-06-09
> **Wybiral said:**
> Happens all the time :)

It even has it's own name: "Guido's little time machine". It works like this:

You need some functionality. You post about it to forums or mailing list. Guido reads it, jumps to his LTM, goes one or two versions of Python back, and adds the module you need, so by time he is back, Python has that module/functionality by default (in core), or downloadable module.

Guido's LTM is one of the best features Python has :-)

---

