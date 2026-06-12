---
title: "WGet onLoad functionality"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by n0000b on 2012-10-25
Hi @ll,

first of all: I am an absolute Linux n0000b. Therefore please be patient with me :)

I am trying to retrieve the loading time of a website. As far as I understood, this is easily been done using WGET:
```
time wget URL
```I also read on the internet, that onLoad events are **not** considered here. So here are my questions:

[LIST=1]
[*]Is it absolutely correct, that onLoad is not considered?
[*]Is there a possibility to activate the loading of onLoad functions?
[/LIST]
I'd like to compare the different loading times of the website (without onLoad and with onLoad), therefore my questions.


I would really appreciate if you could help me out here.




Cheers,
n0000b

---

### Post by n0000b on 2012-10-25
*bump*

---

### Post by maniandram on 2012-10-25
Assuming onLoad is something in JavaScript, the onLoad functions will not be executed when using wget.

wget only downloads the HTML file - it doesn't run any javascript or render the file like in a browser.  your shell code will simply measure the time to download the HTML.

---

### Post by maniandram on 2012-10-25
BTW, meaning info: noob is negative and offensive and newbie is friendly

---

