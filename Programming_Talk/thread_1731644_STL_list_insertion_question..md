---
title: "STL list insertion question."
date: 2011-04-17
forum: Programming Talk
---

### Post by Jonas thomas on 2011-04-17
I'm beginning to gain an appreciation of elegance and power of STL container classes..
They're pretty cool..

I'm working on this homework project where I need to maintain a sorted list of auctions.  I overloaded the "<" and "==" operators to take advantage of find and sort algorithms.

I want to use a genertic stl function to directly insert into the correct spot of the sorted list.
I could hard code this and use the insert at the required spot, or attach at the end of the list and sort, but I've got to think this is a common enough issue to have a generic solution.

I've been poking around:
[http://www.cplusplus.com/reference/stl/list/insert/]("http://www.cplusplus.com/reference/stl/list/insert/")
and
algorithms... oh.. this might be it..
[http://www.cplusplus.com/reference/algorithm/find_end/]("http://www.cplusplus.com/reference/algorithm/find_end/")
[Edit... this looks more promising, but has more overhead it think..
[http://www.cplusplus.com/reference/stl/list/merge/]("http://www.cplusplus.com/reference/stl/list/merge/")
I would require putting the auction I want to add into a seperate list and merging. Seems.. like this would work... but comes across to me as  overkill... ]



It looks like they're are many roads to Rome here... Limited amount of time, and I'd like to avoid being hoisted up by my own petards pursuing my curiosity if posible.... (At least we're past the ides of march.) Mind wandering..... back to task at hand.

Is find_end the best way to go, basically find where you want to insert and then insert? Or... is there something more generic like "insert into appropriate spot of sorted list in one shot"?" and I just to do more digging till I figure it out?

---

