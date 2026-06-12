---
title: "A RapGenius for coding?"
date: 2014-01-27
forum: Programming Talk
---

### Post by mustang on 2014-01-27
I teach high school students how to program in JavaScript. I also assign homework to them as well. I'd like to give them feedback electronically in the form of general comments as well as comments for specific lines of code.
I'm looking for a tool that accomplishes the latter. I want to pull in code from an outside source (say, a git repo) and annotate it like I would annotate lyrics in RapGenius. Is there anything out there that does this?

---

### Post by trent.josephsen on 2014-01-27
Well, I mean... how about a git repo? Provide hosting (or have them use github), teach the students to maintain a code repository and have them give you push. Then "git diff --color <commit>" will helpfully highlight any added comments. With context. And it's an excellent way to teach your students to use distributed revision control, which is more generally useful than Javascript anyway.

(I have no idea what RapGenius is)

---

### Post by mustang on 2014-01-27
> **trent.josephsen said:**
> Well, I mean... how about a git repo? Provide hosting (or have them use github), teach the students to maintain a code repository and have them give you push. Then "git diff --color <commit>" will helpfully highlight any added comments. With context. And it's an excellent way to teach your students to use distributed revision control, which is more generally useful than Javascript anyway.

(I have no idea what RapGenius is)

I would prefer a solution that does not modify their code. For example, if I asked them to fix their mistakes, I don't want my commentary cluttering that. 

Here's an example of a rapgenius page: [http://poetry.rapgenius.com/Saul-williams-coded-language-annotated](http://poetry.rapgenius.com/Saul-williams-coded-language-annotated)

One can click on links to see the full annotation.

---

### Post by trent.josephsen on 2014-01-27
Branches

---

### Post by mustang on 2014-01-28
> **trent.josephsen said:**
> Branches

Trent, at that point I'd be reappropriating git for something that it's not meant to do. Also, my students are at the high school level so they are just learning these tools. I'm after a simple, ideally standalone tool that lets me annotate code.

---

### Post by trent.josephsen on 2014-01-28
You caught me at a bad time yesterday; sorry if my curtness seemed rude.

> **mustang said:**
> Trent, at that point I'd be reappropriating git for something that it's not meant to do.
I think you have a rather narrow interpretation of what git is meant to do. But I'll consider that you may have a point.
> Also, my students are at the high school level so they are just learning these tools.
Which, I respectfully submit, is precisely why they should be learning Git. Or Mercurial or whatever your favorite VCS is. Knowing how to use version control is more useful than any programming language. Heck, even knowing it exists will put them ahead of most high schoolers (and probably an astonishing number of CS graduates).

But back to your question, sorry, I don't know of anything like that (that isn't version control). Perhaps somebody else...?

---

