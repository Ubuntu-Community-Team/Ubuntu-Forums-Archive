---
title: "Qt push buttons still receiving while &quot;inactive&quot;"
date: 2008-10-13
forum: Programming Talk
---

### Post by Mariane on 2008-10-13
Hi, 

I am trying qt4 for the first time, I have a little 
experience with qt3. 

I want some buttons to be temporarily disabled while 
a system call is running. I used:

pushButton->setEnabled(FALSE);

This works as far as the interface looks are concerned, 
the button becomes greyed out for the correct duration. 

But the interface "remembers" which buttons have been 
clicked during their greyed out period. It just waits 
until the buttons are active again and processes the 
click through:  

connect(pushButton, SIGNAL(clicked()), this, SLOT(remember1())); 

In the remember1 slot I have the first line of code which 
is trying to prevent this behaviour. "enableButtons" 
is a boolean variable which is FALSE when the buttons 
are disabled and TRUE when they are enabled: 

void myQtQpp::remember1() {
if (enableButtons == FALSE) return;
... stuff ...
}

But as the interface waits, when it actually processes 
the click, enableButtons has become TRUE again. 

I would like all clicks on disabled buttons to be ignored, 
not just postponed. 

I am going to try to use a timer to hold back the change 
of enableButtons from FALSE to TRUE, so hopefully 
the interface will send the click while enableButtons 
is still FALSE and remember1 will return. But this is 
a rather messy solution. 

If anyone knows how to make a qt4 button really disabled, 
please tell me. 

Mariane

---

