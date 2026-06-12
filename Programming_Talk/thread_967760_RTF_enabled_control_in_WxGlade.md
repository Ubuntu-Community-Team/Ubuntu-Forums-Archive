---
title: "RTF enabled control in WxGlade"
date: 2008-11-02
forum: Programming Talk
---

### Post by MaxVK on 2008-11-02
Hello all. Iv been reading through this thread and you all seem to be very knowledgeable about Python, which means that perhaps you can help me with my sudden dislike of the language!

First of all let me explain that I am a very new Python developer. Iv been through plenty of other languages in my time though, from Assembler on the Amiga (I'm rather old ;) ) through C, C++ and VB on the PC.

I started about a week ago with Python, and I am currently using wxGlade and Scite. All has been going well, and I produced a small and simple application to keep snippets of Python code for me.

And then the problem. Two days ago I discovered that there does not appear to be any kind of control to load and save RTF files.

Iv spent the last two days hunting around for information about this, but so far I have found nothing concrete. Some posts on other sites dating from 2006 suggested that the load/save functionality was imminent, but since those dates Iv found nothing that suggests it has arrived, or is about to.

I have updated everything to the latest versions in the hope that an RTF enabled control would miraculously appear in wxGlade, but so far Iv had no joy. The closest Iv been to RTF of any kind is from the wxWidgets demo, and while it looked great, the text was actually generated in code, and the control could not save or load RTF.

Does anyone have a definite answer for me? Is there an RTF control, and if so how do I get it?

Iv enjoyed the last week of learning, but in all honesty if I cant overcome this (relatively) simple hurdle I cant continue with Python because my next project requires RTF (View/load/save) at the very least.

Sorry if this is not an ideal place to post - Iv already posted a question about this - But having found this thread and a whole bunch of people who seem to know what they are talking about, I thought Id better take the plunge and try for an answer.

Regards

Max

---

### Post by LaRoza on 2008-11-02
> **MaxVK said:**
> Hello all. Iv been reading through this thread and you all seem to be very knowledgeable about Python, which means that perhaps you can help me with my sudden dislike of the language!

And then the problem. Two days ago I discovered that there does not appear to be any kind of control to load and save RTF files.

Um, that isn't something to dislike Python about. Use an another library. You are having problems with wxWidgets, a GUI library, not having RTF support. I suggest you find another library for what you need.

A quick search found this, but I don't know if it does what you want: [http://pyrtf.sourceforge.net/](http://pyrtf.sourceforge.net/)

> 
I have updated everything to the latest versions in the hope that an RTF enabled control would miraculously appear in wxGlade, but so far Iv had no joy. The closest Iv been to RTF of any kind is from the wxWidgets demo, and while it looked great, the text was actually generated in code, and the control could not save or load RTF.

Iv enjoyed the last week of learning, but in all honesty if I cant overcome this (relatively) simple hurdle I cant continue with Python because my next project requires RTF (View/load/save) at the very least.

Sorry if this is not an ideal place to post - Iv already posted a question about this - But having found this thread and a whole bunch of people who seem to know what they are talking about, I thought Id better take the plunge and try for an answer.


You are not having problems with Python, but wxWidgets. I suggest another toolkit if the one you are using doesn't have what you want.

---

### Post by MaxVK on 2008-11-02
PyRTF - I found this yesterday but its not really what I'm looking for.

A different library - Now then, this is something that I hadn't considered because I was chugging along so nicely, and I take your point that my problem is with wxWidgets and not with Python.

Can you give some advice about which library/toolkit would be best. Iv only used wxWidgets so far and I'm still trying to find my feet with libraries and toolkits.

I'm still looking to use something along the lines of wxGlade for design, but I assume that the code editor is pretty much a matter of personal preference.

Many thanks for your response,

Regards

Max

---

### Post by LaRoza on 2008-11-02
> **MaxVK said:**
> PyRTF - I found this yesterday but its not really what I'm looking for.

A different library - Now then, this is something that I hadn't considered because I was chugging along so nicely, and I take your point that my problem is with wxWidgets and not with Python.

Can you give some advice about which library/toolkit would be best. Iv only used wxWidgets so far and I'm still trying to find my feet with libraries and toolkits.

I'm still looking to use something along the lines of wxGlade for design, but I assume that the code editor is pretty much a matter of personal preference.

Many thanks for your response,

Regards

Max

I think you should use your own thread for this issue ;)

See the sticky for GUI toolkits, the other two more popular ones have GUI designers.

---

### Post by MaxVK on 2008-11-02
Thanks LaRoza, and sorry to have butted into your thread.

Regards

Max

---

