---
title: "bash FTP login script with YAFC - &quot;@&quot; char in login"
date: 2010-08-13
forum: Programming Talk
---

### Post by panzerkampf39 on 2010-08-13
Hello,

I'm trying to write ftp login script. Something like that:

```
#!/bin/bash
yafc <<**
open login@login.com:passftp.server.com
dir
close
**
```

My ftp login is e-mail address and is being recognized by script like a hostname and i can't login to the server. What i have to do to make this script working? The escape sequence (/@) doesn't work.

Regards.

---

### Post by DaithiF on 2010-08-13
Hi, I'm not sure about yafc, but when using browser-based ftp you would encode the @ to its %40 urlencoding, ie. username%40domain@ftp.site, so worth giving that a shot. 

if that doesn't work, i noticed you wrote /@ for escaping, maybe thats just a typo and you actually did \@, but if not then try that too.

---

### Post by creepandpeep on 2011-09-26
I was attempting to do the same as the OP with the same result, google search led me straight to this, first on list. . .

changed the @ in login name to %40  - worked.

Issue resolved and headache averted in about 30 seconds thanks to the forums - cheers!

---

