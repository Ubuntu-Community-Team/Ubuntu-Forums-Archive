---
title: "Removing children - Python - XML"
date: 2010-03-20
forum: Programming Talk
---

### Post by MadnessRed on 2010-03-20
Hi, I am having some problems removing children from an xml node.

I had:
```

node = xmldoc.getElementsByTagName('types')[0]
for child in node.childNodes:
    print child.toxml()
    node.removeChild(child)

```

That just printed a few blank lines and did nothing. Then I tried:
```

node = xmldoc.getElementsByTagName('types')[0]
for child in node.childNodes:
    for grandchild in child.childNodes:
        print grandchild.toxml()
        child.removeChild(grandchild)

```

That emptied the children but still left them there.
eg
```
<types>
    <type>jpg</type>
    <type>png</type>
    <type>gif</type>
</type>
```

to
```
<types>
    <type/>
    <type/>
    <type/>
</type>
```

I would like to completely empty types.
Any suggestions?


edit: solved
```

node = xmldoc.getElementsByTagName('types')[0]
while len(node.childNodes) > 0:
    child = node.childNodes[0]
    print child.toxml()
    node.removeChild(child)

```

---

