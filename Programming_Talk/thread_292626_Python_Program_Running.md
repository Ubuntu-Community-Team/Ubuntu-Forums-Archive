---
title: "Python Program Running"
date: 2006-11-04
forum: Programming Talk
---

### Post by Andrew1234 on 2006-11-04
I have a python script that I would like to run on Ubuntu, I have the script running but get the terminal window opening in the background, if I make it a executing file in permissions, I get this window appear:-

Do you want to run "EasyPopulate.pyw", or display its contents?

But the terminal window does not open.

Is there a way of running the program so the program just opens? without any other window appearing?

---

### Post by pachjo on 2006-11-04
do you have a line similar to this at the top of your script?

#!/usr/bin/env python

---

### Post by tseliot on 2006-11-04
type:
```
python EasyPopulate.pyw
```

---

### Post by Andrew1234 on 2006-11-04
Many thanks for the replies, 

I have this at the top of the script
> #!/usr/bin/env python

and it will run in the terminal, but I would like it to run just by double clicking on an Icon. When I set the permissions, it opens OK but the Terminal window opens in the back ground,

---

### Post by junglepeanut on 2006-11-04
Hmm, I think I understand what you are saying.

You have a script which you have chmod to executable, but when it runs it pops open a terminal. Similar to when you create a launcher and choose execute in terminal?

Then maybe there is a way to change this so it doesn't execute from the terminal. I am not sure what permissions you are giving exactly, but I can say that mine if I double click on the icon just execute with out the terminal popping open.

So check that you have given enough permissions. 

I don't think this could be the culprit, as I changed my code and it made no difference.

But I typically use

/usr/bin/python

as when I run top it then list the application as the Applications name where as 

/usr/bin/env python

runs as python in top, so I like to be able to distinguish them easily.

I ran a test script under both environments and could not replicate your issue though.

---

