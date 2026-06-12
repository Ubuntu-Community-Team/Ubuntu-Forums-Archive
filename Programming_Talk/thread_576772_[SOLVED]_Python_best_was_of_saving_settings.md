---
title: "[SOLVED] Python: best was of saving settings?"
date: 2007-10-15
forum: Programming Talk
---

### Post by holihue on 2007-10-15
How is the best way of saving settings for a Python program?

I think about something like a file that contains settings for a program: (example)
```
fullscreen = 1
resx, resy = 1400, 1050
```and maybe run something like exec(file).

Is it a better way, maybe .xml?

---

### Post by Wybiral on 2007-10-15
I would use XML, Python has several good XML modules for you to use to generate and parse.

---

### Post by pmasiar on 2007-10-15
with python, you can just import the config.py module and be done. I do it for quick-and-dirty solutions. For real production, ConfigParser (using old and tried .INI format) is included in std library, why not use it?

with XML, you have TWO problems: editing the config, and parsing it. AND it is hard to read, with all <>.

---

### Post by holihue on 2007-10-15
> **Wybiral said:**
> I would use XML, Python has several good XML modules for you to use to generate and parse.


Can you give an example?

---

### Post by pmasiar on 2007-10-15
ElementTree is excellent XML parser, but plain old INI files are more readable. If you need more that 2 levels of settings (which INI provides), you may want to think more about your overall design. ;-)

---

### Post by Wybiral on 2007-10-15
pmasiar's probably right, if you're just saving a few settings, XML is overkill. If your settings are hierarchical, then XML would be good, otherwise there are probably better ways.

Unlike pmasiar, for XML I prefer the xml.dom.minidom module, probably because I use Javascript a lot and it's easier for me because they use the same functions. [Here's an example of minidom]("http://docs.python.org/lib/dom-example.html").

---

### Post by Quikee on 2007-10-15
I like [yaml]("http://www.yaml.org/") for this things. It's nicer than XML imho for configuration files. 

Or simply pickle if I don't need "external" editing.

If XML I would use Python 2.5 built-in ElementTree or lxml's ElementTree which is a little better.

---

### Post by Quikee on 2007-10-15
For yaml you need PyYaml which is in the repositories.

Your example in yaml (document.yaml): 
```

fullscreen: 1
res: [1400, 1050]
sampleDict: {'a':1, 'b':2}

```

An example of yaml reading: 

```

#!/usr/bin/env python

import yaml

stream = file('document.yaml', 'r')
valuesDict = yaml.load(stream)
stream.close()

print valuesDict['fullscreen']
resx, resy = valuesDict['res']
print 'x: ', resx, 'y: ', resy
print valuesDict['sampleDict']

valuesDict['fullscreen'] = 0
valuesDict['res'] = [1280, 1024]
valuesDict['sampleDict']['c'] = 3

stream = file('newDocument.yaml', 'w')
yaml.dump(valuesDict, stream)
stream.close()
print
print 'newDocument.yaml'
print '----------------'
print yaml.dump(valuesDict)

```

Enjoy ;)

---

