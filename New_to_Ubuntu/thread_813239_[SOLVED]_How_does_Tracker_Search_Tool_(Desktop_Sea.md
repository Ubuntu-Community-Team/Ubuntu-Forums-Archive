---
title: "[SOLVED] How does Tracker Search Tool (Desktop Search) work?"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by swarup on 2008-05-30
Using Hardy Ubuntu 8.04. I went to System->Preferences->Search and Indexing, and enabled Indexing and Watching. The tool is set to watch my Home directory. Once I clicked on "apply", the indexer did its work of indexing all the files. An icon appeared on the upper panel, and by passing my cursor over it for the few 15 minutes, it give progress report of how many files it had indexed and how many were left. Then it completed its (initial) indexing work.

But when I open the Tracker Search Tool and put even a simple word like "the" in the search window and click "Find", the result immediately comes that "Your search returned no results". What needs to be done to get the Tracker Search tool to work?

---

### Post by bjm1904 on 2008-05-30
There are words which are exluded from indexing (i.e. 'the'). Try a word you know is definitely about (i.e. a filename, title, etc.) to test things out.

Edited:

Ok, that was probably just an example, but the point still stands - if you're having genuine problems, then you can try upping the number of words and cache size, and make sure you've enabled everything. If all else fails, there's always beagle

---

### Post by rajaram_s on 2008-05-30
That was somethin even I was wondering.... This tracker search tool hasnt goven me a single valid search entry till date...

---

### Post by swarup on 2008-05-30
> **bjm1904 said:**
> There are words which are exluded from indexing (i.e. 'the'). Try a word you know is definitely about (i.e. a filename, title, etc.) to test things out.

Actually, I started experimenting a bit more and found that you are correct. It IS working. I had tried only one Hindi word and one English word, and it didn't work for either one. But now I've started to experiment more, and have found that although there seem to be some words it doesn't catch for some reason, most words in both English and Hindi, it DOES catch. Very impressive. And fast too, even on my old computer. I'll experiment a bit more to try and get a sense of what it catches and what not, and why.

---

### Post by Bubba64 on 2008-05-30
Gnomedo is a cool search tool. I removed tracker in synaptic. I'm sorry I didn't see the solved

---

### Post by swarup on 2008-05-31
That's ok, I welcome your idea! I'll certainly install Gnomedo and see how it is. And if anyone else has thoughts on search tools, they are surely welcome to share them as well. The more fresh ideas, the better. :)

---

