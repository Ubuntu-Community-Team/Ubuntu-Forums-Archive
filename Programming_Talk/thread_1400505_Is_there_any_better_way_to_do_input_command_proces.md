---
title: "Is there any better way to do input command processing?"
date: 2010-02-07
forum: Programming Talk
---

### Post by Vunutus on 2010-02-07
Specifically I'm using PHP but this applies to any language really.

In many of my projects I encounter situations where I need to process commands from a user. Each time I end up doing an if/elseif/elseif thing like:

```

if($command == "command1")
{
   //blahblahblah
}
elseif($command == "command2")
{
   //blahblahblah
}
elseif($command == "command3")
{
   //blahblahblah
}

```

My current project has probably 50 or more different commands all set up in a manner similar to this. I can't help but wonder if there is any more elegant or efficient way to do this?

---

### Post by sprouty on 2010-02-07
Whats about a case statment instead?

---

### Post by Ferrat on 2010-02-07
If you have 50 similar stuctures with similar "ifs" you might want to try and break it down and create functions that can handle them all so not to re-create the wheel over and over :)

---

### Post by MasterProg on 2010-02-07
Use [switch]("http://php.net/manual/en/control-structures.switch.php") statement instead.

---

### Post by Vunutus on 2010-02-07
Is there any performance advantage of using a switch statement instead? My understanding is that it's pretty much just a different way of formating a block of if's and elseif's. In my opinion a big block of case statements is harder to read than the bracketed format of if's, but if it's somehow faster I'll gladly switch (no pun intended).

---

### Post by pbrane on 2010-02-07
In C/C++ switch statements are generally faster than if/else constructs. The switch statment will *jump* to the correct case after the initial test. Switch constructs are usually jump table optimized by modern compilers. The downside is that a switch requires integral types.

You should check the PHP docs to see if a switch block will give you any speed benefits.
[http://www.php.net/manual/en/control-structures.switch.php]("http://www.php.net/manual/en/control-structures.switch.php")

---

### Post by Some Penguin on 2010-02-08
I find it slightly improbable that this would be a performance bottleneck unless the code being processed for any given command is trivial and there are a LOT of strings to match.  If that WERE the case, e.g. you had thousands of commands to search, you could use prefix trees or hashing (hashing only being applicable if it's simple to extract what needs to  be hashed - e.g. always the first space-separated token).  Or, say, Wu-Manber, which is overkill, but a relatively simple algorithm to implement if you want to learn how to reasonably efficiently look for exact matches of large numbers of strings.


In the likely case where this isn't the actual bottleneck, you should probably prefer clarity and maintainability here for sanity's sake.

---

