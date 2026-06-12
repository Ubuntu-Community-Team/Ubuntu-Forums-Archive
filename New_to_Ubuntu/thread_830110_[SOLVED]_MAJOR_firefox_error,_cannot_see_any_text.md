---
title: "[SOLVED] MAJOR firefox error, cannot see any text"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-06-15
When I open up facebook or ubuntu forums I cannot see any text at all. In ubuntu forums I can see the Absolute Beginner Talk banner and thats it (and ubunut forums in the top left corner).

In facebook I can't see anything except the input boxes.

I get the following error in the terminal:

```

GCJ PLUGIN: thread 0x805f148: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805f148: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805f148: NP_GetValue
GCJ PLUGIN: thread 0x805f148: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805f148: NP_GetValue return
GCJ PLUGIN: thread 0x805f148: NP_GetValue
GCJ PLUGIN: thread 0x805f148: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805f148: NP_GetValue return

(firefox:7841): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Verdana 8.515625'

(firefox:7841): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Verdana 8.25'

(firefox:7841): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Verdana 8.25', text='English Hello'

(firefox:7841): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Verdana 8.515625', text=' '

(firefox:7841): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Verdana 10.064453125'

(firefox:7841): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Verdana 9.75'

(firefox:7841): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Verdana 9.75', text='English Hello'

(firefox:7841): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Verdana 10.064453125', text=' '

(firefox:7841): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Verdana Bold 10.837890625'

(firefox:7841): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Verdana Bold 10.5'

(firefox:7841): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Verdana Bold 10.5', text='English Hello'

(firefox:7841): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Verdana Bold 10.837890625', text=' '

(firefox:7841): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Verdana Bold 10.064453125'

(firefox:7841): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Verdana Bold 9.75'

(firefox:7841): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Verdana Bold 9.75', text='English Hello'

(firefox:7841): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Verdana Bold 10.064453125', text=' '

(firefox:7841): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Verdana Bold 8.515625'

(firefox:7841): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Verdana Bold 8.25'

(firefox:7841): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Verdana Bold 8.25', text='English Hello'

(firefox:7841): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Verdana Bold 8.515625', text=' '

```

The only things I can think of that have changed are Wine wanted to install a Gecko engine. I though this might be the problem so I uninstalled wine, no effect.

Otherwise I copied some .ttf fonts to the font folder. Thats pretty much it.

Any thoughts?

---

### Post by abhiroopb on 2008-06-15
Solved: Seems adding the .ttf fonts was what caused the problem!

---

### Post by dodle on 2008-07-03
I was also having the same problem.

[IMG]http://www.freewebs.com/jordansroom/firefox3.png[/IMG]

After running firefox using the terminal, I was able to figure out that this was caused by a font that I had attempted to install.  Deleting the ~/.fonts folder fixed the problem.

I think this was also the cause of firefox crashing.  Every time I tried to log into ubuntuforums it would instantly shut down and give me a 'segmentation fault' error.

---

