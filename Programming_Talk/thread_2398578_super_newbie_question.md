---
title: "super newbie question"
date: 2018-08-14
forum: Programming Talk
---

### Post by devdock2 on 2018-08-14
Hello Everyone, 

I am currently teaching myself programming, and as such i am running multiple different projects on my desktop. 

What is best practice for structuring projects? Just keeping each project in its own folder? Will this cause problems?

Or, should I install something like vagrant?

I also heard docker - but when I look at the github of the snap package, it says it is no longer being developed. 

So my basic question: is there anything wrong with installing all packages needed globally, and then having multiple folders with each project inside each folder, or will that not work, and i need to intall vagrant or docket to get the right structure

sorry i know super newbie quesiton

---

### Post by TheFu on 2018-08-14
How you should develop depends on the type of programming being done. Which language used and which platforms you target.
Usually is a not a good idea to depend on any OS packages for your development environment, unless you intend to only support that specific platform and no others.  You'll need to setup similar environments for every platform target if you do it that way.

For compiled languages, it is common to make a directory structure.
```
TOP/
   bin/
   include/
   lib/
   docs/
   contrib/
   man/
```
Look at some projects at gitlab for how they are setup.  

If you are using a scripting language like perl,python,ruby for your work, then you should use their version managers.  Never trust the built-in interpreter for any OS. You should provide the exact version of perl or python or ruby that you want and all modules. Do not trust the repository versions.  This is a best practice for all scripting languages, except bash.

For more info you provide on what you are trying to accomplish, the better the answers will likely be.

---

