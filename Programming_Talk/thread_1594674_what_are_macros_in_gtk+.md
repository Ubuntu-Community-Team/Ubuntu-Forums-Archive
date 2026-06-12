---
title: "what are macros in gtk+"
date: 2010-10-12
forum: Programming Talk
---

### Post by c2tarun on 2010-10-12
hi friends
while going through gtk+ programming i m constantly getting this term 'macros'
i have absolutely no idea what it is.
can anyone please explain
detailed explanation will be appreciated.
thanx

---

### Post by lisati on 2010-10-12
A 'macro' is a bit like a shortcut or abbreviation that can help you reduce the amount of typing needed.

Although it's not specific to GTK+, you might want to have a look here: [http://en.wikipedia.org/wiki/Macro_%28computer_science%29](http://en.wikipedia.org/wiki/Macro_%28computer_science%29)

---

### Post by MadCow108 on 2010-10-12
it depends on the language your using. e.g. lisp macros are something completely different than C/C++ macros.

C/C++ macros are basically not much more than "search & replace" tags.
A so called preprocessor scans the source code and replaces each occurence of the macro with some defined text.
This preprocessed source is then passed to the actual compiler. (the processed source can be viewed with gcc's -E flag)

There are many uses. See [http://en.wikipedia.org/wiki/C_preprocessor](http://en.wikipedia.org/wiki/C_preprocessor)

Macros are used extensively in plain C gtk+ (or better gobject which gtk it is based on) to kind of "simulate" polymorphism and other stuff which "higher" level languages (like C++) provide in their base syntax and to provide high portability (see conditional compilation in above link).

(Side note: I do not recommend programming in C gtk+ if avoidable, bindings in other languages (gtkmm, pygtk etc) are considerably easier to handle)

---

### Post by c2tarun on 2010-10-12
> **MadCow108 said:**
> it depends on the language your using. e.g. lisp macros are something completely different than C/C++ macros.

C/C++ macros are basically not much more than "search & replace" tags.
A so called preprocessor scans the source code and replaces each occurence of the macro with some defined text.
This preprocessed source is then passed to the actual compiler. (the processed source can be viewed with gcc's -E flag)

There are many uses. See [http://en.wikipedia.org/wiki/C_preprocessor](http://en.wikipedia.org/wiki/C_preprocessor)

Macros are used extensively in plain C gtk+ (or better gobject which gtk it is based on) to kind of "simulate" polymorphism and other stuff which "higher" level languages (like C++) provide in their base syntax and to provide high portability (see conditional compilation in above link).

(Side note: I do not recommend programming in C gtk+ if avoidable, bindings in other languages (gtkmm, pygtk etc) are considerably easier to handle)



hi madcow
actually i am working on my final year project in which i m converting ubuntu english version to hindi.
i thought to start with gtk programming as gnome has no window manager and most of the applications use gtk+ for window display.
but absolutely i have no idea whether i m going in right direction or wrong direction.
if you have any better idea than please suggest me.
thanx

---

### Post by nvteighen on 2010-10-13
> **c2tarun said:**
> hi madcow
actually i am working on my final year project in which i m converting ubuntu english version to hindi.
i thought to start with gtk programming as gnome has no window manager and most of the applications use gtk+ for window display.
but absolutely i have no idea whether i m going in right direction or wrong direction.
if you have any better idea than please suggest me.
thanx

Definitely in the wrong direction: Translation isn't done that way because strings are taken from a file where the correct string is chosen for the current locale in active. Look here to see how it is done for Hindi: [https://translations.launchpad.net/ubuntu/maverick/+lang/hi](https://translations.launchpad.net/ubuntu/maverick/+lang/hi)

Now: GTK+ is a widget toolkit library and GNOME is a huge collection of applications ("desktop environment") that uses GTK+ as its official library (yes, they were initially created by the same people, but that's irrelevant). It has nothing to do with Window Manager, which in GNOME does exist (Metacity is the default one), whose function is to manage windows' positions.

---

### Post by c2tarun on 2010-10-15
> **nvteighen said:**
> Definitely in the wrong direction: Translation isn't done that way because strings are taken from a file where the correct string is chosen for the current locale in active. Look here to see how it is done for Hindi: [https://translations.launchpad.net/ubuntu/maverick/+lang/hi](https://translations.launchpad.net/ubuntu/maverick/+lang/hi)
 
Now: GTK+ is a widget toolkit library and GNOME is a huge collection of applications ("desktop environment") that uses GTK+ as its official library (yes, they were initially created by the same people, but that's irrelevant). It has nothing to do with Window Manager, which in GNOME does exist (Metacity is the default one), whose function is to manage windows' positions.
 
 
thanks for the direction. this will surely help me a lot.
can you please tell me anything about po and mo files.???
if possible give me the link of any book or any tutorial that explains everything about the working of po and mo files, like how to find them, edit them etc.
thanx a lot.

---

