---
title: "Cannot display colored text with echo command in emacs"
date: 2014-11-19
forum: Packaging and Compiling Programs
---

### Post by eduanras on 2014-11-19
Hello Team,

I would like you to help me to display colored text using echo with [COLOR=#ff0000]EMACS[/COLOR].
Check out the scrip below:

```

#!/bin/bash
text='ColoredAndBoldText'
echo -e "\e[1;30m$text\e[0m"

```

With **EMACS** "M-!" in emacs but output is:  [COLOR=#00ffff]^[[/COLOR][1mColoredAndBoldText[COLOR=#00ffff]^[[/COLOR][0m  End.
With **VIM** the result is **[COLOR=#696969]ColoredAndBoldText[/COLOR]** 

Thanks for your support!!!

---

### Post by schragge on 2014-12-10
Hopefully, [this](http://stackoverflow.com/questions/5819719) can be of some help.

---

