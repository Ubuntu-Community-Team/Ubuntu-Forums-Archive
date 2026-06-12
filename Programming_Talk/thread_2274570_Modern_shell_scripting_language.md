---
title: "Modern shell scripting language"
date: 2015-04-20
forum: Programming Talk
---

### Post by tdennist on 2015-04-20
Hello,

(Apologies if posts like this are discouraged). I wanted to help get the word out about a new programming language I'm building for shell scripting that compiles to bash. The language is called bish, and the idea is to give you a much more modern and comfortable language to program it, but maintain the portability of your old shell scripts (because it compiles to bash). 

Here's a quick example of a bish program that computes Fibonacci numbers to give you a sense of the syntax:

```
def fib(n) {
    if (n < 2) {
        return 1
    }
    return fib(n-1) + fib(n-2)
}
print("fib(5) is: ")
println(fib(5))
```

This program then compiles to bash, meaning it can execute on a very wide variety of Linux-based systems.

You can visit the page on Github for more information and a link to download version 0.1: [https://github.com/tdenniston/bish](https://github.com/tdenniston/bish)

As a side note, if anyone would like to help me get a Debian/Ubuntu package created, any help would be appreciated!

---

### Post by TheFu on 2015-04-20
You'll want to have the first line of any script follow the UNIX standard with *#!/usr/local/bin/bish* or *#!/usr/bin/env bish*

---

### Post by tdennist on 2015-04-20
That is supported (specifically, *#!/usr/bin/env bish -r* is the current syntax). bish is also designed to be ahead-of-time compiled, so this line is optional.

---

### Post by Vaphell on 2015-04-21
OP, are you sure you got enough skill in bash to spit out viable and kosher outputs? That ls | grep example i've noticed doesn't instill much confidence, neither does for (f in files) where files is ls(). 

I don't see support for globs. It's globs that are first class in shells, not ls. Ls is an unreliable plaintext.

you definitely should read Bash FAQ and Bash Pitfalls to see what the state of the art idioms are and why.

---

### Post by TheFu on 2015-04-21
I didn't want to say that, but thanks Vaphell.  My go-to resource for bash stuff is the ABSG and my notes from Michael Potter's &#8220;*Seat Belts and Air Bags for Bash*" presentations.

When I need something that bash can't handle, I switch to perl. Others switch to python, ruby, awk, go, pike .... there isn't any shortage of cross-platform scripting languages.  Perl and python are already installed on most *nix systems.  I know that perl supports being pre-compiled.

The a2p (awk to perl) program is famous, but nobody I know uses it anymore. We write in perl directly.

OTOH, new and better languages are always welcome. I wish you luck.

---

### Post by tdennist on 2015-04-21
Thanks for checking it out and offering criticisms.

**Vaphell**: one advantage to the compiler approach is that I only have to get the code generation right once. Additionally, if I get it wrong, someone else with more bash-fu can correct the mistakes, resulting in a compiler that slowly converges on some notion of bash expertise. I would welcome contributions from people with more bash skill than I :-). Regarding globs: they aren't first-class features yet, but they will be eventually. In the meantime, they can be used via the *@(...)* escape hatch that bish offers.

**TheFu**: The fact that all of those resources exist documenting pitfalls and offering safety belts for bash is the motivation for a language like bish. There is certainly a point where one should switch to more robust languages like the ones you listed, but there is a gap there between the two extremes that bish aims to fill.

Thanks again for taking a look at bish, and I'm happy to answer any other comments!

---

### Post by Vaphell on 2015-04-21
> one advantage to the compiler approach is that I only have to get the code generation right once. 

true, though i can imagine the incorrect understanding of bash scripting potentially influencing the internal design in a harmful way.
And globs should be one of the first things to implement, as they are THE way to interact with files and dirs, which is one of the core functionalities of shells.

Either way if you want to pique the interest and see some userbase down the road, you should be striving to showcase the functionality by compiling common use cases in a proper way right off the bat. Otherwise you risk *"What do i get from using this that I can't get from python with 'import sh'? The dude doesn't know shell well anyway, so how good can the tool be, really?"*

---

### Post by tdennist on 2015-04-22
Good points. I've opened an issue ([https://github.com/tdenniston/bish/issues/66](https://github.com/tdenniston/bish/issues/66)) to support file globbing for the next release. I'll have a look at the bash FAQ you linked to see if there are some commonly occurring idioms that I can list on the front page in bish. Thanks!

---

