---
title: "Need basic help with Python file output"
date: 2010-08-20
forum: Programming Talk
---

### Post by TheShader on 2010-08-20
Hello, I have a little experience about programming. I want to make a configuration file generator with python. I'm thinking of making it like this:

input the variables
open the file
file.write('{some code%d}\n{some code%d}...' %var1 %var2 ...) 

But is there a way of defining the variables in a text file, and making Python find and replace them? Which one is better? Is there a better, or easier way of doing this? Thanks :popcorn:

---

### Post by oldfred on 2010-08-20
I have been teaching myself python. I use geany & glade also. In glade I need the buttons to add to my python code so I wrote a simple parser to find then & output in a format I could directly paste into my code.

This parses a glade file for buttons and outputs a test file. I have only run it from geany so I am not even sure it works on its own yet.

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-

import re, csv

try:
    filename = "test.py"
    ifile = open(filename, "w")
except IOError:
    Return

def main():
    datafile = file('main.glade')
    #!/usr/bin/env python
    # -*- coding: utf-8 -*-
   
    for line in datafile:
        #a = re.search('object class="GtkButton".*?id="(.*?)">', line)        
        a = re.search('object class=.*?id="(.*?)">', line)
        if a:
             quote = a.group(1)
             #self.btn_go = self.builder.get_object("btn_go")
             #print 'self.' + quote +' = self.builder.get_object("' + quote + '")'
             text1 = 'self.' + quote +' = self.builder.get_object("' + quote + '")\n'
             ifile.write(text1)
            
    datafile = file('main.glade')        
    for line in datafile:
        m = re.search('signal name="clicked".*?handler="(.*?)"/>', line)
        if m:
            quote = m.group(1).strip()
            #def on_btn_forward_clicked(self, btn):
            #print 'def ' + quote + '(self, btn):'
            #print '    pass'
            text2 = 'def ' + quote + '(self, btn):\n'
            text3 = '    pass\n'
            ifile.write(text2)
            ifile.write(text3)

def closefile():
    ifile.close()

if __name__ == "__main__":
    # Someone is launching this directly
    main()
```

---

### Post by s1ightcrazed on 2010-08-20
Not sure I understand exactly what you are trying to do. If you're going for a 'hand-editable' config file, something that looks like:

item1=parameter
item2=parameter
# This is a comment 
item3=parameter

Then you could use dictionaries and a split to store and to write them. I've done similar things many times. 

```

config_dict={}
config_file=open('/path/to/config_file, 'r')
for line in config_file:
        if line[0] != "#":
                item, val=line.split("=")
                config_dict[item]=val
config_file.close()

```

or do it all with a generator:

```
config_dict=dict([line.split("=") for line in config_file where line[0] != "#" and line[0] != "\n"])
```

Just do the opposite for the writes.

---

### Post by StephenF on 2010-08-20
The batteries are included.

[http://docs.python.org/library/configparser.html](http://docs.python.org/library/configparser.html)

---

### Post by TheShader on 2010-08-20
Thanks for advices ^^ I've made it a little different, since I had to make it all line-by line. It's very very basic, you can check it. It helps you to generate a server.cfg file for Counter-Strike: Source dedicated server on the Linux command line. It's in Turkish, wrote it for my tutorial for setting up a server ;)

Python script:
[http://lys01.0fees.net/server-cfg-olusturucusu.py.tar.gz]("http://lys01.0fees.net/server-cfg-olusturucusu.py.tar.gz")

---

