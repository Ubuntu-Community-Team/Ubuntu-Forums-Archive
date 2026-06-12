---
title: "scrolling curses with subpad in python"
date: 2013-05-14
forum: Programming Talk
---

### Post by boast on 2013-05-14
I'm using the scrolling technique posted here: [http://stackoverflow.com/questions/2515244/how-to-scroll-text-in-python-curses-subwindow](http://stackoverflow.com/questions/2515244/how-to-scroll-text-in-python-curses-subwindow) 

So I have a pad filled with text, and then I'm using a subpad to scroll through it. I have it set so that when you press 'e' it jumps to specific window positions. But the issue seems to be that some of the old text stays in the screen if it is not overwritten by the new line. 

Is there a way to sort of redraw everything on the screen? It seems when doing the subpad.refresh(...) it doesn't redraw the entire screen, just where new characters will be. 

Here is an example: [http://i.imgur.com/vPblx62.png](http://i.imgur.com/vPblx62.png) if there is a color it should be the entire line

---

