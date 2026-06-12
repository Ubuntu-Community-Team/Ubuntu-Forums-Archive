---
title: "Strange terminal interaction..."
date: 2018-06-13
forum: New to Ubuntu
---

### Post by frog32 on 2018-06-13
Hi! Apologies for the awful title, but hopefully once you read my post you'll understand why I didn't really know what to write there.

I'm doing a few courses online, and at one point I'm just exploring my filesystem and getting accustomed to various commands that I can run. After a simple "ls" to see the contents of my current directory, suddenly a paragraph from a web page that I had left more than 10 minutes prior shows up in the terminal, and a second or two later another paragraph from the same page pops up as well. I mean, it's pretty confusing that it happened at all, let alone that it was from a web page that I did not currently have open.

At no point did I ever copy those paragraphs, and my history somehow shows the first paragraph as a line that I entered (spoilers: I didn't) but not the second paragraph, I assume that's because I pressed ctrl+c before whatever was occurring had finished. The first paragraph started with 'passing' so I immediately got a "passing: command not found", which is when the second paragraph appeared.

Anyone have any idea as to what happened? I'm at a loss.

---

### Post by Holger_Gehrke on 2018-06-14
X has two separate ways of doing copy and paste. The one everybody knows (ctrl-c/ctrl-v -- or in a terminal ctrl-shift-c/ctrl-shift-v) and the older one which works by just marking the text to copy and hitting the middle mouse button (or both the left and right mouse button at the same time) to paste. So if you had for some reason marked that passage of text in the browser (I sometimes mark bits of text to be able to quickly find them again in a long page ...) and then somehow produced a middle-click (laptop keyboard with trackpad ?), that could be it ...

Holger

---

