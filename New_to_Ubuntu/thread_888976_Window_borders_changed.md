---
title: "Window borders changed"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by aldobenart on 2008-08-13
Hi to all.
I installed ubuntu 8.04 from scratch. All worked fine, but at some moment, the aspect of all windows changed. On the top border of the window I can't see the usual symbol to close, minimize, iconize the window. I can see only an icon postioned abaout 1/4 of the total window size from the left border. If I click on the icon, a menu opens, where I can select to close, minimize, maximaze the window and so on.
Any idea to return to the usual aspect of windows?

Thanks in advance.

---

### Post by billgoldberg on 2008-08-13
Go to "system -> preferences -> appearance".

Click "customize" and in the "window borders" tab select the one you want.

---

### Post by Methuselah on 2008-08-13
To add to what billgoldberg said, the default border is called 'Human'

---

### Post by aldobenart on 2008-08-13
Whichever theme I select and wichever border I select, the aspect of the windows remains unchanged. The human theme and the human theme arec already selected Have I to do something after selecting theme / border. The only button available is "close".

---

### Post by suprfish on 2008-08-13
> **aldobenart said:**
> Whichever theme I select and wichever border I select, the aspect of the windows remains unchanged. The human theme and the human theme arec already selected Have I to do something after selecting theme / border. The only button available is "close".

Try other borders; they should update once you click them. Do you have desktop-effects enabled?

---

### Post by Fixman on 2008-08-13
> **aldobenart said:**
> Whichever theme I select and wichever border I select, the aspect of the windows remains unchanged. The human theme and the human theme arec already selected Have I to do something after selecting theme / border. The only button available is "close".

Press alt+f2, write "metacity --replace" (eithout the quotes) and press enter. Then press it again but write "compiz".

---

### Post by aldobenart on 2008-08-13
Here you can see the aspect of my windows.

[IMG]file:///home/alessia/Scrivania/Schermata.png[/IMG]

---

### Post by SunnyRabbiera on 2008-08-13
> **aldobenart said:**
> Here you can see the aspect of my windows.

[IMG]file:///home/alessia/Scrivania/Schermata.png[/IMG]

you cant load it that way, use a site like imageshack or something.

---

### Post by aldobenart on 2008-08-13
Really, I tried to enable desktop effects, but I got an error message telling me that enabling desktop effects was impossible. I couldn't understand when to put alt+f2

---

### Post by aldobenart on 2008-08-13
Ok. Look at 
[http://www.flickr.com/photos/22045109@N03/?saved=1](http://www.flickr.com/photos/22045109@N03/?saved=1)

---

### Post by suprfish on 2008-08-13
Have you tried logging out/in?

---

### Post by aldobenart on 2008-08-13
Of course. I rebooted also

---

### Post by Methuselah on 2008-08-13
The color scheme and the GTK widget/button shapes don't look like Human.
You're saying the appearance doesn't change even when you change the whole theme?

---

### Post by aldobenart on 2008-08-13
Exact, the aspect remains the same, whichever selection I can do. Moreover, I can't see a theme where the three buttons on the top right corner aren't present.

---

### Post by Methuselah on 2008-08-13
What triggered this?
Is there any cause that you could guess?
Did you do something just before noticing the change to the window borders?

---

### Post by aldobenart on 2008-08-13
I dont'know these answers, otherwise, maybe, I colud recover my situation. However, I remember that at some moment I tried to enable desktop effects, even if this operation failed and, at present, I have no graphic effect enabled.

---

### Post by appi2012 on 2008-08-13
Type this in the terminal:
```
sudo apt-get purge gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gtk2-engines-ubuntulooks
```
```
sudo apt-get install gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gtk2-engines-ubuntulooks
```

That will reinstall the gtk engines. It might work.

---

### Post by aldobenart on 2008-08-13
Didn't work! I'm afraid to have to reinstall from scratch!

---

