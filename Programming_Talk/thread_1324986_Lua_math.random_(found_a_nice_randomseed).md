---
title: "Lua math.random (found a nice randomseed)"
date: 2009-11-13
forum: Programming Talk
---

### Post by kumoshk on 2009-11-13
I've long been put out about how there didn't seem to be a way to get a decent randomseed in Lua&#8212;I mean, the system time return didn't have milliseconds (so in my view, the random function wasn't fully functional). I had searched long and hard for a solution, but to no avail.

So, while trying to figure out how to make a network game with LuaSocket, I randomly came across this solution (it requires LuaSocket, by the way):

```
require 'socket'
math.randomseed(socket.gettime()*10000)
print(math.random(100))
```

If you don't multiply it by 10000, it will convert that time into an integer, cutting off the milliseconds, and thus be no better than the regular os.time().

I tried this out and it works fairly well. It's still not perfect as the following code on my 2Ghz dual core AMD Athlon X-2 processor
```
for i=1,20 do math.randomseed(socket.gettime()*10000) print(math.random()) end
```

produced the following result,
```
0.16043688597178
0.16043688597178
0.16043688597178
0.51493899734455
0.51493899734455
0.51493899734455
0.51493899734455
0.51493899734455
0.51493899734455
0.87877474393639
0.87877474393639
0.87877474393639
0.87877474393639
0.87877474393639
0.2350731134578
0.2350731134578
0.2350731134578
0.2350731134578
0.2350731134578
0.2350731134578

```

but it's still a whole lot better, and usable as long as you're not changing the seed faster than my computer can do 3&#8211;6 calculations in Lua 5.1 (64-bit). Keep in mind that the random numbers generated from a single seed shouldn't repeat the same number like this. So, the following code should be perfect for 99% of the programs out there requiring a random function (using a twist on the example above):
```
math.randomseed(socket.gettime()*10000)
for i=1,20 do print(math.random()) end
```

Anyway, I just thought I'd share. Enjoy, and let us know if you find/know a better way.

Note: in the poll up there, don't select Yes if the functionality is great but you just don't want to have to use LuaSocket. It's referring to a better randomseed than the LuaSocket one&#8212;sorry for not specifying these things in the poll.

---

### Post by kumoshk on 2009-11-13
If you want to change the seed very quickly, but not quickly enough for it to repeat itself, you can always do something like this:
```
require 'socket'
for i=1,20 do
    math.randomseed(socket.gettime()*10000)
    print(math.random())
    socket.sleep(1e-400)
end
```
No repeats there. Note that 1e-400 is equivalent to 0.000000000000000000&#8230;0001 (I skipped several zeros.)

---

### Post by kumoshk on 2009-11-13
One alternative to LuaSocket (and any reference to the system time, for that matter) is to use persistent data. I mean, you could use the Pluto library or such to store an integer in a file. You could load that integer when your program starts, increment it every time you want to change seed (using it as the seed) and store the incremented integer back in the file so that you get a different one for sure next time you run the program.

---

