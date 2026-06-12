---
title: "wxpython - spinner widget can't SetFocus()"
date: 2014-05-28
forum: Programming Talk
---

### Post by eightbits2010 on 2014-05-28
I have a script that uses a spinner widget and it works as I would expect.
 In a button event I want to SetFocus for a spinner.  
             
 ```
            self.sc.SetValue(0)           # this works as expected 

            self.sc.SetFocus()            #I get the error message: “ NameError: name 'self' is not defined ”

``` 

 Both of the above instructions are in the same button event handler. I am thinking that the spinner
 widget doesn't have a SetFocus() method (?)

---

### Post by spjackson on 2014-05-29
I think that you would get "object had no attribute 'SetFocus'" if that was the problem. "'self' is not defined" sounds more a question of scope, i.e. the second line isn't in the same function as the first one. Possibly an indentation error? Can you post the whole method without losing indentation information?

---

### Post by eightbits2010 on 2014-05-29
I think it must have been tabs/space issue. I had started using SciTE editor and the default
indent was set to use tabs. I had started the script first using GEDIT and always used space instead of the tab key. I kind of like the SciTE editor as it behaves better than using Terminal mode or IDEL IDE when doing
multiple edits/run cycles. It took me awhile to get the file format straight out.:mad:

---

