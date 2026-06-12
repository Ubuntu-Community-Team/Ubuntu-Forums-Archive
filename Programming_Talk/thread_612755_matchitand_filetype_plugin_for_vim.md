---
title: "matchitand filetype plugin for vim"
date: 2007-11-14
forum: Programming Talk
---

### Post by Railsbuntu on 2007-11-14
Hello all,

In order to do efficient DocBook editing in vim, I was trying to install the matchit plugin to be able to jump from an xml opening tag to its closing tag. It works, but not perfectly.

I have followed the instructions from [this link]("http://www.vim.org/scripts/script.php?script_id=39").

I can get the help for the matchit plugin, but when I press %, I don't jumpt to the associated tag. So I decided to tell vim that the file I am editing is an xml file, by issuing the command:
```
:set filetype=xml
```
And now pressing % works! And actually, it changes the syntax coloring at the same.

So I wanted to test if the filetype recognition plugin was activated:
```
:filetype
```
which returns the following:
```
filetype detection:ON  plugin:ON  indent:OFF
```

So what's happening? Is it my filetype plugin which is not correctly working? Is it not recognizing the correct filetype and how to remedy it?

Best regards,

---

### Post by Modred on 2007-11-15
Using the DocBook filetype (docbk) results in matchit not functioning for me, as well.  My guess is that vim doesn't apply XML rules to DocBook files, although I don't know why that would be.  I don't believe that matchit is malfunctioning.

---

