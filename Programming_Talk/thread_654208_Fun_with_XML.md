---
title: "Fun with XML"
date: 2007-12-30
forum: Programming Talk
---

### Post by max.diems on 2007-12-30
I'm working on an XML book/movie/music list. Would anyone like to help? I'm pretty sure I know what tags I'll use, so I mainly need someone to check the DTD and work on the CSS (I'll still take ideas for changes to tags). Thanks!

**EDIT:** No, you are not being co-opted to do my homework.

---

### Post by CptPicard on 2007-12-30
XML? ... Fun?

What are you talking about? I am afraid that I do not understand :confused:

---

### Post by Wybiral on 2007-12-30
> **CptPicard said:**
> XML? ... Fun?

What are you talking about? I am afraid that I do not understand :confused:

XML isn't THAT bad.

---

### Post by max.diems on 2007-12-30
Sample document:

[html]
<?xml version="1.0" encoding="utf-8"?>
<library version="1.0">[INDENT]<owner>...</owner>

<book>[INDENT]<title>...</title>
<author>...</author>
<series>...</series>
<pages>...</pages>
<publisher>...</publisher>
<edition>...</edition>
<isbn type="isbn-10">...</isbn>
<isbn type="isbn-13">...</isbn>
[/INDENT]</book>

<music>[INDENT]<album>...</album>
<artist>...</artist>
<media>...</media>
[/INDENT]</music>

<movie>[INDENT]<title>...</title>
<director>...</director>
<producer>...</producer>
<actor>...</actor>
...
<actor>...</actor>
<isbn type="isbn-10">...</isbn>
<isbn type="isbn-13">...</isbn>
[/INDENT]</movie>

<publication>[INDENT]<name>...</name>
<type>...</type>
<issue>[INDENT]<pubDate>...</pubDate>
<topics>...</topics>
[/INDENT]</issue>
...
<issue>[INDENT]...
[/INDENT]</issue>
[/INDENT]</publication>
[/INDENT]</library>

<book>- for books
<movie>- for movies
<music>- for CD, tape, 8track, LP, digital recording (listed in <media>)
<publication>- for magazine, newspaper, etc. (listed in <type>)

---

### Post by max.diems on 2007-12-30
> **CptPicard said:**
> XML? ... Fun?

What are you talking about? I am afraid that I do not understand :confused:
Well, you looked at my post, no? :twisted:

Anyway, I'm just taking the advice in your .sig....

---

### Post by CptPicard on 2007-12-30
> **max.diems said:**
> 
Anyway, I'm just taking the advice in your .sig....

So I take it you have sadistic tendencies, thinking XML = violence = fun ;)

Or perhaps it's more like masochistic ones...

---

### Post by max.diems on 2007-12-30
And a DTD would be good to review:

```

<!-- XML Book Collection DTD, version 1.0 -->

<!ELEMENT library (book,music,movie,publication,owner)>
<!ATTLIST library version CDATA #FIXED "1.0">

<!ELEMENT owner (#PCDATA)>

<!ELEMENT book (title,author,pages,edition,publisher,series,isbn)>

<!ELEMENT title (#PCDATA)>
<!ELEMENT author (#PCDATA)>
<!ELEMENT pages (#PCDATA)>
<!ELEMENT edition (#PCDATA|sup)*>
<!ELEMENT publisher (#PCDATA)>
<!ELEMENT series (#PCDATA)>
<!ELEMENT isbn (#PCDATA)>
<!ATTLIST isbn type (isbn-10|isbn-13) "isbn-10">

<!ELEMENT music (album,artist,media)>
<!ELEMENT album (#PCDATA)>
<!ELEMENT artist (#PCDATA)>
<!ELEMENT media (#PCDATA)>

<!ELEMENT movie (title,director,producer,actor,genre)>
<!ELEMENT director (#PCDATA)>
<!ELEMENT producer (#PCDATA)>
<!ELEMENT actor (#PCDATA)>

<!ELEMENT publication (name,type,issue)>
<!ELEMENT name (#PCDATA)>
<!ELEMENT type (#PCDATA)>
<!ELEMENT issue (pubDate,topics)>
<!ELEMENT pubDate (#PCDATA)>
<!ELEMENT topics (#PCDATA)>

<!ELEMENT sup (#PCDATA)>

```

---

### Post by Erdaron on 2007-12-31
I would suggest adding a tag for publications that would indicate at least the first page of the article. (In my own experience, articles in scientific journals are often listed by their first page, makes it easier to find them in a catalog.)

---

### Post by LaRoza on 2007-12-31
> **max.diems said:**
> And a DTD would be good to review:



Use a Schema, not a DTD.

Interestingly, when using Schemas, you get statements like:

> 
The element element is used to define an element.


I will never forget that statement from an XML book I have.

---

### Post by CptPicard on 2008-01-01
> **LaRoza said:**
> 
I will never forget that statement from an XML book I have.

[http://en.wikipedia.org/wiki/Buffalo_buffalo_Buffalo_buffalo_buffalo_buffalo_Buffalo_buffalo](http://en.wikipedia.org/wiki/Buffalo_buffalo_Buffalo_buffalo_buffalo_buffalo_Buffalo_buffalo)

---

### Post by LaRoza on 2008-01-01
> **CptPicard said:**
> [http://en.wikipedia.org/wiki/Buffalo_buffalo_Buffalo_buffalo_buffalo_buffalo_Buffalo_buffalo](http://en.wikipedia.org/wiki/Buffalo_buffalo_Buffalo_buffalo_buffalo_buffalo_Buffalo_buffalo)

Funny. I will have to tell somone.

---

### Post by Wybiral on 2008-01-01
> **CptPicard said:**
> [http://en.wikipedia.org/wiki/Buffalo_buffalo_Buffalo_buffalo_buffalo_buffalo_Buffalo_buffalo](http://en.wikipedia.org/wiki/Buffalo_buffalo_Buffalo_buffalo_buffalo_buffalo_Buffalo_buffalo)

Beautiful!

---

### Post by Samjiman on 2008-01-02
> **CptPicard said:**
> XML? ... Fun?

What are you talking about? I am afraid that I do not understand :confused:

What are *you* talking about? XML rocks, dude. :guitar:
I love it. Beats the crap hands down out of INI files imo. Of course, maybe you prefer YAML.

---

### Post by pmasiar on 2008-01-02
XML was designed for computers, not humans. It is pain to read, use YAML instead:
[http://en.wikipedia.org/wiki/Yaml](http://en.wikipedia.org/wiki/Yaml) : human-readable data serialization format

---

### Post by Samjiman on 2008-01-02
YAML is okay. I don't see how XML is unreadable though.
Unless you lack the necessary brain power to read tags as labels and the contained data within as values, which in my opinion is very easily.

---

### Post by LaRoza on 2008-01-02
> **pmasiar said:**
> XML was designed for computers, not humans. It is pain to read, use YAML instead:
[http://en.wikipedia.org/wiki/Yaml](http://en.wikipedia.org/wiki/Yaml) : human-readable data serialization format

Welcome back!

---

