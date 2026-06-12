---
title: "Statci member functions in C++"
date: 2007-10-20
forum: Programming Talk
---

### Post by bluedalmatian on 2007-10-20
Ive declared 2 static member functions (class methods) in C++ but the compiler is saying 'cannot declare xyz to have static linkage.

This gives me the impression its treating the static keyword as if it was its C meaning, rather than C++?

Im sure its just something simple with the syntax but it looks correct to me?

The header says
static void setMap(map<std::string,DAO*>* themap);

and the source file is:

static void DAO::setMap(map<std::string,DAO*>* themap)
{
	all_daos = themap;
}

all_daos is a static member decalred as:

static map <string,DAO*>* all_daos;

What have I done wrong please?

Thanks
AW

---

### Post by aks44 on 2007-10-20
According to the code you posted (and the incomplete error message), I'd hint you at the actual *file* in which the error occurs. The compiler is probably bitching about the definition, not the declaration.

Remove **static** in front of the definition of **DAO::setMap()** and it should be fine.

Also, don't forget to define somewhere
```
std::map<std::string,DAO*>* DAO::themap;
```


And... huh... globals are Evil (even when they take the sneaky appearance of statics), you know that, right? :p

---

