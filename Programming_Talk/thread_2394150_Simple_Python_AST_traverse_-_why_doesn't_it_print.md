---
title: "Simple Python AST traverse - why doesn't it print?"
date: 2018-06-13
forum: Programming Talk
---

### Post by trilobite2 on 2018-06-13
Hi all - 

 I have a very simple AST coded up in Python - here is the code -  

```
 

class node(): 

  def __init__(self, data, left, right): 
    self.data = data
    self.left = left 
    self.right = right 
    
  def visit(self):
    print self.data
      

#  Post-order traversal   
def postorder(node): 
  if node.left != None: 
    postorder(node.left)
  if node.right != None:
    postorder(node.right) 
  node.visit
    
    
if __name__ == "__main__": 
    a = node(3, None, None)
    c = node(4, None, None)
    b = node('+', a, c)  
        
    postorder(b)


``` 

When run at the command prompt, I just get the prompt back again - nothing prints.  Why?  

Any help is gratefully received!  Many thanks in advance....  :)   

- trilobite2

---

### Post by spjackson on 2018-06-13
> **trilobite2 said:**
> 
```
      

#  Post-order traversal   
def postorder(node): 
  if node.left != None: 
    postorder(node.left)
  if node.right != None:
    postorder(node.right) 
  node.visit

``` 


```

  node.visit[COLOR=#ff0000]**()**[/COLOR]

```

---

### Post by trilobite2 on 2018-06-14
> **spjackson said:**
> ```

  node.visit[COLOR=#ff0000]**()**[/COLOR]

```

Hi spjackson!  

 Great!  Thanks very much for that!  (  **Doh!**   :)   )  
 
I think I'll be having a lot of fun poking around with ASTs in the next few weeks..... :)  

Bye for now - thanks again -  
trilobite2

---

