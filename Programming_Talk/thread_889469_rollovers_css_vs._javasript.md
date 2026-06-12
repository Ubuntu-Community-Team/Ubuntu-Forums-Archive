---
title: "rollovers: css vs. javasript"
date: 2008-08-14
forum: Programming Talk
---

### Post by Peter76 on 2008-08-14
Hello, I've just spent some time making image rollovers for my website using css. When I was about finished I found out this could be accomplished with javascript as well, with fewer lines of code ( I'm quite new to this webdesign stuff ).
Now I'm wondering: which is the better way to go here, use css or javascript?
Answers with explanations please :-)

Thanks, Peter76

---

### Post by Zugzwang on 2008-08-14
IF CSS works well, use CSS. Reason: A lot of surfers deactivate JavaScript (for various reasons). Also there are browser not being able to interpret JavaScript correctly. Not to mention that JavaScript is usually more CPU-intense.

---

### Post by LaRoza on 2008-08-14
> **Peter76 said:**
> Hello, I've just spent some time making image rollovers for my website using css. When I was about finished I found out this could be accomplished with javascript as well, with fewer lines of code ( I'm quite new to this webdesign stuff ).
Now I'm wondering: which is the better way to go here, use css or javascript?
Answers with explanations please :-)

Thanks, Peter76

There is no better way. There are two criteria:

[list]
[*] Which is more reliable?
[*] Which is easier?
[/list]

Both are reliable and easy in modern browsers.

---

### Post by Peter76 on 2008-08-15
bump

---

### Post by Reiger on 2008-08-15
Why? It's been answered like two posts before mine already?

If you want a very picky roll-over effect you're better off combining the two anyways (try mimicking the exact behaviour of your browser's drop-down menu's and you'll see why...).

If not use w/ever is more convenient.

---

### Post by deluser on 2008-08-15
might I recomend the wonderfull world of [JQuery]("http://jquery.com/")

---

### Post by mssever on 2008-08-15
Theoretically, I think it's better to use Javascript. Think of it this way: a website consists of three main concepts--structure, layout, and behavior. (X)HTML takes care of the structure, CSS is for the layout, and Javascript handles behavior. Since rollovers are behavior, it makes sense to keep the parts separate and use JS for them.

However, sometimes practicality beats purity. If, even after writing your scripts unobtrusively, you're still concerned about people who will be able to use your CSS and not your JS, then CSS might be the best option.

---

