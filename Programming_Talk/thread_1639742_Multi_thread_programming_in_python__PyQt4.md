---
title: "Multi thread programming in python / PyQt4"
date: 2010-12-07
forum: Programming Talk
---

### Post by aquavitae on 2010-12-07
Hi

I have never done any multi thread programming before, so I need some advice on the best way to approach it. Here is my problem. I need to write a tool which displays files and certain statistics within a folder structure. It is something a bit like a file browser, but heavily customised and relies on a pre-defined folder structure. The location it reads from is usually on a rather slow network, so I need to populate the browser slowly from a separate process.  I am writing the entire tool in python using PyQt4 for the GUI.

My intention is to write two components: the Gui, probably a QTableModel/View and the filesystem scanner, running in a separate process. But there seem to be many ways of doing this and I don't know whats best. Python has its own threading and mulitprocess libraries, but I'm not entirely sure what the difference is. Qt also has its own QtConcurrent library which I could also use. My idea is that the scanner should continuously scan the filesystem, looking for changes by looking for changes in the access times. When a change is found, it signals the GUI to update.

Does this approach sound ok? What would be the best way of getting there?

---

