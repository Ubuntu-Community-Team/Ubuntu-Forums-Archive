---
title: "Help for creating a basic Editor"
date: 2013-02-08
forum: Programming Talk
---

### Post by Yuva Raj on 2013-02-08
Hai,
i would like to create a simple basic editor like Bluefish which should support C,c++ language.
which tool is used to create a GUI? and should we connect the editor with compiler to compile the language?

Since im newbie,i dont know how to get the concept & resouce.
Please help :(

---

### Post by r-senior on 2013-02-08
The major toolkits have source view controls that provide support for syntax highlighting, line numbers, right margin, etc. GTK, for example, has a gtksourceview3 control to edit code. This is the same control used by gedit. Another GTK one is Scintilla, as used by Geany. Qt and wxWidgets probably have equivalents.

Once you have an idea of which source view control to use, you need to pick your programming language. C, C++ and Python would be the obvious choices and they have libraries for interacting with the different toolkits.

Then, depending on your toolkit, you might choose to use a GUI designer. Glade for GTK, QtCreator for Qt, etc.

In terms of connecting to a compiler, you might want to look at Geany's approach, which fires off make or the appropriate compiler.

Obviously there are already plenty of editors so the assumption would be that you are doing this for learning and/or enjoyment. 

Zetcode is a good source of introductory tutorials to get the feel of different toolkits and their use with different languages:

[http://www.zetcode.com/](http://www.zetcode.com/)

---

### Post by Yuva Raj on 2013-02-08
> **r-senior said:**
> The major toolkits have source view controls that provide support for syntax highlighting, line numbers, right margin, etc. GTK, for example, has a gtksourceview3 control to edit code. This is the same control used by gedit. Another GTK one is Scintilla, as used by Geany. Qt and wxWidgets probably have equivalents.

Once you have an idea of which source view control to use, you need to pick your programming language. C, C++ and Python would be the obvious choices and they have libraries for interacting with the different toolkits.

Then, depending on your toolkit, you might choose to use a GUI designer. Glade for GTK, QtCreator for Qt, etc.

In terms of connecting to a compiler, you might want to look at Geany's approach, which fires off make or the appropriate compiler.

Obviously there are already plenty of editors so the assumption would be that you are doing this for learning and/or enjoyment. 

Zetcode is a good source of introductory tutorials to get the feel of different toolkits and their use with different languages:

[http://www.zetcode.com/](http://www.zetcode.com/)

Thank you for your reply sir :)
I 've got some knowledge after i did some search in google.

But i have one important doubt. 

Can we embedd our editor in our website if we created by GTK or QT?

---

### Post by r-senior on 2013-02-08
> **Yuva Raj said:**
> Can we embedd our editor in our website if we created by GTK or QT?
What do you mean by embed?

---

### Post by Yuva Raj on 2013-02-08
> **Yuva Raj said:**
> Thank you for your reply sir :)
I 've got some knowledge after i did some search in google.

But i have one important doubt. 

Can we embedd our editor in our website if we created by GTK or QT?

Look at this sir : [https://compilr.com/](https://compilr.com/)

We would like to design something like this where one can compile the code online without installing software on every machine.

So,if we created an GUI using GT or QT,can we place our editor in our website Similar to Compilr online IDE?

---

### Post by r-senior on 2013-02-08
A GTK or Qt desktop application cannot be embedded in a website, unless there is some magic technology I don't know about.

I don't know how that site works, but I suspect it's using Javascript-based controls at the front and some sort of virtual shell at the back.

I signed up. It looks pretty cool, although I couldn't compile or run anything.

---

### Post by Yuva Raj on 2013-02-08
> **r-senior said:**
> A GTK or Qt desktop application cannot be embedded in a website, unless there is some magic technology I don't know about.

I don't know how that site works, but I suspect it's using Javascript-based controls at the front and some sort of virtual shell at the back.

I signed up. It looks pretty cool, although I couldn't compile or run anything.

Yes,its runs by Javascript.
how to make like this interface using Javascript? 

Is there any tools to create a UI for web like QT for desktop?
Waiting for your response sir!

---

### Post by hakermania on 2013-02-08
Without wanting to dishearten you in any way, I think that one with limited knowledge on web development should begin with something less complex, like a simple web page with some extras built with Javascript/HTML5.

Consider that compiling and running someone's code automatically requires a lot of security checks; you wouldn't like a rootkit compiled with your compiler and run on your server, would you?

Just some notice...

---

### Post by GeneralZod on 2013-02-08
> **r-senior said:**
> A GTK or Qt desktop application cannot be embedded in a website, unless there is some magic technology I don't know about.


[*coughs*](http://ssj-gz.blogspot.co.uk/2013/01/emscripten-qt-progress-faster-better.html) ;)

---

### Post by Yuva Raj on 2013-02-08
> **hakermania said:**
> Without wanting to dishearten you in any way, I think that one with limited knowledge on web development should begin with something less complex, like a simple web page with some extras built with Javascript/HTML5.

Consider that compiling and running someone's code automatically requires a lot of security checks; you wouldn't like a rootkit compiled with your compiler and run on your server, would you?

Just some notice...

I admit that i've not required knowledge know :(
But, my fate ..its my final year project.

I dont know how to react,that is the reason i came here for ubuntu user's help!

---

