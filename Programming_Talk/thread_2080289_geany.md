---
title: "geany"
date: 2012-11-03
forum: Programming Talk
---

### Post by conradin on 2012-11-03
Hi all, 
(I wasn't sure where to put this, but I'm sure many of you use geany)
I want to add a custom button to the geany toolbar. I am trying to use geany to compile and upload code to my arduino.

I would like to make that process a 1 click task, by using a custom button on the toolbar. I was thinking, if I can find the place where the existing buttons are, perhaps I could copy one, and make my own. But I haven't figured it out yet. I looked on the geany website, this option is currently on the wish list.

---

### Post by slavik on 2012-11-03
Since it's an open source project. There should be a link to where they host their code.

---

### Post by ssam on 2012-11-04
i think you can set a custom command for the compile and run buttons, would that be a solution?

---

### Post by conradin on 2012-11-05
> **ssam said:**
> i think you can set a custom command for the compile and run buttons, would that be a solution?

Yes, that would be a solution. After all, the concept of adding a bunch of custom buttons is neat, but all I really want to do is one command to compile and upload arduino code. 

So please, how do I do that?

I tried modifying the toolbar sourcecode, and it worked, I got a button in there, but I havent figured out how to change the functions of it.

---

### Post by lykeion on 2012-11-05
I'd recommend you to *first* compile it *then* upload it to arduino. What if compilation fails?

You can easily compile C and Python in Geany simply with F8 (correct me if I'm wrong here)

If you'd like to automate uploading to arduino, write a script and pass the compiled file as parameter

---

