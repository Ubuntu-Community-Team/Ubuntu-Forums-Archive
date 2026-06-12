---
title: "[Python] Local imports are unrecognized in SPE."
date: 2010-05-01
forum: Programming Talk
---

### Post by Jesdisciple on 2010-05-01
I went to a lot of trouble to ensure that local imports were working before I learned of SPE.  I didn't test them before changing my directory structure, but now they seem to be broken when running from SPE.  When I run Python through gnometerminal I can import just fine...  I can't think of anything else to test that would shed light on my situation, so if anyone else could it would be much appreciated.

---

### Post by smartbei on 2010-05-01
You could also develop in SPE and run from the terminal - that actually isn't such a bad option.

What do you mean by 'local imports'? Do you mean python files in the same directory that you are importing? Or do you mean a directory you have added to the PYTHONPATH or something along those lines (if so, perhaps SPE uses a different version of python)?

---

### Post by Jesdisciple on 2010-05-01
> **smartbei said:**
> You could also develop in SPE and run from the terminal - that actually isn't such a bad option.Meh.  I like having a Run menu option and hotkey in my editor.  Nonetheless I might end up needing to do that.

> **smartbei said:**
> What do you mean by 'local imports'? Do you mean python files in the same directory that you are importing? Or do you mean **a directory you have added to the PYTHONPATH** or something along those lines?The bold is correct.  =)

> **smartbei said:**
> (if so, perhaps SPE uses a different version of python)...Can it have its own installation?  The boilerplate text is identical.

But regardless, SPE is somehow clobbering my PYTHONPATH now that I thought to check that.

---

### Post by Jesdisciple on 2010-05-01
I just found out that pygame can't open GIF images when run in the terminal, but it can from SPE.  This seems like a strong indication that SPE has its own Python, so how can I tell SPE which Python to use?

---

