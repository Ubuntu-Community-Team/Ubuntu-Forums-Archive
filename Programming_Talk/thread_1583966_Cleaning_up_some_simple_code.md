---
title: "Cleaning up some simple code"
date: 2010-09-28
forum: Programming Talk
---

### Post by lazypeterson on 2010-09-28
Alright, basically I have an array Guys that I need to pass on a bunch of arguments to. I feel like there's a cleaner way of doing this, perhaps with an array: 

```
            Guys[0].Cash = 50; // Set up each guy's initial cash amount
            Guys[1].Cash = 75;
            Guys[2].Cash = 45;
            Guys[0].MyRadioButton = radioButton1; // Correlate the radio buttons in the guy array
            Guys[1].MyRadioButton = radioButton2;
            Guys[2].MyRadioButton = radioButton3;
            Guys[0].MyLabel = label5; // Labels on the form
            Guys[1].MyLabel = label6;
            Guys[2].MyLabel = label7;
            Guys[0].Name = "Joe"; // Guys' names
            Guys[1].Name = "Bob";
            Guys[2].Name = "Al";
```

I'm just not sure exactly how. Or is this pretty much the best/only way to do this?

Thanks

---

### Post by schauerlich on 2010-09-28
I'm assuming this is C++? It's probably easiest to put Cash, MyRadioButton, MyLabel and Name into a constructor, and push the Guy objects into a std::vector.

```
std::vector<Guy> guys;
guys.push_back(Guy(50, radiobutton1, label5, "Joe"));
// etc

```

---

### Post by nvteighen on 2010-09-28
> **schauerlich said:**
> I'm assuming this is C++? It's probably easiest to put Cash, MyRadioButton, MyLabel and Name into a constructor, and push the Guy objects into a std::vector.

It could be any of these: C (yeah, each "Guy" could be a struct), C++, Java, Javascript :P

This is a nice example of how syntax is not everything there's in a language... ;)

EDIT: After thinking a bit more, as this could be valid C (hm... maybe with some extension to accept BCPL-style comments), this also could be valid Objective-C...

---

### Post by lazypeterson on 2010-09-28
Oh I'm sorry... this is C#.

---

### Post by schauerlich on 2010-09-28
> **lazypeterson said:**
> Oh I'm sorry... this is C#.

Well, I'm not familiar with C#, but I'm sure there's some standard container that you could use to hold the objects (maybe called an array, list, vector, collection, etc).

---

### Post by unknownPoster on 2010-09-28
> **schauerlich said:**
> Well, I'm not familiar with C#, but I'm sure there's some standard container that you could use to hold the objects (maybe called an array, list, vector, collection, etc).

ArrayList

:)

---

