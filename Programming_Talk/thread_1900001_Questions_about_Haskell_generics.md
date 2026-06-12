---
title: "Questions about Haskell generics"
date: 2011-12-25
forum: Programming Talk
---

### Post by ceclauson on 2011-12-25
Okay, so I'm starting a project that I thought Haskell would be a good language for, but I'm finding myself tripping over the intersection of typeclasses and generics.

What I'm trying to do now is write some code that performs Gaussian Elimination on a matrix--but the matrix is parameterized in a type that supports operations associated with a general algebraic field (i.e., addition, multiplication, division, etc), not just real or complex numbers.

So to start, I declare a type class "FieldElement" that represents an algebraic field, with all the operations you can perform on elements of that field:

```

class FieldElement a where
	fadd, fsub, fmul, fdiv	:: a -> a -> a
	fnegate, finvert	:: a -> a
	fIsZero, fIsUnity	:: a -> Bool

```

For test purposes, I declare the Haskell "Double" type to be a member of "FieldElement":

```

instance FieldElement Double where
	fadd = (+)
	fsub = (-)
	fmul = (*)
	fdiv val1 val2
		| val1 == val2	= 1.0
		| otherwise 	= val1 / val2		
	fnegate = negate
	finvert val = 1 / val
	fIsZero val = val == 0.0
	fIsUnity val = val == 1.0

```

There might eventually be some rounding issues with this to sort out later, but fine for now.  Next I want a type class that represents something that row operations can be performed on (i.e. swaps, scaling rows, etc).  The trick is, though, I want it to be parameterized in a specific field element type.  So if this were Java, it would be

```

interface RowOpable<E extends FieldElement>

```

This is what I ended up doing:

```

class RowOpable a where
	swapRows	 :: (FieldElement s) => a s -> Int -> Int -> a s
	scaleRow	 :: (FieldElement s) => a s -> Int -> s -> a s
	addScaledRowInto :: (FieldElement s) => a s -> Int -> s -> Int -> a s

```

The compiler accepts it, but I'm not even really sure that it's what I want, so if someone can comment that would be great.

Next I want a Matrix type.  The matrix has to be parameterizable in a FieldElement.  This is what I have:

```

data (FieldElement a) => Matrix a = Matrix {
	size	:: Int,
	dat	:: [[a]]
}

```

Again, not sure that this is what I want, but the compiler accepts it.  Next, I try to create a matrix instance:

```

theMatrix = Matrix {
	size = 5,
	dat = [
		[ 4.0,  2.0,  3.0,  6.0,  1.0],
		[ 8.0, 10.0,  4.0,  6.0,  2.0],
		[ 4.0,  9.0,  1.0, 10.0, 11.0],
		[13.0,  3.0, 10.0,  8.0,  3.0],
		[10.0, 34.0,  1.0,  2.0,  1.0]
	]
}

```

Now the compiler complains about the monomorphism restriction.  I know I could turn this off with a compiler switch, but at this point I'm not even sure if I've gone about this the right way.  If these were Java classes/interfaces I'd know exactly what to do, but I was hoping to use Haskell for this, in part just to learn it better.

So if anyone has any comments/suggestions it would be much appreciated.

Thanks in advance.

---

### Post by schauerlich on 2011-12-25
```
interface RowOpable<E extends FieldElement>
```

would translate to

```
class (FieldElement e) => RowOpable e where
```

---

### Post by ceclauson on 2011-12-25
Thanks for the reply.

Are you sure, though, that this is the case?  As I understood it, the class declaration:

```

class (FieldElement e) => RowOpable e where

```

Says that "RowOpable" is a subtype of "FieldElement", which isn't what I want.

So just to clarify, my understanding is that this is essentially like

```

interface RowOpable extends FieldElement

```

instead of

```

interface RowOpable<E extends FieldElement>

```

Is this wrong?

Thanks again.

---

### Post by schauerlich on 2011-12-25
> **ceclauson said:**
> Thanks for the reply.

Are you sure, though, that this is the case?  As I understood it, the class declaration:

```

class (FieldElement e) => RowOpable e where

```

Says that "RowOpable" is a subtype of "FieldElement", which isn't what I want.

So just to clarify, my understanding is that this is essentially like

```

interface RowOpable extends FieldElement

```

instead of

```

interface RowOpable<E extends FieldElement>

```

Is this wrong?

Thanks again.

Whenever you have something like this:
```

(Foo a) => Bar a
```

That means that [FONT="Courier New"]a[/FONT] is any type which declares an instance of [FONT="Courier New"]Foo[/FONT]. You're placing a restriction on what types [FONT="Courier New"]a[/FONT] can be. It has nothing to do with [FONT="Courier New"]Bar[/FONT]. By analogy, you would be saying that [FONT="Courier New"]a[/FONT] is any type that implements [FONT="Courier New"]Foo[/FONT]. [FONT="Courier New"]a[/FONT] is NOT an interface, it is a type that implements the specified interface.

---

### Post by ceclauson on 2011-12-27
Thanks for the continued replies.

I'm still trying to understand this, though.  An immediate problem I see with the declaration:

```

class (FieldElement e) => RowOpable e where

```

Is that once you start writing methods below, you only have one type variable.  There should in fact be two, one to represent the "RowOpable" type, and the other to represent the "FieldElement" that is used in the row ops.

So for example, lets say I want to declare a typeclass "List", and I've already declared a typeclass "Listable", and only "Listable" things can be put in lists.  By your formula, I have

```

class (Listable e) => List e where

```

I'd like to have a function like:
```

addToList :: (Listable e, List l) => l -> e -> l

```

However, note that there are two type variables in this function--one for the list, the other for the listable object.  In the formulation:

```

class (Listable e) => List e where

```

You only have one type variable, which is why I believe that this is actually the syntax for saying that List is a subtype of Listable, which is not what I want.

I've done some more reading in the interim, I think what I'm trying to do in Haskell parlance is declare a typeclass for a type constructor (specifically, one that takes a concrete type and produces a concrete type as a result, or *->*).  An example for this I've found online is the "Functor" typeclass:

```

class Functor f where
  fmap                  :: (a -> b) -> f a -> f b

```

The question I guess I'm trying to figure out here is whether there's a way to declare a type constructor that places a limitation on the input type--i.e., the input type has to be a subtype of a certain typeclass.

So thanks for your reply, but it's still not clear to me that this applies to the situation that I'm describing.

Thanks.

---

### Post by schauerlich on 2011-12-27
> **ceclauson said:**
> Thanks for the continued replies.

I'm still trying to understand this, though.  An immediate problem I see with the declaration:

```

class (FieldElement e) => RowOpable e where

```

Is that once you start writing methods below, you only have one type variable.  There should in fact be two, one to represent the "RowOpable" type, and the other to represent the "FieldElement" that is used in the row ops.


You're right, I read your original post wrong. Sorry. So, in your example in the OP, the type variable [FONT="Courier New"]a[/FONT] would be something like [FONT="Courier New"][][/FONT] (ie some container) and [FONT="Courier New"]s[/FONT] might be [FONT="Courier New"]Double[/FONT], and you want to make sure that any [FONT="Courier New"]a[/FONT] you choose is only allowed to contain a type that implements [FONT="Courier New"]FieldElement[/FONT]? Ex:

```
class FieldElement e where
    -- whatever

instance FieldElement Double where
    -- whatever

class RowOpable a where
    -- whatever

instance RowOpable [] where
    -- whatever

```

where [FONT="Courier New"]RowOpable [Double][/FONT] is legal but [FONT="Courier New"]RowOpable [Bool][/FONT] is not?

I'm not terribly experienced with Haskell, but given that understanding, I think what you had in the OP is correct, specifying [FONT="Courier New"]FieldElement s[/FONT] in the type of each function. I'm not sure if there's a cleaner/less redundant way to do it.

Does this look like what you want?

```
class FieldElement a where
  fmul :: a -> a -> a
  
instance FieldElement Double where
  fmul = (*)
  
class RowOpable a where
  scaleRow :: (FieldElement s) => a s -> Int -> s -> a s
  
data (FieldElement a) => Matrix a = Matrix {
  size :: Int,
  dat :: [[a]]
  } deriving (Show)

instance RowOpable Matrix where
  scaleRow m row scalar = Matrix {size = size m, dat = newdat}
    where 
      (before, (e:after)) = splitAt row (dat m) -- unsafe, but just an example
      newdat = concat [before, [map (fmul scalar) e], after] -- yuck

m1 = Matrix {
  size = 2,
  dat = [[1.0..5.0],[6.0..10.0]] :: [[Double]]
  }

-- illegal
-- m2 = Matrix {
--   size = 1,
--   dat = [[True, False, True, False, True]] :: [[Bool]]
--   }


-- example:
-- > scaleRow m1 1 2.0
-- Matrix {size = 2, dat = [[1.0,2.0,3.0,4.0,5.0],[12.0,14.0,16.0,18.0,20.0]]}
```

Simplified, of course. 

The problem you had with the monomorphism restriction is that floating point literals have the type [FONT="Courier New"](Fractional t) => t[/FONT], not [FONT="Courier New"]Double[/FONT], so there's an ambiguity there. If you specify the type of dat it stops complaining.

---

