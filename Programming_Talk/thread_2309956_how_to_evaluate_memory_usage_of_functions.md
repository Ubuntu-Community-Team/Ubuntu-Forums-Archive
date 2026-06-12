---
title: "how to evaluate memory usage of functions?"
date: 2016-01-14
forum: Programming Talk
---

### Post by Dreamer Fithp Apprentice on 2016-01-14
I've been fiddling with functions of the sort that can be used in many scripts lately, and I'm wondering about the consequences of either:

 just throwing all the functions I write into a profile or rc file or files that get loaded automatically,

 vs

having all my functions in one big source file that gets sourced explicitly and loads all of them  in any script where I want to use any of them

vs.

putting them all in separate sourceable files in the same directory and sourcing just the ones I want for each script.

Specifically, I'm wondering how to best quantitatively evaluate how much memory these approaches use.  I could try different setups and then use something that measures overall memory usage of course, but that seems to vary from time to time for not-go-obvious reasons anyway, and I wonder if I might be trying to look for a small signal in a lot of noise that way. Anybody got any suggestion for a better way? Or some relevant observation like "you can load a King James 
Bible's worth of funcitons" and it only uses 10 mb of RAM"?

Could I assume the size of the file containing the function(s) is approximately the amount of RAM it will take to load them?

Thanks for any thoughts you have on this.

---

### Post by mystics on 2016-01-15
> **Dreamer Fithp Apprentice said:**
> Could I assume the size of the file containing the function(s) is approximately the amount of RAM it will take to load them?


Unless I'm severely mistaken, no. The file is basically text. What that code can create on the other hand is a lot more. Consider the following C code:

```

public void sorryMrStack()
{
    double a[10000][10000][10000][10000];
    printf("Serves Mr. Stack right!\n");
    return;
}

```

Now, the actual text to hold this is manageable. However, calling that function requires allocating 10000^4 * sizeof(double) memory. That is significantly more than that text takes up. Assuming sizeof(double) is 8 bytes, it would take 8 * 10^16 bytes in order to hold that four-dimensional array. So while the text maybe consists of a few hundred bytes at most, that array would likely be measured in terabytes, and that's if we don't want to move to less understood measurements like petabytes.

That said, I don't believe languages automatically load functions into memory like this unless they are actually used by the program. In other words, I'm not automatically loading fprintf into every C program just because I wrote

```

#include <stdio.h>

```

In other words, the fact fprintf is included in stdio.h has no bearing on the memory usage of my program. If I never call the program, it will never show up in memory, as the compiler would ignore it during compilation time. In this regard, shoving thousands of functions into a single file has little bearing on memory usage of the program.

However, I do believe that it is considered good practice to keep the content of files as related as possible. In this regard, you probably should split them up into easy-to-identify files.

And with regards to your question with actual analysis, you might be able to find an IDE with good debugging capabilities. You could set a breakpoint before the function call, step into the function, and see what the IDE says is the memory usage (assuming the IDE provides that information). That should give you at least a rough estimate. Unfortunately, I'm not sure what tools Linux has for this. All my debugging on Linux is with gdb, and I'm not sure if that is capable of displaying memory usage.

Edit: I should probably add that the example I gave above was just really extreme. How much memory a function uses changes from function to function and how much more or less memory it uses than the file is dependent on a lot of factors.

Edit: Edit: I just realized you were talking about scripts while I assumed C. Sorry if this is way off from what you were talking about.

---

### Post by Dreamer Fithp Apprentice on 2016-01-15
Thanks, Mystics.
> **mystics said:**
> I just realized you were talking about scripts while I assumed C. Sorry if this is way off from what you were talking about.Not at all actually. 95% of the ideas you expressed are relevant even if the details would have to be adapted. And the other 5 is still interesting.

But I should have made it clearer with a more concrete example. In coming up with this (which adapts one of your ideas if I understood it correctly) I think I've made it clearer to myself as well, and maybe come up with a way to test it. Let's say I have a 1 mb file in my path that is called "functions". Then  I run a script like this in a terminal:

```
#!/bin/bash
echo "free memory BEFORE reading functions: $(free | grep Mem: | tr -s " " | cut -d" " -f4)"
. functions
echo "free memory AFTER reading functions: $(free | grep Mem: | tr -s " " | cut -d" " -f4)"

```

Note that I don't actually use any of the functions yet, just source the file so they will be AVAILABLE to use in the script.
In principle, if all other things remained equal (and repeatedly running "free" in lxterminal shows they don't, but let's assume it) does my RAM usage go up by just 1 mb between the 2 "free" tests?

Alternately, instead of sourcing functions in the script
let's say I took the same text and put it in /etc/profile. and rebooted and ran free or something else to evaluate memory usage. Then deleted that  code form /etc/profile, rebooted and checked again. Would I expect an extra mb of code in that file to mean any instance of bash uses just one more mb than it would have and RAM usage would be otherwise unaffected?

Obviously actually USING one of the functions could use any amount of memory whatever, up to all that is on the system, and would depend on the actual content of the function. But I'm just talking about the consequences of reading the functions so they are available to be used, even if they aren't.

If it's only a mb, I don't really need to be concerned and can just do it however is easiest to use/understand/inspect/maintain, which is probably just to put them all in one file and source it at the beginning of any script where I need any of them. I doubt I'll ever have a mb's worth.

And is my massaged free command above a decent way to quantify this?

---

### Post by Dreamer Fithp Apprentice on 2016-01-22
Adapting Mystic's idea to Bash, I used the "free" command referred to above at the beginning and end of the "functions" file itself, storing the results as variables, calculating the difference, and echoing the diff both to standard out and a log file. Seems to work, and since nobody has piped up to say "No, no, no! Free doesn't work like that!", and since the question as stated is "how to evaluate memory usage of functions" I'll mark this solved. Now I know HOW to evaluate (presumably) and I'm evaluating. As to the actual effect of methods of loading functions on RAM usage, it turns out to be as I suspected: Even running the commands as part of the function loading sourced file, so that the amount of other stuff the system is doing in the interim is minimised, it is still a very noisy signal. Right now I've only got one function in there. The numbers in the log range from about -1 mB to +1mb. So I'm going to try running some statistics program on those numbers to see if I have a statistically significant answer, but for now, clearly the amount of RAM used this way is negligible. As I add more functions (and probably some variable definitions as well) presumably the amount will grow and eventually I'll have enough stats to confirm or refute my suspicion that the amount of extra RAM used will be approximately the same as the size of the file.

Assuming I don't lose track in the meantime, the comet doesn't strike, and they don't come drag me off to a rubber walled room or find me a place in the gulag, I'll report my findings here later.

---

### Post by mystics on 2016-01-24
I'm actually curious to see what you come up with those tests. I'm not very familiar with bash, especially its inner workings. It'll be interesting to see how it compares to C.

---

