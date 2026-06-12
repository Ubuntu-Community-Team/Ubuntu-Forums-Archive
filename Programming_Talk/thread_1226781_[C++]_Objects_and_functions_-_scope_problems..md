---
title: "[C++] Objects and functions - scope problems."
date: 2009-07-29
forum: Programming Talk
---

### Post by credobyte on 2009-07-29
I can't figure out how to call [COLOR=Blue]WelcomeMessage()[/COLOR] without creating my player as a global object ( before all other functions ) :-s [COLOR=Blue]A[/COLOR] example will say that I do not have a function called [COLOR=Blue]WelcomeMessage()[/COLOR], [COLOR=Blue]B[/COLOR] example will say that I do not have a variable player. Any ideas ?

A:
```
void StartGame()
{
    Player player("Alkash");
    WelcomeMessage();
}

void WelcomeMessage()
{
    cout << "Welcome, " << player.name << "! \n";
}

```B:
```
void WelcomeMessage()
{
    cout << "Welcome, " << player.name << "! \n";
}

void StartGame()
 {
     Player player("Alkash");
     WelcomeMessage();
 }

```

---

### Post by Mirge on 2009-07-29
> **credobyte said:**
> I can't figure out how to call [COLOR=Blue]WelcomeMessage()[/COLOR] without creating my player as a global object ( before all other functions ) :-s [COLOR=Blue]A[/COLOR] example will say that I do not have a function called [COLOR=Blue]WelcomeMessage()[/COLOR], [COLOR=Blue]B[/COLOR] example will say that I do not have a variable player. Any ideas ?

A:
```
void StartGame()
{
    Player player("Alkash");
    WelcomeMessage();
}

void WelcomeMessage()
{
    cout << "Welcome, " << player.name << "! \n";
}

```B:
```
void WelcomeMessage()
{
    cout << "Welcome, " << player.name << "! \n";
}

void StartGame()
 {
     Player player("Alkash");
     WelcomeMessage();
 }

```

If using example A, put a function prototype before StartGame() definition.

```

void WelcomeMessage();
void StartGame();

void StartGame()
{
    Player player("Alkash");
    WelcomeMessage();
}

void WelcomeMessage()
{
    cout << "Welcome, " << player.name << "! \n";
}

```

---

### Post by credobyte on 2009-07-29
> **Mirge said:**
> If using example A, put a function prototype before StartGame() definition.

```

void WelcomeMessage();
void StartGame();

void StartGame()
{
    Player player("Alkash");
    WelcomeMessage();
}

void WelcomeMessage()
{
    cout << "Welcome, " << player.name << "! \n";
}

```

Yeah, I already did it as a temporary solution, but I would like to know if there's a way to do this without pre-declaring functions or variables ( player is an object and is being created from default values, containing user input as a name, so .. I can't really make it before all other functions ) ?

---

### Post by Mirge on 2009-07-29
Well, if you went with example B:

```

void WelcomeMessage()
{
    cout << "Welcome, " << player.name << "! \n";
}

void StartGame()
 {
     Player player("Alkash");
     WelcomeMessage();
 }

```
Then you would need to pass your Player object to the WelcomeMessage() function. Though I'd still recommend using function declarations.

An example rewrite of B:

```

void WelcomeMessage(Player* p)
{
     cout << "Welcome, " p->name << "!" << endl;
}

void StartGame()
{
     Player player = Player("Alkash");
     WelcomeMessage(&player);
}

```

---

### Post by credobyte on 2009-07-29
> **Mirge said:**
> Well, if you went with example B:

```

void WelcomeMessage()
{
    cout << "Welcome, " << player.name << "! \n";
}

void StartGame()
 {
     Player player("Alkash");
     WelcomeMessage();
 }

```Then you would need to pass your Player object to the WelcomeMessage() function. Though I'd still recommend using function declarations.

An example rewrite of B:

```

void WelcomeMessage(Player* p)
{
     cout << "Welcome, " p->name << "!" << endl;
}

void StartGame()
{
     Player player = Player("Alkash");
     WelcomeMessage(&player);
}

```

Lifesaver :) Thnx - problem seems to be solved !

---

### Post by Mirge on 2009-07-30
> **credobyte said:**
> Lifesaver :) Thnx - problem seems to be solved !

No worries. I used a pointer so that you're passing the address of the object, rather than creating a copy of the object itself (performance & memory usage). In such a small example, it likely wouldn't matter... but it would be considered better practice, imho.

& in that context (function parameter).. is passing the "address-of" the object.

Using -> means "points to", used with pointers. If you were to pass a copy of the object instead of the address of the object, you'd use "." instead.

Pointer: p->name
Copy: p.name

---

### Post by dribeas on 2009-07-30
If you are really working with C++ and you want to learn the language this is more idiomatic:

```

class Player
{
public:
   Player( std::string const & name ) 
       : name_( name ) {}                        // initialization list: copies name
   std::string const & name() const { // const: accessor does not modify
      return name_;
   }
private:
   std::string name_;
};

void welcome( Player const & player ) // welcome function will not modify the passed in parameter
{
   std::cout << player.name() << std::endl; // can call name() as it is declared const: does not modify the object
}
void start_game()
{
   Player player( "the name" );
   welcome( player );
}
int main()
{
    start_game();
    // player is undefined here
}

```

But if you create the variable in the scope of the 'start_game' function it will not be visible outside of it (after the call, in main you will not be able to use it). You can encapsulate the player object (together with other data you might need) inside a 'game' object, then the start_game() would be the initialization/construction of that object and the objects would be available from within the 'game' object during the whole life span of that object.

There are a couple of advantages on using references instead of pointers, most of which boil down to 'reference semantics are more clear'. You do not have to deal with management problems: inside your function you do not need to think on whether you are assuming ownership of the passed in pointer (and must thus delete it) or not: with references ownership is never passed in. From the other side, the caller does not need to deal with ownership: if you pass a pointer into a function, will the function take ownership and delete it?, when you pass a reference you know that your object will still be there after the function call. The function does not need to deal with null pointers passed as arguments and does not need to check for pointer validity before dereferencing. The user knows that it cannot pass a null pointer into the function and cannot by mistake call the function with no parameter (null pointer). With a function that takes a pointer, the compiler will allow you to pass '0' (null) and the function will die if it tries to dereference it. With references the user must do extra effort to pass a null reference (can create a pointer variable that holds '0' and dereference it in the call, but if you avoid using pointers in general (unless you need to) this will be very rare.

---

