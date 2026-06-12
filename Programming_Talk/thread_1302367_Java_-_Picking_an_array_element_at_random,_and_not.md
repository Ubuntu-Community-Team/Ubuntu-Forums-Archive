---
title: "Java - Picking an array element at random, and not repeating (through 50 elements)"
date: 2009-10-27
forum: Programming Talk
---

### Post by lazypeterson on 2009-10-27
I'm working on a basic game where the user is given a U.S. state and then is asked to identify the capital (via a text box).

Right now, I've got it to where it will pick a state at random and tell you if you've guessed correctly or not. However, many states will repeat before going through all fifty.

As a beginning programmer, I'm a little bit stumped. I was thinking, perhaps I could go through the list randomly, add each array number that's already been hit to a whole other array... and then compare each randomly chosen element in the array with the numbers in the new array beforehand to make sure the state has not been done. That sounds a little overkill to me, I can't help but feel there's an easier way to do this.

I searched around for some algorithms relating to this with no luck. Any help would be greatly appreciated!!!!

---

### Post by Dark_Stang on 2009-10-27
It would be easier to do a linked list and just remove that state from the list after it has been guessed correctly.

---

### Post by NovaAesa on 2009-10-27
What I would do, is randomly permutate the array using the Fisher-Yates algorithm, then just go through the array in a linear fashion.

[http://en.wikipedia.org/wiki/Fisher&#8211;Yates_shuffle](http://en.wikipedia.org/wiki/Fisher&#8211;Yates_shuffle)

Easy!

---

### Post by Arndt on 2009-10-27
> **lazypeterson said:**
> I'm working on a basic game where the user is given a U.S. state and then is asked to identify the capital (via a text box).

Right now, I've got it to where it will pick a state at random and tell you if you've guessed correctly or not. However, many states will repeat before going through all fifty.

As a beginning programmer, I'm a little bit stumped. I was thinking, perhaps I could go through the list randomly, add each array number that's already been hit to a whole other array... and then compare each randomly chosen element in the array with the numbers in the new array beforehand to make sure the state has not been done. That sounds a little overkill to me, I can't help but feel there's an easier way to do this.

I searched around for some algorithms relating to this with no luck. Any help would be greatly appreciated!!!!

If rearranging the array is not a problem, you can do it like this: get a random number i between 1 and N, pick state i, do something with it, then exchange state N and i. Set N = N-1. Do again until N == 0.

---

### Post by kavon89 on 2009-10-27
Use an [ArrayList]("http://www.j2ee.me/javase/6/docs/api/java/util/ArrayList.html"). Remove the state that is chosen [make sure you use the list's current size for the nextInt() in your loop], or use two of them and add the state to the other list while removing it from the other if you need to use the chosen states for something else.

---

### Post by unknownPoster on 2009-10-27
> **NovaAesa said:**
> What I would do, is randomly permutate the array using the Fisher-Yates algorithm, then just go through the array in a linear fashion.

[http://en.wikipedia.org/wiki/Fisher–Yates_shuffle]("http://en.wikipedia.org/wiki/Fisher%E2%80%93Yates_shuffle")

Easy!

I really like this approach, especially because of the O(n) complexity. 

/me is an algorithms geek.

---

