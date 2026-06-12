---
title: "I have like 50 XML files - what is the easiest way to combine them into one document?"
date: 2008-02-14
forum: Programming Talk
---

### Post by spaceballl on 2008-02-14
Hi all!

I have like 50 XML files. Is it possible to take them and combine them into one giant file? Each XML file has one root node and i want one document w/ all the nodes

---

### Post by shawnhcorey on 2008-02-14
You can include then via ENTITY.  Below foo.xml includes goo.xml.  Note that goo.xml cannot contain a DOCTYPE.

You can create one master XML that contains all 50 XMLs.

foo.xml:
```
<?xml version='1.0' encoding='UTF-8'?>

<!DOCTYPE foo
[
  <!ENTITY goo_xml SYSTEM "goo.xml">
]>

<foo>
  &goo_xml;
</foo>

```

goo.xml:
```
<?xml version='1.0' encoding='UTF-8'?>

<goo>
  Inside goo.xml
</goo>

```

---

### Post by Gen2ly on 2008-02-14
or cat *.xml > onefile.xml

---

### Post by shawnhcorey on 2008-02-14
> **Dirk.R.Gently said:**
> or cat *.xml > onefile.xml

Only if you don't have to read it as an XML file.

---

### Post by Geekkit on 2008-02-14
> **shawnhcorey said:**
> Only if you don't have to read it as an XML file.

Not true but only if ... the first document contains the open element tag and the last element contains the close element tag. :)

---

### Post by tgalati4 on 2008-02-14
You will have to edit the file if you cat the individual files.  You could write a perl script or use an editing macro to delete the excess xml elements.

Or cat all the files together and try to load it and see what happens.  Open your application in the command line so you can see the results.  Post back with what you find.

---

### Post by popch on 2008-02-15
> **Geekkit said:**
> Not true but only if ... the first document contains the open element tag and the last element contains the close element tag. :)

And if none of the files between contain any XML headers. Which would make them non-XML files.

---

