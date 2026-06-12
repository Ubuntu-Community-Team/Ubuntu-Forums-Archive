---
title: "My Program for UBUNTU - ScreenFace-1.0"
date: 2007-07-10
forum: Programming Talk
---

### Post by xavier_r on 2007-07-10
If you love command line and curses based applications you would like this...
If you dont like command line be sure to give this a try, it will present to you some powerful command line applications that you may require for everyday tasks, such as music, email, chatting, browsing etc.

Very easy to install, very small file only about 10KB, but i guess it also makes using command line easier...
It gives an easy interface to launch apps and manage menu...
Plus it also gives you a process manager...

So install and try it out...
Tell me how it makes you feel about doing the command line

For best effects ;)
open
$ vi ~/.bashrc
and add ScreenFace to the end

ScreenFace is S-capital and F-Capital...
and is derived from
Screen from** GNU Screen**
Face from** Interface**

I hope you will ike the software as much as I did :)
Please give your feedback...

---

### Post by Note360 on 2007-07-10
It was interesting, but part of using the command line is to use the shell and customize that to your specifications. I mean it could be useful, but I still find just basic alias's and stuff to be more useful. Something like this should be customized (eg selecting the shell (S) drops you into, Also why are the Menu Items and the Commands to run that commands in seperate files. It should probably be in a simular format to.

.app_list
```

Web-Browser | firefox
Instant Messenger | pidgin

```

Then use something simple like split to split those lists apart and then strip the whitespace before and after. This would be to make sure that the 2 files dont get mixed up and mismatched commands cannot happen.

---

### Post by xavier_r on 2007-07-10
> **Note360 said:**
> It was interesting, but part of using the command line is to use the shell and customize that to your specifications. 
Remember **["A Day without X"]("http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/")**
Wanna make the command line a working place, rather than using custom commands...
init 3, no GUI ;)

> 
 Also why are the Menu Items and the Commands to run that commands in seperate files. It should probably be in a simular format to. Then use something simple like split to split those lists apart and then strip the whitespace before and after. 


I get that...
But its easier to read into array from files in PHP...
And i used two arrays...
And i have plans for making mutiple apps, in one menu item... 
At that time i will need one file menu.list maybe...
At this moment I just wanted to keep it simple... program optimization comes later... :)


> This would be to make sure that the 2 files dont get mixed up and mismatched commands cannot happen.
They wont happen... I have that in mind... rest assured...

Did u notice one major bug by the way...
That time display is event driven... :lolflag:

I thought i had to respond to that...

---

### Post by Note360 on 2007-07-10
Wow I didn't notice that... I feel ashamed.

Good work though I like it all around, but it wont be replacing my zsh shell just yet. Maybe one day. Some bugs. I might test it out a bit more later on. 

(also for the | lists you would read the array use a for loop and then split it then you would have embedded arrays inside the primary array).

---

### Post by xavier_r on 2007-07-12
Did anyone else try it out? :)

---

