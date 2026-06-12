---
title: "Python Twisted"
date: 2010-11-11
forum: Programming Talk
---

### Post by Sailor5 on 2010-11-11
Ahoy Sailors!

So I'm merging my Twisted driven application with a PyQt interface. I'm currently trying to send a variable when a button is clicked. But I can't figure it out. I'd need to be able to it some what like this.
```
def Button_Clicked(self):
        out ="s:"+self.lineEdit.text()
        out = str(out)
        self.sendLine(out)
```You could run this deferred under connectionMade passing it's self variable as an argument. But I don't want to send text just when someone has connected. I want to send it when a button is pressed.

Anyone know how?

Thanks Bye!

---

### Post by Sailor5 on 2010-11-18
My milkshakes don't bring any boys to the yard. Bump!

---

### Post by mo.reina on 2010-11-18
i suggest going over to the #twisted channel at freenode and asking them.  they're quite helpful.

---

