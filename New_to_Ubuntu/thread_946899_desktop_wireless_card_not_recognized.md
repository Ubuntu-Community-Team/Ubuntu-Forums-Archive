---
title: "desktop wireless card not recognized"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by chaddiesel on 2008-10-13
I am fixing an old PC for a roommate and have installed linux. We are trying to get a wireless card to work on it. The card we got was an Encore wireless G adapter. I cannot get ubuntu to realize the card is in there.

I'm guessing i need to install a driver for it. I yanked a Linksys G card out of another computer in the house and that one works fine in the roommate's computer. Is there an easy way to make this Encore card work, or should we scrap it?

---

### Post by fooman on 2008-10-13
i recently got 2 encore wireless-g cards running in ubuntu using ndiswrapper.  what card is that?

run the following in a terminal,  find the wireless device in the list and post that line back here:

```
lspci
```

---

