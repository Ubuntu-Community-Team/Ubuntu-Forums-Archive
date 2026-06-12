---
title: "Python and Lottery (probabilities | predictions) any tips?"
date: 2008-12-12
forum: Programming Talk
---

### Post by picturefreedom on 2008-12-12
I couldn't find any related topics for this, so i'm making one :)

anyhow, as regular lotto player and as a python newbie, where should i start looking? any **tutorials , concepts and modules** for this topic is greatly apprecieted. :)

---

### Post by CptPicard on 2008-12-12
Take it from someone whose main field of endeavour is writing code for professional sports betting operation... there's nothing there in lottery to be predicted and playing it is a fool's errand. Your expectancy of profit is dismally low.

---

### Post by mentallaxative on 2008-12-12
Are you sure you are not falling for the gambler's fallacy?

---

### Post by jespdj on 2008-12-12
The lotto is random, it is impossible to predict the outcome of the lotto. So there is no way you could ever write a computer program that predicts the outcome of the lotto.

If someone ever tries to sell you such a program, then you can be 100% sure that it's a scam.

---

### Post by CptPicard on 2008-12-12
Actually there is *one* way to try to maximize winnings in lottery, and that is seeing which numbers are commonly played by others, so that if you *do* win, it's likely that there are no others sharing with you.

Of course, this is totally meaningless with regards to actual long term profitability, but still..

---

### Post by picturefreedom on 2008-12-12
> **mentallaxative said:**
> Are you sure you are not falling for the gambler's fallacy?

maybe i am, but then, i guess i'm just looking for somehing to spice up my picks.

---

### Post by picturefreedom on 2008-12-12
> **CptPicard said:**
> Actually there is *one* way to try to maximize winnings in lottery, and that is seeing which numbers are commonly played by others, so that if you *do* win, it's likely that there are no others sharing with you.

Of course, this is totally meaningless with regards to actual long term profitability, but still..

will choosing frequent numbers drawn (programmaticaly in this context) , raise the activity of my chosen picks?

i'm not looking for good predictions, it would be stupid to think otherwise, i guess in python context, what's the easy way spot silly patterns?

---

### Post by frankleeee on 2008-12-12
The lottery is generally a way of taxing the poor.

---

### Post by loell on 2008-12-12
> **frankleeee said:**
> The lottery is generally a way of taxing the poor.

irrelevant unless expressed pythonically! :lolflag:


for patterns, err use regex :D

I dunno if pymvpa might be the one you're looking for..

---

### Post by cb951303 on 2008-12-12
if you have access to all winning numbers in the past you can do statistical analysis with python.

---

### Post by Delever on 2008-12-12
> **cb951303 said:**
> if you have access to all winning numbers in the past you can do statistical analysis with python.

And next numbers will be (not) predicted :D

EDIT: 
If there would be pattern in random lottery numbers, it would not be lottery, because numbers would not be random.

---

### Post by cb951303 on 2008-12-12
> **Delever said:**
> And next numbers will be (not) predicted :D

EDIT: 
If there would be pattern in random lottery numbers, it would not be lottery, because numbers would not be random.

well of course he can't predict :D it would be good opportunity for him to develop his python skills though.

---

### Post by HelioJorge on 2013-03-22
> **picturefreedom said:**
> I couldn't find any related topics for this, so i'm making one :)

anyhow, as regular lotto player and as a python newbie, where should i start looking? any **tutorials , concepts and modules** for this topic is greatly apprecieted. :)

Hi, the best I could come up with was: :arrow:


[COLOR=#0000AA]import[/COLOR] [COLOR=#00AAAA]_random_[/COLOR]numbers = [COLOR=#00AAAA]range[/COLOR]([COLOR=#009999]1[/COLOR], [COLOR=#009999]50[/COLOR])chosen = [][COLOR=#0000AA]while[/COLOR] [COLOR=#00AAAA]len[/COLOR](chosen) < [COLOR=#009999]6[/COLOR]:    number = random.choice(numbers)    numbers.remove(number)    chosen.append(number)chosen.sort()[COLOR=#00AAAA]print[/COLOR]([COLOR=#AA5500]"This week's numbers are"[/COLOR], chosen)[COLOR=#00AAAA]print[/COLOR]([COLOR=#AA5500]"The bonus ball is"[/COLOR], random.choice(numbers))I hope this helps.

---

