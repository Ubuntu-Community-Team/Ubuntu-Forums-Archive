---
title: "JavaScript (and perl...)"
date: 2010-01-01
forum: Programming Talk
---

### Post by StOoZ on 2010-01-01
I have a HTML, which has a javascript button:
[PHP]<p><input type="submit" id="submitButton" value="Submit" /></p></
form><script language="Javascript">runMeAndFinish();</script></body></
html>"[/PHP]

in order to emulate the 'runMeAndFinish()' function call, I want to see the request the JS is building when I click this button, any idea how to do it???

thanks,

---

### Post by korvirlol on 2010-01-01
[PHP]<input type = 'button' value = 'Click me' onclick = 'runMeAndFinish();'>[/PHP]

---

### Post by StOoZ on 2010-01-05
thanks,
Anyhow I managed to solved it in a different way.

---

### Post by myrtle1908 on 2010-01-05
> **StOoZ said:**
> I want to see the request the JS is building when I click this button, any idea how to do it???

[http://www.getfirebug.com](http://www.getfirebug.com)

---

### Post by StOoZ on 2010-01-26
> **myrtle1908 said:**
> [http://www.getfirebug.com](http://www.getfirebug.com)
Thanks. used something similar to this,with chrome.

---

