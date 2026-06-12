---
title: "swfc error"
date: 2011-01-31
forum: Programming Talk
---

### Post by happy_linux_user on 2011-01-31
Hello. :) I am new here, and I'm happy so I'm here. :)

I need help with swfc console application. This application create swf files from sc script. It returned error all the time. Here is terminal output:

```
andrej@andrej-laptop:~/Plocha/pokus$ swfc kocka.sc
interpolation=linear
pin=center
red=
shear=
ratio=
luminance=
rotate=
blend=
alpha=
green=
below=
above=
commandname=change
name=b1
scalex=
scale=100%
scaley=
x=
filter=
y=
pivot=
blue=
"kocka.sc", line 5 column 30: error- internal error 2: value noinstancename should be set
andrej@andrej-laptop:~/Plocha/pokus$ 

```and this is my script. I think, this code is correct.

```
.flash filename="box.swf" version=5 fps=25
    .box b1 100 100 color=yellow fill=red
    .put b1 pin=center scale=0%
    .frame 100
    .change b1 pin=center scale=100%
    .frame 200
    .change b1 pin=center scale=0%
.end
```I will happy for every ansver. Thanks. :)

P.S Please, use simple english in your ansver to me, I'm from Slovakia.

---

