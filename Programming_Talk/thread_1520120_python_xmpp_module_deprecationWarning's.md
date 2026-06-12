---
title: "python xmpp module deprecationWarning's"
date: 2010-06-29
forum: Programming Talk
---

### Post by ja660k on 2010-06-29
hey all, i downloaded python module 'xmpp' from apt-get
but when i try to use it... i get these warnings


```

/usr/lib/python2.6/dist-packages/xmpp/auth.py:24: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha,base64,random,dispatcher,re
/usr/lib/python2.6/dist-packages/xmpp/auth.py:26: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5


```

what should be done?
should i just get the newest source for 'xmpp'?

---

### Post by km0r3 on 2010-06-29
> **ja660k said:**
> hey all, i downloaded python module 'xmpp' from apt-get
but when i try to use it... i get these warnings


```

/usr/lib/python2.6/dist-packages/xmpp/auth.py:24: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha,base64,random,dispatcher,re
/usr/lib/python2.6/dist-packages/xmpp/auth.py:26: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5


```

what should be done?
should i just get the newest source for 'xmpp'?

Actually, those warnings do not mean that something is really broken. They are just warnings.

In this case those warnings tell you that the modules are deprecated because you're using the `md5` module, but there's the `hashlib` library which is better.
Unless you don't have the standard Python interpreter everything should still work.

I think it's safe to say, that you can ignore those messages at the moment.

---

### Post by StephenF on 2010-06-29
> **km0r3 said:**
> Actually, those warnings do not mean that something is really broken. They are just warnings.
I have first hand experience of once case where all functionality was gutted from a deprecated function.

---

### Post by -grubby on 2010-06-29
> **StephenF said:**
> I have first hand experience of once case where all functionality was gutted from a deprecated function.

In Python? I doubt it.

---

### Post by jpkotta on 2010-06-30
> **-grubby said:**
> In Python? I doubt it.

They're deprecated for a reason.  They'll be removed eventually.  Python 3.x has no sha or md5 module.  I admire the fact that Python actually removes cruft.

> **ja660k said:**
> hey all, i downloaded python module 'xmpp' from apt-get
but when i try to use it... i get these warnings


```

/usr/lib/python2.6/dist-packages/xmpp/auth.py:24: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha,base64,random,dispatcher,re
/usr/lib/python2.6/dist-packages/xmpp/auth.py:26: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5


```

what should be done?
should i just get the newest source for 'xmpp'?

You can prevent the messages with the following:
```

import warnings

with warnings.catch_warnings():
    warnings.simplefilter("ignore", category=DeprecationWarning)
    import xmpp

```

---

