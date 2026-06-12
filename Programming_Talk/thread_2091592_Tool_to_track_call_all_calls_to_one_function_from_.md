---
title: "Tool to track call all calls to one function from another function"
date: 2012-12-05
forum: Programming Talk
---

### Post by cybo on 2012-12-05
I need to track down all calls from func1 to func2 in the code. The language I use is C. I started doing it manually but I was wondering if there is an automated tool to do that. 

Here is some pseudo code

```
func1
  func3
  func4
  func5
  func2

func3
  func6
  func4
  func2
  func7

func4
  func2
  func3
  func7
  func8
  func5

func5
  func6

func6
  func7

func7
  func2


```

So for example if I tell to the that tool to track down all the calls of func2 from func1 it will produce the following results:

func1->func2, func1->func3->func2, func1->func4->func2, func1->func5->func6->func7->func2, func1->func7->func2 etc.

Any help is appreciated.

---

