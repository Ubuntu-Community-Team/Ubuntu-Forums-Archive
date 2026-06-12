---
title: "perl regexp to match bash comments"
date: 2010-12-17
forum: Programming Talk
---

### Post by roccivic on 2010-12-17
Hi folks,

I'm having a really hard time writing what should be a really straightforward PERL regular expression. I need to match all comments in PNM and PGM image files. So I need to match strings that:

[LIST]
[*]can start with anything
[*]have a hash symbol '#'
[*]are followed by any character except for '\n', '\r' or '\r\n'
[*]are terminated by '\n', '\r' or '\r\n'
[/LIST]

So far I tried this (which of course does not work)
[PHP]$data = preg_replace( '/#./m', '', $data ); [/PHP]

---

### Post by Arndt on 2010-12-17
> **roccivic said:**
> Hi folks,

I'm having a really hard time writing what should be a really straightforward PERL regular expression. I need to match all comments in PNM and PGM image files. So I need to match strings that:

[LIST]
[*]can start with anything
[*]have a hash symbol '#'
[*]are followed by any character except for '\n', '\r' or '\r\n'
[*]are terminated by '\n', '\r' or '\r\n'
[/LIST]

So far I tried this (which of course does not work)
[PHP]$data = preg_replace( '/#./m', '', $data ); [/PHP]

What about this?

```
$data = preg_replace( '/#.*/m', '', $data );
```

---

### Post by roccivic on 2010-12-17
> **Arndt said:**
> What about this?

```
$data = preg_replace( '/#.*/m', '', $data );
```

It works great, thanks.

Was only one character away...

---

### Post by shawnhcorey on 2010-12-17
> **roccivic said:**
> Hi folks,

I'm having a really hard time writing what should be a really straightforward PERL regular expression. I need to match all comments in PNM and PGM image files. So I need to match strings that:

[LIST]
[*]can start with anything
[*]have a hash symbol '#'
[*]are followed by any character except for '\n', '\r' or '\r\n'
[*]are terminated by '\n', '\r' or '\r\n'
[/LIST]

So far I tried this (which of course does not work)
[PHP]$data = preg_replace( '/#./m', '', $data ); [/PHP]

Why are you asking for Perl and then write in PHP?

---

### Post by roccivic on 2010-12-17
That's cause PHP uses Perl Compatible Regular Expressions: [http://www.php.net/manual/en/ref.pcre.php](http://www.php.net/manual/en/ref.pcre.php) (as well as the deprecated POSIX regex).

---

### Post by shawnhcorey on 2010-12-17
> **roccivic said:**
> That's cause PHP uses Perl Compatible Regular Expressions: [http://www.php.net/manual/en/ref.pcre.php](http://www.php.net/manual/en/ref.pcre.php) (as well as the deprecated POSIX regex).

OK, if you say so:
```
m{ \# [^\r\n] .*? (?: \r\n | \r | \n ) }msx;
```

---

### Post by roccivic on 2010-12-17
Your regexp also works great, although I had to strip the spaces and curly brackets:

[PHP]$data = preg_replace( '/#[^\r\n].*?(?:\r\n|\r|\n)/m', '', $data );[/PHP]

Thanks ;)

---

### Post by shawnhcorey on 2010-12-18
> **roccivic said:**
> Your regexp also works great, although I had to strip the spaces and curly brackets:

The curly brackets are delimiters.  The /x option at the end allows whitespace in the pattern.

---

