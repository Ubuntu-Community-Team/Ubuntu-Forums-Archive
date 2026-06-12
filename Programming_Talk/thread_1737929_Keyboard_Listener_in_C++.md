---
title: "Keyboard Listener in C++"
date: 2011-04-24
forum: Programming Talk
---

### Post by MrStill on 2011-04-24
Hello,

I have suddenly found myself with some free time and I want to learn a little about game development. I have decided to do something small using model-view-controller architecture. Just a circle I can control with the keyboard. But, I am having some difficulties with the controller.   

I am wanting to write a keyboard listener in C++. I have a vague idea about how it should work; but, I'm not sure I have started in the right place. 

The ideal way would be to have an object for each key I am interested in watching, as there will not be many and I want to reduce conditional logic. These objects will have observers which they notify on each event. But, this sounds impossible as all keystrokes come in as the same stream. Also, I haven't worked out the threading aspect of it either.  

I spent some time with Google and didn't get very far. Any advise I could get would be nice.

Thanks in advance.

---

