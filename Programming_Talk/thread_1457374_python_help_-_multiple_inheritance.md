---
title: "python help - multiple inheritance"
date: 2010-04-18
forum: Programming Talk
---

### Post by Choad on 2010-04-18
[s]ok i am sure i have run in to this problem before and gotten past it but i can't for the life of me remember how.[/s]
solved :)
```

>>> class A( object ):
...     def __init__( self ):
...             listA.append( self )
... 
>>> listA = []
>>> listB = []
>>> class B( object ):
...     def __init__( self ):
...             listB.append( self )
... 
>>> class C( A, B ):
...     def __init__( self ):
...             super( C, self ).__init__()
... 
>>> listA
[]
>>> listB
[]
>>> C()
<__main__.C object at 0x7fe3261fae10>
>>> listB
[]
>>> listA
[<__main__.C object at 0x7fe3261fae10>]
>>> 

```

[s]why doesn't the instance of C get added to listA and listB? it only ever gets added to the list whose object type is listed first in the definition of class C[/s]

solution:
```

>>> lista = []
>>> listb = []
>>> class A( object ):
...     def __init__( self ):
**...             super( A, self ).__init__()**
...             lista.append( self )
... 
>>> class B( object ):
...     def __init__( self ):
**...             super( B, self ).__init__()**
...             listb.append( self )
... 
>>> class C( A, B ):
...     def __init__( self ):
...             super( C, self ).__init__()
... 
>>> C()
<__main__.C object at 0x7fc2b566fc50>
>>> lista
[<__main__.C object at 0x7fc2b566fc50>]
>>> listb
[<__main__.C object at 0x7fc2b566fc50>]
>>> 

```

---

