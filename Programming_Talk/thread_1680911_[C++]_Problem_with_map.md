---
title: "[C++] Problem with map"
date: 2011-02-03
forum: Programming Talk
---

### Post by erotavlas on 2011-02-03
Hi,

I'm getting stuck with the following code. I have to add a new element to the map. I have to search inside the map if an element with a key = name is present. If no all work, I can insert a new element with function insert. While if yes I want to extract the corresponding value that is the multimap, after I have to add the new element to existent multimap and finally I have to insert all to map.


```

map<string, multimap<vector<string>, float> > map;
multimap<vector<string>, float> multimap;

map<string, multimap<vector<string>, float> >::const_iterator it = map.find(name);
if (it != map.end())
{
         multimap = map[name];
 }
 // update the multimap
 multimap.insert(pair<vector<string>, float>(inputvector, value));

// update the map
map.insert(pair<string, multimap<vector<string>, float> >(name, multimap));

multimap.clear();

```

Where is the problem?

---

### Post by Zugzwang on 2011-02-03
> **erotavlas said:**
> Where is the problem?

First of all, you didn't describe the problem you are actually having. Does you compiler throw you errors/warnings? If yes, then consider calling your map somewhat different than "map", because how is the compiler supposed to know that you mean the object "map" and not the class/template "map".

Do you have the problem that your code is slow? If yes, then consider skipping all this copying business altogether and use references, using the fact that by applying the []-operator, non-existing elements in the map are created automatically. Here's an untested example:
```

map<string, multimap<vector<string>, float> > mymap;

multimap<vector<string>, float> > &mymultimap = mymap[name];
mymultimap.insert(pair<vector<string>, float>(inputvector, value));

```

---

### Post by erotavlas on 2011-02-03
Thank you for your answer. I'm sorry for my poor explanation. Instead to copy the code, I have re-written it and so I have made a mistake for the name of the map, multimap (I have used reserved word) .
I would like to add a new element in the outer (map->mymap). If the map does not already contain an element with a given name, I will insert the new element. If the element with a given name is already present I would like to access to it corresponding value and update first the inner (multimap->mymultimap) and finally I would like to add it to outer map.

The problem is that If the map does not contain the element that I will insert, all work well.

```

// update the multimap
multimap.insert(pair<vector<string>, float>(inputvector, value));
 
// update the map
map.insert(pair<string, multimap<vector<string>, float> >(name, multimap));
 
multimap.clear();

```
But If the map already contain the element I would like to extract the corresponding value (multimap->mymultimap).

```

map<string, multimap<vector<string>, float> >::const_iterator it = map.find(name);
if (it != map.end())
{
         multimap = map[name];
}

// update the multimap
multimap.insert(pair<vector<string>, float>(inputvector, value));

// update the map
map.insert(pair<string, multimap<vector<string>, float> >(name, multimap));

multimap.clear();

```

I think that the problem is this line multimap = map[name]; The statement does not extract the multimap associated with name.
I hope that I was quite clear.

---

### Post by Zugzwang on 2011-02-03
> **erotavlas said:**
> If the element with a given name is already present I would like to access to it corresponding value and update first the inner (multimap->mymultimap) and finally I would like to add it to outer map.


This is the part that seems to be unnecessarily complicated. The code that I've provided you does the same, but without re-inserting the modified multimap back to the map. Rather, it modifies the multimap in situ. For what you seem to try to do, this is the better way of doing it.

In case you really want to go with your copying-around solution, "multimap = map[name];" should do what you intended it to. You can also access your iterator instead: "multimap = it->second;"

If you still have questions, please supply us with a *working* minimal .cpp example file that compiles and runs without external dependencies (except for the STL library) that also produces some output, and state which output your have expected instead. If this post doesn't answer your question, such a minimal example will clarify your question.

---

