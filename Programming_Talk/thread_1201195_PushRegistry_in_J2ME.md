---
title: "PushRegistry in J2ME?"
date: 2009-06-30
forum: Programming Talk
---

### Post by ittiam on 2009-06-30
I am totally new to J2ME and am kind of struggling. My basic idea was to create a background process in a mobile phone. The way for that was PushRegistry where in you register a datagram/socket connection and even when the application exits, the AMS will monitor the connection and whenever there is data it will automatically trigger the startapp of the midlet. 

I am just not able to make this work. The mobile receives data for the first time and then on it does not. 

Some more questions

1) When the startApp() has finished executing and I do not call destroyApp, will the application continue running?

2) I really do not understand what they mean when they say "application not running". To make the application not running (exit) is by calling destroyApp/notifyDestroyed(). So even after I do this if a data comes on the connection registered using PushRegistry, will it start the application again? From what I understand it should but not happening.

---

