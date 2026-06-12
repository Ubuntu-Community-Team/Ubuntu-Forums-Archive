---
title: "BASH: Text string variable with spaces"
date: 2007-09-29
forum: Programming Talk
---

### Post by ryanVickers on 2007-09-29
I'm quite confused with this.  This
```

#!/bin/bash
variable="Hello there!"
echo $variable

```
makes the variable return "Hello there!", like it should, but in this code
```

showopt=", "$showopt"Test Archive"

```
(showopt is blank at this point)
it seems to return "," meaning it ignored everything after the space.  How might I fix this!?!?!:confused:

---

### Post by newlinux on 2007-09-29
for me:

```
#!/bin/bash
showopt=", "$showopt"Test Archive"
echo $showopt

```

returns:

, Test Archive

Are you sure it is only returning ", "? Is there anything else in your script that might affect this?

---

### Post by ryanVickers on 2007-09-29
Well, here's the whole script:

_[COLOR=SlateGray]*I'm sorry, please see the main page (signature)*[/COLOR]_

In theory, it should work, shouldn't it?!!

---

### Post by ryanVickers on 2007-09-29
_**[COLOR=Red]I've done a little more testing, and found it's a zenity problem rather than BASH.[/COLOR]**_

---

