---
title: "Java to Haskell"
date: 2010-04-19
forum: Programming Talk
---

### Post by Ravenshade on 2010-04-19
Hi guys, I'm trying to convert a piece of code from Java to Haskell, but I'm somewhat baffled by the lack of loops. One tutorial particularly Haskell for C programmers (I am not a C programmer at heart but hey..) suggests that there are no need for 'for loops' and in fact demonstrated a piece of code that wasn't explained. 

This is the code that took quite a while to figure out and refine with help from a variety of sources. I now have a better understanding of how java functions. This piece of code simply checks for duplicates, strips the duplicates out and prints the remaining numbers. 

```
class problem1d {
    
    public static void main(String[] args) {

        //Declare the initial array
        
        int[] numeral = { 17, 6, 45, 2, 3, 17, 6, 9, 8, 6, 1, 4, 12};
        int[] finalNum = new int[13]; //define as empty to be filled.
        
        boolean hasBeenCopied = false;
        int numDuplicated = 0;
        
        //Check all numeral's items
        for(int i=0; i<numeral.length; i++){
            hasBeenCopied = false;
            //Cycle destination array
            for(int j=0; j<numDuplicated; j++){
                //Check if current item in destination array is equals to current item in source array
                //This means that this number has been copied before
                if( numeral[i]==finalNum[j]){
                    hasBeenCopied=true;
                    break;
                }
            }
            if(!hasBeenCopied){
                //Copy current number into destination array
                finalNum[numDuplicated++] = numeral[i];
            }
        }
        int i=0;
        for (i=0; i<numDuplicated; i++) {
        //while (i < finalNum.length) {
            //System.out.println(finalNum[i]);
            System.out.println(finalNum[i]);
            //i++; //increment while loop to end!
        //}
        }
    
    }

}
```





That's the Java out of the way, this is what I have so far in a hs file, whether for right or wrong the information I have gathered doesn't like running in stand alone applications, however, this is the source so far... 

```
module Main where

main = do
    putStrLn "Hello World!"
    
    let numeral = [17, 6, 45, 2, 3, 17, 6, 9, 8, 6, 1, 4, 12] :: Int
    let finalNum = [] :: Int
    
    let hasBeenCopied = TRUE :: Boolean
    let numDuplicated = 0 :: Int

```

As you can see I've restricted the types (or so I've been lead to believe) so that there is little confusion where data is supposed to go, of course I'm a little unsure what the type syntax are. 

Hopefully this is all correct, but now I need to work on those for loops but I can't seem to get any information on the matter (perhaps not looking hard enough) could someone direct me to a specific page that deals with what I'm asking for? Thank you:KS

---

### Post by Some Penguin on 2010-04-19
Not a Haskell guru, but from work waaaay back with other functional languages I suggest that that particular iteration can be replaced with recursion.


pseudocode:


list_without_dupes(X) = list_without_dupes_helper(X, new empty list Y)

list_without_dupes_helper(X,Y) =
  if X is empty:  return Y

  otherwise, let X be (W,Z) where W is the first item and Z is the rest of the list --
  then return list_without_dupes_helper(Z,Y + W) if W is not already in Y,
  list_without_dupes_helper(Z,Y) if W is already in Y


Of course, for efficiency reasons, you wouldn't want to actually replicate the original Java code (repeated linear scans, oh my!).  In Java, a Set (HashSet, say, unless the set was huge) provides much faster lookups.  Haskell probably has a similar construct, but without having used it I can't tell you what it would be.

---

### Post by CptPicard on 2010-04-19
Because Haskell is a pure-functional language, loops would be impossible, because you could never increment the loop counter, as there is no (re)assignment.

Instead, use a tail recursion, or more likely in this case, some kind of list comprehension, or a combination of map/filter/reduce.

---

### Post by Ravenshade on 2010-04-19
*gulp* this is starting to remind me of z notation. 

A tail recursion or
List comprehension 

I'll take a look into both of them, thank you and thank you for your explanation on why it isn't possible ^_^

---

### Post by Ravenshade on 2010-04-19
> **Some Penguin said:**
> Not a Haskell guru, but from work waaaay back with other functional languages I suggest that that particular iteration can be replaced with recursion.


pseudocode:


list_without_dupes(X) = list_without_dupes_helper(X, new empty list Y)

list_without_dupes_helper(X,Y) =
  if X is empty:  return Y

  otherwise, let X be (W,Z) where W is the first item and Z is the rest of the list --
  then return list_without_dupes_helper(Z,Y + W) if W is not already in Y,
  list_without_dupes_helper(Z,Y) if W is already in Y


Of course, for efficiency reasons, you wouldn't want to actually replicate the original Java code (repeated linear scans, oh my!).  In Java, a Set (HashSet, say, unless the set was huge) provides much faster lookups.  Haskell probably has a similar construct, but without having used it I can't tell you what it would be.


Sorry there penguin, didn't see that pseudo code. It actually sounds plausible (even if at first glance completely mind blowing). 

Thanks for the help!

---

### Post by Reiger on 2010-04-19
In this case, what you need is filter, and pattern matching; for a variation on the theme: what if you need _sorted_ output? For instance selection of authors by name from a book catalogue?

---

### Post by Ravenshade on 2010-04-20
That confused me. I only need to get numbers out >_>

---

### Post by Alasdair on 2010-04-20
Don't start by trying to write the main function. Often it's much easier to start by working bottom-up rather than top-down. A good place to begin would be by writing a removeDuplicates function.

```

-- | Remove duplicates takes a list whose elements can be compared,
-- and returns a list with the duplicates removed.
removeDuplicates :: Eq a => [a] -> [a]
...

```

It's going to be a recursive function so think about the different cases, first we have the base case - the empty list. That's fairly trivial:

```

removeDuplicates [] = []

```

Now, if the list isn't empty we use pattern matching to split the list into it's head (x) and tail (xs). We now have two more cases to consider, 1) x is an element of xs, and 2) x is not in xs. This logic can be written using guards, like so. 

```

removeDuplicates (x:xs)
    | x `elem` xs = ...
    | otherwise   = ...

```

Now just think about how you have to recurse on the list in order to remove all the duplicate values. Hope that helps!

---

### Post by Ravenshade on 2010-04-20
That's definitely different.... I was gonna go against someone's advice and replicate the whole thing... 

```
-- helloWorld in haskell
import Data.IORef

--Define Foreach
foreach = flip mapM_

--Define While
while test action = do
    val <- test
    if val then do {action; while test action}
        else return

--Helpers for use with while
incr ref = modifyIORef ref (+1)
test ref f = do { val <- readIORef ref; return (f val)}

-- Exercise them. Equivalent Python code:

-- for x in range(1,11): 

--     print x

-- i = 0

-- while i < 5:

--     print "Still running"

--     i += 1


module Main where

main = do
    putStrLn "Hello World!"
    
    let numeral = [17, 6, 45, 2, 3, 17, 6, 9, 8, 6, 1, 4, 12] :: Int
    let finalNum = [] :: Int
    
    let hasBeenCopied = TRUE :: Boolean
    let numDuplicated = 0 :: Int
    
    foreach [
    
```Whereby I was going to force haskell into for and while functions... *cough* :lolflag: guess who got stuck trying figure out how to get it to work on the array. 


I will however try very hard to figure out how to recurse the list ^-^

---

### Post by CptPicard on 2010-04-20
I think your attempts to forcefully "un-Haskell" this problem is a brilliant demonstration of why we've been saying for years that functional programming really makes clear actual problem structure and solution strategies, while imperative programming tends to focus more on specifying machine operations to achieve some result.

You should really think more of how your problem works... there is a simple solution to this when you get it. No need to go for monads :D

---

### Post by Reiger on 2010-04-20
> **Alasdair said:**
> Don't start by trying to write the main function. Often it's much easier to start by working bottom-up rather than top-down. A good place to begin would be by writing a removeDuplicates function.

```

-- | Remove duplicates takes a list whose elements can be compared,
-- and returns a list with the duplicates removed.
removeDuplicates :: Eq a => [a] -> [a]
...

```

It's going to be a recursive function so think about the different cases, first we have the base case - the empty list. That's fairly trivial:

```

removeDuplicates [] = []

```

Now, if the list isn't empty we use pattern matching to split the list into it's head (x) and tail (xs). We now have two more cases to consider, 1) x is an element of xs, and 2) x is not in xs. This logic can be written using guards, like so. 

```

removeDuplicates (x:xs)
    | x `elem` xs = ...
    | otherwise   = ...

```

Now just think about how you have to recurse on the list in order to remove all the duplicate values. Hope that helps!

To expand; and clarify my own post by way of using the above as example:

```

{-
 - recursive function with pattern matching:
 - syntax is: funcNam pattern = funcDefinition
 - named parts of the pattern are available as locally scoped values
 - most specific patterns (cases) should be written at the top,
 - least specific ones at the bottom; because Haskell attempts to 
 - match patterns in that order, which means that if two patterns would match a given input
 - the top most of the two will be used.
 -}

-- this is the base case: matches the empty list, and returns an empty list
removeDuplicates [] = []
-- the recursive case: the pattern here is a list with a head element x and a tail xs
removeDuplicates (x:xs)= ... -- use the variables x and xs here

```

Now think what filter does, and define a function based on x that will filter out all other occurrences of the element x from the tail list xs.
Then the recursive function becomes quite trivial to write.

---

