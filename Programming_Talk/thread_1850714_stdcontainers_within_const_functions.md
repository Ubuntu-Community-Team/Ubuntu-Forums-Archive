---
title: "std::containers within const functions"
date: 2011-09-27
forum: Programming Talk
---

### Post by roadkillguy on 2011-09-27
This is rather frustrating... are std::list's and std::vector's begin() and end() not marked as const?  Whenever I try to use them, I get the error:

```
Terrain.cpp: In member function ‘const Chunk* Terrain::getContainingChunk(float, float, float) const’:
Terrain.cpp:40: error: conversion from ‘std::_List_const_iterator<Chunk*>’ to non-scalar type ‘std::_List_iterator<Chunk*>’ requested

```

Which is annoying.  I cant iterate through a std::list and at the same time call the member function const, even though it's not changing anything by iterating.

There must be a better way to this.  What might it be?  My function must be const, and it must iterate through a std::list, returning the matching chunk of terrain.

---

### Post by muteXe on 2011-09-27
Can you declare a const iterator and go thru this?

```

    std::vector<YOUR_CLASS*>::const_iterator i;
    for(i = YOUR_LIST.begin(); i != YOUR_LIST.end(); ++i)
    {      
         i->YOUR_METHOD
    }

```

?

---

### Post by roadkillguy on 2011-09-27
Would you look at that!  Worked like a charm.  I didn't know there was a separate const_iterator type.

Thanks!

---

### Post by muteXe on 2011-09-28
No worries dude :)
I wasn't familiar with it until a nice guy from this forum told me about it.

mute

---

