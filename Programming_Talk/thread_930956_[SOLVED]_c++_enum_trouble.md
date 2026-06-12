---
title: "[SOLVED] c++ enum trouble"
date: 2008-09-26
forum: Programming Talk
---

### Post by chris200x9 on 2008-09-26
Hi I'm writing a dope wars clone and I am having trouble with enum I've enumed drugs like weed and crack so I can keep track of them like drugs[weed] but now I'm having trouble though with a check if they have 0 of a drug they are trying to sell the user puts in a choice then I see if drugs[choice] == 0. but I keep getting the error ```
 no match for 'operator[]' in '((Guy*)this)->Guy::drugs[choice]' 
```

---

### Post by dwhitney67 on 2008-09-26
I (we) have no idea how you declared 'drugs', thus I cannot tell if it is an array, a vector, or something else.

You may want to consider posting some more code.

P.S.  Why are you prefacing 'drugs' with 'Guy::'.  Is drugs a static object?  And if it is, then there is no need for the 'this->'.  You should also never have to cast the pointer of 'this' to anything.  Something like this should suffice (if 'drugs' is an array, vector, etc):
[PHP]this->drugs[choice];[/PHP]

---

### Post by chris200x9 on 2008-09-27
hi, my code is
```
 	cout << "what would you like to sell?\n";
			cin >> choice;
			if ( drugs[choice] == 0)
			{
				cout << "you don't have any " << choice;
			}

```

and I declared drug like this
```

enum drugs {
		weed,
		crack
	};

```

and I have this a my private variable 
```
 int drugs[]

```


I am sorry for my bad design but I started and my design just kept getting worse as time went on, as a newbie I just want to get a *working* version and the worry about rewriting it cleaner.

---

### Post by John164918a on 2008-09-27
The enum type is only useful for specifying names of things within the source code. That is to say if you want to be able to type and then print "heroin" for instance then you need to use strings. You could select your drug by typing in an integer which would then index an array of strings or a Drugs class.

Also in the first declaration you posted, drugs is an enumerative type. The next one should declare an instance of drugs_instance_with_a_different_name so it would look like

```

enum drugs drugs_instance_with_a_different_name;
```

The enum type drugs is not a variable and cannot be used to store information.
The instance of drugs can be used to store information.

Also, the compiler just told you you cant index into an enum like you can an array.

---

### Post by chris200x9 on 2008-09-27
thanx! so your basically saying I would need to do something like this: [http://ubuntuforums.org/showthread.php?p=5544215#post5544215](http://ubuntuforums.org/showthread.php?p=5544215#post5544215) correct?

---

### Post by dwhitney67 on 2008-09-27
> **chris200x9 said:**
> thanx! so your basically saying I would need to do something like this: [http://ubuntuforums.org/showthread.php?p=5544215#post5544215](http://ubuntuforums.org/showthread.php?p=5544215#post5544215) correct?

What was posted by John164918a is not entirely correct; there are cases where enumerated values are used as integer indexes into arrays (vectors, maps, etc).

You probably should consider writing test programs to augment your knowledge of the STL map before you start tinkering with your game application.

You should consider defining a structure to hold specific drug information that your game's drug dealer will need, and not just rely on the drug's name and quantity.

For example:
[PHP]
#include <map>
#include <string>

class DrugDealer
{
  public:
    ...

  private:
    // Structure to add info for each type of drug available
    //
    struct DrugFact
    {
      unsigned int amountInStock;
      std::string  unitType;        // "kilo", "keys", "grams", etc.
      float        costPerUnit;
    };

    // Handy-dandy typedefs (for those who do not like to type)
    //
    // The "key" of the STL map is the drug-name.  The "value" is
    // the a DrugFact structure.
    //
    typedef std::map< std::string, DrugFact > DrugStore;
    typedef DrugStore::iterator               DrugStoreIter;

    // Declaration of class-member data drugs.
    //
    DrugStore m_drugs;
};
[/PHP]

---

### Post by chris200x9 on 2008-09-28
thanx! :D

---

