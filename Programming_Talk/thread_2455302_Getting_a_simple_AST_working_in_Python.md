---
title: "Getting a simple AST working in Python"
date: 2020-12-17
forum: Programming Talk
---

### Post by trilobite2 on 2020-12-17
Hi all -  

 For a very long time, I've had problems understanding abstract syntax trees and how to implement them for interpreters or compilers.  
I don't have a problem with lexing (creating tokens) but when it comes to arranging said tokens into an AST I hit a brick wall.  

I'm aware that there is this site here which looks at ASTs -  [https://ruslanspivak.com/lsbasi-part7/](https://ruslanspivak.com/lsbasi-part7/)  -  but the code there is under the MIT license and I want the code I put together to be "public domain" - this means that I can't use that code.  

Anyway - this is what I've come up with so far -  
```

#  ast.py  

#  This code is released to the public domain 
#  under the Unlicense. 
#  "Share and enjoy......"   :)  

#  expr : term ((PLUS|MINUS) term)*
#  term : factor ((MUL|DIV) factor)* 
#  factor : INTEGER | LPAREN expr RPAREN 


# Simple node-type for numbers and operators
class node() 
  def __init__(self, ntype, nvalue): 
      self.ntype = ntype
      self.nvalue = nvalue 
      
  def __repr__(self): 
      print self.ntype, self.nvalue       


# Binary node-type for number OP number.  
class binnode()
  def __init__(self, ntype, op, left, right): 
      self.ntype = ntype
      self.op = op
      self.left = left
      self.right = right 
      
  def __repr__(self): 
      print self.ntype, self.op, self.left, self.right 
      

```

So, any help to develop this further is much appreciated!  
Many thanks - bye for now - 
- t

---

### Post by spjackson on 2020-12-18
For a program you need data structures and algorithm. You've made a start at some data structures but you are lacking an algorithm. Choose an algorithm [https://en.wikipedia.org/wiki/Category:Parsing_algorithms](https://en.wikipedia.org/wiki/Category:Parsing_algorithms) then have a go at coding it.

---

### Post by trilobite2 on 2020-12-18
> **spjackson said:**
> For a program you need data structures and algorithm. You've made a start at some data structures but you are lacking an algorithm. Choose an algorithm [https://en.wikipedia.org/wiki/Category:Parsing_algorithms](https://en.wikipedia.org/wiki/Category:Parsing_algorithms) then have a go at coding it.

Hi spjackson -  thanks for your reply!  

Ok -  I'll check out that link and will go from there.  
Thanks again, bye for now - 

- t.

---

