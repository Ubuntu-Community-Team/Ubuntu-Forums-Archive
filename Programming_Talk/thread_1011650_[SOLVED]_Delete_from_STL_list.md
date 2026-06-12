---
title: "[SOLVED] Delete from STL list"
date: 2008-12-15
forum: Programming Talk
---

### Post by kjohansen on 2008-12-15
This is related to my earlier thread [http://ubuntuforums.org/showthread.php?t=1009636](http://ubuntuforums.org/showthread.php?t=1009636)

Recap: 
"Item Request" has an Id and a quantity and some other non important fields.

I am reading a file, some lines say to add an "Item Request" to a list some say to decrease the quantity of a a request with a specific Id and some say to delete a specific Id.  If instead of deleting an item request I just set its quantity to 0 the rest of the logic of my code works, but the list gets REALLY big.  If I use erase, I get the wrong results.

[php]
                for(it=items.begin();it!=items.end();++it)
                {
                    if(it->ID==orderID) //orderID is a var in this scope
                    {
                        if(it->size > decreseAmount) //decreaseAmount is a var in this scope
                        {
                            it->size-=decreaseAmount;
                        }
                        else
                        {
                            it->size-=decreaseAmount;
                            items.erase(it);
                        }
                        break;
                    }
                }

[/php]

I have tried several different ways to erase an entry. I found another forum with the suggestion to use remove which apparently moves the entries to the end of the list and then use erase on the end, I have tried just remove, but always the rest of it breaks.

I have written my own sorting routine that does not involve iterators only size and random access (i had to switch to vectors to do this).

I have checked the size before and after and it is correct.  Is this the proper way to delete an entry in a vector or a list?

Edit: I forgot to mention that later on in the logic I am sorting the list using the built in sort command (list.sort()).  I mention this because I dont know if somehow the erase is not updating the list.end() and it is somehow sorting the wrong thing, I dont know I have been looking at this for two days and cant find an error.

---

### Post by Lux Perpetua on 2008-12-15
What is "asks"? You have an iterator to "items", yet you're erasing it from "asks". I'm confused.

---

### Post by kjohansen on 2008-12-15
> **Lux Perpetua said:**
> What is "asks"? You have an iterator to "items", yet you're erasing it from "asks". I'm confused.
that was just a typo when posting...

the erase is from the same list as the iterator...

---

### Post by AnRa on 2008-12-15
[php]
                for(it=items.begin();it!=items.end();++it)
                {
                    if(it->ID==orderID) //orderID is a var in this scope
                    {
                        if(it->size > decreseAmount) //decreaseAmount is a var in this scope
                        {
                            it->size-=decreaseAmount;
                        }
                        else
                        {
                            it->size-=decreaseAmount;
                            it = items.erase(it);
                        }
                        break;
                    }
                }

[/php]

---

### Post by dwhitney67 on 2008-12-15
> **kjohansen said:**
> ...

[php]
                for(it=items.begin();it!=items.end();++it)
                {
                    if(it->ID==orderID) //orderID is a var in this scope
                    {
                        if(it->size > decreaseAmount) //decreaseAmount is a var in this scope
                        {
                            it->size-=decreaseAmount;
                        }
                        else
                        {
                            //it->size-=decreaseAmount;
                            items.erase(it);
                        }
                        break;
                    }
                }

[/php]

The code you posted originally is correct, although there is no need to decrement 'size' if you plan to erase the item from the items list (hence I have commented it out above).

Once you erase an item, your iterator is going to be useless, unless you reassign it as demonstrated by AnRa in the previous post.  Since you (and he) are using a 'break' statement to get out of the loop, reassigning the iterator is pointless.

If you are still having problems in the code, then it is another issue other than what you have posted.

---

### Post by aapocketz on 2008-12-15
> **dwhitney67 said:**
> The code you posted originally is correct, although there is no need to decrement 'size' if you plan to erase the item from the items list (hence I have commented it out above).

Once you erase an item, your iterator is going to be useless, unless you reassign it as demonstrated by AnRa in the previous post.  Since you (and he) are using a 'break' statement to get out of the loop, reassigning the iterator is pointless.

If you are still having problems in the code, then it is another issue other than what you have posted.

dwhitney bacardi is correct, this code scares me because you invalidate an iterator in a for loop, but the break statement would make it ok.  I could see a situation where someone would remove the critical break statement, so you should consider at least adding a comment line or something to that effect.

also consider seeing if you can use an stl find or remove_if algorithm for this function, or something like that.  Looks like you want to find the order ID, and if you find it, decrement the size or remove it if its too small.  Sometimes the stl algorithms are too restrictive though.

---

### Post by kjohansen on 2008-12-15
Final answer:  hash_sets overflow much more quickly than I expected.

thanks for the confirmation on my erase syntax, and I did end up using the find function with a custom operator....

---

