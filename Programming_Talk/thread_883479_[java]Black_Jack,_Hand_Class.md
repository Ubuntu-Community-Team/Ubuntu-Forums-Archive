---
title: "[java]Black Jack, Hand Class"
date: 2008-08-08
forum: Programming Talk
---

### Post by Pyro.699 on 2008-08-08
Hello,

I'm currently working on a program that simulates a Simple Blackjack hand. For each of the players I've just used something like:

[php]
	static String[] player = new String[31];
	static String[] dealer = new String[31];
[/php]

What i would like to do is have something setup that is more... manageable; like:

[php]

class Main{
	static Hand player = new Hand();
	static Hand Dealer = new Hand();
	
	...
}

class Hand{
	static hand = new String[31];
	void add(String x){
		hand[hand.length-1]=x;
	}
...
}
[/php]

The problem with that is because *hand* is static it seems there is only one instance of it... it will always say i have 2 of the exact same cards in their hand (same suit and value).

Thanks for your help
~Cody Woolaver

---

### Post by NovaAesa on 2008-08-08
Having a variable set as static will make the variable belong to the class rather than instances of the class. It would probably be better to have hand as non-static (you just leave out the static keyword). I'm kinda a bit confused about why you have "Dealer" in your Main class as an array though. Isn't there only one dealer per hand?

---

### Post by dwhitney67 on 2008-08-08
You may also want to consider designing your application before you lay down one line of code.

The things you should consider wrt the Black Jack Game is the Cards (and their face values) and the Number of Cards.  There is also one Dealer.  There can be N Players.

Start thinking in OOD terms to define what each of these represent and "can do":
[LIST]
[*]Game
[*]Cards
[*]Dealer
[*]Player
[/LIST]

---

### Post by Pyro.699 on 2008-08-08
Its an array because it represents the number of cards they can have... i have the cards system set up like this:

each card can be represented as suit:value. suit values range from 0-3 (spades,clubs,hearts,diamonds), then the value ranges go from 0-12(0=ace,12=king). The dealer array could look like this..

[0] => 2:9 //10 of hearts
[1] => 0:12 //king of spades

its set to 31 because thats just a set number i can use... the max number of cards in a hand could be...

2,3,4,5,6
2,3,4,5,6
2,3,4,5,6
2,3,4,5,6

HIGHLY unlikely, but still possible so i guess i could set it to 20, although, there would need to be ways to identify when the user split the 2's

but player[31] = player 1 and dealer[31] = the only dealer

Could you show me how to make an instance of *hand*?

thanks again
~Cody Woolaver

---

### Post by Pyro.699 on 2008-08-08
> **dwhitney67 said:**
> You may also want to consider designing your application before you lay down one line of code.

The things you should consider wrt the Black Jack Game is the Cards (and their face values) and the Number of Cards.  There is also one Dealer.  There can be N Players.

Start thinking in OOD terms to define what each of these represent and "can do":
[LIST]
[*]Game
[*]Cards
[*]Dealer
[*]Player
[/LIST]
i actchually do have all those classes setup, i just forgot that it would be more efficient to have the players hand setup like that too.

Thanks
~Cody Woolaver

---

### Post by NovaAesa on 2008-08-08
I agree with dwhitney67 on this one. You should really design the classes before you start coding. I had assumed that you were already trying to do this from a OOP (Object Oriented Programming) point of view, but maybe I'm wrong about that.

I would start with designing a "card" class. Two member variables would probably be needed for it, two integers. One for suit and one for rank. You would then need methods that could access these variables i.e. getSuit and getRank. You would keep designing the different abstract "objects" in this way until you have each part of the problem solved. You then string them all together :P

btw, in Java, you can create an instance of an object by using:
<ObjType> <refName> = new <ObjType>(<paramListCommaDeliminated>);

Just replace the things in angle brackets with what you require.

---

### Post by dwhitney67 on 2008-08-08
Heed the suggestion from my earlier post.

Write down the requirements of the game, then maybe write some Use Cases that explain how the requirements will be met.  Then from the Use Cases, pull of the objects that will be needed by the application.

If "Hand" turns out to be one of those objects, describe its functionality.  Off the top of my head, a Hand can be empty, or it can be with 2 cards, maybe more.  What do the cards add up to?  If it is 21, is it a black jack?  Will you permit a splitting of the initial 2 cards?

I know you want to start programming, but in my opinion you need to take a step back to design your application.  Yes it sucks, but that is how things are done in the real world.

---

### Post by drubin on 2008-08-08
> **dwhitney67 said:**
> 
[LIST]
[*]Game
[*]Cards
[*]Dealer
[*]Player
[/LIST]

I could even go further and say replace Cards, with Card(one single card) and add a Deck class as well that handles getting cards, shuffling and such

---

### Post by Tomosaur on 2008-08-08
If you're using OOP - then you should use objects. Create a card class, and your life will be so much easier. From there you can just generate a full deck of cards and assign each card to a hand.

OOP allows you to think about a problem as if it's in the 'real world'. Take advantage of that fact during your design (and really it only has to be a sheet of paper to work stuff out on - it's not like you're building an OS here :P ), and you'll find you just won't really run into this kind of problem. Don't think about cards as numbers - think of them as cards. When you need to find out what a particular card is, you can just use:
```

int number = card.getNumber();
int suit = card.getSuit();

```

Easy!

---

### Post by TreeFinger on 2008-08-08
> **dwhitney67 said:**
> You may also want to consider designing your application before you lay down one line of code.

The things you should consider wrt the Black Jack Game is the Cards (and their face values) and the Number of Cards.  There is also one Dealer.  There can be N Players.

Start thinking in OOD terms to define what each of these represent and "can do":
[LIST]
[*]Game
[*]Cards
[*]Dealer
[*]Player
[/LIST]

What would be contained in the Game class?

---

### Post by dwhitney67 on 2008-08-08
The game's "engine".  Shuffle the deck of cards, prompt the player to lay down a bet, deal out the cards, prompt player if he/she wants to hit or stay, etc.

I should further note that the Game should contain everything in it's environment (Deck, Dealer, Players, etc.).  Probably the first question to ask the game operator is how many players will play the game.

---

### Post by Pyro.699 on 2008-08-08
This is just a project im working on to a) better my experiance with programming (which is what this is doing, thankyou all for your comments<3) b) learn some fun card games in the process, the idea of having an engine would imply it could be used in other settings, aslong as the "game" calss changed.

What would the contents of the Player class be? which would contain data, objects and methods such as: the current cards in the players hand, adding a new card to the players hand, removing a card from the players hand, counting how many cards they have, recognizing when the player has split their cards (according to the rules you can split infinate times, meaning if i have 4,4,4,4 then i could split it 3 times, giving me 4 seperate runs beginning with 4).

Thanks for your help
~Cody Woolaver

---

### Post by issih on 2008-08-08
I'd agree that its worth thinking through how you want the overall structure of your classes to work together ahead of time. Often you will only find the best solution once you have started and have to go back and rejig things, but thats just life.

One thing that hasn't been said (I think) is that it is well worth trying to think about things in as abstract a way as possible. Try to make the objects very generic, and include as little code specific to your game as possible. This makes things much more reuseable.

For example, if you want to make a shoe of cards to deal from, you could just have that shoe representing N decks of cards as a simple array of length N*52, then randomly assign n 1's n 2's n 3s and so on....

For blackjack the suits are irrelevant so why bother recording them.

That show will work perfectly for your needs, but is useless if you ever want to do anything else.

Instead define a card object that is just a simple placeholder with variables for suit and value.

Then a deck which creates 52 cards defining a full deck of cards, possibly with optional jokers and a few obvious functions, e.g. shuffle.

Now define a shoe as holding n decks and a shuffle function that iterates through each deck and calls shuffle on the Deck object.

Doing it this way creates generic objects that can be useful in any card game you create from here on out.

You can extend this thinking to game play too, its not directly applicable to your game, but I have a "stack" class somewhere, which literally is the idea of a pile of cards, that you can add to or take away from. This object calls a validation method every time the stacks contents are changed.

By inheriting off this base class and simply altering the validation method you can create stacks that basically implement all the gameplay areas of a lot of patience type games.

Be as generic as possible and subclass things so that you can utilise polymorphism

Hope that helps

---

### Post by dwhitney67 on 2008-08-08
> **Pyro.699 said:**
> ...
What would the contents of the Player class be? which would contain data, objects and methods such as: the current cards in the players hand, adding a new card to the players hand, removing a card from the players hand, counting how many cards they have, recognizing when the player has split their cards (according to the rules you can split infinate times, meaning if i have 4,4,4,4 then i could split it 3 times, giving me 4 seperate runs beginning with 4).

Thanks for your help
~Cody Woolaver
Think about what the Player possesses and what actions the Player can do.  A Player will find no joy at the BJ table without a pot o' gold (i.e. funds).  A Player will have to wager a bet.  A Player will hold onto a set of Cards; perhaps this can be a Hand object?  A Player will be able to 'hit' (to obtain another Card for their Hand), or 'stay'.  A Player should be compensated if they win.

As for where to store the Player's waged amount while a particular round is in progress, perhaps it can be added to the Dealer's pot (after all, the dealer is representing the "house").

The other attributes you mentioned about a Player are also true.  For now, I would worry about the Player holding one hand of cards; worry about splitting and double-down bets later on.

---

### Post by Pyro.699 on 2008-08-08
That is all true, but the entire point of this thread was to figure out a way that i can have a class that contains all the cards. I understand i need to plan out, and i have started to do that and i need help with the area of making the class, not planning it out.

How do i make an instance of a variable in a class, and not the vairable belong to the class (look at the first post).

Thanks
~Cody Woolaver

---

### Post by nvteighen on 2008-08-08
Thanks! You have inspired me for my next Python-learning exercise: a card game... but probably not Black Jack. (Don't sue me for stealing ideas, please!).

It's quite a good task for a OOP language. Good luck!

---

### Post by dwhitney67 on 2008-08-08
> **Pyro.699 said:**
> ...
How do i make an instance of a variable in a class, and not the vairable belong to the class (look at the first post).

Thanks
~Cody Woolaver
The class can hold an instance of an object; typically developers refer to this as a data member of the class.

If the class needs an instance of an object that is not part of the class, then this object will either have to be passed into the Class's constructor (as a referenced object), or as a parameter into a function, or the external object can be designed to be a singleton object.

Here's an example of how to pass an object by reference into the constructor:
[PHP]class SomeClass
{
  public:
    SomeClass( SomeOtherClass & other )
      : m_other( other )
    {
    }

    ...

  private:
    SomeOtherClass & m_other;
};

int main()
{
  SomeOtherClass other;

  SomeClass someClass( other );

  ...
}[/PHP]

I'm sure you are familiar with passing parameters (by reference) to class methods.  Let me know if you need an example for a Singleton object, or just google for it.

---

### Post by Pyro.699 on 2008-08-08
Thankyou,

What about variables that become an instance to the class? say for every instance of the class that is called, there is a new variable for that aswell.

Thanks
~Cody Woolaver

---

### Post by dwhitney67 on 2008-08-08
> **Pyro.699 said:**
> Thankyou,

What about variables that become an instance to the class? say for every instance of the class that is called, there is a new variable for that aswell.

Thanks
~Cody Woolaver
If you have a class, such as this one:
[PHP]class Foo
{
  public:
    Foo() {}

  private:
    int m_value1;
    int m_value2;
    static int m_value3;
};[/PHP]
And then instantiate two or more of these classes; for instance:
[PHP]Foo foo1;    // this is an instance of the Foo class, and 'foo1' is the variable.
Foo foo2;
Foo foo3;[/PHP]
Each of these objects will have a unique member data for 'm_value1' and 'm_value2'.  As for 'm_value3', each of the objects will share this value because it is declared as static.

The same concept applies if a class were to hold more complex data objects.  The best thing to do when you have questions like this is to write simple 20-30 line programs that you can use to test your questions.

---

### Post by issih on 2008-08-08
Brief point, the OP is asking about java, a language in which just about everything is passed by reference by default, you don't need to use the & operator. The last few replies have been showing how to do things in c++, much of the syntax is the same, but there are subtle differences. The ideas are all very similar at this point, but there are important subtleties to be aware of.

Object instantiation:

C++:  Foo aFoo;
java: Foo aFoo = new Foo();

Passing Object by reference:

C++:  void myMethod(Foo & aFoo){}
java: void myMethod(Foo aFoo){}

Initialisation of class fields in constructor:

C++:  Foo(Class1 param1, class2 param2):
        aClass1(param1),
        aClass2(param2)
      {}

java: Foo(Class1 param1, Class2 param2){
           aClass1 = param1;
           aClass2 = param2;
      }

Also in java the method scope modifiers are attached to each method so methods generally have a form like:

public void methodName(ParamType paramName)

C++ specifies the modifiers with

public:

and that scope then applies to all methods listed until another modifier is found or the class definition ends.

Finally I don't think java uses a semicolon after the class definition terminating '}', but I can't actually remember.

---

### Post by drubin on 2008-08-08
> **issih said:**
> Brief point, the OP is asking about java, a language in which just about everything is passed by reference by default, you don't need to use the & operator. The last few replies have been showing how to do things in c++, much of the syntax is the same, but there are subtle differences. The ideas are all very similar at this point, but there are important subtleties to be aware of.

Every single Object is passed by reference, only primitive char,int,double,float, are passed by value in Java

> **issih said:**
> 
Finally I don't think java uses a semicolon after the class definition terminating '}', but I can't actually remember.
It does not, but putting it there will not cause a syntax error.

---

