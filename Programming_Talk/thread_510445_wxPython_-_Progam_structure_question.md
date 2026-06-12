---
title: "wxPython - Progam structure question"
date: 2007-07-26
forum: Programming Talk
---

### Post by ironfistchamp on 2007-07-26
Hey all,

Just started using wxPython and I love it. wxGlade is damn useful. Anyway, all the stuff I have seen has just one class for the main frame. I am writing some test programs and wondered how I might link events to functions in other classes and other modules. Could anyone give me any hints, perhaps using the example below.



```


#snip
wx.EVT_BUTTON(self,ID_THIS_BTN, <the function name?>)
#snip some more


```

```


def this_func(<frame reference?>, a_var):
    
    frame_ref.text_box.WriteText("HELLO WORLD")


```

That is a rough example and some main bits are missing as I don't exactly know what to put there. Any help would be great.

Thanks

Ironfistchamp

---

### Post by dwblas on 2007-07-30
To link to another file, you would import it
import another_file            ## don't include the '.py'
For a class in that file
SC = another_file.SomeClass( init_params )
To call a function within that class
SC.function_name( function_params )
You may want to try one of the many tutorials on the web as that is the best way to learn about importing.

---

### Post by ironfistchamp on 2007-07-30
Thanks for the reply. I understand how to import and use functions from other classes and that, I was just talking in terms of wxPython. I couldn't get it to work correctly and was wondering about the syntax for calling external functions from events. 

If anyone can give me some specific info on this or point me at a tutorial that would be great.


Thanks again

Ironfistchamp

---

### Post by dwblas on 2007-07-30
Look at this link at the top of the programming forum.  If that isn't enough then a Google for "python tutorial" will return more.
[http://ubuntuforums.org/showthread.php?t=333867](http://ubuntuforums.org/showthread.php?t=333867)

---

