---
title: "&quot;Poll Results&quot; algorithm question"
date: 2010-06-16
forum: Programming Talk
---

### Post by Krupski on 2010-06-16
**[COLOR="Red"]Note: This is NOT homework, I am not a student and I am aware of this board's policy concerning homework. This is a personal hobby question.[/COLOR]**

Hi all,

I have a small message board which has as one of it's features the ability to post a POLL.

The poll can have any number of choices, and any number of votes allowed per user.

The poll code in it's "stock" form shows the percentage of each vote as a bar chart and all bars of course add up to 100%.

Now, here's my question: I think that is wrong. Consider this example:

```

Considering Neapolitan Ice Cream, do you like:
[ ] Chocolate
[ ] Vanilla
[ ] Strawberry
[ ] None - I hate ice cream!
You may choose up to 3 options

```

Now, imagine that 10 PEOPLE voted and they voted like this:

* 9 like chocolate
* 8 like vanilla
* 3 like strawberry
* 1 hates ice cream

This data tells me that 90% of the voters like chocolate, 80% vanilla and 30% strawberry. It also tells me that 30% like all 3 flavors, 80% like only vanilla and chocolate and 90% like ONLY chocolate.

So, in my opinion, the bar graph SHOULD look like this:

```

Chocolate:   ##################   [90%]
Vanilla:     ################     [80%]
Strawberry:  ######               [30%]
Hate it:     ##                   [10%]

          Total Votes: 10

```

However, the code currently produces a graph like THIS:

```

Chocolate:   #########            [43%]
Vanilla:     ########             [38%]
Strawberry:  ###                  [14%]
Hate it:     #                    [ 5%]

          Total Votes: 10

```

Sure, it adds up to 100%, but the data doesn't seem to give the proper "feel" for what the actual votes were. Looking at "chocolate", I would think "hmmm less than 1/2 like chocolate" when in fact 90% do.

So, which "way" is right? My way, or the "stock" way the board does it?

Thanks for any input!

-- Roger

---

### Post by ja660k on 2010-06-16
> **Krupski said:**
> 
Now, imagine that 10 PEOPLE voted and they voted like this:

* 9 like chocolate
* 8 like vanilla
* 3 like strawberry
* 1 hates ice 


Im a little confused, the data suggests that 21 people voted,
9 like chocolate
8 like ...
...
...

or in your poll one person can chose multiple options?

---

### Post by kknd on 2010-06-16
Since it's a multiple choice poll, I think your way is more adequate.

---

### Post by trent.josephsen on 2010-06-16
> **Krupski said:**
> Now, imagine that 10 PEOPLE voted and they voted like this:

* 9 like chocolate
* 8 like vanilla
* 3 like strawberry
* 1 hates ice cream

This data tells me that 90% of the voters like chocolate, 80% vanilla and 30% strawberry. It also tells me that 30% like all 3 flavors, 80% like only vanilla and chocolate and 90% like ONLY chocolate.
Only if all the people who like strawberry also like vanilla, and all the people who like vanilla also like chocolate.  Personally, I like strawberry and vanilla, but not chocolate.

If you want to visualize these kinds of relationships, a bar graph won't cut it; you need a Venn diagram or similar.

> So, which "way" is right? My way, or the "stock" way the board does it?

The numbers the board gives you are not meaningful.  Consider the implications.  43 percent of what?  The obscure and unhelpful answer is "43 percent of total votes".  This means that people like me who like only two types of ice cream are counted twice, while people who like all three are counted three times, and people who don't like ice cream are counted only once.

Your way makes intuitive sense, but I suppose there's probably some corner case where it might be useful to consider the percent of total votes.  I've been trying to come up with one unsuccessfully.

---

### Post by Queue29 on 2010-06-16
> **trent.josephsen said:**
> 

If you want to visualize these kinds of relationships, a bar graph won't cut it; you need a Venn diagram or similar.



Not to mention people can probably vote for "I like Vanilla" and "I hate Ice Cream" at the same time. 

Anyway this is a pretty simple case of unionized summation versus intersect summation, neither of which can be well represented by a bar graph unless you show *all* possible combinations and their respective percentages. Which means:

% People who like only Chocolate
% People who like only Vanilla
% People who like only Strawberry 
% People who like Chocolate and Vanilla
% People who like Chocolate and Strawberry
% People who like Vanilla and Strawberry
% People who like Chocolate, Vanilla, and Strawberry
% People who Don't like ice cream
% People who Don't like ice cream and like Chocolate
% People Who Don't like ice cream and like Strawberry
% People Who Don't like ice cream and like Vanilla
% People Who Don't like ice cream and like Chocolate and Vanilla
% People Who Don't like ice cream and like Chocolate and Strawberry
% People Who Don't like ice cream and like Vanilla and Strawberry

---

### Post by DanielWaterworth on 2010-06-16
Another interesting way of visualisation is to find trends like 'people who like chocolate are also likely to like vanilla'. It's just basic statistics to find them.

---

### Post by Bachstelze on 2010-06-16
No way is right or wronG. That's what's nice with statistics: you can make them say pretty much whatever you want, depending on how you formulate them.

---

### Post by DanielWaterworth on 2010-06-16
> **Bachstelze said:**
> No way is right or wronG.

Statistics is wrong. You know 80% of statistics are made up and another 40% are impossible.

---

### Post by Lux Perpetua on 2010-06-17
> **Krupski said:**
> 
So, which "way" is right? My way, or the "stock" way the board does it?

Thanks for any input!

-- RogerYour way is sensible, and the other way is moronic. (Your percentages actually mean something.)

---

