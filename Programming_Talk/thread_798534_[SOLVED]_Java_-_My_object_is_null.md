---
title: "[SOLVED] Java - My object is null"
date: 2008-05-18
forum: Programming Talk
---

### Post by mike_g on 2008-05-18
I got a really annoying problem and I cant figure out whats causing it. I have quite a lot of code so I'll try and post just the relevant parts. 

In my main class I have an object thats basically a hashmap to store codes. The object is setup and codes loaded at the start of my constructor:
```
        CodesList codes = new CodesList();
        codes.load();
```
I have a class thats basically a window to view the codes in. I added an item to the dropdown menu that creates a new codeview window:
```
        discountCodes.addActionListener(new ActionListener()
        {
            public void actionPerformed(ActionEvent e)
            {
                new DiscountCodesWindow(codes);
            }
        });  
```
It passes the codes list to the new object. In the new object constructor though it seems to be null. IE this:
```
    public DiscountCodesWindow(CodesList l) 
    {
        list = l;
        System.out.println(list);
    }
```
Prints 'null', when if I do the same thing in the calling class theres no problem with the list; it prints out the content. Does anyone know whats could be causing the problem with passing the object here? I'm doing more or less the same thing with other classes and I have had no problem with it o_O

---

### Post by mike_g on 2008-05-18
Ok, I figured out what it was. I had declared the object as a local variable within my constructor. Man I'm dumb :( lol

---

