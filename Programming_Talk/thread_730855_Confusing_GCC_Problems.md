---
title: "Confusing GCC Problems"
date: 2008-03-21
forum: Programming Talk
---

### Post by t3hi3x on 2008-03-21
I am having some problems with gcc. I am playing with xine-lib, LOVE IT!

Anyway, this tutorial:

[http://linoleum.leapster.org/archives/4-An-introduction-to-playing-audio-with-xine-lib-Part-1.html](http://linoleum.leapster.org/archives/4-An-introduction-to-playing-audio-with-xine-lib-Part-1.html)

has a short little c example of how to use the API, but the problem is that a simple copy and paste jacks the thing up. I get a ton of errors that seem to do with the encoding. I would like to post them, but I'm not on a developing machine at the moment.

Is there a way to remove the encoding while copying/pasting into a text editor? I even tried vim, but it still did wacky things - you should try it :)

I know the code works, because I retyped it, and compiled and executed just fine.

Oh, if you want to compile it, you need libxine-dev from the repositories, and a simple gcc x.c -o x -lxine will compile it.

---

### Post by Keith Hedger on 2008-03-21
This seems to work```
cat 'x.c'  | tr -dc [\\n,[:print:]] > out.c
```
wher x.c is the input file
you can check to see if there are any odd characters in the file with ```
cat --show-nonprinting out.c
```

---

### Post by t3hi3x on 2008-03-21
Just out of curiosity, do you know what causes it? Just wrong encoding?

BTW this is the error report using gedit.

> xineex.c:7: error: stray ‘\342’ in program
xineex.c:7: error: stray ‘\210’ in program
xineex.c:7: error: stray ‘\227’ in program
xineex.c:7: error: stray ‘\342’ in program
xineex.c:7: error: stray ‘\210’ in program
xineex.c:7: error: stray ‘\227’ in program
xineex.c: In function ‘main’:
xineex.c:9: error: stray ‘\342’ in program
xineex.c:9: error: stray ‘\210’ in program
xineex.c:9: error: stray ‘\227’ in program
xineex.c:9: warning: initialization makes integer from pointer without a cast
xineex.c:11: error: stray ‘\342’ in program
xineex.c:11: error: stray ‘\210’ in program
xineex.c:11: error: stray ‘\227’ in program
xineex.c:11: error: storage size of ‘engine’ isn’t known
xineex.c:12: error: stray ‘\342’ in program
xineex.c:12: error: stray ‘\210’ in program
xineex.c:12: error: stray ‘\227’ in program
xineex.c:12: error: storage size of ‘ap’ isn’t known
xineex.c:13: error: stray ‘\342’ in program
xineex.c:13: error: stray ‘\210’ in program
xineex.c:13: error: stray ‘\227’ in program
xineex.c:13: error: storage size of ‘vp’ isn’t known
xineex.c:14: error: stray ‘\342’ in program
xineex.c:14: error: stray ‘\210’ in program
xineex.c:14: error: stray ‘\227’ in program
xineex.c:14: error: storage size of ‘stream’ isn’t known
xineex.c:30: warning: passing argument 2 of ‘xine_open’ makes pointer from integer without a cast
xineex.c:38: error: stray ‘\342’ in program
xineex.c:38: error: stray ‘\210’ in program
xineex.c:38: error: stray ‘\227’ in program
xineex.c:38: error: expected ‘)’ before numeric constant


---

### Post by Keith Hedger on 2008-03-22
I think its just the html tags getting in the way if you look at the page source you will see lots of embedded tags ie ```
int main(int argc, char &lowast;&lowast;argv)<br />
```
Just another badly made web page!

---

