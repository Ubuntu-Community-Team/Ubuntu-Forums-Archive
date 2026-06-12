---
title: "[Python] Tk radiobutton odd behavior, all get selected"
date: 2012-01-13
forum: Programming Talk
---

### Post by Frozen Forest on 2012-01-13
There is something strange about the radiobuttons in this code, if I click on one of them do all three get selected, why? Using Python 3.2 if it might have any effect.

[PHP]class Gui:
    
    def __init__(self):
        self.frame = Frame(Tk())
        self.frame.pack()
        radio_type = ('A','B','C')
        radio_type_var = StringVar()
        radio_type_var.set("L")
        for i in range(0,len(radio_type)):
            c = Radiobutton(self.frame, text=radio_type[i], variable=radio_type_var)
            c.pack(anchor=W)
            c.grid(row = (i + 1), column = 0)
        self.frame.mainloop()

if __name__ == "__main__":
    Gui()[/PHP]

---

