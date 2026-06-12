---
title: "File/send/Opera"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by rosswmcgee on 2008-05-08
With fire fox you can send a web link with file/send/ evolution opens and off your msg goes. How do you do that with Opera?:)

---

### Post by mano cazalet on 2008-05-08
in Tools - Preferences - Advanced - Programs you have to add the client you want to use to send mails. By default it is set to opera, but you can change it, editing that option and adding the shortcut to evolution

---

### Post by olejorgen on 2008-05-08
[http://nontroppo.org/tools/buttonmaker/](http://nontroppo.org/tools/buttonmaker/)

Choose the external program button
Program to execute: evloution
Other options:<option required to start evolution displaying new mail with content ARG> %u

Make button -> drag to desired place

---

### Post by rosswmcgee on 2008-05-09
I see advanced, and add but do not know howe to go from there.

---

### Post by olejorgen on 2008-05-09
I think mano* miss-understood the question. You need to figure out how to get evolution to open with a compose window containing a specified text in the mail body

---

### Post by mano cazalet on 2008-05-09
Yes,

thats right.
Press Ctrl + F12 and go to programs.
There you must edit the option mailto or if you don't have this option add it.

It should be:
protocol: mailto
action: uncheck the open with opera and set to open with default application if evolution is your system wide default email client or set it to open with other application and select evolution in /usr/bin

---

### Post by rosswmcgee on 2008-05-09
Ok I did that. How then when I click on File at the top of the left hand page do I find the option to send?

---

### Post by olejorgen on 2008-05-09
[Send URL]("opera:/button/Send%20document%20address%20in%20mail,,,%22Send%20URL%22,Window%20Mail%20View%20Icon")

Drag this link to a toolbar. It will create a button. It is possible to create a menu entry in File too, but this is more work. See [http://operawiki.info/Opera](http://operawiki.info/Opera) for more info

---

### Post by rosswmcgee on 2008-05-11
When I do that I get a pop up msg saying default action does not support this protocol. I tried it both ways with the usr/bin and just with default application. 

Perhaps I should phrase the question, how to send an email link with opera. Lets say I see an article on the web I wish to send to some one how do I do it?

---

### Post by olejorgen on 2008-05-11
That is strange, when I set evolution as my email app, and click that button, I get the behavior you want

---

