---
title: "Java GUI .form file and Difference in windows and linux and mac"
date: 2008-02-27
forum: Programming Talk
---

### Post by mattgaunt on 2008-02-27
Heya everyone,

Im working on a group project to make a program that creates word-search programs.

Anyway, the GUI for it is using the java GUI libraries but they look different in windows, linux and mac, jus the text size and button size and so on. For instance text next to a button can be viewed fully in windows :

"Title :"

but in linux the button kinda covers the text so looks like :

"Ti..."

Any ideas wot causes this and any possible fixes??

Also the GUI has been programmed using netbeans, now netbeans makes a file of type .form, now sometimes big chunks of the GUI doesnt appear but is fixed if u move a button in netbeans and then move it back and save it. One of my friends assumed this was because it changed the .form file, but any ideas on reasons for this to happen and again any fixes??

Gaunt

---

### Post by harlan on 2008-02-27
Do you use AWT or Swing?
Because AWT uses the OS graphic lib

---

### Post by mattgaunt on 2008-02-27
Thanks for the reply, it looks like we've used a bit of both, alot of the buttons are Swing but some of the event handlers are AWT.

Any hints on what we should look for / change? or could it be a whole host of changes we'd need to do to make it all nice and pretty?

Gaunt

---

### Post by mattgaunt on 2008-02-28
Ive spent quite a bit of today attemptin to fix some bugs in the code and it seems alot like it uses mainly the Swing library, so is there a way to standardise the appearance of it??

Gaunt

---

