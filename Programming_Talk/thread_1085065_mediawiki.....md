---
title: "mediawiki...."
date: 2009-03-02
forum: Programming Talk
---

### Post by sandyd on 2009-03-02
how do you add stuff (such as warnings) to a page?
Is it an extension, or do it code it manually?

For example, here in wikipedia, they have a warning about Music only relating to europe .etc.etc.etc

[http://en.wikipedia.org/wiki/Music](http://en.wikipedia.org/wiki/Music)
-------------------------------------------------
Another thing

how to i add the bar on the right hand side (see link below) such as in wikipedia? I mean the bar that shows the picture, the description and everything

Is it also  an extension, or do it code it manually?

[http://en.wikipedia.org/wiki/Paramore](http://en.wikipedia.org/wiki/Paramore)

---

### Post by simeon87 on 2009-03-03
On Wikipedia they use templates for such messages at the top. A template is simply another page that is placed in the current page. In the source, it says:

```

{{Globalize/Europe}}

```

The {{ and }} indicate that the content of the template Globalize/Europe (actually an ordinary page in the namespace Template) will be placed here. The template itself can be found here: [http://en.wikipedia.org/wiki/Template:Globalize/Europe](http://en.wikipedia.org/wiki/Template:Globalize/Europe).

The bar on the right is the same thing, it's a template. They're also called infoboxes. In this case, the source of that wiki page contains:

```

{{Infobox Musical artist <!-- See Wikipedia:WikiProject Musicians -->
| Name                = Paramore
| Img = Paramore rio.jpg
| Img_capt = Paramore at the [[Rio de Janeiro]], [[Brazil]], in October 24, 2008.
...

```

Once again, the {{ }} denote a template being placed in the page. The name of the template is Infobox Musical artist and the parameters are separated by vertical bars. What parameters a template has, can usually be found on the page of the template itself, in this case [http://en.wikipedia.org/wiki/Template:Infobox_Musical_artist](http://en.wikipedia.org/wiki/Template:Infobox_Musical_artist).

Extensions are used when you want to extend the functionality/features of the MediaWiki software but that's not needed here. Also, see [http://en.wikipedia.org/wiki/Help:Template](http://en.wikipedia.org/wiki/Help:Template) for more information about templates.

---

### Post by sandyd on 2009-03-07
Thanks!

---

### Post by sandyd on 2009-03-07
but could someone help me with the stuff thats actually... in the template?

wikipedia locked the templates so i can't use the edit function to see the codes they used.

---

### Post by simeon87 on 2009-03-08
> **carlee said:**
> but could someone help me with the stuff thats actually... in the template?

wikipedia locked the templates so i can't use the edit function to see the codes they used.

When a template is locked, the 'Edit this page' link disappears but a 'View source' appears so you can always see the source of a page, you just can't always edit it.

---

### Post by sandyd on 2009-03-08
> **simeon87 said:**
> When a template is locked, the 'Edit this page' link disappears but a 'View source' appears so you can always see the source of a page, you just can't always edit it.

ahh, thanks for clarifying that


never saw that one comming.....

---

### Post by sandyd on 2009-03-09
I was just thinking of an easier way, such as linking the templates to wikipedia

ive heard (and done) interwiki linking, BUT is there some way i can .... display the entire page im linking instead of leaving just a link?

(yes, im being lazy)

---

