---
title: "Possible seeds for srand"
date: 2009-04-22
forum: Programming Talk
---

### Post by geo909 on 2009-04-22
Hello all,

I would really appreciate any help with my problem below:

I am running an algorithm who generates random permutations
(as lists of integers) and checks if they have some certain property.

But I have a problem:

For the creation of these permutations, I use the pair
*srand* and *rand*. I use time for srand:
```
srand( (unsigned int)time( NULL ) );
```

But things go so quickly, that several seeds will be the same.

Is there another way to seed the RNG except from time?


Thanks a lot in advance..

---

### Post by Arndt on 2009-04-22
> **geo909 said:**
> Hello all,

I would really appreciate any help with my problem below:

I am running an algorithm who generates random permutations
(as lists of integers) and checks if they have some certain property.

But I have a problem:

For the creation of these permutations, I use the pair
*srand* and *rand*. I use time for srand:
```
srand( (unsigned int)time( NULL ) );
```

But things go so quickly, that several seeds will be the same.

Is there another way to seed the RNG except from time?


Thanks a lot in advance..

Of course, you can give any number to srand. But maybe you mean, is there another simple source of automatically varying numbers? What programs which need much randomness do is look at all sorts of sources on the computer, disk traffic, file system statistics, time, etc. sshd does this, but I don't know if there is a separate module in the sshd package that can be used generally. There is also a module, the name of which I forget right now, which can be installed in the operating system, and does the same thing.

But in any case, do you mean you use this sequence to get random numbers:

```
srand(time(0));
n1 = rand(100);
srand(time(0));
n2 = rand(100);
srand(time(0));
n3 = rand(100);
```

and so on? If so, stop that at once. You should call srand just once in the program. But perhaps you do mean that the program run takes less than a second so the next run gets the same seed? You could add a one-second delay, I suppose.

---

### Post by bobdob20 on 2009-04-22
You could use /dev/urandom to get random numbers instead.

---

### Post by Arndt on 2009-04-22
> **bobdob20 said:**
> You could use /dev/urandom to get random numbers instead.

That's the module I meant. Maybe it's there from the outset nowadays. Note that you should take the seed from there, then use a good pseudorandom generator.

---

### Post by geo909 on 2009-04-22
Hi, 
Thanks a lot for your reply.

> 
But in any case, do you mean you use this sequence to get random numbers:

```
srand(time(0));
n1 = rand(100);
srand(time(0));
n2 = rand(100);
srand(time(0));
n3 = rand(100);
```

and so on? If so, stop that at once. You should call srand just once in the program


Not literally this, but yes, this is the idea of what I was doing! 

Now that you told me I ran some experiments and I understood the mistake... I see how I can do my work now.

Thanks for clearing things out!


EDIT: I missed the other replies when I wrote that. Thanks to all. It was actually me that was making
a mistake, so I am fine now

---

