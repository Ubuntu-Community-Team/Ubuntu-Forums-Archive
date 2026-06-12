---
title: "wxPython Font, Controls and Sizer Problems"
date: 2012-07-12
forum: Programming Talk
---

### Post by theLured on 2012-07-12
Hello, I'm having trouble with sizers :)

My program needs to allow for font size changes, and I've had some problems getting the results I need.
Either my buttons are not resizing right, or the text is going off them, or the frame isn't resizing properly.
I've googled for hours with no solution, and a lot of confusion.

For my program, I want this layout.
[http://bayimg.com/kaPlBaADn]("http://bayimg.com/kaPlBaADn")

The width of A,B,C,D and E should all be as long as the longest button in this group. The A button has the longest label length
The A-E button's height will either be one or two lines, the height size can be different for each, or all the same, it doesn't matter much.

F should be as long as the buttons in A-E
G-J will all be in the middle, and their width should be the total width of A and F.
Finally the window has to then be resized to fit it all

So I'm wanting a window where all the controls are automatically sized to fit the text, and then the frame is set to that final size.

I've tried mixing sizers and using wx.EXPAND, but after hours of experimenting, I have no idea how to do this.
It seems like a really simple problem.

---

### Post by theLured on 2012-07-17
bumpity bump bump

---

