---
title: "multiple sub classes in python"
date: 2013-06-03
forum: Programming Talk
---

### Post by jamesbon on 2013-06-03
I am learning python and in the example in book talks about multiple superclasses  following is the example in book


```


[COLOR=#00008B]class[/COLOR] [COLOR=#2B91AF]Calculator[/COLOR]:
[COLOR=#00008B]      def[/COLOR] calculate(self,evaluate): 
            self.value=eval(expression)
[COLOR=#00008B]class[/COLOR] [COLOR=#2B91AF]Talker[/COLOR]:    [COLOR=#00008B]def[/COLOR] talk(self): 
[COLOR=#00008B]       print[/COLOR] [COLOR=#800000]'Hi, my value is '[/COLOR], self.value
[COLOR=#00008B]
class[/COLOR] [COLOR=#2B91AF]TalkingCalculator[/COLOR]([COLOR=#2B91AF]Calculator[/COLOR],[COLOR=#2B91AF]Talker[/COLOR]): 
[COLOR=#00008B]      pass
[/COLOR]
```[COLOR=#00008B]
  [/COLOR]But when I type it in terminal 

```

>>> [COLOR=#00008B]class[/COLOR] [COLOR=#2B91AF]Calculator[/COLOR](object):
                [COLOR=#00008B]def[/COLOR] calculate(self,evaluate):
                      self.value=eval(expression)
>>> [COLOR=#00008B]class[/COLOR] [COLOR=#2B91AF]Talker[/COLOR](object): 
[COLOR=#00008B]             def[/COLOR] talk(self): 
[COLOR=#00008B]                   print[/COLOR] [COLOR=#800000]'Hi, my value is '[/COLOR], self.value
>>> [COLOR=#00008B]class[/COLOR] [COLOR=#2B91AF]TalkingCalculator[/COLOR]([COLOR=#2B91AF]Calculator[/COLOR], [COLOR=#2B91AF]Talker[/COLOR]):
             [COLOR=#00008B]pass
[/COLOR]
```
I get following error
```

>>> TalkingCalcultor.__bases__
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'TalkingCalcultor' is not defined

```


[COLOR=#00008B]Also the original formatting of my post is lost....how do I get it back here Ubuntu forums have seem to changed a lot...[/COLOR]

---

### Post by r-senior on 2013-06-03
You'll kick yourself ... you missed an 'a'.

---

