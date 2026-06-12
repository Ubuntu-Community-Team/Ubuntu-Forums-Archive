---
title: "[Java] Generics design problem"
date: 2008-09-06
forum: Programming Talk
---

### Post by CptPicard on 2008-09-06
Tinny, I'm looking at you... ;)

Ok, so here I've got another of these cases where I feel like I'm just fighting a static type system without really understanding how I should go about this :( (not to mention that dynamic typing would solve the problem trivially) So I would love to hear design ideas.

Situation is as such: I have a hierarchy of *Analyzers* for particular games. There is an abstract superclass *AnalyzerBase*, an abstract subclass *SparseAnalyzerBase* and then a number of concrete analyzers, let's just generally call a subclass of *SparseAnalyzerBase* a *GameAnalyzer*.

A common feature of all analyzers is that they manipulate a large array of *Records*, that have the following (simplified) interface:

```

public interface IAnalyzerRecord<T extends Comparable<? super T>> {
	
	public ArrayList<T> getRow();
	
}

```

The array of "Comparables" is the key here as it is being used to implement lexical ordering of records. Implementations of IAnalyzerRecord are typically inner classes of various Analyzer classes.

AnalyzerBase and SparseAnalyzerBase are currently as follows

```

public abstract class AnalyzerBase<T extends IAnalyzerRecord<?>> implements Serializable {

...

public abstract class SparseAnalyzerBase<T extends IAnalyzerRecord<K extends Comparable<? super K>>> 
	extends AnalyzerBase<T> {


```

Now, these definitions are, of course, wrong, but should perhaps give an idea of what I am trying here. :(

I can make at least the compiler like the definitions of classes if I do SparseAnalyzerBase like so:

```

public abstract class SparseAnalyzerBase<T extends IAnalyzerRecord<?>> 
	extends AnalyzerBase<T> {

```

But the problem is that in SparseAnalyzerBase, I really want to "know" that IAnalyzerRecord really does return to me an ArrayList of Comparables, because this comparison info is to be used in searching records in methods that would be nicely shareable among subclasses.

In particular, if in SparseAnalyzerBase I attempt to do

```

	private void foo(T x) {
		x.getRow().get(0).compareTo(x.getRow().get(1));
	}

// barfs with

The method compareTo(? super T) in the type Comparable<? super T> is not applicable for the arguments (capture#2-of ?)

```


I can make the compiler shut up with 

```

public abstract class SparseAnalyzerBase<T extends IAnalyzerRecord<? extends Comparable>> 
	extends AnalyzerBase<T> {

```

but this of course results in warnings,

```

Comparable is a raw type. References to generic type Comparable<T> should be parameterized
```

Which is probably ok as I know I won't be giving it weird stuff at runtime, but I still would love to hear if I'm doing it wrong and there are better ideas, I am quite uncomfortable with this...


I willingly admit that I suck at generics and always just feel like I'm doing some voodoo to make the compiler like me....

EDIT: Hmmph... I found a way to do it by explicitly declaring the "row item" type, I still don't quite like it though...

```

public abstract class SparseAnalyzerBase<I extends Comparable<? super I>, T extends IAnalyzerRecord<I>> 
	extends AnalyzerBase<I, T> {

```

---

### Post by tinny on 2008-09-08
To be honest I to find all those generic sharp edges to be quite confusing (most of my professional work is still done with Java 1.4 :( ). Im very average with Generics.

So I played around with your example for an hour or so and I just kept chasing my tail and coming back to your original solution. So the type system beat me :(

If I was to approach this problem with a clean slate I think id look at a solution that leveraged more off pure polymorphism as opposed to a templating approach.

So sorry, I cant help with this one. Good luck.

(Id be very interested to see any solid generic solution you come up with)

---

### Post by CptPicard on 2008-09-08
Thanks for giving it a shot, I appreciate it. It's actually valuable to know that I'm not the only one having issues with this so it's not just because I suck, but because it's probably genuinely a problematic approach :)

I do think that Java's Generics are in some fundamental sense missing something... I am not sure what it is. Perhaps some kind of type-inferencing logic that would make declarations like in the first "suggestion" to actually work -- IMO what I tried first makes sense, but the type system doesn't like it.

I ended up just going for the solution of essentially declaring both the item type and the record type, which is parametrized by the same item type. At least it does what I need it to do, although somewhat inelegantly. The good part is that all the concrete Analyzers aren't generic, so they just extend the base class with types filled in, so the ugliness doesn't spill out into the general API :)

EDIT Errr damn I am such an idiot... of course you can get away with just declaring the item type as the Analyzer's "T" and then you have an IAnalyzerRecord<T> implemented inside... I guess I didn't originally see it because I just couldn't think about parametrizing the public class analyzer by the inner class parameter type (it's slightly "not what I mean" really... but if I must give the inner item type, I don't need the "record type" anymore...)

---

### Post by tinny on 2008-09-08
:lolflag:

My brain just melted :)

---

### Post by CptPicard on 2008-09-08
Actually, my declarations of my own idiocy were premature, I was just hacking around in this again... I really do need to declare both item type and record type, it is not sufficient to only give item type and rely on polymorphism for the record type.

Then again, I guess I understand now better why I need to do it like this...

---

### Post by Desty on 2008-11-10
Hi CptPicard,  I just ran into it with a slightly more obviously-dynamic-typing-ish case and thought it would be worth discussing:
```
public boolean isBetterThan(List<Comparable<?>> competingScoreValues) {
		List<Comparable<?>> scoreValues = getAttributeValues();
		Iterator<Comparable<?>> iterator = competingScoreValues.iterator();
		for(Comparable<?> scoreValue : scoreValues) {
			**if(scoreValue.compareTo(iterator.next()) > 0)**
				return true;
		}
		return false;
	}
```
This spews a similar error message to the one you posted. I suspect that essentially, this is the Java compiler telling me to get bent because I'm trying to have my cake and eat it by attempting to compare any Comparable subclass against any other.

For example, the code implies that scoreValue might actually be an integer, while iterator.next() might return a String. i.e.:
```
		Comparable<?> a = "Hi!";
		Comparable<?> b = 1;

		if(a.compareTo(b) > 0)
			return true;
```
So the error makes sense from a static-typing point of view - there are combinations of (Comparable<?>) subtypes that cannot be compared against one another.

Perhaps what we really want is something like:
```
public int isBetter(Comparable<?something> a, Comparable<?something> b) {
		return a.compareTo(b);
}
```
Where "?something" is a kind of pattern-match where we say "anything, as long as ?something of a is the same type of ?something in b.

Uh. So, anyone know if this is possible in Java? :) Maybe not, since it would not be verifiable at compile-time.
My lame hack solution so far has been to simply remove the <?> specifier from <Comparable<?>>, and put up with Java's whinging about unsafe typing. Ultimately, this is a case of a dynamic-typing, where the contents of the lists (and their types) are decided solely at runtime.
](*,)

---

### Post by Shin_Gouki2501 on 2008-11-10
i know its german but with some translator help you may be able to find enlightment as i did:
[http://www.mathematik.uni-marburg.de/~henkel/paradigmen/GenericsInScalaUndJava.pdf](http://www.mathematik.uni-marburg.de/~henkel/paradigmen/GenericsInScalaUndJava.pdf)

i hope this help's you with the variance problem.

---

### Post by achelis on 2008-11-10
> **Desty said:**
> Hi CptPicard,  I just ran into it with a slightly more obviously-dynamic-typing-ish case and thought it would be worth discussing...


Errm, I'm not exactly sure I understand what you are trying to do but... (and not sure if it should be discussed in this thread or moved to another??)
```

public <E> int  isBetterThan(Comparable<E> score1, E score2) {
	return score1.compareTo(score2);
}

```

This would require that score2 is of some type that score1 is able to compare...

As for the list thing it is required that the getAttributes method returns objects of the type the list of comparables can compare to:
```

public <E, F extends Comparable<E>> boolean isBetterThan(List<F> competingScoreValues) {
	Iterator<E> iterator = getAttributes();
	for (F f : competingScoreValues) {
		if(f.compareTo(iterator.next()) > 0)
			return true;
	}
	return false;
}

```

@CptPicard: I'm afraid you lost me in the intro... and not sure I'd be able to help anyways ;)

---

### Post by Desty on 2008-11-10
> **achelis said:**
> Errm, I'm not exactly sure I understand what you are trying to do but... (and not sure if it should be discussed in this thread or moved to another??)
Perhaps; I replied to this one because it was one of the only hits on google for the compareTo type error message.

Thanks for your code here - I wasn't aware of this more flexible generic syntax. I think it'll work for my code \\:D/ (with all the silly smilies, I'm surprised there's no thumbs-up one)

---

### Post by drubin on 2008-11-10
> **tinny said:**
> To be honest I to find all those generic sharp edges to be quite confusing (most of my professional work is still done with Java 1.4 :( ). Im very average with Generics.
/me too.

I use the basics but the further down the generic lists you go the more complicated your code is to understand. Just my 2cents.

---

