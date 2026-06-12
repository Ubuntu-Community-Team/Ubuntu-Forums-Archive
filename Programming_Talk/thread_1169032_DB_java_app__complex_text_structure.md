---
title: "DB java app / complex text structure"
date: 2009-05-24
forum: Programming Talk
---

### Post by badperson on 2009-05-24
Hi,

If you're writing an app that will read data from an xml file and import it into a database, and you have lots of stuff like this:

```
<entry>
<heading>Here's a heading</heading>
<para>This morning <date>4/34/09</date> I had a <emph type="bold">really</emph> good cup of coffee.</para>
<heading>Here's another heading</heading>
<para>Then I got me some more cowbell</para>
</entry>
</entry>
```


from a design standpoint, do you want to have a heading table with an entry_id value that will map to that entry, and so on? It seems to me that if the data gets too complex, there's all sorts of potential to screw up an inner join statement and get god knows what as your output. 

Is it better to have one text field, leave all the xml markup there and let the app sort it all out? Of course if you're creating an xml document by extracting different text fragments out of the db your could also end up with a document that doesn't parse...

bp

---

### Post by soltanis on 2009-05-25
I don't understand how using an ID as your primary key would screw anything up (that would be the smart thing to do, unless you can think of a better way to organize the entries).

---

### Post by badperson on 2009-05-26
I just mean that reconstructing a sentence out of a bunch of little parts feels counter-intuitive to me, even though I guess that's the way it's normally done...so I suppose I answered my own question.

---

### Post by DocForbin on 2009-05-26
> **badperson said:**
> 
```
<entry>
<heading>Here's a heading</heading>
<para>This morning <date>4/34/09</date> I had a <emph type="bold">really</emph> good cup of coffee.</para>
<heading>Here's another heading</heading>
<para>Then I got me some more cowbell</para>
</entry>
</entry>
```

hrm, this is invalid xml, but if you have multiple entries, multiple headings per entry, and multiple paras per heading, I guess you may want 3 tables

entries (entry_id)
headings (entry_id, heading_id, text)
paras (entry_id, heading_id, para_id, text)

A lot of this just depends on what you want to do with the data, it may make sense to use one table and stuff all the xml in it.

---

