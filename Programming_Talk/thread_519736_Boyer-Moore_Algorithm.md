---
title: "Boyer-Moore Algorithm"
date: 2007-08-07
forum: Programming Talk
---

### Post by Lster on 2007-08-07
Hi all

I have been playing around with string searching algorithms. I've programmed a naive-search algorithm and it actually seems pretty fast to me.

However I really wanna program the Boyer-Moore algo' as this is supposed to be fast. I understand about it counting backwards so it can move forwards and I understand the first table. What is the second table though? - this I really don't get. I understand that the needle is shifted on the maximum of table 1 and table 2.

Is the Boyer&#8211;Moore&#8211;Horspool algo' simply the Boyer-Moore Algorithm without the second table? Also, how does it compare with other algorithms like Bitap and Knuth&#8211;Morris&#8211;Pratt algo's.

Thank you,
Lster

PS: Please correct me if I have got anything wrong...

---

### Post by Lster on 2007-08-07
*Bump*

---

### Post by Soybean on 2007-08-07
> **Lster said:**
> However I really wanna program the Boyer-Moore algo' as this is supposed to be fast. I understand about it counting backwards so it can move forwards and I understand the first table. What is the second table though? - this I really don't get. I understand that the needle is shifted on the maximum of table 1 and table 2.
I assume you've looked at the wikipedia entry? That's what I'm going by, and I'm going to refer to its example. ([http://en.wikipedia.org/wiki/Boyer-Moore_string_search_algorithm](http://en.wikipedia.org/wiki/Boyer-Moore_string_search_algorithm))

In the example, the search pattern is "ANPANMAN".

After preparing the tables, the first thing you do is check the 8th character in the text. There are 3 possibilities to consider:
1) It's a character that doesn't occur in the search pattern at all, such as "X". In this case, jump ahead 8 more characters.
2) It's a character that does occur in the search pattern, but it's not "N". Let's use "P". In this case, go to the first table to see how far to jump. For "P", it's 5 characters.
3) It is "N", the last character in the search pattern. Now you need to start stepping backwards to see if the whole word matches. If it's a *partial* match, how much do you jump ahead by? Without the second table, the answer is to check the first table and jump from the spot where the mismatch occurred. For example, in the string "....PMAN.X...Y.", using only the first table, you would match "N", "A", "M", then find that "P" wasn't a match. Without the second table, you can't take advantage of the fact that you've just checked those characters, so the best you can do is use the first table and jump 5 characters ahead from the "P" (next test would be at the "X"). With the second table, you can see that what you just tested was "MAN" preceded by "not N", so you can jump 6 characters from the "N" -- the next test would be at the "Y". Note especially the different jump points: in the first case, you jump from where the mismatch occurred, while in the second you jump from the first character you tested (the end of the partial match). 

Does that help at all? I'm not always the best at explaining things. ;)

> Is the Boyer–Moore–Horspool algo' simply the Boyer-Moore Algorithm without the second table?
Yes. Easier to implement and explain, but slower-running.
> Also, how does it compare with other algorithms like Bitap and Knuth–Morris–Pratt algo's.
KMP and Boyer-Moore are similar: both linear-time. Boyer-Moore has an extremely fast best case time, but I believe KMP has a better worst-case. I think Bitap is hard to compare; it looks like the benefits of Bitap come from it mapping well to low-level functions, rather than from being a particularly fast algorithm.

I would *guess* (note that this is only a guess, and not even a particularly educated one) that on a theoretical level, the three would rate:
1) KMP
2) Boyer-Moore
3) Bitap
While in practice, it might well be the exact opposite... depending on a lot of things. Especially if you want a fuzzy search. I'm not sure if the other two can be adapted for fuzzy searching, but Bitap definitely can.

---

### Post by Lster on 2007-08-07
> I assume you've looked at the wikipedia entry? That's what I'm going by, and I'm going to refer to its example. ([http://en.wikipedia.org/wiki/Boyer-M...arch_algorithm](http://en.wikipedia.org/wiki/Boyer-M...arch_algorithm))

Yeah - I have. I found it a little confusing, though.

> After preparing the tables, the first thing you do is check the 8th character in the text. There are 3 possibilities to consider:
1) It's a character that doesn't occur in the search pattern at all, such as "X". In this case, jump ahead 8 more characters.
2) It's a character that does occur in the search pattern, but it's not "N". Let's use "P". In this case, go to the first table to see how far to jump. For "P", it's 5 characters.

I'm fine with this.

> 3) It is "N", the last character in the search pattern. Now you need to start stepping backwards to see if the whole word matches. If it's a partial match, how much do you jump ahead by? Without the second table, the answer is to check the first table and jump from the spot where the mismatch occurred. For example, in the string "....PMAN.X...Y.", using only the first table, you would match "N", "A", "M", then find that "P" wasn't a match. Without the second table, you can't take advantage of the fact that you've just checked those characters, so the best you can do is use the first table and jump 5 characters ahead from the "P" (next test would be at the "X"). With the second table, you can see that what you just tested was "MAN" preceded by "not N", so you can jump 6 characters from the "N" -- the next test would be at the "Y". Note especially the different jump points: in the first case, you jump from where the mismatch occurred, while in the second you jump from the first character you tested (the end of the partial match).


...

Am I correct?

> Does that help at all? I'm not always the best at explaining things. 

YES! Thank you lots!

---

### Post by Soybean on 2007-08-07
> **Lster said:**
> So you are working out how much you would have to shift "MAN" back (in "ANPANMAN") to find another instance, which is impossible. So we move back:

8 - 3 + 1

8 being the length; 3 the last correct characters and 1 is a constant increase. Am I correct?
Oh, sorry, I knew I was leaving something out! What you're actually doing there is shifting over 6 places because that's the closest that an instance of "ANPANMAN" could possibly begin... because the "AN" in "PM**AN**" could be the beginning of a new "**AN**PANMAN".

If you look at the second table again in the wikipedia entry, you can probably work out why each entry has the value it does... and they have some example code that includes creating such a table, but unfortunately they mention repeatedly that that part of the code is bad. ;) 

But basically, the second table is a list of all possible suffixes, along with a value that can be described as, "if this much of the string matches (but no more), then the soonest possible occurrence of the search pattern is ___ jumps away." If your search pattern has no repeating characters, then all the values will be the length of the pattern. But if there are repeating characters or patterns in your search pattern, the second table can help make bigger jumps.

---

### Post by Lster on 2007-08-08
I understand now. Brilliant - thank you so much for your help.
Lster

---

