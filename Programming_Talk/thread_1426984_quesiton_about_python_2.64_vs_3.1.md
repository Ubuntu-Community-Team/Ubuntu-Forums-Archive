---
title: "quesiton about python 2.64 vs 3.1"
date: 2010-03-10
forum: Programming Talk
---

### Post by XXMy_Little_ShinigamiXX on 2010-03-10
hi all, im on a tutorial now where i guess a new kw argument has been added to the function print():
the end="" expression is i guess fairly new? i suppose this is only in 3.1 as the tutorial warned me to upgrade before i did any of this. but im a little iffy on the upgrading part. i mean ive done some reading up and i get mixed reviews, i mean some ppl say theyres too many bugs others say it works fine. does anyone have any feedback vs the two? :popcorn:

---

### Post by snova on 2010-03-10
> **XXMy_Little_ShinigamiXX said:**
> hi all, im on a tutorial now where i guess a new kw argument has been added to the function print():
the end="" expression is i guess fairly new?

One of the things Python 3 changed was the conversion of the print statement to a print function. I think the end parameter was there from the start though (of the 3.0 series).

> i suppose this is only in 3.1 as the tutorial warned me to upgrade before i did any of this.

The thing about Python 3 is that it isn't exactly an updated version- both the 2.x and 3.x series will be maintained for some time to come. Features are also backported regularly- 2.6 included a lot of things from 3.0, and I believe either 2.7 or 2.6 is taking features from 3.1.

> but im a little iffy on the upgrading part. i mean ive done some reading up and i get mixed reviews, i mean some ppl say theyres too many bugs others say it works fine. does anyone have any feedback vs the two? :popcorn:

Bugs? I don't know what that could refer to; it's as stable as the 2.x series as far as I know.

The reason you are recommended to avoid Python 3, though, is for other reasons- it is an incompatible progression of the language and 2.x code will not work without modification. This isn't a major issue for vanilla Python code, but there are a lot of very large, important libraries that are entirely cut off from Python 3.

The general rule for now is to stick with Python 2.x. In time, as more third-party code supports Python 3, it will become the main version of the language. But not yet.

---

