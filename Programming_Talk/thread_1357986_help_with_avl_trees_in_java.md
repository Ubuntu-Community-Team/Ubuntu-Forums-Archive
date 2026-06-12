---
title: "help with avl trees in java"
date: 2009-12-17
forum: Programming Talk
---

### Post by DiTeN on 2009-12-17
Hello friends,

i want to know if could help me how to print an AVL Tree, by levels, and from left to right and from right to left

and if could insert duplicated items,

i have this insert... which does not allowes duplicated....

```
private AvlNode<AnyType> insert( AnyType x, AvlNode<AnyType> t )
    {   int cont=1;
        if( t == null )
            return new AvlNode<AnyType>( x, null, null );

        int compareResult = x.compareTo( t.element );

        if( compareResult < 0 )
        {
            t.left = insert( x, t.left );
            if( height( t.left ) - height( t.right ) == 2 )
                if( x.compareTo( t.left.element ) < 0 )
                    t = rotateWithLeftChild( t );
                else
                    t = doubleWithLeftChild( t );
        }
        else if( compareResult > 0 )
        {
            t.right = insert( x, t.right );
            if( height( t.right ) - height( t.left ) == 2 )
                if( x.compareTo( t.right.element ) > 0 )
                    t = rotateWithRightChild( t );
                else
                    t = doubleWithRightChild( t );
        }
        else
            
            //;  // Duplicate; do nothing

        t.height = Math.max( height( t.left ), height( t.right ) ) + 1;
        return t;
    }
```

as far i been reading i find that i need a counter, but my english isn't well and i can't catch everything....
i will be very thankful if you people can help me...
thanks a lot!!!

sorry for my bad english!!!

---

### Post by kwyto on 2009-12-18
hablas espanol?

---

### Post by kwyto on 2009-12-18
in case you speak another language. 

the algorithm you are showing, not only inserts but also balances the tree. 
to print the tree in POSTORDER: left child, right child, root
to print the tree in INORDER: left child, root, right child
to print the tree in PREORDER: root, left child, right child

now, if you want to allow duplicates them use a regular insertion algorithm for binary trees. the reason for using your algorithm is to maintain a balanced tree in order to do search and insertion in O(log n). hope this helps.

---

### Post by Can+~ on 2009-12-18
> **kwyto said:**
> hablas espanol?

español.

> and if could insert **duplicated items**,

as far i been reading i find that i need a **counter**, but my english isn't well and i can't catch everything....
i will be very thankful if you people can help me...
thanks a lot!!!

Maybe you want to add a counter to the node structure, like:

```
class AvlNode ...
{
    //some stuff here
    private int counter;

    ...
}
```

And whenever you insert something, and find it already on the tree, add one to the counter.

---

### Post by kwyto on 2009-12-18
dude,  spanish is my first language, i wrote espanol because i was too lazy to write it correctly, but if correcting me makes you feel good , well done, otherwise stick to helping the guy in whatever language he speaks instead of wasting time on insignificant stuff. thank you

---

### Post by Can+~ on 2009-12-18
> **kwyto said:**
> dude,  spanish is my first language, i wrote espanol because i was too lazy to write it correctly, but if correcting me makes you feel good , well done, otherwise stick to helping the guy in whatever language he speaks instead of wasting time on insignificant stuff. thank you

Actually, I thought that you were trying to speak spanish when you didn't know the language (I noticed the location under your avatar). I also speak spanish as my first language, and reading "espanol" particularly bothers me, just a little. Sorry if you were offended, though.

---

### Post by DiTeN on 2009-12-19
thank you people for the help.
Yes, español es mi lengua nativa, soy de Uruguay.
 
the answer you did me was what i did, 
thank you so much again!!!!

---

