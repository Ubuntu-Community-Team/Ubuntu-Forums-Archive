---
title: "[SOLVED] Tracker what is it? what does it do? do i need it?"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by wawadave on 2008-11-02
Tracker what is it? what does it do? do i need it?
If i don,t need it how do i get rid of it?

useing the 8.10 version of ubuntu

---

### Post by ww711 on 2008-11-02
The name of the application gives it away, it 'tracks' your files on your pc - essentially a search tool.

If you don't want the tracker application, you can remove it from through synaptic package manager or use 

```
sudo apt-get remove tracker
```

---

### Post by mc4100 on 2008-11-02
Tracker is tool that indexes information about the files on your Computer: location, content, file type, etc., which means you can perform extensive searches very quickly. You don't **need** it, and can remove it if it's taxing you CPU too much (as it periodically updates it's 'indices'), but it's a convenience.
For more information, see the project homepage:

[http://www.gnome.org/projects/tracker/](http://www.gnome.org/projects/tracker/)
> To locate a file you only need to remember something about it, such as a word in the document or the artist of the song. 

---

### Post by Mazza558 on 2008-11-02
As others have said, it indexes your PC's files so you can find things quickly. It even indexes file contents (so you can find a document by searching a sentence from it). Depending on how often you want to search for things, it can be good or bad for you. I like to use it with the deskbar applet.

---

### Post by wawadave on 2008-11-02
Ok thank you very much for this info!!!!

---

