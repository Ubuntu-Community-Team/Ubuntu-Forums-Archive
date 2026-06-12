---
title: "tkinter and python"
date: 2011-05-24
forum: Programming Talk
---

### Post by Bigmon on 2011-05-24
I wonder if anyone can help. I cannot understand why in the following code, the command "self.add_one" does not work with parenthesis. IE "self.add_one()":

```
    

def create_check_button(self):
        
        self.radio_button = BooleanVar()
        Checkbutton(self,
        text = "Check For Natalie",
        variable = self.radio_button,
        command = self.add_one
        ).pack()

    def add_one(self, total=0):
        self.total = total
        
        if self.radio_button.get():
            self.total+=1


```

---

### Post by simeon87 on 2011-05-24
When you do self.add_one() then you are already calling the function. In this case you just want to pass the function to the CheckButton so that *it* can call the function when someone clicks on the check button. You are passing the function but you are not calling it so you have to use self.add_one instead.

---

### Post by Bigmon on 2011-05-24
I see. Thanks.

---

