---
title: "A strange behaviour in Lua"
date: 2015-03-03
forum: Programming Talk
---

### Post by Matthew_Harrop on 2015-03-03
I have been writing a program in Lua for sometime and have noticed a strange behavior:

Consider the following code fragment:

> 
local array = {}
array[1] = 'a'
array[2] = 'b'

print(#array) --Provides the answer 2



However when this code fragment is run:

> 
local array = {}

array[2] = 'b'

print(#array) --Provides the answer 0



Now I have an idea why this might occur, but i just wanted to be sure. Is it because the counting system identifies a 'nil' and simply stops? Would that then mean that every time I use the '#array' statement I could end up with an incorrect result?

Has anybody else encountered this?

---

