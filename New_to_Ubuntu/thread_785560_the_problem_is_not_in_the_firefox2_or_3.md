---
title: "the problem is not in the firefox2 or 3"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by singetak on 2008-05-07
I uninstalled firefox 3 from heron and installed firefox 2 but the problem that i have didn't disappear.The problem is that the browser suddenly closes.
Any idea about this.

---

### Post by subzero316 on 2008-05-07
There may be several reasons. Firefox does have a few stability issues.
Try the new OPERA browser.

---

### Post by singetak on 2008-05-07
i need the firefox addons.can i use them for the opera

---

### Post by stchman on 2008-05-07
> **singetak said:**
> I uninstalled firefox 3 from heron and installed firefox 2 but the problem that i have didn't disappear.The problem is that the browser suddenly closes.
Any idea about this.

You may have a hardware problem.  FF never all the sudden closes.

---

### Post by singetak on 2008-05-07
I think the FF3 always suddenly closes. The FF2 made it once after i installed it but when i restarted it worked properly so i will stick with FF2.
Moreover the FF3 is slower.

---

### Post by Dark Aspect on 2008-05-07
> **singetak said:**
> I uninstalled firefox 3 from heron and installed firefox 2 but the problem that i have didn't disappear.The problem is that the browser suddenly closes.
Any idea about this.

Well you could try loading firefox via terminal with:

```
firefox
```

and

```
firefox-3.0
```

for firefox 3 I believe.Then maybe if it crashes it will give a hint why in the terminal.This is probably a hardware problem as mentioned above since I have never had this problem.

BTW:I agree that Firefox 3.0 is much slower then FF2.

---

### Post by omkarwagh on 2008-05-07
yeah im getting the same problems with ff3. when i do something as right click->save target as, ff3 has a 50% probability of randomly closing without giving any warnings whatsoever.

---

### Post by spectrevk on 2008-05-07
> **stchman said:**
> You may have a hardware problem.  FF never all the sudden closes.

Yes it does, nearly constantly anytime there's flash video involved. I had this problem in FF3 for a while, until I read somewhere on here about a (apparently unnecessary) flash-related library package for firefox that is known to cause stability issues. I removed that package, FF3 works great now, no crashes on flash video sites.

---

### Post by ubuntu27 on 2008-05-07
> **stchman said:**
> You may have a hardware problem.  FF never all the sudden closes.


> **spectrevk said:**
> Yes it does, nearly constantly anytime there's flash video involved. I had this problem in FF3 for a while, until I read somewhere on here about a (apparently unnecessary) flash-related library package for firefox that is known to cause stability issues. I removed that package, FF3 works great now, no crashes on flash video sites.

Yes, Mozilla Firefox closes automatically without any notice. I never test it with FF3, but with FF2 I had the same problem.

This bug or problem is very well known. People call it **"The magical disappearing browser"**

Search for it in a search engine such as google. You'll see that it is affecting hundreds of people.

---

### Post by tjwoosta on 2008-05-07
i also have difficulties with firefox just ramdomly closing

this has been hapening ever since ubuntu gutsy

i have tried firefox 2 & 3 and even opera, but sadly my problem still persists

i have tried removing flash completely as well as trying different flash players.

the web browser will still randomly close once in a while even without flash!

i believe the problem is something to do with ubuntu not the web browsers, or flash because everything works fine with fedora and with windows vista

---

### Post by spectrevk on 2008-05-08
> **tjwoosta said:**
> i also have difficulties with firefox just ramdomly closing

this has been hapening ever since ubuntu gutsy

i have tried firefox 2 & 3 and even opera, but sadly my problem still persists

i have tried removing flash completely as well as trying different flash players.

the web browser will still randomly close once in a while even without flash!

i believe the problem is something to do with ubuntu not the web browsers, or flash because everything works fine with fedora and with windows vista
I beleive it's libflashsupport that causes the problem...again, someone else on these forums pointed it out. I simply removed it, but there's another fix here: [http://ubuntuforums.org/showpost.php?p=4834089&postcount=4](http://ubuntuforums.org/showpost.php?p=4834089&postcount=4)

---

