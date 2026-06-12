---
title: "User Input Keys To Get Value From Dictionary in wxPython"
date: 2011-05-19
forum: Programming Talk
---

### Post by steveone on 2011-05-19
Hello all. I am attempting to create a GUI dictionary application in wxPython that allows the user to enter a word in a text box and the meaning is returned to them. How would I tell my dictionary to use the text box text as the key for the value? So far I figured I can get the the entered text via:

```

def defClick(self,event):
      label = event.GetEventObject().GetLabel()
      if label == "Define":
          try:
              k = self.input.GetValue()

```but how do I associate the key to the dictionary and then tell the dictionary to output the value to a specific location? Any help is appreciated. Thanks in advance.

---

### Post by simeon87 on 2011-05-19
Is the dictionary a Python dict data structing (e.g., {"word": "meaning", "word 2": "other meaning"} or is it a separate data structure? In any case, let's say that you have a function lookup:

```
def lookup(word):
    # code here that returns the meaning of the word
```

Then you can do:

- Get text from user input
- Call lookup(word) to get the meaning
- Set text to the right widget in the GUI.

I'm not familiar with the specifics of wx but that's the general idea.

---

### Post by steveone on 2011-05-19
> **simeon87 said:**
> Is the dictionary a Python dict data structing (e.g., {"word": "meaning", "word 2": "other meaning"} or is it a separate data structure? In any case, let's say that you have a function lookup:

```
def lookup(word):
    # code here that returns the meaning of the word
```Then you can do:

- Get text from user input
- Call lookup(word) to get the meaning
- Set text to the right widget in the GUI.

I'm not familiar with the specifics of wx but that's the general idea.

Yes, it is a python dictionary structure. That's exactly what I would like to do. So I would Bind the button click to the lookup function then output to static text widget for example. Is (word) an actual parameter that can be used? 
Also where should I put the dictionary. BTW if anyone has Skype it makes it faster to understand if you can see what I am attempting.

---

### Post by simeon87 on 2011-05-19
> **steveone said:**
> Yes, it is a python dictionary structure. That's exactly what I would like to do. So I would Bind the button click to the lookup function then output to static text widget for example. Is (word) an actual parameter that can be used? 
Also where should I put the dictionary. BTW if anyone has Skype it makes it faster to understand if you can see what I am attempting.

You could do something like:

```
the_dict = {"word": "meaning"}
```

and then you can get the meaning by doing ```
meaning = the_dict[text]
``` in the function of the button, where text is the user text. Then you have to look in the wxPython documentation to see how you can set a text to a widget. It's probably something like ```
widget.set_text(meaning)
```.

---

### Post by steveone on 2011-05-19
Thanks simeon87. I'll play around with this and see what I can get going with it.

---

