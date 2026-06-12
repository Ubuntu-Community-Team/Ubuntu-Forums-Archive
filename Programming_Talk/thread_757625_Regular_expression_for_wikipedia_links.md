---
title: "Regular expression for wikipedia links"
date: 2008-04-17
forum: Programming Talk
---

### Post by [h2o] on 2008-04-17
I need to parse wikipedia links to extract the data (url/article name) using Python.

The links are of these types.

1) Link without title: [[My Article]]
2) Link with title [[My Article|Description of My Article]]
3) Hypertext link [[http://example.com]](http://example.com])
4) Hypertext link with title [[http://example.com](http://example.com) Link to example.com]

I am primarily interested in the URL part, not the description (although getting that as well doesn't hurt, but it's really not needed).

To make it more clear what I want, here is some sample code on how I want it.
```

>>s = "[[Main Page]], [[An Article|This is a title]] [http://example.com Our website] but you can also visit [http://google.com]"

>>m = re.findall(REGEX, s)
>>print m
[('Main Page', ''), ('An Article', 'This is a title'), ('http://example.com','Our website), ('http://google.com', '')]

```

I have found regexs that solves both (1) and (2) but none that handles the mixed content.

Anyone with more regex-skills than me who is up to the challenge? :)

---

### Post by ghostdog74 on 2008-04-17
you want to parse url into its components?? or parse the contents of the website to extract links? 
One module you can look into is [urlparse]("http://www.python.org/doc/lib/module-urlparse.html") to parse url into its components.

---

### Post by [h2o] on 2008-04-17
> **ghostdog74 said:**
> you want to parse url into its components?? or parse the contents of the website to extract links? 
One module you can look into is [urlparse]("http://www.python.org/doc/lib/module-urlparse.html") to parse url into its components.

No, I don't want to parse urls. I want to parse strings that contain wikipedia-style links to extract the article/page they link to. I think my example is quite straight forward.

---

### Post by JHSaunders on 2008-07-17
You could split up the problem, though it may not be as efficient, first search for all links (i.e. things between [[ ]]) and then separate the links form there, this avoids needing one monolithic regex expression.

---

