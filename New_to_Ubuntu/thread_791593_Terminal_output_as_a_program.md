---
title: "Terminal output as a program?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by mrfraser89 on 2008-05-12
Hey guys, I have a terminal command that I use to check the ink levels in my epson printer.

The command I use in a terminal window is

```

sudo escputil -i -r /dev/usb/lp0

```


But when I make a 'shortcut' to run this, it doesn't actually show anything (obviously it does it and then disappears or it runs in the background?) So how can I get a terminal to output the results? Running it in terminal works perfectly :)
(If code tags don't work, how do I do code tags :P)

---

### Post by tukuyomi on 2008-05-12
Hello, you'll want to write a script to execute it. Here is a sample: Open your text editor and copy/paste
```

#!/bin/sh

zenity --info --text="$(escputil -i -r /dev/usb/lp0)"

exit 0

```
Save in your ~ (your /home/'user') directory as, say 'checkInk', and make it executable (either with right-click -> Proprieties) or with the command ```
$ chmod +x ~/checkInk
```
Now Make a launcher on your Desktop with 
"Name: Check Ink
 Command: gksudo ./checkInk"
And test! :)

---

