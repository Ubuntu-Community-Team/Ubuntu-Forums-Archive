---
title: "Cannot debug on mono"
date: 2012-04-02
forum: Programming Talk
---

### Post by shmparvez on 2012-04-02
I was debugging my application on mono develop and everything was  working awesome. Now debugging never works for me starting today.

I dont know what has changed. Its really critical to get it back up now.

Can someone help me?

Thanks

---

### Post by Zugzwang on 2012-04-03
Perhaps you can start by explaining what happens when you try to debug something, including possible error messages, unexpected behaviour of the MonoDevelop GUI, etc.

Without any details, the best advice that anyone can give to the problem "it doesn't work", is unfortunately often only "then fix it".

---

### Post by shmparvez on 2012-04-03
Agreed. I am debugging the application I have (C#) in mono develop. It runs in debug mode and I can see the debug spew in the application output window. It never hits any breakpoints I set. I tried system.diagnostics debug break option but that does not hit break point either. 
Right now I am debugging and fixing the issues by adding debug trace but that has significantly slowed me down. 

Thanks for the help.

---

### Post by directhex on 2012-04-03
You're using the soft debugger built into MonoDevelop, not the old hard debugger from the mono-debugger package?

Which Ubuntu release?

---

### Post by pt123 on 2012-04-05
what is mono's equivalent of starting the application by clicking the debug button in Visual Studio?

---

### Post by directhex on 2012-04-06
> **pt123 said:**
> what is mono's equivalent of starting the application by clicking the debug button in Visual Studio?

Clicking the debug button in MonoDevelop.

---

### Post by pt123 on 2012-04-07
> **directhex said:**
> Clicking the debug button in MonoDevelop.

Thanks didn't see the button, and couldn't find in the Build menu, just realised there is seperate "Run" menu.

---

### Post by shmparvez on 2012-04-10
How can I find out which debugger I am using. All I know is that I installed mono package using apt-get and I had the debugger working and now it does not work. 
its version 2.6 (thats what shows up if I do help -> about)

---

### Post by TokyoJeff on 2012-04-18
Same problem here.  I suspected it was something to do with using the Alpha version of 12.04 Ubuntu, either some library conflict or the Mono package itself, so I downloaded the monodevelop and dbg packages, compiled and installed them myself to the 2.8.8 release.

No change.  Still can't set breakpoints.  Rather frustrating, but I guess I did it to myself by using Alpha Ubuntu....  I hope the fix it soon in the real 12.04 release.

---

