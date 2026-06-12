---
title: "Learning new languages, Go and Rust"
date: 2015-07-13
forum: Programming Talk
---

### Post by Anonimista on 2015-07-13
I've been reading a lot about these two languages for the last couple of days and I believe I have a pretty good grasp of their pros and cons. I am going to start experimenting with both of them and I would appreciate any first hand experiences about either of them from you guys. Pointers, things to watch for, anything. Thanks.

---

### Post by trent.josephsen on 2015-07-13
I'm a big fan of C, as my post history will attest, and whenever a new language comes along that claims to replace C, I always look into it to find out why it won't. I'm from a hardware background, and I'm not too interested in those languages that can only replace C *sometimes*. They appear pretty regularly, but most of them have implicit assumptions about the *kinds* of programs that they're targeting. Assumptions like the following:

[LIST]
[*]"Small memory leaks aren't a big deal."
[*]"It's not necessary to compile to machine code."
[*]"Vtables don't represent a significant performance penalty. Everyone uses dynamic dispatch, anyway."
[*]"Every sizeable program needs $FEATURE." ($FEATURE is often garbage collection, hashtables, multi-threading or networking.)
[*]"Anything that goes in the runtime isn't overhead, since it would be there anyway."[/LIST]
When you dig deeper, most "C-killers" don't really compete with C, except in the common arena where they also compete with C++ and C# and Java and a bunch of others. Which is why I am super intrigued by Rust. Memory safety at compile time? That's something *different*. Algebraic data types with *no runtime cost* (beyond what you'd have by writing loads of equivalent and potentially-buggy C code)? Stack allocation by default and heap allocation *you can't forget to free*? **That** definitely gets my attention.

Rust is young.[1] It hasn't stood the test of time; heck, it hasn't even been allowed to sit the exam. But it solves problems that I used to imagine intractable, and that makes it very interesting. I don't know if I have anything more to say beyond that, but then I guess I'm not really sure what you were expecting to hear. I'm excited about it, I guess :)

/r/rust and StackOverflow are good places to get actual help with the language, but you probably already know that.

[1] "Rust" (the project) is about 5 years old, but the language currently called by that name wouldn't have been recognizable for the first few of those.

---

### Post by Anonimista on 2015-07-14
Thanks for the input, really appreciate it. Right now I do most of my work in Python and PowerShell and as much as I like scripting I got a bit tired of it and really want to try out a new compiled language. I don't mind that Rust is young, I won't be using it for anything useful right now. I started to read through the rust Book last night and it does have a learning curve as I expected.

---

### Post by Wybiral on 2015-07-14
I've been using Go for some of my hobby projects recently and I'm pleased. It's a little weird if you're used to object oriented languages as it wants to use [interfaces]("http://jordanorelli.com/post/32665860244/how-to-use-interfaces-in-go") to define a sort of [duck type]("https://en.wikipedia.org/wiki/Duck_typing") abstraction. You care more about what methods and attributes something has than you do what type it is in an inheritance tree. You can do some neat stuff with that.

Channels and Goroutines are definitely some of the strongest features in the language. There are some basic examples [here]("https://tour.golang.org/concurrency/1").

Another strong feature is the package system and ability to easily import from places like github (see the [go get]("https://golang.org/cmd/go/#hdr-Download_and_install_packages_and_dependencies") command line tool).

I've never gotten around to trying Rust.

Anyway, good luck!

---

### Post by Anonimista on 2015-07-15
Yes, most of the criticism I've read is about Go missing OO features. People seem to complain about its error handling the same way they complain about Java's checked exceptions. What appeals to me is Go's simplicity, Rust seems more difficult to pick up. The other thing that is important to me is a language's standard library (ie. what I can do with it). Go's seems more mature (no surprise) than Rust's, but I read a [blog post by Bruce Eckel]("http://bruceeckel.github.io/2015/02/15/why-not-go-there/") that says that Go doesn't fit well some problem domains like prototyping/scripting and high performance computing. 

None of the above bothers me though, I'll try both Go and Rust.

---

