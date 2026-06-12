---
title: "Trouble with Java/Facebook"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by ProPyro on 2008-09-23
I've seen some similar problems that others have had where flash pages load up as a gray box, well I'm having this problem with the Facebook photo uploder on Fire Fox 2. It will ask me if I want to trust the applet I'm loading, I'll say to trust it or add it to the white list and then I get a gray box that just sits there.  I installed "Sun Java 5.0 runtime" thinking that might be the problem but it didn't help anything.  I've got a screen shot of my problem in "action", if any of you have any idea how to fix this it would be greatly appreciated if you can let me know.

---

### Post by HellNoire on 2008-09-23
Could it be flash that you need and not Java?

---

### Post by ProPyro on 2008-09-23
I doubt it, when I use the computers at school on IE load it up and it has the Java logo all over it.

---

### Post by LowSky on 2008-09-23
in terminal type

sudo apt-get install ubuntu-restricted-extras

follow the prompts

then restart ubuntu, everything should work

---

### Post by ProPyro on 2008-09-24
Thanks LowSky, I tried that and it started to help, the applet box flashed black a few times but then it went back to being a gray box.  I restarted both my computer and firefox after it downloaded an update after restarting.

---

### Post by Sef on 2008-09-24
1) What Ubuntu are you using?

2) Are you using a 32-bit or 64-bit os?

---

### Post by k0rv3n on 2008-09-26
Hi I have the same problem. I am using Ubuntu 8.04 x64, Firefox 3

I have java for Firefox installed and when I load the page it says "loading applet" in the status bar for a while and then "Start: applet not initialized". I have tested other applets and they work fine.

---

### Post by tlocotes on 2008-10-19
If you are using firefox, and you have the latest version of java, then the problem lies in your registry. Had the same problem, and it drove me nuts! Run a program specified to clean your registry, and you should be fine. I found a great review page of cleaning software at [http://byebar.bezoogle.com/pp/registry](http://byebar.bezoogle.com/pp/registry)

---

