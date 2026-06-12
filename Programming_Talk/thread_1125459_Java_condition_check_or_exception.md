---
title: "Java: condition check or exception?"
date: 2009-04-14
forum: Programming Talk
---

### Post by Habbit on 2009-04-14
Hi there fellow programmers. I've been working on some graphing code in Java to draw graphs like this one: [en.wp:Spanish Congress of Deputies after 2008 election.png]("http://en.wikipedia.org/wiki/File:Spanish_Congress_of_Deputies_after_2008_election.png"). I'm currently walking in circles over a design decision on the code that decides which party gets each seat in the chart: the rows that my algorithm will "allow" (in order to maintain continuity) might all be full because the algorithm is positioning a party with just a few seats near the logical "end" of the chart. In that case, I want to allow all rows to be selected.

The decision I have to make is: do I introduce an "if" within the loop, thus penalizing all iterations (one per seat, so potentially hundreds) just for the sake of the last few seats, or would I be better off considering that case an exception and thus handling it with try/catch?

Perhaps some code will help see my status: ```
        for (ResultPaintInfo curRes : results) { // Once per party
            boolean firstSeat = true;
            Arrays.fill(allowedRows, false);
            Arrays.fill(curparty_seats, (short)0);
            
            for(short party_remSeats = curRes.getSeats()
                    ; party_remSeats > 0; --party_remSeats) { // Once per seat
---->           int row = dPS_minloc(usedArc_next, allowedRows, !firstSeat);
---->           if (row < 0)    // TODO: No row was allowed (nearly full graph!)
---->               throw new IllegalStateException();
                // ...
                if (row > 0)
                    allowedRows[row-1] = rows_remSeats[row-1] > 0;
                allowedRows[row] = rows_remSeats[row] > 0;
                if (row + 1 < rows.length)
                    allowedRows[row+1] = rows_remSeats[row+1] > 0;
                firstSeat = false;
            }
            // ...
        }
```The condition I want to control is detected by dPS_minloc, a private static function in the same class, so the question stands: should dPS_minloc signal a failure to find a suitable row with a -1 like it does currently (thus forcing this code to use an "if" within the per-seat loop), or should it raise some exception that I can catch from inside the loop? I'm currently inclined towards the latter, but it seems "unclean" from the point-of-view of the normal use of exceptions.

---

### Post by simeon87 on 2009-04-14
> **Habbit said:**
> The condition I want to control is detected by dPS_minloc, a private static function in the same class, so the question stands: should dPS_minloc signal a failure to find a suitable row with a -1 like it does currently (thus forcing this code to use an "if" within the per-seat loop), or should it raise some exception that I can catch from inside the loop? I'm currently inclined towards the latter, but it seems "unclean" from the point-of-view of the normal use of exceptions.

Exceptions should only be used for error conditions that the application can possibly recover from elsewhere; they should not be used for structuring the 'normal' control flow. The -1 as 'failure' is acceptable as long as the documentation describes it.

For example, a function that searches for a substring in another string can either return the index (>= 0) of the substring but it can also return -1 which indicates 'not found'. Throwing an exception would be wrong because no error has actually occurred, the string just wasn't in the other string.

---

### Post by Habbit on 2009-04-14
> **simeon87 said:**
> Exceptions should only be used for error conditions that the application can possibly recover from elsewhere; they should not be used for structuring the 'normal' control flow. The -1 as 'failure' is acceptable as long as the documentation describes it.

For example, a function that searches for a substring in another string can either return the index (>= 0) of the substring but it can also return -1 which indicates 'not found'. Throwing an exception would be wrong because no error has actually occurred, the string just wasn't in the other string.

Hmm.. I may have not explained myself too well... There will be "no doc" on this part of the code because it is strictly private to my class (not even protected), I just found it better to have some particular code sliced off to a helper function "dPS_minloc". Thus, the fact that throwing an exception from it is "unclean" is not relevant to my design because that exception will never be "leaked" into the public/protected area. I'm just asking whether using the exception mechanism for that kind of flow control within a loop will perform better than explicit flow control ("if"), given that the probability of the "exceptional condition" actually occurring is around 1%.

---

### Post by CptPicard on 2009-04-14
Erm... and you know that this place is a some kind of bottleneck? It doesn't seem like there is a reason to assume it is. Premature optimization?

The fact that you're dealing with internal, localized code just makes it even less reasonable to use an exception for what really is a flow control issue. Exceptions are not flow control, but non-local error/exceptional condition reporting, tools.

And to answer the (I guess pointless) performance issue -- if an if branch was slower than an exception, we'd probably see all extremely optimized code use nothing but exception handlers... but we do not ;)

---

### Post by Arndt on 2009-04-14
> **CptPicard said:**
> Erm... and you know that this place is a some kind of bottleneck? It doesn't seem like there is a reason to assume it is. Premature optimization?

The fact that you're dealing with internal, localized code just makes it even less reasonable to use an exception for what really is a flow control issue. Exceptions are not flow control, but non-local error/exceptional condition reporting, tools.

And to answer the (I guess pointless) performance issue -- if an if branch was slower than an exception, we'd probably see all extremely optimized code use nothing but exception handlers... but we do not ;)

I may be misunderstanding something, but isn't it a multi-level break which the OP wants? It breaks out to a label.

If that doesn't work (but I think it does, in Java), one can add a flag which is tested in the 'for' statements - the effect on execution time is surely negligible. An exception costs much more.

---

### Post by Habbit on 2009-04-14
Decision implemented! Thanks to everybody for your input. The final code uses a simple "if" and collapses the also special "first seat" case with the "graph is full" case. This has also allowed me to simplify dPS_minloc. ```
            for (/* ... */) {
                int row = dPS_minloc(usedArc_next, allowedRows);
                if (row < 0) {
                    // No row was allowed: either this is the first seat
                    // of this party, or the graph is nearly full and the
                    // new seat cannot be contiguous to an old one
                    row = dPS_minloc(usedArc_next, null);
                    if (row < 0)    // Now _this_ should not happen!
                        throw new IllegalArgumentException("Insufficient space in graph");
                }
                // ...
            }
```

Edit: BTW, how do I mark the thread as "solved"?

---

### Post by kjohansen on 2009-04-14
marking a thread solved was heavy on the server and has been disabled.

on a side note: I had a class project to efficiently solve the kevin bacon number problem.  the fastest java solutions from the class used exceptions instead of if statements to check if a node was in a hash list. so it may be bad design, but is probably faster...

---

### Post by Habbit on 2009-04-14
> **kjohansen said:**
> the fastest java solutions from the class used exceptions instead of if statements to check if a node was in a hash list. so it may be bad design, but is probably faster...

So the JITer does have a way to cue the processor that a certain branch is much less likely than the other. Well, I guess that in my particular case, where the exceptional case is about 1% probable, the time spent in constructing the exception object and unwinding the stack would be worse than the "if" branching overhead.

---

