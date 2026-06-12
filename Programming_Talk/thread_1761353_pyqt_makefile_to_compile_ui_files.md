---
title: "pyqt: makefile to compile ui files"
date: 2011-05-18
forum: Programming Talk
---

### Post by MattThLinuxNewb on 2011-05-18
Hi all,

This a question aimed at anyone with some experience writing makefiles.
Some background: When developing Qt applications with python, if you use Qt Designer to make your front-end you need to compile .ui files into python code before running your main python script.
Rather than doing this manually for every ui file every time I make a change I wrote a small bash script to automate it: 

```
#!/bin/bash

for file in *.ui
do
echo "Parsing $file..."
pyuic4 $file > $(echo $file | sed 's/\(.*\.\)ui/ui_\1py/')
done

python main.py
```

The problem with this script is that it just compiles everything, every time, regardless of whether it is actually needed. This seemed like the perfect job for a makefile so I attempted to write one to do a similar thing:
```
ui_%.py : %.ui
        pyuic4 $(.SOURCE) -o $(.TARGET)
```
This gets the error "No targets. Stop" apparently because an inferred rule cant be the default target. Is there any way to get around this, or do something similar to achieve the same result?

Regards,
Matt

---

