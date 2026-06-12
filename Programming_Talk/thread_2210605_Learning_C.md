---
title: "Learning C"
date: 2014-03-11
forum: Programming Talk
---

### Post by Toliot on 2014-03-11
I'm back ubuntu!

I'd like this post to serve as my ongoing struggles within the realm of linux.
That being said I'd like to go over why I've jumped back into Ubuntu linux(having the dual-boot up for years now, jumping on ubuntu only now with this goal in mind), I want to learn C,
rather I should say I want to learn to program, and become a proficient software developper and one day hopefully be making my own OS or helping in the open-source community of Ubuntu,

This is going to be a rather dull question but what sources would you guys recommend I use to become an effective programmer in C? Also what can I expect to learn from these sources?
Any other recommendations you guys can make regarding programming would be great too

I've jumped into learning C the hard way just because I feel like I can handle a more advanced approach to this realm of programming because I have some foundation in "scripting" languages like python and ruby, this being said I would assume that I know general programming methodology but nothing substantially intricate.

I'm going to continue with "learning c the hard way" for now until I recieve some other recommendations(even encouragement with this source would be highly appreciated, as I'm only on the 5th lesson and don't know what's to come) and customize this beautiful OS to my liking!

I look forward to reconnecting with the community and I apoligize for any typos I might have in advance.

---

### Post by lisati on 2014-03-11
*Thread moved to **Programming Talk**.*

---

### Post by Bachstelze on 2014-03-11
I suppose one has to start somewhere, but be advised that "making your own OS" is a very long shot from where you seem to be now. Being a good programmer is necessary but very very far from sufficient to make even the most rudimentary of OSes.

As for learning C specifically, I don't know "Learn C the hard way", but it's probably as good as anything else. If it has exercises, make sure you do all of them and do them seriously (don't hesitate to post your answers here for comments). If it doesn't, or has too few, get a copy of the canonical book by Kernighan and Richie, and do the exercises there. I can't speak for other programming languages, but learning C is a lot like learning a "human" language. There is no exhaustive list of what to do and what not to do in any given situation, so you have to develop sufficient familiarity with the language to be able to instinctively do The Right Thing™ to accomplish a given task, because in C more than in other languages, mistakes can be catastrophic and have more serious consequences than a mere misunderstanding (or program crash).

---

### Post by agszepp on 2014-03-11
Besides The C Programming Language by Kernighan and Ritchie, another very good book is C Programming: A Modern Approach. It explains everything very well, and there are lots of exercises that help you to apply what you have learned.

---

### Post by trent.josephsen on 2014-03-12
I looked through Learn C the Hard Way, and it seems ok. It takes an editorial tone in places that I feel it should lose. The bit at the end where the author castigates K&R for defining functions that don't terminate in certain conditions seems pretty hypocritical given that his code is absolutely riddled with functions that don't check bounds or test against NULL. I'll cut him some slack and imagine that before publication he's planning to go back and change all the %s specifiers in his printf calls.

Overall, for learning C, it's probably no worse than K&R, which (whatever Zed may say) is still the gold standard by which all other books are measured. Better, maybe, for people with not so much programming experience (K&R was written largely for Pascal and FORTRAN programmers).

---

### Post by Toliot on 2014-03-12
Thanks for all the replies guys! 

> **Bachstelze said:**
> 
As for learning C specifically, I don't know "Learn C the hard way", but it's probably as good as anything else. If it has exercises, make sure you do all of them and do them seriously (don't hesitate to post your answers here for comments). If it doesn't, or has too few, get a copy of the canonical book by Kernighan and Richie, and do the exercises there. I can't speak for other programming languages, but learning C is a lot like learning a "human" language. There is no exhaustive list of what to do and what not to do in any given situation, so you have to develop sufficient familiarity with the language to be able to instinctively do The Right Thing&#8482; to accomplish a given task, because in C more than in other languages, mistakes can be catastrophic and have more serious consequences than a mere misunderstanding (or program crash).

What I was referring to when I said make my own OS, I meant as a final goal, like its been a dream of mine since a young age (or that might have just been the night I saw diehard) either way I would love to eventually have that much knowledge about all this stuff. Anyways the guide itself "learn C the hardway" says it would teach me basics of kernel/I don't remember what else, but that stuff sounds like it would be pretty close to the OS/layer no ?
If I'm going hard-copy route(which I'm trying to avoid as I'm trying to save the planet/not spend much $) I'm considering that exact book, it's been recommended by quite a few sources already.

In regards to what the last guy said, can you please clarify what you mean? Is there a more... effective way to call variables from the printf function (I'm so sorry if I used the wrong terminology right there, coming from ruby/python and even there it has been years since I touched that craft). Anything you guys tell me now will probably assist me greatly down the line so I don't make the wrong habits early.

In the recent future my friends from university want to make some accounting program over the summer break, do you guys think that would be a more feasable goal? (trying to not deviate from C since I'm trying to learn the language in the process/more about computaaar).

I apoligize for the long post but I'm basically flying solo in this field of endless sources of information, I just need to know what feeds to focus on, if that makes sense. I looked at the stickies here on C and wondering if you guys can say anything good about : [http://www.paulgriffiths.net/program/c/](http://www.paulgriffiths.net/program/c/) , [http://www.faqs.org/faqs/C-faq/faq/](http://www.faqs.org/faqs/C-faq/faq/) .

If i'm not wrong I think some guy might have actly recommended the griffiths stuff, ^^ if you did, sorry I've been writing this post for like 5 minutes already, for now those 3 sources (2 above and learncthhway) should suffice right?

Anyways I just want to re-iterate that it's a blessing to be back in this community, forgot how awesome linux is, and the people that help keep it alive.

Oh yeah final question, is there a point in deviating from gedit at my current "knowledge" base of C(which is none basically)? I'm hesitant but all the IDE's look so enticing/awesome... 
<3<3

---

### Post by King Dude on 2014-03-12
I suggest checking out "C Programming for Dummies" from your local library and taking a C programming class at a community college, using the book as a reference. Also, I suggest acquiring the [Code::Blocks IDE]("http://www.codeblocks.org/") and the [GNU Compiler Collection (GCC)]("http://gcc.gnu.org/").

---

### Post by trent.josephsen on 2014-03-12
> **Toliot said:**
> [C]an you please clarify what you mean? Is there a more... effective way to call variables from the printf function (I'm so sorry if I used the wrong terminology right there, coming from ruby/python and even there it has been years since I touched that craft). Anything you guys tell me now will probably assist me greatly down the line so I don't make the wrong habits early.

Nah, it's just that the author doesn't apply his criticisms of K&R to his own code. Specifically,

```
printf("%s", foo);
```
has undefined behavior if foo is NULL or points to an unterminated string, so (for example) his function (taken from chapter 47)
```
bstring read_line(const char *prompt)
{
    printf("%s", prompt);

    bstring result = bgets((bNgetc)fgetc, stdin, '\n');
    check_debug(result != NULL, "stdin closed.");

    check(btrimws(result) == BSTR_OK, "Failed to trim.");

    return result;

error:
    return NULL;
}
```
is just as incorrect and defective as the K&R 'copy' function he criticizes in the final chapter, and for the same reasons. (I therefore find it ironic and amusing that this function is basically meant to be a "safer" wrapper around fgets.) He uses %s everywhere without checking bounds, so the suggestion that he should go back and change it everywhere was just me being snide.

(For your enlightenment, if you have a string that might be unterminated and you want to print it without overstepping bounds, this is how you do it:
```
printf("%.*s", MAX_STRING, s);
```
where MAX_STRING is the longest the array s can be. Usually this isn't necessary.)

[quote=King Dude]I suggest checking out "C Programming for Dummies" from your local library and taking a C programming class at a community college, using the book as a reference.[/quote]

Really? I mean, I have nothing against the book, but it has fairly lukewarm reviews and I'm not sure why you'd suggest it over... well, any one of a thousand mediocre C books out there. What do you like about it?

---

### Post by Toliot on 2014-03-12
> **trent.josephsen said:**
> 
Really? I mean, I have nothing against the book, but it has fairly lukewarm reviews and I'm not sure why you'd suggest it over... well, any one of a thousand mediocre C books out there. What do you like about it?

As am I interested in understanding the plus of "for dummies" books in general. I have "Islam for dummies" and "Calculus for dummies" just collecting dust under a mountain of other more informative books (about similar topics and otherwise).

Can someone give me a quick pointer on the difference between these two print statements? 

```
	printf("The size of an int: %u\n", sizeof(int));
```

```
     printf("The size of an int: %ld\n", sizeof(int));
```

I understand that %ld and %u call different stuff but in the guide I'm following they say to use one over the other since they are calling unsigned int's (does this simply mean that the variable(INT) is declared but not assigned a value or that it's not declared+no value), like with all my posts I apoligize if I look like a retard(and will man the printf function worst comes to worst)

Thanks a lot for the input guys!

---

### Post by trent.josephsen on 2014-03-12
"unsigned" means that a type can only hold nonnegative values. A "regular" or signed int can hold (at least) any integer from -32768 to +32767, but an unsigned int can hold the integers from 0 to (at least) 65536. (These are minimum ranges; real implementations normally have much broader ones.) The other unsigned types (unsigned short, unsigned long, etc.) have similar properties.

The sizeof operator yields a value of type size_t, which is an unsigned type and probably an alias (typedef) for one of the following: unsigned short, unsigned int, unsigned long, or unsigned long long. The C89 standard didn't provide a printf specifier capable of unambiguously converting a size_t, so before C99 corrected that oversight, you had to either cast it to unsigned long or know which type it really was in order to print it with printf. Neither of those printf calls is portable. The %u specifier says "treat this argument as an unsigned int", which will work if size_t is a typedef for unsigned int, but may fail if it's a typedef for some other type. The %ld specifier says "treat this as a **signed** long", which will likely work if size_t is a typedef for unsigned long, but may fail for values larger than LONG_MAX or if size_t is a typedef for an unsigned type of a different size. (I don't know why anyone would use %ld instead of %lu -- mere carelessness, perhaps.)

The upshot of this is that neither %u nor %ld is the appropriate specifier for a size_t; use %zu, which is in C99 and always works no matter what size_t is a typedef for.

---

### Post by Toliot on 2014-03-13
Thanks trent ! :D I wish there was thumbs up on this forum, everyone would probably have 1000's 

btw what's benefit of using net-beans/code::blocks or emacs(what is exactly functionality apart from being "IDE")

---

