---
title: "tkinter and python - return value from a method"
date: 2011-05-25
forum: Programming Talk
---

### Post by Bigmon on 2011-05-25
I wonder if someone can help. Iam using Tkinter and in my program, when a checkbutton is ticked it adds 1 to a score, and when it is unchecked, 1 is taken off. This seems to work, as I can see the total change as I check and uncheck. However, I cannot seem to return this value out of the method to use it elsewhere.```


    def create_check_button(self):
        
        self.radio_button = BooleanVar()
        Checkbutton(self,
        text = "Check For Natalie",
        variable = self.radio_button,
        command = self.add_one
        ).pack()

        self.radio_button1 = BooleanVar()
        Checkbutton(self,
        text = "Check For Graham",
        variable = self.radio_button1,
        command = self.add_one
        ).pack(side="bottom")

        self.radio_button2 = BooleanVar()
        Checkbutton(self,
        text = "Check For Cash Spend",
        variable = self.radio_button2,
        command = self.add_one
        ).pack()

        self.radio_button3 = BooleanVar()
        Checkbutton(self,
        text = "Check For Bank Statement",
        variable = self.radio_button3,
        command = self.add_one
        ).pack()



        self.radio_button4 = BooleanVar()
        Checkbutton(self,
        text = "Check For Credit Card",
        variable = self.radio_button4,
        command = self.add_one
        ).pack(side="bottom")

        

    def add_one(self, total=0):
        """this function is passed to Checkbutton
above - hence no () above. Everytime a checkbutton is
true one is added to the score. One is taken off with unchecking.
If the total is zero then a warning box will come up"""
        
        self.total = total
        
        if self.radio_button.get():
            self.total+=1
        if self.radio_button1.get():
            self.total+=1
        if self.radio_button2.get():
            self.total+=1
        if self.radio_button3.get():
            self.total+=1
        if self.radio_button4.get():
            self.total+=1
        check_button_total = self.total
        print(check_button_total)
        return check_button_total


```

I tried putting total as a global value but when I unchecked the box ,the value did not go down.
Can any experienced programmers help ?

---

### Post by simeon87 on 2011-05-25
The value is not going down because you are never subtracting anything from self.total. In your code, the value can only go up.

If you want to do it like that, you should recompute the value of total each time add_one runs, based on the current state of all the check buttons. So for example:

```
total = 0
if self.radio_button.get():
    total += 1
if self.radio_button1.get():
    total += 1
if self.radio_button2.get():
    total += 1
if self.radio_button3.get():
    total += 1
if self.radio_button4.get():
    total += 1
self.total = total
print total
```

You can then use self.total elsewhere in your code.

---

### Post by Bigmon on 2011-05-25
Ah, yes I see. Thank you very much.
:KS

---

