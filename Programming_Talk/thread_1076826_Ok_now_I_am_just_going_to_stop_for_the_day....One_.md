---
title: "Ok now I am just going to stop for the day....One more question before I go though?"
date: 2009-02-21
forum: Programming Talk
---

### Post by Leo Dragonheart on 2009-02-21
I know this is an example for the comma operator and my question has nothing to do with that. My question is: Why would you write a = (b=3, b+2); why not write a = 5? I think this computing stuff is not going to click with my logical mind....:(

```
For example, the following code:

a = (b=3, b+2);

Would first assign the value 3 to b, and then assign b+2 to variable a. So, at the end, variable a would contain the value 5 while variable b would contain value 3.
```

---

### Post by Krupski on 2009-02-21
> **Leo Dragonheart said:**
> I know this is an example for the comma operator and my question has nothing to do with that. My question is: Why would you write a = (b=3, b+2); why not write a = 5? I think this computing stuff is not going to click with my logical mind....:(

```
For example, the following code:

a = (b=3, b+2);

Would first assign the value 3 to b, and then assign b+2 to variable a. So, at the end, variable a would contain the value 5 while variable b would contain value 3.
```

Maybe to make it easier for the programmer himself to understand?

Here's an example of how a similar "mess" actually makes sense:

```

data = (port=0x1000, port+0); // data points to the data register
stat = (port=0x1000, port+1); // stat points to the status register
cnfg = (port=0x1000, port+2); // cnfg points to the config register

```

Of course, an equally easy way to do it (if not easier) is just to say:

"data = 0x1000+0"
"stat = 0x1000+1"
...etc


Make sense? 

-- Roger

---

### Post by Leo Dragonheart on 2009-02-21
> **Krupski said:**
> Maybe to make it easier for the programmer himself to understand?

Here's an example of how a similar "mess" actually makes sense:

```

data = (port=0x1000, port+0); // data points to the data register
stat = (port=0x1000, port+1); // stat points to the status register
cnfg = (port=0x1000, port+2); // cnfg points to the config register

```

Of course, an equally easy way to do it (if not easier) is just to say:

"data = 0x1000+0"
"stat = 0x1000+1"
...etc


Make sense? 

-- Roger

No it does not make sense to me. I think what you are saying is some people like the high road, and some people like the low road? Isn't coding complicated enough. It just don't make sense to me to write: 
```
(looo + (oooo / ooooo) - oooonnnnn == (nnnn) + "nnggggg" - gggg code) <- "exactly how I see the above code" 
```when you get exactly the same thing from: ```
("long code")<- see how clean and crisp this is, short and to the point....
```

---

### Post by simeon87 on 2009-02-21
The lesson from this could be that you shouldn't use all the features of a language. Just because a language supports goto doesn't mean you should use it ;)

---

### Post by Leo Dragonheart on 2009-02-21
> **simeon87 said:**
> The lesson from this could be that you shouldn't use all the features of a language. Just because a language supports goto doesn't mean you should use it ;)

That is a good point. It does put my brain back in cruise control as far as trying to understand it, but it still perplexes me. Thanx for the input.

---

### Post by WW on 2009-02-21
> **Krupski said:**
> Maybe to make it easier for the programmer himself to understand?

Here's an example of how a similar "mess" actually makes sense:

```

data = (port=0x1000, port+0); // data points to the data register
stat = (port=0x1000, port+1); // stat points to the status register
cnfg = (port=0x1000, port+2); // cnfg points to the config register

```

Of course, an equally easy way to do it (if not easier) is just to say:

"data = 0x1000+0"
"stat = 0x1000+1"
...etc


Make sense? 

-- Roger

From a software engineering standpoint, it makes even more sense to write
```

port = 0x1000;
data = port + 0;
stat = port + 1;
cnfg = port + 2;

```
Then you are not repeating "port = 0x1000" or the explicit value of the port in each statement.  If you later change the port, you only change the value in one place instead of in every line that you used it.

---

### Post by wmcbrine on 2009-02-22
It's just an example. Like everything else you're complaining about. Why would you do *that*, specifically? You wouldn't. No one would. But it shows you, in compact form, the sorts of techniques you *could* use, in other situations where they'd make more sense, without getting into the long-winded details of those situations.

---

### Post by Krupski on 2009-02-22
> **WW said:**
> From a software engineering standpoint, it makes even more sense to write
```

port = 0x1000;
data = port + 0;
stat = port + 1;
cnfg = port + 2;

```
Then you are not repeating "port = 0x1000" or the explicit value of the port in each statement.  If you later change the port, you only change the value in one place instead of in every line that you used it.

True... but I was trying to keep with the format the OP used so as not to add to confusion.

-- Roger

---

### Post by Leo Dragonheart on 2009-02-22
> **wmcbrine said:**
> It's just an example. Like everything else you're complaining about. Why would you do *that*, specifically? You wouldn't. No one would. But it shows you, in compact form, the sorts of techniques you *could* use, in other situations where they'd make more sense, without getting into the long-winded details of those situations.

Could you please show me an example where you would use the long version on my original example where you can not use the short version please? Thanx....

Oh and by the way I am not complaining I am trying to understand...Seeing as I am only three days old at coding, I just take for granted that the lesson is correct, and therefore I am just trying to understand what I am missing that's all...

---

### Post by wmcbrine on 2009-02-22
> **Leo Dragonheart said:**
> Could you please show me an example where you would use the long version on my original example where you can not use the short version please?No. It's not about "long version" vs. "short version", it's about "this is how the comma operator works." If you want a more meaningful example, I'd have to dig around to find one in some working code, or else go to more effort to contrive one. I'm not going to do that, sorry.

I don't think I've ever personally used the comma operator, actually. But that doesn't mean it's useless... just not common.

---

