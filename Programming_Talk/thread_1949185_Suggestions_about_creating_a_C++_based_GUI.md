---
title: "Suggestions about creating a C++ based GUI"
date: 2012-03-29
forum: Programming Talk
---

### Post by Michael-Siu on 2012-03-29
Hello everyone I would like to hear some suggestions about a text editor I am developing in C++ for a project at school.

First of all it's a console application using the graphics.h library available on the Borland's compiler.

I am supposed to create my own GUI creating object like textboxes, buttons, labels, windows, etc.

But I have some concerns while creating an object which I called richtextbox. This object is supposed to hold the text written by the user. My concerns are if in my class richtextbox i should add a pointer to a list of chars written by the user and having all the text in memory before saving it to a .rtf file or should I write into a temporary file everything the user inputs, and then rewrite from the temporary file into the end file.

Remember that the user has to be able to use backspace and go forward and backward in the text.

I've already created all the other object but I'm still working out the richtextbox. Honestly i wouldn't like to have everything on my memory but in some cases it's essential like when i have to justify the text or use the backspace to erase the text.

Those are my concern so what do you guys think would be better to make my application lighter and useful.

---

### Post by muteXe on 2012-03-30
cant you just save them locally in a class, and then when you come to save to file, read these variables out? You dont have to track in real-time that the user adds or deletes characters to a textbox do you?

---

### Post by nvteighen on 2012-03-30
Hm... I see a couple of problems here.

The Borland Graphics Interface (BGI) is a (S)VGA graphic library meant for DOS, not really a GUI library like you seem to want (e.g. a window in Windows, GNOME, KDE, etc.). BGI is much closer to SDL (in concept... I really doubt BGI is nearly as good in quality as SDL) than anything else.

This is important because RTF requires you to have some way to render fonts correctly. You should check how BGI handles fonts and whether it is possible to show truetype/opentype fonts in a more-or-less decent way that resembles what you'd see in some word processor or somewhere else.

---

### Post by Michael-Siu on 2012-03-30
Yes, nvteighen the Borland's graphics library is meant for DOS and similar to SDL, but not as powerful, and what I am trying to do is simulate in a very primitive way a GUI creating the classes for the objects I mentioned before. 

I said an .rtf file because the text file is not going to be just plain text but have format, that's why I didn't say a .txt file.

It doesn't necessarily has to be a standard .rtf file, I will create my own identifiers inside the text to determine the font, size and color. Thus only my application is going to be able to read the file in the proper way.

Perhaps not many people use the Borland compiler, I personally hate it I prefer g++ for my console applications but unfortunately I'm forced to use it.

And muteXe yes I am supposed to track in real-time what the user inputs because the textbox is not a real textbox is just a squared image printed into the screen, I am supposed to make it act like a textbox. 

My question is, am I going to run out of memory if I insert into a stack every key the user presses.

---

