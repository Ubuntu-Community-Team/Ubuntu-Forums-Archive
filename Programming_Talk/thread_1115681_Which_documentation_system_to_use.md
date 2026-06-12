---
title: "Which documentation system to use"
date: 2009-04-04
forum: Programming Talk
---

### Post by ZuLuuuuuu on 2009-04-04
Hello,

After completing a program, or during the development process I need to write some documentation, like tutorials, manual etc... I want to write a simple text file and then want it to be converted into HTML, PDF and CHM automatically. Which documentation system do you suggest as the best option?

---

### Post by Arndt on 2009-04-04
> **ZuLuuuuuu said:**
> Hello,

After completing a program, or during the development process I need to write some documentation, like tutorials, manual etc... I want to write a simple text file and then want it to be converted into HTML, PDF and CHM automatically. Which documentation system do you suggest as the best option?

Look at texinfo.

---

### Post by ZuLuuuuuu on 2009-04-04
> **Arndt said:**
> Look at texinfo.

Does not have Windows binaries, I guess? It might be a problem.

I found 3 options so far: Texinfo, Doxygen and POD (Plain Old Documentation) but I would like to hear the advantages/disadvantages from the users of these.

Note: I included POD because I know some Perl. So, documentation systems for other languages like Python or Ruby are not for me.

I have one more question: When I look at some plain text documentations, I see that the lines are wrapped so that they don't exceed 80 character width. Is there an easy way to do wrapping automatically while you are writing or do they do this manually? If they do this manually then isn't that hard to change all the wrapping when for example you decided to remove a sentence or even a word etc?

---

### Post by hessiess on 2009-04-04
Doxygen is reasnable, but it produces terrable HTML.

---

### Post by Arndt on 2009-04-04
> I have one more question: When I look at some plain text documentations, I see that the lines are wrapped so that they don't exceed 80 character width. Is there an easy way to do wrapping automatically while you are writing or do they do this manually? If they do this manually then isn't that hard to change all the wrapping when for example you decided to remove a sentence or even a word etc?

I write text in Emacs, and there are practical commands to restore the
justification of the text. M-q, for example, rejustifies the current paragraph.

There is probably an Emacs mode to do automatic wrapping, but I don't use it; I press Return (or Linefeed) when needed.

(I think "justify" is not the word I want, because I don't necessarily mean straight right-edge margins, but it will serve.)

---

