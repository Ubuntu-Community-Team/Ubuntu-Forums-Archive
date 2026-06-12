---
title: "Python minidom - disappearing element in NodeList"
date: 2008-03-26
forum: Programming Talk
---

### Post by louis_nichols on 2008-03-26
Hi all!

I'm working with Python under windows, but this issue should be pretty general, so I am posting here, hoping for an answer.

I am working on an application which uses python's minidom implementation to build XML files.

Generally, this works well, but I have one spot where I am stuck and just can't seem to get a break.

Long story short, I do something like this:

```
sourceChildren = someXML.getElementsByTagName('string')[0].childNodes
destChildren = someOtherXML.getElementsByTagName('string')[0].childNodes

for element in sourceChildren:
     destChildren.insertBefore(element, destChildren.lastChild)
```

Now, I do this routine in several places in the code and it works well. Except in one place, where sourceChildren simply loses an element by the second iteration of the loop. I see this in debugging mode: at the first iteration, sourceChildren has 2 elements but by the second, it has only one element.

I really tried every kind of loop there and no joy. I tried stuff like this:

```
for i in range(0; len(sourceChildren)):
     destChildren.insertBefore(sourceChildren[i], destChildren.lastChild)

while i<= 50:
    try: destChildren.insertBefore(sourceChildren[i], destChildren.lastChild)
    except IndexError: pass
    i+=1
```

And even a couple of other things.

 Does anyone have any suggestions for a workaround? Or anything else...

---

### Post by Wybiral on 2008-03-26
Do you have a complete test that will recreate the problem?

Also, unless you're too invested already in minidom, [ElementTree]("http://docs.python.org/lib/module-xml.etree.ElementTree.html") is a much simpler / more Pythonic XML library (it's generally preferred by the Python community for parsing / creating XML documents).

---

### Post by louis_nichols on 2008-03-26
Hi Wybiral and thank you for your interest in helping me!

I am working on a simple way to recreate the error. I am not able to post the actual code and, because, as I said, I use the sequence in several places form which only one doesn't work, I fear it will be difficult to reproduce. But I am trying.

I forgot to mention this in the initial post, but because of the particularities of the situation, I imagine this is quite a longshot, but I am close to desperate now, so I figure I got nothing to lose. :)

---

### Post by louis_nichols on 2008-03-26
Hi!

I am not able to provide a definitive replication method, but here is one more example of the absurdity of it all:

```
def combinePreps(sourceXML, destXML):
    sourcePrep = sourceXML.parentNode.childNodes[1]
    destPrep = destXML.parentNode.childNodes[1]
    print sourcePrep.childNodes.length
    
    for i in range(0, sourcePrep.childNodes.length):
        destPrep.insertBefore(sourcePrep.childNodes[i], destPrep.lastChild)
        print sourcePrep.childNodes.length
```

So in this case, the first print outputs 2. The second print outputs 1. The next thing at output is an index error (list index out of range)...

---

### Post by louis_nichols on 2008-03-26
OK. Hopefully last post.

I think I found a solution (very unexpected thing, because I have been working on this, on and off, for like 1 month). The idea is like this:

Instead of doing
```
for i in range(0, sourcePrep.childNodes.length):
        destPrep.insertBefore(sourcePrep.childNodes[i], destPrep.lastChild)
```

I used
```
for i in range(0, sourcePrep.childNodes.length):
        destPrep.insertBefore(sourcePrep.childNodes[0], destPrep.lastChild)
```

Because, apparently (and very unexpectedly, I might add - I'm not sure this is the desired behavior), the method insertBefore (appendChild behaves the same) removes the node from the source XML object, instead of just making a copy of it at destination...

---

