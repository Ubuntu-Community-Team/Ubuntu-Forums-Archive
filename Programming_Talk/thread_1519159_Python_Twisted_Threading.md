---
title: "Python Twisted: Threading"
date: 2010-06-27
forum: Programming Talk
---

### Post by Chamillionaire2 on 2010-06-27
Ahoy Sailor!

So, I'm finally getting to grips with Twisted and Python, And after a month or so, We're finally reaching the end of my first project (Would have been faster if I'd done more work on it each day) However I've once again hit a snag.

Here's an example of what's going wrong.
```
class Echo(LineReceiver):
  def menu():
   while 1:
    choice = buttonbox(msg='',choices=('one','two'),root=None)
    if (choice=='one'):
            print "You clicked button one!"
    else:
            print "You clicked button two!"
    self.sendLine(choice)

menuf = Thread(target=menu)
menuf.start()
```

Now this works when the class bit isn't there, However I need to be able to send lines in that specific definition, So I need to be able to .start() the def, Whilst it being under the lineReceiver class.

Thanks Bye!

---

