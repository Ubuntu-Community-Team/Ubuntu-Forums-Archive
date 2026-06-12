---
title: "Go: Cannot iterate list"
date: 2010-09-15
forum: Programming Talk
---

### Post by The Cog on 2010-09-15
I thought I'd have a stab at Google's Go language. Incredibly, I've spent most of the evening trying to put three strings in a List and get them out again. Can't do it. I think they're in there but I can't iterate over them.

I think I'm getting something out of the channel, but the compiler won't let me use them as a string. In C or java I'd just cast it back to the right type. It seems that Go is broken in this respect - type conversion just doesn't work.

Maybe it's easier just to write a custom list implementation for every type you want to put in a list?

```
package main

import "container/list"
import "fmt"

type Stringer interface {
    String() string
}
    
func main() {
    items := list.New()
    
    item := new(list.Element)
    item.Value = "Apple"
    items.PushBack(item)
    item = new(list.Element)
    item.Value = "Banana"
    items.PushBack(item)
    item = new(list.Element)
    item.Value = "Cherry"
    items.PushBack(item)
    
    itemChan := items.Iter()
    for {
        x := <- itemChan    // x is of type <something dark and mysterious>
        got := string(x)     // Yes it's a flaming string!
        if closed(itemChan) {
            fmt.Printf("That's all, folks\n")
            break
        }
        fmt.Printf("got %s\n", got)
    }
}


```

---

### Post by GenBattle on 2010-09-15
I don't have my own code on me right now, so i can't remember exactly how to do type casting in GoLang. If i rememeber right it's something like:

```
ok, converted := x.(string)
```
Which should give you a boolean value indicating whether the casting/conversion was successful, and the converted value/pointer. This process always has to be done in Go when you go from an interface type to some other type.

This is only a guess at this stage, but **type switches** are also something you should check out on the same page as conversions:
[http://golang.org/doc/go_spec.html#Conversions](http://golang.org/doc/go_spec.html#Conversions)

---

### Post by Queue29 on 2010-09-16
Go sucks. I spent 3 months learning the language, using it in all sorts of little projects. I finally gave in and realized that just because it's from Google and has 3 famous people behind it doesn't mean it's any good. And it isn't good. Take a step back and think about how many features are missing from the language. Now take a step forward and look at something like D. Now ask yourself why anyone would design Go the way they did, and what kind of sick and twisted mind you would have to have to actually use it.

I mean seriously. Ask yourself why you're using a language that doesn't even support generics.

---

### Post by Queue29 on 2010-09-16
Oh, and I hope you aren't too attached to that [new]("http://groups.google.com/group/golang-nuts/browse_thread/thread/9165d853de57374e/b5e72d81edc11789?q=remove+new&lnk=ol&") keyword.

---

### Post by DanielWaterworth on 2010-09-16
> **Queue29 said:**
> Go sucks. I spent 3 months learning the language, using it in all sorts of little projects. I finally gave in and realized that just because it's from Google and has 3 famous people behind it doesn't mean it's any good. And it isn't good. Take a step back and think about how many features are missing from the language. Now take a step forward and look at something like D. Now ask yourself why anyone would design Go the way they did, and what kind of sick and twisted mind you would have to have to actually use it.

I mean seriously. Ask yourself why you're using a language that doesn't even support generics.

interfaces alleviate some of the pain of the lack of templates. I quite like go, the emphasis on duck-typing is great.

---

### Post by GenBattle on 2010-09-16
I like Go as a language, it just has a very different set of priorities from other languages. All other languages have a similar feature set, and aim for small incremental improvements. Go is doing something very different from the status quo to try and get some radical new ideas off the ground, which aren't compatible with the normal model of programming. They sacrifice structures like templates and proper object-linked inheritance hierarchies to gain compilation and run speed, so you end up with something closer to C than C++ or D.

Overall i think it's definitely something worth trying, even if just to sample something a little different.

---

### Post by The Cog on 2010-09-16
@Queue29 : I may well come to that conclusion myself. But I'm a stubborn bugger, and I'd rather it was my conclusion than someone else's. I'll keep on trying for a while.

The problem I get with the code I posted is with these two lines:
>         x := <- itemChan    // x is of type <something dark and mysterious>
        got := string(x)     // Yes it's a flaming string!
 and the compiler error is:
> cannot convert x (type interface { }) to type string: need type assertion

Is it really not possible to put strings in a list and get them back out again?

---

### Post by The Cog on 2010-09-16
Aah! This one works:
```
package main

import "container/list"
import "fmt"
  
func main() {
    items := list.New()
    
    item := new(list.Element)
    item.Value = "Apple"
    items.PushBack(item)
    item = new(list.Element)
    item.Value = "Banana"
    items.PushBack(item)
    item = new(list.Element)
    item.Value = "Cherry"
    items.PushBack(item)
    
    itemChan := items.Iter()
    for {
        a := <- itemChan 
        if closed(itemChan) {
            fmt.Printf("That's all, folks\n")
            break
        }
        b := a.(*list.Element)
        c := b.Value
        got := c.(string)
        fmt.Printf("got %s\n", got)
    }
}
```
and produces:
> got Apple
got Banana
got Cherry
That's all, folks
But there are things I don't understand. According to the source code of container/list.go, I think the Iter() call should produce a stream of the original values set into the elements (strings in my case). Instead, it seems to produce a stream of pointers to Element structures. How does that happen?
```
func (l *List) iterate(c chan<- interface{}) {
	for e := l.front; e != nil; e = e.next {
		c <- e.Value
	}
	close(c)
}

func (l *List) Iter() <-chan interface{} {
	c := make(chan interface{})
	go l.iterate(c)
	return c
}
```

---

### Post by tc_zot on 2010-10-11
Any reason you are putting list.Elements into the list and not just putting strings in it?  This works for me:

```
package main

import "fmt"
import "container/list"

func main() {
    items := list.New()
    items.PushBack("Apple")
    items.PushBack("Banana")
    items.PushBack("Cherry")
    for x := range items.Iter() {
        fmt.Printf("got %s\n", x)
    }
    fmt.Printf("That's all, folks\n");
}
```

---

### Post by The Cog on 2010-10-15
Ah, thank you. I must have been having a bit of brain fade. I had looked at the definition > func (l *List) PushBack(value interface{}) *Element {
and had convinced myself that it needed to be supplied with a *Element type. And then of course I was fighting against the fact that I was getting an *Element back out again. I though it was proving needlessly difficult to use. Maybe I ignored the interface{} type because I don't fully understand that yet - seems to be a bit like a void type. Yes, dropping strings in is much easier and more natural.

Now I'm off to find more about the range keyword.

---

### Post by tc_zot on 2010-10-16
> **The Cog said:**
> Ah, thank you. I must have been having a bit of brain fade. I had looked at the definition 
and had convinced myself that it needed to be supplied with a *Element type. And then of course I was fighting against the fact that I was getting an *Element back out again. I though it was proving needlessly difficult to use. Maybe I ignored the interface{} type because I don't fully understand that yet - seems to be a bit like a void type. Yes, dropping strings in is much easier and more natural.

Now I'm off to find more about the range keyword.

Good!  I figured the "go sucks" replies didn't help.  Beyond containing no information about your problem, they (incorrectly) reinforce the feeling that your troubles were par for the course.

People don't seem to understand that Go was written by the creators of UNIX; not exactly what you would call noobs.  In fact, I'd be surprised to find a detractor who's not a noob, compared to them.  My advice is to keep pursuing learning it and ignore the static.


Bill

---

### Post by The Cog on 2010-10-16
I will keep on, but slowly. It's very much a spare time curiosity project for me. I know that in a few years, some kind of improvement in concurrency handling is needed, and want to keep my eye on what's brewing. I had a look at erlang but that really didn't feel right with me - it was just toooo different.

---

### Post by KarteekKumarM on 2012-02-27
Had the same problem, figured it out after some reading from go-docs....

// got := string(x)     // type conversion - wont work
got := x.(string) // type assertion - will work

---

