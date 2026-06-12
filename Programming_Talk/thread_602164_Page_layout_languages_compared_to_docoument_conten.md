---
title: "Page layout languages compared to docoument content description"
date: 2007-11-03
forum: Programming Talk
---

### Post by Peter Mount on 2007-11-03
Hi

I've googled and yahoo-ed and alta-visted but I can't come up with anything that clearly explains the defintions of and differences between:

page layout languages and
document content description

This is in regards to web pages. Can anybody just point me to something on the web that explains this? I'm guessing "page layout languages" is xhtml and "document content description" is css but I need the "official meanings". You know how it is when you get an assignment that uses specific terminology that you haven't seen before.

Thanks.

---

### Post by pmasiar on 2007-11-04
[http://en.wikipedia.org/wiki/List_of_XML_markup_languages](http://en.wikipedia.org/wiki/List_of_XML_markup_languages)
[http://en.wikipedia.org/wiki/Markup_language](http://en.wikipedia.org/wiki/Markup_language)

Page layout defines how document looks like (HTML, CSS for web). Contens is described by [http://en.wikipedia.org/wiki/Semantic_Web](http://en.wikipedia.org/wiki/Semantic_Web) (that article explains relation to HTML). Read up also RDF, OWL, RDFa.

This kind of searches are more productive to start at wikipedia in my experience.

---

### Post by Peter Mount on 2007-11-04
Thanks pmasiar

That looks really good. Thanks very much for that.

Have a good day

---

### Post by CptPicard on 2007-11-04
Mind you, in your original post you had it exactly the wrong way around. :)

Document content description tries to add some sort of semantic information into the document that tells *what is there* in the document. Like, I could write this XML that describes contents of a book:

```

<book>
  <title>CptPicard's cookbook</title>
  <recipe name="macaroni and water">
    <ingredient>
      macaroni
    </ingredient>
    <ingredient>
      water
    </ingredient>
    <preparation>
       Put macaroni water. Boil. Enjoy.
    </preparation>
  </recipe>
</book>

```

Ok... so.. suppose we wanted to now print this book. We will use something like CSS or some other layout language to tell us where for example the title of the book goes, how paragraphs are placed on the page, etc... they often to together, but serve separate purposes. In particular, mixing content and layout tends to be a no-no, it makes for unmaintainable and unprocessable data.

---

