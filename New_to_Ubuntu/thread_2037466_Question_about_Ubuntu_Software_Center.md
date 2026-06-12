---
title: "Question about Ubuntu Software Center"
date: 2012-08-04
forum: New to Ubuntu
---

### Post by dcampbelatcs on 2012-08-04
I have a question about the Ubuntu Software Center:

Shouldn't it display all the applications from all the PPAs that I have added to the list?  

For example: I wanted to install "acroread".  I could not find it anywhere in the Ubuntu Software Center.  So I opened a terminal and typed "sudo apt-get install acroread" and this worked.

If it worked, then it means I have access to it, right?  So doesn't that mean it should appear in the Software Center?  

I must not be getting something.

---

### Post by gifford on 2012-08-04
The software center does not display all software installed on your system. As far as I know, the software listed and sources are from the Ubuntu repositories, not those you add on your own.

Try installing and using synaptic to see your installed software and related repositories. Ubuntu tweak is also useful.

---

### Post by Bufeu on 2012-08-04
[https://help.ubuntu.com/community/Repositories/Ubuntu/](https://help.ubuntu.com/community/Repositories/Ubuntu/)

---

### Post by Paqman on 2012-08-04
> **gifford said:**
> As far as I know, the software listed and sources are from the Ubuntu repositories, not those you add on your own.


No, it will show PPAs and 3rd party repos as well. But it is quite choosy about what it displays, in that it tries to only show actual applications and hides all the libraries and other geeky bits away by default.

Like you say, Synaptic will show absolutely everything.

---

