---
title: "[SOLVED] matlab text in graph"
date: 2008-04-17
forum: Programming Talk
---

### Post by Claus7 on 2008-04-17
Hello,

I want to insert text in a graph(plot) in matlab via commands. From my search I have found out that I can do it either via *legend* or *text* command.
With the first one I cannot avoid the small preview of the line in the graph and with the other I have to specify the coordinates in which the text will be located.

Could I add text and _only_ text without having to specify anything else?
And also, if it has to do with legend command, this text not to be surrounded by any box.

Regards!

---

### Post by WW on 2008-04-17
If you don't specify the coordinates of the text, how does matlab know where to put it?

I guess you want something like the "automatic placement" that the legend function has, but for just a piece of text, and not an actual legend.  I don' t think there is such a function.

This function
```

function h = textul(txt)
    a = axis;
    wdth = a(2)-a(1);
    ht = a(4)-a(3);
    pos = [a(1)+0.05*wdth a(4)-0.05*ht];
    h = text(pos(1),pos(2),txt);
end

```
will put text near the upper left corner (down 5% of the height, and over 5% of the width).  You could experiment with something like that.

---

### Post by aJayRoo on 2008-04-17
Try the 'gtext' function. You pass it a string and then click where you want it to be placed in the figure, simple as that! Type:
```
help gtext
```
at the Matlab prompt for full usage information. Hope that helps.

---

### Post by Claus7 on 2008-04-18
Hello,

thank you aJayRoo. As a matter of fact I found out about gtext moments I posted this thread, yet if you have to do more than 20 diagrams or so, and not only that but also many other things, this is a little bit time consuming, yet it works.
Just for the information of anyone who is interested the command should be like that :
```
gtext('string'), where in string we type what we want (' ' are needed)
```

WW:thank you for your response. This was exactly what I was looking for. And nice place where it displays the message! Just for everyone's information I copied the code to a file which I named **textul.m** .Then in my script (of matlab commands), I typed, before the plot command,** textul('string') **and I saw the string on the left up corner of my graph.

Regards!

---

