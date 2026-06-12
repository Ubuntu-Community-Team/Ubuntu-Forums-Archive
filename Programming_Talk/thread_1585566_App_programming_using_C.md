---
title: "App programming using C"
date: 2010-09-30
forum: Programming Talk
---

### Post by HrQlX on 2010-09-30
Hi @all,
I am new to Ubuntu and try to find the appropriate software/packages to program apps using C or C++.
The resulting app shouldn't be command-line based, but "pretty". 

Any ideas how and where to start?

Thanks, HrQlX

---

### Post by Sub101 on 2010-09-30
If you are completely new to programming I would suggest starting by building a simple app *without* using any IDE, as they can get in the way of you learning what is going on. Also I would avoid going into GUI apps straight away. The basis is the most important bit.

However if you are experienced then what I use to develop C++ is Eclipse with the C++ plugin and Qt Creator.

---

### Post by HrQlX on 2010-09-30
Hi Sub101,
First of all thanks for your quick reply.
Although I'm new to Ubuntu, I'm fairly familiar with programing small and medium sized command-line programs as part of my studies. Now I got annoyed by how overpriced programs are some of my friends have to use for their businesses and wanted to give it a go myself. 
Therefore the IDE is what I really want to get my hands on...

---

### Post by worksofcraft on 2010-09-30
A great way to start is by doing this [glade tutorial]("http://glade.gnome.org/").

Glade is a gui interface designer that has bindings to many languages including C and C++. I found it handy to be able to test my GUI with a simple Python script before coding things in C++ and I've heard that your apps designed with this will also port to Windows systems!

---

### Post by Joeb454 on 2010-09-30
If you're looking for the C libraries - install [build-essential](apt://build-essential) from the repositories

---

### Post by HrQlX on 2010-09-30
Hi,
@Joeb454: The build-essential package was easy to find, but thanks anyway.

@worksofcraft: Yes, thank you. Glade is the sort of program I was looking for. 

Thanks for your help so far. I'll give Glade a go... But any suggestions for further tutorials or programming environments are appreciated!

---

### Post by Sub101 on 2010-09-30
If the aim is to create a GUI you have, in my opinion, two main paths which are GTK and QT. They are both GUI libraries for use with C++ (and some other languages).

[http://www.wikivs.com/wiki/GTK_vs_Qt](http://www.wikivs.com/wiki/GTK_vs_Qt)


PS. There is also WxWidgets but I know very little about it

---

