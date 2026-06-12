---
title: "grep to display a line starting with."
date: 2006-11-24
forum: Programming Talk
---

### Post by NESFreak on 2006-11-24
kinda noob question
I want grep to only display lines starting with an expression instead of a line containing the expression.

What command should i therefore use?
(it's for a bash script i'm trying to get working. strange bug with "turbo" being seen as "Galaxian Turbo" turbo "Turbo" (turbo does run though)
NESFreak

!!!!!!!!!!!!!

nevermind
man is your friend
>        The  caret ^ and the dollar sign $ are metacharacters that respectively
       match the empty string at the beginning and end of a line.  The symbols
       \<  and \> respectively match the empty string at the beginning and end
       of a word.  The symbol \b matches the empty string at  the  edge  of  a
       word,  and \B matches the empty string provided it’s not at the edge of
       a word.

---

