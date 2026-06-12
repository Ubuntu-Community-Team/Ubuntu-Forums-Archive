---
title: "codeblocks"
date: 2007-04-25
forum: Programming Talk
---

### Post by leg on 2007-04-25
I am trying to install codeblocks on my amd64 fiesty fawn. I have been following [this]("http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_from_source_on_Linux") guide but am falling over at the ./bootstrap step.

I have installed: 
[LIST]
[*]build-essential - 11.3
[*]autoconf - 2.61-3
[*]automake - 1:1.10+nogfdl-1
[*]gcc - 4:4.1.2ubuntu1
[*]libwxgtk2.6-0 - 2.6.3.2.1.5ubuntu6
[*]libwxgtk2.6-dev - 2.6.3.2.1.5ubuntu6
[*]wx-common - 2.6.3.2.1.5ubuntu6
[/LIST]and tried the AC_LOCAL export on that page but am receiving the error```
./bootstrap: 67: libtoolize: not found

```Any ideas as to what I have missed.

---

### Post by leg on 2007-04-25
Sorry I have figured it out. I needed to install libtool.

---

