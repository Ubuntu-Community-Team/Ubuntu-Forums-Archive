---
title: "kdecore (KProcess): WARNING: _attachPty() 11  ? What is this error?"
date: 2008-09-25
forum: Programming Talk
---

### Post by TRAyres on 2008-09-25
Hey all - 
Just installed Kdevelop and tried to do the stock "Hello, world!" example. 

The current problem is that it will compile and run, and exit normally, but I get this error:
konsole --workdir '.../test1/debug/./src' -e /bin/sh -c '.../test1/debug/./src/test1 ; echo "Press Enter to continue!";read dummy'
kdecore (KProcess): WARNING: _attachPty() 11

I'm using Ubuntu 8.04. Can someone help me fix that error, or let me know if it is something serious?

Thanks all!

---

### Post by Zugzwang on 2008-09-25
Dear OP (original poster),

[LIST]

[*] Whenever you get an error message like this, use google (or your other favorite search machine) to find for similar problems and its solutions. This is generally considered to be polite as it avoids answering the same question over and over again. In this case, you could have simply googled for: [..."_attachPty()"...], which would have yielded [...[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/141284](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/141284)...]. If you have already searched for the problem, please state here why the answers you found are insufficient. Also make sure to strip everything from the error message that it special for your case before searching, like for example the class name of your class in which the error occured, your home path, etc.
[/LIST]

The problem is reported to be fixed with Konsole 4.0.83 in Kubuntu 8.10 (Intrepid).

---

