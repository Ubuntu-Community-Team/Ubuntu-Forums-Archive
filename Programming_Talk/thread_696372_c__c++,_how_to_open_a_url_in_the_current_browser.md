---
title: "c / c++, how to open a url in the current browser?"
date: 2008-02-13
forum: Programming Talk
---

### Post by KPexEA on 2008-02-13
Is there any way to "detect" the current browser and open up a URL in it? Preferrably launch it if it is not running already and if it is running then  open up a new tab. Would this be different depending on the window manger, like gnome or KDE, as I would rather have a generic solution that worked on any WM.

My current fall back plan if there is no such thing as a "default" browser is to have the user have an input box where they put the path to the browser in like "/etc/firefox" or something like that, but in that case is it possible to detect if it is running already and if so open the url in a new tab instead of a whole new instance?

Thanks
Kevin

---

### Post by pedro_orange on 2008-02-14
I believe there is an environmental variable 'x-www-browser' that contains default browser location.

If you do:

```
sudo update-alternatives --config x-www-browser
```

I get an output:

```
There is only 1 program which provides x-www-browser
(/usr/bin/firefox). Nothing to configure.
```

I know this is Bash, but might help a bit ^^

---

### Post by hakermania on 2010-06-17
include stdio.h
system("firefox http://mysite.com");

:)

---

### Post by nvteighen on 2010-06-17
> **hakermania said:**
> include stdio.h
system("firefox http://mysite.com");

:)

No.

```

#include <stdlib.h>

int main(void)
{
    system("firefox -new-tab http://www.google.com");
    return 0;
}

```

But this is awful... I'm sure there has to be another way to do this.

---

### Post by Zugzwang on 2010-06-17
Despite the necromancy in the thread, isn't it probably the best idea to leave this tabbing stuff to the default web browser, whichever that may be?

```

#include <stdlib.h>

int main(void)
{
    system("x-www-browser http://www.google.com");
    return 0;
}

```

BTW: For firefox on Ubuntu 10.04, this *does* open a new tab if the browser is already running.

---

### Post by juancarlospaco on 2010-06-17
xdg-open 'http://www.google.com'

---

### Post by soltanis on 2010-06-18
Either one seems to work, at least on my system (10.04).

---

### Post by nvteighen on 2010-06-18
Well, xdg-open is clearly the nicest of all. I'll write that tip down somewhere.

---

### Post by juancarlospaco on 2010-06-18
Python example:

import os
os.system('xdg-open [http://python.org/](http://python.org/)')

*EDIT:ups!, i forget the title says "c / c++"*

---

