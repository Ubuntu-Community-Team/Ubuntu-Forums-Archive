---
title: "How to do a particular thing in C ??"
date: 2011-10-03
forum: Programming Talk
---

### Post by ClientAlive on 2011-10-03
Hi,

We worked with switch statements for our class project for this week. We did a program for the Christmas song The 12 Days of Christmas. If you remember how that song goes, it repeats lines over and over as it builds on itself each following day. So the program using switch statement alone required a lot of redundant content. I wrote the program the way we were instructed, and that is what I'll turn in. I did want to try an idea I had on the side though. That's where I was hoping you would help.

Attached is the program I wrote for class so you can see what I'm talking about, if you like. The other version on the side I would like to try would require a list of variables, all uniquely labeled, and to be able to insert that into my printf line so I can reuse it throughout. This is what I'm not sure how to do exactly.

So, for instance, there is a line: "On the X day of christmas my true love gave to me . . ."

and I'd like to insert the words: "first, second, third . . . twelfth" into the "X" in the line so I can just make a list of the days: "first, second, third . . . twelfth" and not write it in each time.

That part isn't as big of a deal, but the lines in the verse that follow that one are. I just used that for the example because it was easy. I think the same concept should work for the line for each of the days too. Doing it like that should make for a lot smaller program I think. A neater one.

Can anyone help me with how to do that concept in C? Or at least what it is called so I can look it up?
------------------

Edit:

Maybe not for you, but when I reread that it looks really confusing. All I was trying to say is to be able to assign some unique . . . errr . . . thing, to each line of the song and then call on that unique 'thing' within my printf statement. To be able to have more than one in my printf statement where needed (as the song progresses).

Thanks

---

### Post by lisati on 2011-10-03
*Thread moved to **Programming Talk**.*

---

### Post by slavik on 2011-10-03
very terrible ... sounds like an intro course :)

There are two ways that you can do this.

some hints:
1. learn about arrays and how you can use them for that.
2. learn how switch statements work without the break in the case.

---

### Post by ClientAlive on 2011-10-03
> **slavik said:**
> very terrible ... sounds like an intro course :)

There are two ways that you can do this.

some hints:
1. learn about arrays and how you can use them for that.
2. learn how switch statements work without the break in the case.


Yeah, it is an intro course. CSC 150, Computer Science I. Extremely slow paced and simple. Leaves me longing for more.

We did look at an example where you omit the break in the case but I guess I never though about how that might work for this. I'll have to ponder that for a minute.

Thanks for the tips. I'll google on those things and see what I come up with.

:D

---

### Post by ve4cib on 2011-10-03
Other options would be to write a "printGifts(int n)" function that prints out the gifts for one day.  For example, printGifts(4) would print "Four Mockingbirds\n".

Then you can call that function inside a loop:

```

for(int day=1; day<=12; day++)
{
    printf("For the %nth day of Christmas my true love gave to me:\n",day);
    for(int gifts=day; gifts>=1; gifts--)
    {
        printGifts(gifts);
    }
}

...

void printGifts(int n)
{
    switch(n)
    {
    case 1:
        printf("A partridge in a pear tree\n");
        break;
    case 2:
        printf("Two turtle doves\n");
        break;
    ...
    }
}

```

You could also use recursion if you really wanted, though that is probably not necessary.

Personally I think Slavik's suggestion of using a switch without breaks is probably the best solution to this particular problem though.

---

### Post by ClientAlive on 2011-10-03
> **ve4cib said:**
> Other options would be to write a "printGifts(int n)" function that prints out the gifts for one day.  For example, printGifts(4) would print "Four Mockingbirds\n".

Then you can call that function inside a loop:

```

for(int day=1; day<=12; day++)
{
    printf("For the %nth day of Christmas my true love gave to me:\n",day);
    for(int gifts=day; gifts>=1; gifts--)
    {
        printGifts(gifts);
    }
}

...

void printGifts(int n)
{
    switch(n)
    {
    case 1:
        printf("A partridge in a pear tree\n");
        break;
    case 2:
        printf("Two turtle doves\n");
        break;
    ...
    }
}

```

You could also use recursion if you really wanted, though that is probably not necessary.

Personally I think Slavik's suggestion of using a switch without breaks is probably the best solution to this particular problem though.


Whoa . . .  That's wAyyy beyond anything I've ever seen before. I can sort of, barely, follow it, kinda.  :)

I keep thinking about the things we've learned so far and they seem to have some common element in them; but, that element seems to be backwards of what I was thinking I'd want to do.

We've learned different ways of having the user's input be assigned to the variable's value then use a printf statement to print out whatever you want to have as a response to that input. I don't think that anything like that would work for what I was thinking about.

The problem is I'm having a bit of a difficult time conceptualizing the logic behind what I was hoping to do (if that makes any sense). I guess I was trying to label the lines then call on the label and have the line printed out. Just that alone though doesn't solve the problem of user interaction. I mean, just that wouldn't include it.

The more I try to think about the logic behind something like that the more complex it seems it would be. At first I though it was a very simple idea (maybe it is and I just don't know). You would have to have the user's input control how the printf (or whatever equivalent) was assembled. It seems this involves at least one level of abstraction (I hope I said that right. I just made it up cause' I don't know what else to call it)

 When I think about what we've been learning several things come to mind. Things like "one directional" (the user enters something and the program does one, single thing based on that, then it's game over. If what I was asking about involves as complex of logic as I think it does I might have a while before I get there.  :(
--------------------

Edit:

One thing is for sure. This song is a rich learning tool for all kinds of programming concepts (so it seems).

---

### Post by ClientAlive on 2011-10-03
Well, wait a minute. If a person just removed the breaks would the users input stop before reaching the end, no matter what they put in? I mean, wouldn't it just print out all the cases without stopping, even if the user put in a lower number? But if there was a way to make it so it did stop based on the number the user puts in . . .

So, for instance, if the user input is 3 it prints case 1, case 2, case 3 and then stops. If the user puts in 4 it prints case 1, case 2, case 3, case 4 then stops. And so on. We didn't look at omitting the break in that context though. I'll have to see if I can find something on the internet that explains it a little better.

---

### Post by ClientAlive on 2011-10-03
What if I did something like what's in the attachment here? But it doesn't address the ordinal words in the line. That's another thing and I didn't try to address that yet. What do you think?
-----------------

Edit:

Or maybe what's in the second one is better?

---

### Post by trent.josephsen on 2011-10-03
I don't want to do your homework for you, but maybe it will help if I observe two things:

1_ Twelve Days of Christmas has twelve verses.  The first one starts with a partridge and a pear tree; the last one starts with twelve drummers drumming.  All 12 verses include a partridge.  Eleven verses include two turtle doves.  Only ten verses include three French hens, and so on down the line.  It may help to write out the entire song longhand, and pay attention to the procedure you follow in your head to determine what the next line is.

2_ The numbers in sequential case labels don't have to be in ascending order.

In general, switch statements are tricky beasts to think about (especially with more than a few cases), and you shouldn't feel stupid or frustrated if you can't come up with the solution quickly.

---

### Post by ClientAlive on 2011-10-03
> **trent.josephsen said:**
> I don't want to do your homework for you, but maybe it will help if I observe two things:

1_ Twelve Days of Christmas has twelve verses.  The first one starts with a partridge and a pear tree; the last one starts with twelve drummers drumming.  All 12 verses include a partridge.  Eleven verses include two turtle doves.  Only ten verses include three French hens, and so on down the line.  It may help to write out the entire song longhand, and pay attention to the procedure you follow in your head to determine what the next line is.

2_ The numbers in sequential case labels don't have to be in ascending order.

In general, switch statements are tricky beasts to think about (especially with more than a few cases), and you shouldn't feel stupid or frustrated if you can't come up with the solution quickly.


Thanks trent.josephsen. Yeah, well it started out as our assignment and I did the assignment using the only knowledge of C we've learned before. That resulted in a solution with a tremendous amount of redundancy, a much larger file than I think necessary; and, probably, requires 10 times the overhead to run than it should. I know, it's such a tiny program that 'overhead' probably is not something to even think about. Just that things like that might be good to start thinking about and learning about early.

So, I got this brite idea I'd take it to another level on my own. Just for funzies, you know? Well it seemed like a simple idea. I could almost picture it in my head. Then when it came to figuring out the logic necessary to match the idea things got extremely complicates extremely fast. Whoa! I just didn't think there would be so much to it.

Now, granted, I'm only about 4 weeks into programming - ever in my life. I imagine my mind isn't much trained for coming up with the kind of logical patterns involved in programming. I'll probably mess around with this little side thing (the song program) here and there. I know what I think would be an elegant solution, and I could describe it in human terms, just don't know how to implement it since I haven't learned much yet. Well, thanks though. If I figure something out I'll attach it to a post here just for the heck of it.

:)

---

