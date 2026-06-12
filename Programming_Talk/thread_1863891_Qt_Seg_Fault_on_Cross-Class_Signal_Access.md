---
title: "Qt Seg Fault on Cross-Class Signal Access"
date: 2011-10-18
forum: Programming Talk
---

### Post by Tk007LwZFJW5ej on 2011-10-18
I have a class called appWindow that subclasses QMainWindow. It contains a QProgressBar* called webLoad and an instance of another class:

```
firstpage  = new articlePage;
```articlePage contains a QWebView called wordSearch.

I want the progress bar to show the progress of wordSearch while loading, so, in appwindow.cpp, I have:

```
connect(firstPage->wordSearch, SIGNAL(loadProgress(int)), webLoad, SLOT(setValue(int)));
```.

When I try to access a signal of a member variable of another class, I get a seg fault. There's only one case in which I've made this work: accessing the clicked() signal of QPushButton *quit of appWindow from main.cpp to quit the application. 
I always instantiate the class before trying to connect signals. I can access signals of in-class member variables just fine. I've been banging my head over this for days. What could I be doing wrong?

---

### Post by hakermania on 2011-10-18
Hello, I don't know an instant solution to your question, but I would suggest asking at
[www.qtcentre.org/forum.php](www.qtcentre.org/forum.php) or at
[http://www.qtforum.org/index.html](http://www.qtforum.org/index.html) :)

---

### Post by karlson on 2011-10-18
> **StarKid said:**
> I have a class called appWindow that subclasses QMainWindow. It contains a QProgressBar* called webLoad and an instance of another class:

```
firstpage  = new articlePage;
```articlePage contains a QWebView called wordSearch.

I want the progress bar to show the progress of wordSearch while loading, so, in appwindow.cpp, I have:

```
connect(firstPage->wordSearch, SIGNAL(loadProgress(int)), webLoad, SLOT(setValue(int)));
```.

When I try to access a signal of a member variable of another class, I get a seg fault. There's only one case in which I've made this work: accessing the clicked() signal of QPushButton *quit of appWindow from main.cpp to quit the application. 
I always instantiate the class before trying to connect signals. I can access signals of in-class member variables just fine. I've been banging my head over this for days. What could I be doing wrong?

Have you analyzed the core dump?

---

