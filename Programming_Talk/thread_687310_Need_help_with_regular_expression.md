---
title: "Need help with regular expression"
date: 2008-02-04
forum: Programming Talk
---

### Post by Interestedinthepenguin on 2008-02-04
What regular expression would I use to extract <body> tags from a file?  

These tags aren't always plain <body>; sometimes it's < body>, < body > (note the spaces), or < body someattributes >.  What regexp(s) would I use in order to snag all opening body tags, regardeless of how they're formatted?

Thanks.

PS:  I'm not sure if this matters, but I'll be using grep and sed.

---

### Post by pmasiar on 2008-02-04
Parsing HTML by hand is IMHO sucker's game in general. If you have some simple static well-formed HTML, like in the case of <body> you may have luck, but in general - is better to use HTML parser, they solved most tricky corner cases for you.

I would use Python and ElementTree parser, but then I use Python everywhere I can get away with it :-) YMMV

---

### Post by ghostdog74 on 2008-02-04
> **Interestedinthepenguin said:**
> What regular expression would I use to extract <body> tags from a file?  

These tags aren't always plain <body>; sometimes it's < body>, < body > (note the spaces), or < body someattributes >.  What regexp(s) would I use in order to snag all opening body tags, regardeless of how they're formatted?

Thanks.

PS:  I'm not sure if this matters, but I'll be using grep and sed.

how about providing a sample for people interested to play with and describing what you expect the final result to be

---

### Post by hyperair on 2008-02-04
Try... 
```
<\s*body[^>]*>
```

---

### Post by pmasiar on 2008-02-04
To get feeling what you might volunteered for if you want to parse HTML by hand, read  about why dot-star is sometimes pronounced death-star: read  [Death to Dot Star!](http://www.perlmonks.org/?node_id=24640) at PerlMonk :-)

---

### Post by hyperair on 2008-02-04
I still stand by my regex! =O

---

### Post by aks44 on 2008-02-04
> **hyperair said:**
> <\s*body[^>]*>

With that regex, **<bodywhatever>** is matched too (which is incorrect).

This fixes that specific flaw:
```
/<\s*body(\s*>|\s+[^>]+>)/i
```(note the ending **i** so that the regex is case insensitive)


Handling of incorrectly formed HTML with a plain **>** inside an attribute value (it should be the **&gt;** entity, but all browsers will happily parse it anyway**[COLOR="DarkRed"]*[/COLOR]**) is left as an exercise for the reader. :D

Example: **<body attr="hello > world">**


Handling of correctly formed XHTML that (for some obscure reason) uses a namespace prefix is left, too, as an exercise for the reader.

Example of such a case:
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html 
     PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<foo:html xmlns:foo="http://www.w3.org/1999/xhtml" xml:lang="en" foo:lang="en">
  <foo:head>
    <foo:title>Tricky case</foo:title>
  </foo:head>
  <foo:body>
    Document contents...
  </foo:body>
</foo:html>
```


These are definitely the kind of "tricky corner cases" that pmasiar was evoking, and the very reason why you should use a dedicated HTML parser (not an XML parser, mind you, as my first example would then not be parsed correctly despite the fact that all browsers will accept it**[COLOR="DarkRed"]*[/COLOR]**).

**[COLOR="DarkRed"](*)[/COLOR]:** if the browser thinks it's dealing with plain old HTML ; of course in XHTML mode it will fail to validate.



> **hyperair said:**
> I still stand by my regex! =O
Still standing? :p

---

### Post by Wybiral on 2008-02-04
> **hyperair said:**
> I still stand by my regex! =O

RE is great for some situations, it just doesn't do well with hierarchical data like XML. You can parse simple things out of XML using RE, but XML is meant to be represented in a hierarchical / tree-like structure. I would use an XML parser as pmasiar suggested, however for true HTML I would probably use [BeautifulSoup]("http://www.crummy.com/software/BeautifulSoup/") since it can handle badly formed HTML (like most of the internet).

---

### Post by hyperair on 2008-02-04
T_T I give up.

---

### Post by aks44 on 2008-02-04
While we're at it, I'll push the point a little farther...


It's quite easy to write a regex that checks if a string is a well-formed e-mail address, right?

Here's the beast, have fun!
[http://code.iamcal.com/php/rfc822/full_regexp.txt](http://code.iamcal.com/php/rfc822/full_regexp.txt)

:popcorn:


EDIT: this is a PHP / PCRE regex (Perl Compatible Regular Expression), other regex engines may require a different one.

---

### Post by pmasiar on 2008-02-04
Of course email is so much simpler, parsing it is like a child's play!

That one is a keeper! :-) 

Thanks, aks44, you proved the point beyond reasonable doubt. We can now rest the case :-)

---

### Post by Interestedinthepenguin on 2008-02-04
Wow, I didn't know I was opening a can of worms by trying to find HTML tags using regexps!

While I am a little lost as to what some of you are talking about, I appreciate the responses.:)

The regexps that hyperair and aks44 provided are good, and I am tinkering with those.

Please excuse my ignorance, but what does ```
s*
``` do in regexps?  

I am trying to extract body tags so that I can have sed insert text just after them.:oops:

---

### Post by aks44 on 2008-02-04
> **pmasiar said:**
> Of course email is so much simpler, parsing it is like a child's play!

That one is a keeper! :-)

To be honest, I provided a link to the fully unrolled regex, but it is not meant to be used as is. There is [some (much shorter) PHP code]("http://code.iamcal.com/php/rfc822/") that incrementally generates that regex from the grammar of RFC 2822. ;)


> **Interestedinthepenguin said:**
> Please excuse my ignorance, but what does ```
s*
``` do in regexps?

Let's dissect it then. :) I'll take mine, not for its "correctness" (ahem) but just because it is slightly more complex, so hopefully you'll learn more.

**<\s*body(\s*>|\s+[^>]+>)**
```
<             match the opening angle bracket
\s*           match a whitespace (\s = space or tabulation) zero or more times (*)
body          match the literal string "body"
(...|...)     match one of the choices inside the parenthesis, they are separated by |
First choice:
    \s*       match zero or more whitespaces
    >         match a closing angle bracket
Second choice:
    \s+       match one or more (+) whitespaces
    [^>]+     match one or more (+) characters that are in the character set ([])...
              ...this set happens to match anything but (^) the closing angle bracket
    >         match a closing angle bracket

```


> **Interestedinthepenguin said:**
> I am a little lost as to what some of you are talking about [...] I am trying to extract body tags so that I can have sed insert text just after them.:oops:
The problem IMHO with regexes is that they can quickly turn into something absolutely unmanageable if you want to stick to the HTML specification. I believe the example I gave earlier about parsing e-mail addresses speaks for itself.
Another big problem is that most of the HTML on the Web doesn't even comply with the official HTML specifications (we all know who we must thank for that...) so this makes it even harder to parse it using simple regexes.
All you'll be able to get this way is a "good enough" approximation that will work most of the time, but that will miserably fail in some extreme cases. If it fits your needs, good for you, but please, please always remember that this is only a very dirty and Evil hack.

The proper way to do what you want would be, as others suggested, to use an HTML parser (I'd say BeautifulSoup is more adapted than the ElementTree XML parser, for the reasons we already pointed out), then insert a node in the parser's DOM tree and finally serialize it again as plain text. Granted, this requires way more work that just using a few regexes, so it's up to you to decide the tradeoff you really need (development time vs correctness).

---

### Post by pmasiar on 2008-02-04
> **aks44 said:**
>  BeautifulSoup is more adapted than the ElementTree XML parser, for the reasons we already pointed out

Thanks for reminding me about BeautifulSoup, I used ET, it was simple and worked fine, but you are right, HTML in the wild is total mess - and with coming IE* it looks becoming quite a lot messier. I'll try BS next time.

ET is also in core since 2.5 so no installing is needed. :-)

> this requires way more work that just using a few regexes, so it's up to you to decide the tradeoff you really need (development time vs correctness).

Doing it right often takes more time in the first round. Only after 2nd or 3rd round of changes you often realize that those guys were not as stupid as they seemed to, and all the complications were results of sweat and blood, trying to prevent you from problems later.

---

### Post by aks44 on 2008-02-04
> **pmasiar said:**
> TDoing it right often takes more time in the first round. Only after 2nd or 3rd round of changes you often realize that those guys were not as stupid as they seemed to, and all the complications were results of sweat and blood, trying to prevent you from problems later.

+1
TBH I consider the "worse is better" approach a total heresy. But one size does not fit all... ;)

---

### Post by pmasiar on 2008-02-04
> **aks44 said:**
>  I consider the "worse is better" approach a total heresy. But one size does not fit all... ;)

I don't think that "worse is better" and "do it right enough so you can maintain it later" are complete opposites. You don't want to build abstraction layers on top of each other into stratosphere either. As Buddha said: use middle road, avoid extremes :-)

But I think we had discussion about "worse is better" before, maybe we can continue this interesting discussion there?

---

### Post by Interestedinthepenguin on 2008-02-06
Thanks for the explanation, aks44.:)

---

