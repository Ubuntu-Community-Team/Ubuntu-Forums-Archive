---
title: "[WEB] Embedding Images in Pages"
date: 2011-07-11
forum: Programming Talk
---

### Post by ki4jgt on 2011-07-11
In high school I stumbled upon a program by Microsoft, which allowed users to compile webpages (with images included) into one single file. The file extension was .mhtml. Are their any Linux programs which will compile all files in an html file into a single file?

---

### Post by An Sanct on 2011-07-11
Hey there!

Here is a full overview of that [standard]("http://en.wikipedia.org/wiki/MHTML"), in short all modern browsers support this functionality.

---

### Post by ki4jgt on 2011-07-11
> **An Sanct said:**
> Hey there!

Here is a full overview of that [standard]("http://en.wikipedia.org/wiki/MHTML"), in short all modern browsers support this functionality.

I'm looking for a great compiler for it. The repos don't have one or mhtm/l doesn't return anything.

---

### Post by slavik on 2011-07-11
1. install firefox extension
2. restart firefox
3. open needed html page
4. save as mhtml
5.
6. profit

---

### Post by An Sanct on 2011-07-11
> **ki4jgt said:**
> I'm looking for a great compiler for it. The repos don't have one or mhtm/l doesn't return anything.

It cannot be said, that it is a compiler ... well, besides the Firefox thing, mentioned in the above post, there are also other browser plugins/support on the wiki I posted...

Be kind and read what is in the links people post, don't just reply without checking them. (_And this note goes to *everyone* asking questions here..._)

---

### Post by ki4jgt on 2011-07-11
> **An Sanct said:**
> It cannot be said, that it is a compiler ... well, besides the Firefox thing, mentioned in the above post, there are also other browser plugins/support on the wiki I posted...

Be kind and read what is in the links people post, don't just reply without checking them. (_And this note goes to *everyone* asking questions here..._)

I did, I read that before I even asked the question. I'm wanting an actual editor. Like in Windows MS Word will actually allow you to write MHTML documents and save them as such, however OO or LO seems to be missing this functionality.

---

### Post by ssam on 2011-07-11
or this method
[http://en.wikipedia.org/wiki/Data:_URI_scheme](http://en.wikipedia.org/wiki/Data:_URI_scheme)

as seen on the google 404 page
[http://www.google.com/whatever](http://www.google.com/whatever)

---

### Post by juancarlospaco on 2011-07-11
[http://tools.ietf.org/html/rfc2397](http://tools.ietf.org/html/rfc2397)

You can do it using HTML, CSS or Js. Do NOT use any Microsoft format, you dont need it.

I suggest you by encoding images as .SVG (Inkscape for example) or as .WebP (Google Tool).

Note that .SVG images you can draw it as small as you can, it dont loossee resolution upon Scaling.

Go here: [http://www.scalora.org/projects/uriencoder/](http://www.scalora.org/projects/uriencoder/)

---

### Post by ki4jgt on 2011-07-11
> **ssam said:**
> or this method
[http://en.wikipedia.org/wiki/Data:_URI_scheme](http://en.wikipedia.org/wiki/Data:_URI_scheme)

as seen on the google 404 page
[http://www.google.com/whatever](http://www.google.com/whatever)

???

---

### Post by PaulM1985 on 2011-07-11
> **ki4jgt said:**
> ???

What are you not sure about in this post?

This looks like what you want.  You want to embed information in your web pages, ssam's link shows you how it is done in html.  Did you actually read it or instantly dismiss it because it wasn't mhtml?  The second link (for google) did you look at the source for it?  That was ssam providing you with an example of where it is used.

Paul

---

### Post by ki4jgt on 2011-07-11
> **PaulM1985 said:**
> What are you not sure about in this post?

This looks like what you want.  You want to embed information in your web pages, ssam's link shows you how it is done in html.  Did you actually read it or instantly dismiss it because it wasn't mhtml?  The second link (for google) did you look at the source for it?  That was ssam providing you with an example of where it is used.

Paul

I did not dismiss it. I did not get how it related. The ??? was a what are you trying to show me type question. It was not meant to be smart. Quit assuming I'm not reading things :-) I've read everything you guys have posted. I pretty much guessed that was what he was trying to show me, but did not want to miss something in the process.

---

### Post by An Sanct on 2011-07-11
*in the google "whatever" sample, if you open up the source, you see:

```
<style>     *{margin:0;padding:0}html,code{font:15px/22px arial,sans-serif}html{background:#fff;color:#222;padding:15px}
body
{**background:url(data:image/png;base64,iVBORw0KGgoAAAANSU**hEU *..... and so on ....*
```This is where the image is embedded.

Simply said, use a simple HTML editor and then view the page with a mhtm(l) compatible browser, then do a "Save as" and select the preferred format. Viola - you have the mhtml, you wanted.

(no compiler needed :))

---

### Post by ki4jgt on 2011-07-11
> **An Sanct said:**
> *in the google "whatever" sample, if you open up the source, you see:

```
<style>     *{margin:0;padding:0}html,code{font:15px/22px arial,sans-serif}html{background:#fff;color:#222;padding:15px}
body
{**background:url(data:image/png;base64,iVBORw0KGgoAAAANSU**hEU *..... and so on ....*
```This is where the image is embedded.

Simply said, use a simple HTML editor and then view the page with a mhtm(l) compatible browser, then do a "Save as" and select the preferred format. Viola - you have the mhtml, you wanted.

(no compiler needed :))

OK, funny :-) LOL, compiler = Editor. Anyway, thanks. I pretty much knew Opera did this, but was hoping there was an actual program for it :-( I'll go with Opera on this then. Thanks guys.

---

