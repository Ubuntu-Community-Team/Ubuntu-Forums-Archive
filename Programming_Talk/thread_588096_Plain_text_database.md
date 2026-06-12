---
title: "Plain text database?"
date: 2007-10-23
forum: Programming Talk
---

### Post by kentl on 2007-10-23
Is there some kind of library for Python, Bash, C, C++, Java or Haskell that allows me to use a plain text file as a database?

It should be as logical as possible, so that a user often can just fire up his text editor to add/change/remove information.

It does not have to be a relational database, and if it is it doesn't need to implement very many SQL-functions. And it doesn't have to be fast. :-)

What's important is that the text files should have a logical structure and that it should be possible for a human to edit them outside my application using a text editor.

If nothing exists I'll just have to implement this myself, as it shouldn't be that hard. Still if it already exists, I could just build upon the existing framework.

---

### Post by pmasiar on 2007-10-23
I am not sure why you need the ability to edit database by hand. No db engine would be happy about that.

sqlite is excellent SQL library (no SQL server) - and I did tried it :-). Better install it via synaptic tho.

csv is module to handle comma-separated values (no SQL). It allows to read data into dicts.

When I needed similar functionality before, I just used dict literals as data storage, in separate source module.

---

### Post by ZuLuuuuuu on 2007-10-23
I didn't try it but maybe SQLite is just for your needs:

[http://www.sqlite.org](http://www.sqlite.org)

---

### Post by kentl on 2007-10-23
I want it to be easy to look up and change data using just a text editor. That way I can just copy my database in an e-mail to someone and they'll understand it immediately.

That rules SQLite out I'm afraid. I guess there's nothing like this already. I'll do it myself then. Thanks! :-)

---

### Post by Nekiruhs on 2007-10-23
> **kentl said:**
> I want it to be easy to look up and change data using just a text editor. That way I can just copy my database in an e-mail to someone and they'll understand it immediately.

That rules SQLite out I'm afraid. I guess there's nothing like this already. I'll do it myself then. Thanks! :-)
I'd love to help. I've been meaning to implement something like this for the longest time. We can talk over email:
pyprogrammer AT gmail DOT com

---

### Post by duff on 2007-10-23
Unless I'm missing something, why not just use a CSV file?

---

### Post by digitalbenji on 2007-10-23
Hi,
   You could easily write your own class to do this, in fact, I'm pretty certain I've written some stuff that could easily be applied to this task.  You obviously should not edit the txt files when they are loaded.  If you want, I'll dig up the classes for you (c++ code).

Thanks,

---

### Post by Nekiruhs on 2007-10-23
> **digitalbenji said:**
> Hi,
   You could easily write your own class to do this, in fact, I'm pretty certain I've written some stuff that could easily be applied to this task.  You obviously should not edit the txt files when they are loaded.  If you want, I'll dig up the classes for you (c++ code).

Thanks,
Oh I know I can. I'm just debating how to organize the text file so I can parse it.

---

### Post by aks44 on 2007-10-23
> **Nekiruhs said:**
> Oh I know I can. I'm just debating how to organize the text file so I can parse it.

Depending on the structure you need, a good ol' INI format could be fine, or you may have to use XML. Anyway don't expect anything even remotely performant.

---

### Post by kentl on 2007-10-23
I wrote you a mail Nekiruhs, sound pretty interesting. We can continue our discussion in mail and on IRC/Jabber/ICQ/MSN/AIM. :-)

To others:
Performance certainly isn't a priority, for me. There are other databases which deliver in that aspect.

Also XML isn't what I'm looking for, as I consider it to be pretty human unfriendly (try writing a complex mathematical expression by hand [in your favorite text editor] using TeX, then use MathML). That said, I do like XML, but it's not for this project if you ask me. Creating a custom language with a parser is certainly one thing that needs to be done.

It will be similar to a CSV file for sure. Just add functionality for a little bit more intelligent behavior. Perhaps you'll start each column with a regular expression defining the data type of the column. Also you might reference another table in your text file, using some form of fk<->pk relationship. Also the database engine should make it easy to retrieve a record, update it and store it. So that you have the option of doing so using a command line interface or your favorite text editor.

---

### Post by stylishpants on 2007-10-23
I like to use YAML for this sort of thing.

It's designed to be a human readable file format that makes it easy to serialize various built-in and user-defined data types to disk.

Libraries are available in Ruby and Python at least, and probably other languages too.


[http://en.wikipedia.org/wiki/Yaml](http://en.wikipedia.org/wiki/Yaml)

---

