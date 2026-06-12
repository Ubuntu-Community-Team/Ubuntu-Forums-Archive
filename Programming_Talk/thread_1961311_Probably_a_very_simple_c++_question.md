---
title: "Probably a very simple c++ question"
date: 2012-04-19
forum: Programming Talk
---

### Post by earthpigg on 2012-04-19
[The header.]("http://pastebin.com/YtTg4fnY") (tried commenting out "private" to make it all public just in case that was the cause.)
[The implementation.]("http://pastebin.com/NBDmvwU2")
[The main()]("http://pastebin.com/6mKDD92A")

The error I'm getting is 

```
...main.cpp|16|error: cannot call member function &#8216;void ShuffledDeck::displayDeck()&#8217; without object|
||=== Build finished: 1 errors, 0 warnings ===|

```

And it's pointing me to ShuffledDeck:displayDeck(); in the main.cpp.

Doesn't "deck currentDeck[52]" in the header declare an object, and isn't it populated in the implementation file?

(I'm trying to learn good habits; I know I could code this with*out* using classes or even functions...)

---

### Post by Tony Flury on 2012-04-19
> **earthpigg said:**
> 
Doesn't "deck currentDeck[52]" in the header declare an object, and isn't it populated in the implementation file?


It declares an array of deck instances, but according to the error message the displayDeck function is a method of the ShuffleDeck class.

I think you have your classes/methods messed up.

---

### Post by earthpigg on 2012-04-19
> **Tony Flury said:**
> It declares an array of deck instances, but according to the error message the displayDeck function is a method of the ShuffleDeck class.

I think you have your classes/methods messed up.

Here's what the displayDeck function is:

```
void ShuffledDeck::displayDeck()
{
   cout << endl << "Displaying deck:" << endl;
   for (int i = 0; i < 52; i++)
   {
      cout << "Card #" << i+1 << ":\t" << currentDeck[i].m_value << "  "
      << currentDeck[i].m_face << "  " << currentDeck[i].m_suit << endl;
   }

}
```

And, inside class ShuffledDeck:

```
class ShuffledDeck
{
public:
   ShuffledDeck();

   //mutators
   void shuffle();

   //accessors
   void drawOne();
   void drawCards(int);
   void displayDeck();

//private:
   struct deck
   {
      int m_value;
      string m_face;
      string m_suit;
   };

**   deck currentDeck[52];**
   void generateDeck();
};
```

Isn't currentDeck now an object, displayDeck a method, and ShuffledDeck a class?

---

### Post by dwhitney67 on 2012-04-19
> **earthpigg said:**
> [The header.]("http://pastebin.com/YtTg4fnY") (tried commenting out "private" to make it all public just in case that was the cause.)
[The implementation.]("http://pastebin.com/NBDmvwU2")
[The main()]("http://pastebin.com/6mKDD92A")

The error I'm getting is 

```
...main.cpp|16|error: cannot call member function ‘void ShuffledDeck::displayDeck()’ without object|
||=== Build finished: 1 errors, 0 warnings ===|

```

And it's pointing me to ShuffledDeck:displayDeck(); in the main.cpp.

Doesn't "deck currentDeck[52]" in the header declare an object, and isn't it populated in the implementation file?

(I'm trying to learn good habits; I know I could code this with*out* using classes or even functions...)

You need to have an instance of the class (ShuffledDeck) before you can call a non-static method of that class.  For example
```

int main()
{
    ShuffledDeck theDeck;

    theDeck.displayDeck();
}

```

P.S.  In the future, please don't code on PasteBin.  Post it here at Ubuntu Forums.  There's no telling how long your code will be available at PasteBin, and should it ever get deleted, then this thread is worthless to the next person who comes along.

---

### Post by earthpigg on 2012-04-19
I knew I was going to slap myself on the forehead. Thanks, dwhitney67!

> **dwhitney67 said:**
> P.S.  In the future, please don't code on PasteBin.  Post it here at Ubuntu Forums.  There's no telling how long your code will be available at PasteBin, and should it ever get deleted, then this thread is worthless to the next person who comes along.

Roger that.

---

