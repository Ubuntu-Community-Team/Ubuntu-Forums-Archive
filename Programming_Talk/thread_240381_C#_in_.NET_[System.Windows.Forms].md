---
title: "C# in .NET [System.Windows.Forms]"
date: 2006-08-20
forum: Programming Talk
---

### Post by Thund3rstruck on 2006-08-20
Hi guys,

 I finally decided to start porting over some of my enterprise C#.net applications to Linux recently and I was quite disappointed to learn that there is no System.Windows.Forms.* namespace or classes available. 

 I have been tooling around with GTK# but I'm having difficulties using it since the controls are named differently (where is listBox, ListView, TreeView, etc??). 

 Can someone recommend a good msdn-style reference for GTK# (with code samples for each method)? 

 Additionally, is there an IDE I can use where I can draw the controls on the forms automatically (Visual Studio style) instead of having to tediously tell the controls exactly where on the form the need to be drawn manually? MonoDevelop doesn't seem to have a graphical forms editor.

---

### Post by meng on 2006-08-20
I thought mono had Windows.Forms compatibility
[http://www.mono-project.com/WinForms](http://www.mono-project.com/WinForms)
EDIT: or at least may have it soon

---

### Post by Thund3rstruck on 2006-08-21
System.Windows.Forms is not available in the version in the repos (v0.10), perhaps I will look at the dev version. 

Any suggestions on a code resource like msdn for GTK#? Also, I wonder why Intellisense doesn't work for GTK libraries like it does for .NET FCL libs?

---

### Post by mostwanted on 2006-08-22
> **Thund3rstruck said:**
> SAny suggestions on a code resource like msdn for GTK#?

[http://www.go-mono.com/docs/](http://www.go-mono.com/docs/)

---

