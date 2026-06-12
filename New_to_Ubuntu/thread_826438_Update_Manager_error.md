---
title: "Update Manager error?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by ravenvii on 2008-06-11
I just did a clean install of Ubuntu Hardy today, and ran Update Manager. When it finished, it says there was an error during one of the updates, gedit I think. But when I tried running it again, it says my system is up-to-date.

So do I just ignore that error, or what?

---

### Post by iaculallad on 2008-06-11
> **ravenvii said:**
> I just did a clean install of Ubuntu Hardy today, and ran Update Manager. When it finished, it says there was an error during one of the updates, gedit I think. But when I tried running it again, it says my system is up-to-date.

So do I just ignore that error, or what?

Drop to your terminal and issue the commands below:

```
sudo apt-get update && sudo apt-get upgrade
```

And try to post any errors it prompts.

---

### Post by ravenvii on 2008-06-11
already did those commands. Apt acted as if my computer is completely up to date, like if that error has never happened.

---

### Post by Tatty on 2008-06-11
It sounds fine but just to check try running

```
sudo apt-get install -f
```

That should fix any problems which might exist

---

### Post by ravenvii on 2008-06-11
Apt-get install -f acted if everything is peachy.

Guess everything is fine despite what Update Manager says?

---

