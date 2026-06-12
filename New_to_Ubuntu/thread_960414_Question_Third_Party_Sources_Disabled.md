---
title: "Question: Third Party Sources Disabled"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by suomalainen on 2008-10-27
Ubunteros,

I'm in the process of upgrading to 8.04LTS. During the upgrade process the following appeared.

"Some third party entries in your source list were disabled. You can re-enable them after the upgrade with the software properties tool or your package manager."

What does this message mean exactly? Where is the "Software Properties Tool" located ?

Does Package Manager mean Synaptic Package Manager?

Thank you

---

### Post by philinux on 2008-10-27
This is normal behaviour. Check system>admin>software sources.

---

### Post by suomalainen on 2008-10-27
ok. I'll post results as soon as install finishes. Looks like I may need an hour or so.

---

### Post by jesuisbenjamin on 2009-10-31
> **suomalainen said:**
> ok. I'll post results as soon as install finishes. Looks like I may need an hour or so.

It's been more than an hour...

Now i am in the same situation. So i went to Software Sources, in the third party tab.
Some 'sources' (i guess) are entitled 'disabled on upgrade to Jaunty', so i tick these. Other 'sources' (or whaterver it is) refer to Intrepid Ibex in their title, should i tick these too? It seems unnecessary.

Can anyone coach me on this? And can anyone please tell me what i am doing? It's a bit obscure to me.

Thanks ;)

---

### Post by jesuisbenjamin on 2009-11-03
Is there no Ubuntu Guru to bring light upon these matters?

---

### Post by waspbr on 2009-11-03
I am no guru, but the reason why those sources are deactivate on a distribution upgrade is that they were only relevant to the previous version of ubuntu.

Say if you are using intrepid and you want to upgrade into jaunty, it makes sense that jaunty has its own sets of update third-party repositories. To most repositories all you have to do is go to System>Administration > Software Sources > Third party apps tab and select a previous source line and make choose the edit option. If your previous version was intrepid then you may want to update the distribution section to jaunty. 

if you think this to confusing then it may be a good idea to just remove the line and re-enter it by looking for the repository yourself (google it).

---

### Post by konqueror7 on 2009-11-03
you may read further about repositories in detail [here]("https://help.ubuntu.com/community/Repositories/Ubuntu")...

---

