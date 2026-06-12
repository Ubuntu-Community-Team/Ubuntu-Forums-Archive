---
title: "Quick Regex Question"
date: 2008-04-18
forum: Programming Talk
---

### Post by solarwind on 2008-04-18
How do I match an HTML start container type tag?

Example, I want to match:    <a href="http://somesite.com/somefile.html">

but NOT    <br />

What I have right now is:    <\w+\s*[^>]*>

It means
<, one or more word character, zero or more spaces, zero or more of anything that's not a > and finally a tag end.

However, this also matches single tags like <br />. I don't want it to match those. What is a solution to this?

---

### Post by stroyan on 2008-04-19
You can try matching the closing tag that should always be there.
<(\w+)[^>]*?>([^<]*?)</\1>
Watch out that the pattern can span multiple lines.
And remember that it should be case insensitive.

---

### Post by stroyan on 2008-04-19
Buy the way.  The "visual-regexp" package in the ubuntu universe repository is an interesting way to try out regular expressions.

---

### Post by ghostdog74 on 2008-04-19
why not make your match more specific, eg if you are really just wanting to match href, then put href in your search pattern.

---

### Post by aks44 on 2008-04-19
**@stroyan:** what about matching eg. [COLOR="DarkRed"]<a href="foo"><b>bar</b></a>[/COLOR] ? Your [COLOR="DarkRed"]([^<]*?)[/COLOR] forbids that.

**@solarwind:** the regex you're looking for would probably be along the lines of:
(case-insensitive, \s spanning multiple lines)
```
<[a-z]+(\s*|\s+[^>]*[^/>])>
```
I'm pretty sure the second part of the alternative needs a lot of adjustments though, but you get the idea...




Now I'll be beating a dead horse, but... why in the first place use regexes to parse HTML?

There are sooo many cases of "acceptable" (but not necessarily well-formed) HTML that break "simple minded" regexes like the one I provided...

eg. [COLOR="DarkRed"]<a href="foo>bar">foobar</a>[/COLOR]

---

### Post by pmasiar on 2008-04-19
Parsing HTML by hand-carved Regexes is sucker's game. This is exactly the reason why XML parsers are there: somebody invested lot of time doing it right. IMHO it is faster and more forward-looking to learn how to use generic XML/HTML parser than hoping you can create custom regex handling special cases, and do it right, and create all valid test cases, and test it.

Have fun.

---

### Post by solarwind on 2008-04-19
1. I don't use Ubuntu, I use Arch Linux, but I'll give the visual-regexp package a try.
2. Trust me, I've tried xml libraries. That's not what I want. I need to see the document as a whole, scan it for tags, find a specific tag, extract data, and so on.
3. Thanks for the help, I'll try it out and post back.

---

