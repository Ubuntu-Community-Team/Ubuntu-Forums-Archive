---
title: "A clipboard manager that works ... FOR ME"
date: 2012-10-12
forum: New to Ubuntu
---

### Post by Langstracht on 2012-10-12
I cut and paste a lot.  But far and away most of them are one shot.  There are none too many I would like saved forever.

Consequently I have been trying to find a clipboard manager that I can selectively save stuff to OR allows me to delete the ones I don't want.

I have found neither.  They save everything.  Or they clear everything.

Does anyone know of a utility that would do what I want?

TIA

---

### Post by stinkeye on 2012-10-12
Try **glipper**, has a snippets plugin and you can also set number of items kept in history.
The history has to be set to at least 1 for the snippets to show.

---

### Post by Langstracht on 2012-10-12
I had tried glipper (and klipper and parcellite ...) before ... but I did not use/try the plug-in.

I think you are saying I should use glipper to collect "everything" and then us the plug-in to cull them. If so, I can do that.  Could make for a lot of maintenance though ...

And not nearly as good as hitting, oh I don't know, F12, to tell the manager "keep this one for me please".  

Thanks for your response

---

### Post by Frogs Hair on 2012-10-12
Pastie has an edit function, but you have to remove the entries you don't want by highlighting and deleting . You can get the .deb from the link below. 

[https://launchpad.net/~hel-sheep/+archive/pastie/+sourcepub/2054688/+listing-archive-extra](https://launchpad.net/~hel-sheep/+archive/pastie/+sourcepub/2054688/+listing-archive-extra)

---

### Post by Langstracht on 2012-10-12
Thanks.  

I'll see if I can follow that up.

---

### Post by Lyfang on 2012-10-12
A clipboard manager should be enabled by default in Ubuntu? See also: [MASTER Copy-Paste doesn't work if the source is closed before the paste]("https://bugs.launchpad.net/ubuntu/+bug/11334")

---

### Post by Langstracht on 2012-10-12
Sorry ... but I'm not exactly sure what that has to do with, or to do with dealing with, my problem.

---

### Post by Lyfang on 2012-10-13
> **Langstracht said:**
> Sorry ... but I'm not exactly sure what that has to do with, or to do with dealing with, my problem. Sorry no answer. Yes, I agree, that post was a bit off-topic, but Ubuntu has a general problem (bug) that when you copy text and close that program, the clipboard gets empty (lost the text experiance?). I suggest you could ask a question or file a bug of a feature request or Wishlist bug at Launchpad too: [https://bugs.launchpad.net/ubuntu/+source/glipper](https://bugs.launchpad.net/ubuntu/+source/glipper) or [https://bugs.launchpad.net/ubuntu/+source/parcellite](https://bugs.launchpad.net/ubuntu/+source/parcellite) (Launchpad account needed)

---

### Post by Langstracht on 2012-10-14
I'm no programmer but I would have thought it would not be difficult to include a toggle to turn the manager on and off or a switch to selectively save selections.  And I'm a bit surprised that none (that I can find anyway) do that.  You'll realize that my initial post was hoping that there was one available.

Do you know (or can you speculate) which of the links you offered is most liable to take this on?

---

### Post by Lyfang on 2012-10-29
Try Glipper and the "Snippets" plugin. But unfortunately Glipper 2.4 seems to suffer from this bug: [Snippets are not allways available]("https://bugs.launchpad.net/ubuntu/+source/glipper/+bug/775945").

---

### Post by Langstracht on 2012-10-31
Thank you for that.  Glipper and the plugin seem to do the job.  Not exactly what I was looking for.  But close enough.

So thanks so much once again.

---

### Post by Lyfang on 2012-11-11
Thanks for creating this thread! However I found Glipper a bit buggy and the Snippets plugin is not always working properly. I also filed this bug: [Glipper large memory footprint]("https://bugs.launchpad.net/ubuntu/+source/glipper/+bug/1077713"). I plan to try Parcellite since it's a lightweight GTK+ clipboard manager. But Glipper has more features and the Snippets plugin (for permanent storage) is very useful.

---

### Post by Langstracht on 2012-11-11
While I marked the thread "Solved" ... that is not to say that it is problem free.  

I too find Glipper buggy, very buggy in fact ... to the extent of having to add it (again and again) to the panel perhaps half the time I start it.

However, I never did find an acceptable alternative and, having added it to the panel again, find it does the job and seems not to lose any data.

---

### Post by avsprasad on 2012-12-12
Anamnesis. Read this: [http://www.webupd8.org/2010/09/anamnesis-new-linux-clipboard-manager.html](http://www.webupd8.org/2010/09/anamnesis-new-linux-clipboard-manager.html)

---

