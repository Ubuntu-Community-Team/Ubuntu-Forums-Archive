---
title: "LaTeX characters"
date: 2009-10-08
forum: Programming Talk
---

### Post by Gwasanaethau on 2009-10-08
Hi all,

Hopefully this is a simple question to answer, but unfortunately my cyberspace scanning via a well known search engine has come to nothing.

Basically, I was wondering how one goes about inserting straight quotes into a LaTeX document. LaTeX automatically 'curlifies' all the quotes.

As an extension to this, is there a way of getting LaTeX to show characters based on their Unicode code-point?

Thanks!

---

### Post by Can+~ on 2009-10-08
Curly quotes are inserted in this fashion:
``Hello''

I've never tried using "straight" quotes.

Not sure about your second question, do you want to enter additional characters directly? Try input encoding (I use it for spanish characters):
```
\usepackage[utf8]{inputenc}
\usepackage[spanish]{babel}
```

Edit: I also found:
[http://pokristensson.com/unicodelatex.html](http://pokristensson.com/unicodelatex.html)

---

### Post by Gwasanaethau on 2009-10-08
Thank you, Can+~, that link to the XeTeX stuff looks very interesting. It might be just what I'm looking for.

---

### Post by Can+~ on 2009-10-08
> **Gwasanaethau said:**
> Thank you, Can+~, that link to the XeTeX stuff looks very interesting. It might be just what I'm looking for.

I would recommend you to stick with plain LaTeX and look for the appropriate input encoding for your language.

---

### Post by Gwasanaethau on 2009-10-08
In addition, [this]("http://mjtsai.com/blog/2005/07/29/roman-straight-quotes-in-pdflatex/") turned out to be useful. I tried this before but couldn't get it to work &#8211; seems to be grand now!

Thanks again!

P.S. I will give your recommendation a go&#8230;

Update: **\usepackage[utf8]{inputenc}** is precisely what I'm looking for, thanks!

---

### Post by unutbu on 2009-10-08
Maybe this?
```
Here are the {\tt"}straight{\tt"} quotes.
Here are the {\tt\char'15}single{\tt\char'15} quotes.

```

---

### Post by Gwasanaethau on 2009-10-09
Hi all,

Thanks a million for your replies. After digesting and distilling your suggestions, I've found a solution that works. As a test, I made the following file (named **test.xetex** in my home directory):
```
% filename: test.xetex:

\documentclass{article}
\usepackage{fontspec}
\setromanfont{DejaVu Serif}
\begin{document}

\section{Straight Quotes in XeTeX Test}
Can it render these correctly? Let's see!
CC='"gcc -m64"'test

\section{Curly Quotes in XeTeX Test}
Can it render these correctly? Let's see!
CC=‘“gcc -m64”’test

What about German? Let's see! ä ö ü ß

And now French? à é ë ù ç œ

Norwegian? ø æ å

Greek? &#945;&#946;&#947;&#948;

Russian? &#1087;&#1086;-&#1088;&#1091;&#1089;&#1089;&#1082;&#1080;

Korean? &#4370;&#4449;&#4523;&#4352;&#4467;&#4527;&#4363;&#4467;&#4535;

\end{document}
```

I then ran **xelatex ~/test.xetex** on it, and got the PDF output as attached. This is perfect for what I need! It turns out that XeTeX does not see quotes as LaTeX does – if you want curly quotes, you have to use the correct 'curly quote' code-points (U+201{8,9,C,D}). The Korean text doesn't appear correctly because I don't have a TTF font capable of showing Hangeul (yet!)

---

