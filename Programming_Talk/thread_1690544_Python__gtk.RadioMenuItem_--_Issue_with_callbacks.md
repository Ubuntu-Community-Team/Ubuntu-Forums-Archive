---
title: "Python:  gtk.RadioMenuItem -- Issue with callbacks"
date: 2011-02-18
forum: Programming Talk
---

### Post by arm-c on 2011-02-18
Hello,

I am having a difficult time finding a solution to an issue I am having when using the gtk.RadioMenuItem to create a group.  I will appreciate anyone who can give me a good solution to this.

Issue:  The radio group contains several items.  When one is selected, it executes the code as expected; however, when a second one is selected in the group, the program FIRST re-executes the callback from the selected item and SECOND executes the callback for the newly selected item.

I do not understand this behavior in the program and can find nothing about it through internet searches and python documentation.  There was one link that indicated a similar problem when using gtk; however, no real solution I could see was pasted on [Stack Overflow]("http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBMQFjAA&url=http%3A%2F%2Fstackoverflow.com%2Fquestions%2F418591%2Fsignal-fires-twice-from-gtkmm-popup-list&rct=j&q=python%20gtk.RadioMenuItem%20signal%20twice%20called&ei=BdteTYTYIoGclgeV8ayrDA&usg=AFQjCNFOzBOYYS56MQ_iBIbkgEBf7hsCWA&cad=rja")

[http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBMQFjAA&url=http%3A%2F%2Fstackoverflow.com%2Fquestions%2F418591%2Fsignal-fires-twice-from-gtkmm-popup-list&rct=j&q=python%20gtk.RadioMenuItem%20signal%20twice%20called&ei=BdteTYTYIoGclgeV8ayrDA&usg=AFQjCNFOzBOYYS56MQ_iBIbkgEBf7hsCWA&cad=rja](http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBMQFjAA&url=http%3A%2F%2Fstackoverflow.com%2Fquestions%2F418591%2Fsignal-fires-twice-from-gtkmm-popup-list&rct=j&q=python%20gtk.RadioMenuItem%20signal%20twice%20called&ei=BdteTYTYIoGclgeV8ayrDA&usg=AFQjCNFOzBOYYS56MQ_iBIbkgEBf7hsCWA&cad=rja)

---

