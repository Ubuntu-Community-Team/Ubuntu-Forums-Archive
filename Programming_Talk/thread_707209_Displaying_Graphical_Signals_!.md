---
title: "Displaying Graphical Signals !"
date: 2008-02-25
forum: Programming Talk
---

### Post by KrishM on 2008-02-25
Hello! Everybody,
         I am new to Eclipse, & i am planning to use GNOME, SWT with GTK for displaying signals that are computed. 
 
 Can anyone please help me in giving proper direction to start my work? Is there any library which i can use to get the desired.

Thanks in Advance.

"I am glad to join the forum as there are many good helpful topics given."

---

### Post by Zugzwang on 2008-02-25
Could you please elaborate on "signals"? There are a couple of definitions around for that and we can't guess what you actually mean. When talking about signals here, what it usually meant is described [here]("http://en.wikipedia.org/wiki/Signal_%28computing%29"), but this is probably not what you mean.

Is it possible that you want to make some oscilloscope like program?

---

### Post by KrishM on 2008-02-25
Hello! Zugzwang,
       Thanks for taking time & rreplying. By signals i meant signals like Sinusoidal signals or square wave signals or Ramp signals, in general there will be points on X-Y Co-ordinate axes & then just join them to get the proper signal!!!!

       I hope this helps in clarifying my point.-----> Thanks again.

---

### Post by Zugzwang on 2008-02-25
Hi there.

Reading some tutorials for GUI making in your setting should be enough to get this task done. You will need to have some "custom drawing canvas" for actually drawing your lines which should in fact be pretty simple. I only know SWING so I can't give you any details, but SWT should have something similar.

You might also want to consider getting around all this GUI stuff and instead exporting a text file which is then processed by gnuplot for visualization. Shouldn't be too hard either if you have some general programming skills.

---

### Post by KrishM on 2008-02-25
Hello! Zugzwang, 
          Can you please let me know from where can i get to read about all inbuilt classes, its properties, its signals, its functions used in Eclipse. Also from where can i get detailed discription of SWT Widgets, its properties n all. Like i tried to See help in Eclipse but of no use. Also about SWT, GTK n all????

I tired to develope a hello world example in Eclipse with importing SWT for its widgets, i understood many of the things but few i didn't like " display.dispose() ", "display.readAndDispatch()" n all???? So please let me know any book or proper documentation wherein i can start it properly.

Thanks in Advance.

---

### Post by Zugzwang on 2008-02-25
For documentation & tutorials, Google is your friend. For example there's a tutorial at [http://www.cs.umanitoba.ca/~eclipse/]("http://www.cs.umanitoba.ca/~eclipse/"). It shouldn't be too hard to find the official page of SWT with the documentation. Since I don't know SWT, you've got to find that yourself.

The help files of IDEs usually only cover the IDE itself and not the libraries you can use (except you install extra help files provided that they are actually existing).

---

