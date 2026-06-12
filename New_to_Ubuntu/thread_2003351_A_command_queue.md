---
title: "A command queue?"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by thejeswi.nk on 2012-06-14
Hello Ubuntu community!

The problem:
I want to download a few files.. suppose file a, b, so on
and I use wget.

I wrote a shell script who's contents was:
wget [http://....filea](http://....filea)
wget [http://....fileb](http://....fileb)
wget [http://....filec](http://....filec)
and so on..

But they all run  simultaneously!
How do I make them to run one after the other?
Thanks in advance! :)

---

### Post by thejeswi.nk on 2012-06-14
Got a solution!

Found the keyword until in the bash manual.

until wget [http://..filea;](http://..filea;) do echo ""; done 
until wget [http://..fileb;](http://..fileb;) do echo ""; done
until wget [http://..filec;](http://..filec;) do echo ""; done

No, only after file a has been downloaded it goes to file b, and so on!

---

