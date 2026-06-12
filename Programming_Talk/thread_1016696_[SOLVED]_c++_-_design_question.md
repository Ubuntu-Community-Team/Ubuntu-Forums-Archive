---
title: "[SOLVED] c++ - design question"
date: 2008-12-20
forum: Programming Talk
---

### Post by Despot Despondency on 2008-12-20
Hey, I'm trying to write a class, called Country, which consists of a 

- string, which is the name of the country

- vector<Country>, which is a vector of the neighboring countries.

At the moment my class looks like this 

```

#ifndef COUNTRY_H
#define COUNTRY_H

#include <vector>
#include <string>

class Country{

 public:

  Country();
  Country(std::string);

  std::string getName();

 private:

  std::string name;

  std::vector<Country> neighbours;

};
#endif

```

Now I want to be able to add neighbours to a country, but I don't want the function to be public. 

To be more specific, I am going to create an Atlas class that will create, and store, the countries and read in the neighbours. So is there a way that I can add neighbours to a country from the atlas class, but not from anywhere else.

Any help would be greatly appreciated.

---

### Post by user_none on 2008-12-20
Have a look at the [friend]("http://www.codersource.net/cpp_tutorial_friend.html") modifier.

---

### Post by Despot Despondency on 2008-12-20
That looks like what I need, thanks. Seems like the best solution to me, but if anyone has any other ideas of how to do this then I would love to hear.

---

### Post by StOoZ on 2008-12-20
I dont think it will work , because , Country in here :
[PHP]std::vector<Country> neighbours;
[/PHP]

is an incomplete object.
it should be :
[PHP]std::vector<Country*> neighbours;[/PHP]

---

