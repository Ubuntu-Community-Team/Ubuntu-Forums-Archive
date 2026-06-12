---
title: "Custom BASH Shell Startup Text"
date: 2011-04-23
forum: Outdated Tutorials &amp; Tips
---

### Post by dacoolio on 2011-04-23
When I open up a terminal on my computer, I'm greeted with a pretty cool welcome message, including block text (see attachments). Here's how to get something like it on your own computer.


The file that I used to edit the BASH startup is called .bashrc, which is located in your home directory. .bashrc contains information that is called each time a new BASH session is started.

At the end of .bashrc, I have this:

```

echo "Welcome to"
toilet -f mono12 -F metal BASH

```

The first line makes the terminal print "Welcome to" on the first line of the newly opened terminal. The next line uses a program called toilet to output block text to whatever text you want. The man page pretty much sums it up:

```

toilet(1)                                                            

NAME
       TOIlet - display large colourful characters

```

In the above example, the -f option sets the font. In my .bashrc, I use mono12 type font, although there are many others to choose from. -F sets the filter to be used in the outputted text. To see different filter options, run

```
toilet -F list
```

There you have it! A cool new .bashrc file that you can customize to output a nice welcome message. Enjoy!

---

