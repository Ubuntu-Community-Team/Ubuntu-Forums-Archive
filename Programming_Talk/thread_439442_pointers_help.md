---
title: "pointers help"
date: 2007-05-10
forum: Programming Talk
---

### Post by scotty2hott2k on 2007-05-10
right, so im using c++ and the guichan gui library (its pretty nice :)) and tinyXML (which is also very good).

Right now my problem,

when for example you define a widget of button type in guichan it is gcn::Button* button, now i have a vector of these and wish to pass the vector by reference into the function:

the function prototype looks like:

```
function (vector <gcn::Button*>* buttons);
```

now, in that function i can access buttons->size() perfectly well, however when i try and access a specific member of the vector and its members i get an error saying that the member doesn't contain a member function of the name im trying to call (when it does).

hopw this is all making sense, ive just got myself in a bit of a muddle as if been chopping and changing things trying to make it work and have managed to confuse myself even more in the process.

thanks in advanced,

scott

---

### Post by thumper on 2007-05-11
My first observation is that you shouldn't be storing raw pointers in a vector.  Use a shared pointer instead.

Secondly, passing a vector in by reference can be done with the &.

```
function(vector<gcn::Button*>& buttons)
```

Now if you still want to do it your way, and a gcn::Button has a method getName, you can access it by

```
for (std::size_t i = 0, max = buttons->size(); ++i; i < max)
{
   sometype name = (*buttons)[i]->getName();
   // ...
}
```

---

