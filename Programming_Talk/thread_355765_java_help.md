---
title: "java help"
date: 2007-02-07
forum: Programming Talk
---

### Post by sailingboarder on 2007-02-07
in netbeans, i am making a gui with many text fields, and would like to store the values in a list
for simplicity, i will name the text fields text0, text1, text2, and so on and these would correlate to list value text[0], text[1], text[2], etc.
is it possible to write a simple loop that will do store the value of text*i* in text[*i*] 
```
text[*i*] = text*i*.getText()
```instead of typing out every value separately
```
text[0] = text0.getText()
text[1] = text1.getText()
text[2] = text2.getText()
```

i am just looking for a way to save alot, and i mean alot, of typing

---

### Post by Nikron on 2007-02-07
You could always put the fields in a list(ArrayList, LinkedList)

Or if they are in the same GUI container, you could use that as the list.

ie
```

for(i = 0; i <text.length; i++)
   text[i] = list.get(i).getText();

```

---

### Post by Ragazzo on 2007-02-07
Can you put the textfields in an array? Then you could use a loop text[i] = textField[i].getText();

---

### Post by Nikron on 2007-02-07
> **Ragazzo said:**
> Can you put the textfields in an array? Then you could use a loop text[i] = textField[i].getText();

You could do that too..

---

### Post by Tomosaur on 2007-02-07
> **sailingboarder said:**
> in netbeans, i am making a gui with many text fields, and would like to store the values in a list
for simplicity, i will name the text fields text0, text1, text2, and so on and these would correlate to list value text[0], text[1], text[2], etc.
is it possible to write a simple loop that will do store the value of text*i* in text[*i*] 
```
text[*i*] = text*i*.getText()
```instead of typing out every value separately
```
text[0] = text0.getText()
text[1] = text1.getText()
text[2] = text2.getText()
```

i am just looking for a way to save alot, and i mean alot, of typing

You can't do that kind of thing with variable names. Most you could hope for would be to put the variations of text*n* in a List or an Array.

Oh, you can increment i when you're specifying an array slot, but in your case, your text areas would also need to be in an array, so your code would look like this:
```

TextArea[] text_areas = new TextArea[15];
//blah blah blah
String[] user_input = new String[text_areas.length];
for(int i = 0; i < text_areas.length; i++){
  user_input[i] = text_areas[i].getText();
}
```

That will do what you want.

---

### Post by sailingboarder on 2007-02-07
same as next post

---

### Post by sailingboarder on 2007-02-07
but to add all of the text fields to the array, would i have to type that manually?

is there a way in netbeans to add all of the fields to an array automatically?

---

### Post by Nikron on 2007-02-07
> **sailingboarder said:**
> but to add all of the text fields to the array, would i have to type that manually?

is there a way in netbeans to add all of the fields to an array automatically?

How man text fields do you have?

I mean if your really lazy you can just do..
```

TextField fields[] = new TextField[x];
for(i = 0; i < x; i++)
   fields[i] = new JTextField();

```

unless you already have them seperately named as instances variables...

---

### Post by sailingboarder on 2007-02-07
i'm looking at about 120 or so text fields, so i'm not just being lazy

i probably will eventually(as in 2morrow) just type everything out and make it simpler(though longer)

i was just looking for a quick alternative, but now it seems like it would just b easier to type everything in by hand, since i already have them laid out in the design window of netbeans

---

### Post by phossal on 2007-02-08
This sounds like a design error. A GUI with 120 text fields sounds either like a very long form, better implemented via the web using something simple like PHP, or DB data best displayed using a table. 

What are you working on?

---

### Post by Nikron on 2007-02-08
I have to agree, I can't even imagine anything that could vaguely require 120 fields on the same window.

---

### Post by sailingboarder on 2007-02-11
it was for a school  project, and i needed a quick fix, but that has passed, and now i am working on a better designed system, where i will ask all the information over several forms instead of just one

the project is a latin study guide, and this particular problem is about adding vocabulary to the database, each verb has about 120 different forms
so the massive form was just a quick fix before one deadline, and now i'm going back and redoing the entire module

thanks for all the help

---

