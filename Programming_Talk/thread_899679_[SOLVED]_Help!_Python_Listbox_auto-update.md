---
title: "[SOLVED] Help! Python Listbox auto-update?"
date: 2008-08-24
forum: Programming Talk
---

### Post by aktiwers on 2008-08-24
Hi all,

I have yet another question regarding Python.

I have written this function:
[php]
def skriv():
    
    f = open(dokument, "r") # Reads text document
    linie = f.readlines() 

    count = len(linie) # Counts amount of lines in the doc
    print count
    
    
     # Loop that make prints the text from the document (simulating scrolling text)
    for x in range(0, count):    
        time.sleep(tid)
        return linie[x]
    skriv()
[/php]Now I have this Tkinter Listbox that I want to pass the loops output too, so I call the
function from the Listbox. 

But it only displays the first line? How can I make it run so that it updates inside the Listbox? 

Like if I replace the "return" statement with "print" in the loop, it works perfectly in terminal..  but not in the Listbox? :(

---

### Post by days_of_ruin on 2008-08-24
```

def skriv():
    
    f = open(dokument, "r") # Reads text document

    
    for line in f:    
        time.sleep(tid)
        yield line
```

To use this do:
```
for i in skriv():
    #do something with this line
```

---

### Post by meanburrito920 on 2008-08-24
I'm a bit confused why your original function is recursing itself.. perhaps you could shed some light on the reason?

---

### Post by aktiwers on 2008-08-25
> **meanburrito920 said:**
> I'm a bit confused why your original function is recursing itself.. perhaps you could shed some light on the reason?

I just got a new job, on a school, where they want to setup some screens around the building. They then want these screens to display info about what location each class need to be at.

Like in the airport or something. :)

Therefor I need the program to read the text from the text file, and that file is going to be big sometimes so it needs to be "auto-scrolling"(sorry I dont know any better word to describe it) to handle a lot of text and run in a endless loop so that it does not stop.

I am still confused about how to really do this in tkinter. Maybe Listbox is a bad choise?

---

### Post by days_of_ruin on 2008-08-25
> **aktiwers said:**
> I just got a new job, on a school, where they want to setup some screens around the building. They then want these screens to display info about what location each class need to be at.

Like in the airport or something. :)

Therefor I need the program to read the text from the text file, and that file is going to be big sometimes so it needs to be "auto-scrolling"(sorry I dont know any better word to describe it) to handle a lot of text and run in a endless loop so that it does not stop.

I am still confused about how to really do this in tkinter. Maybe Listbox is a bad choise?

You should use the Text widget.

---

### Post by aktiwers on 2008-08-25
Okay I changed it to Text.

[php]
startframe = Frame(root)
startframe.pack()

startT = Text(startframe, bg="white", font=("verdana", 20))
startT.insert(END, skriv())
startT.pack()
startT.update()
        [/php]Thanks a lot for your help. Can you give me any hint on how I make the skriv() function run?
Right now it only displays 1 line from the loop in skriv().

---

### Post by aktiwers on 2008-08-25
No one?

---

### Post by days_of_ruin on 2008-08-25
> **aktiwers said:**
> Okay I changed it to Text.

[php]
startframe = Frame(root)
startframe.pack()

startT = Text(startframe, bg="white", font=("verdana", 20))
for line in skriv():
    startT.insert(END, line)
    startT.pack()
    startT.update()
        [/php]Thanks a lot for your help. Can you give me any hint on how I make the skriv() function run?
Right now it only displays 1 line from the loop in skriv().

I edited the code above
I am not familiar with Tkinter so I am not sure if that will work.

---

### Post by meanburrito920 on 2008-08-25
have you tried days_of_ruin's code? I think that's your best bet at the moment.

Edit: sorry, I didn't realize that days_of_ruin had already posted again. But his solution should work assuming you used his function. The problem with your original function is that the return exits the function. However, if you want your function to keep recursing, I would suggest against recursing inside the function. Instead, put the function inside a 

while True:

loop.

---

### Post by aktiwers on 2008-08-26
Really thanks a lot guys! That did the trick! :)

---

### Post by days_of_ruin on 2008-08-26
> **aktiwers said:**
> Really thanks a lot guys! That did the trick! :)

Great!Be sure to mark this thread as solved then.

---

