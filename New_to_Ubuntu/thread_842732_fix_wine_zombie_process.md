---
title: "fix wine zombie process??"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by andyho on 2008-06-27
[COLOR="Indigo"]I have a program that will run ok in Wine. It's kinda a chat program. A customer will come on and then after the session is done, Wine sends it into a zombie process. Then I have to kill the process and reopen it. Is there something I can do to prevent that from happening so that it will continue to stay active? For some reason even though it's showing as a zombie process, it will continue to show that I'm active on the website the chat is linked to?! Which if a customer tries to contact me after Wine has made it a zombie process, it'll dump the customer, looking like I "hung up" on them in a sense. Am I able to fix it or do I just have to live with shutting it down every time? Thanks guys!! :KS[/COLOR]

---

### Post by Hospadar on 2008-06-27
Probably not really, while wine is a wonderful tool that makes a lot of things possible, it still has a lot of bugs compared to a native windows environment.  You could try monkeying with some settings in winecfg, or making a script to kill and restart the program more conveniently.  If neither of those provide solutions, and you need to run this on linux (or you just really want to) you could look into running a windows virtual machine.  they can be a little tricky to set up but tend to have near-perfect compatability.  You might ask around here for some advice on how to set that up, use the googletron, or look in the community doc link in my sig.

---

