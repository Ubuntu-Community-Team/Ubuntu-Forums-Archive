---
title: "[C++] Bitwise operator"
date: 2010-09-15
forum: Programming Talk
---

### Post by xnerdx on 2010-09-15
I've got a question regarding the use of the bitwise operator for right shift. I'm working with a program and I'm trying to understand how it works but the way they use the bitwise operator >> has me baffled. The following is the code I'm referring to:
```

WoWGuid itemGuid;
int8 SrcInvSlot;
uint8 SrcSlot;
recv_data >> itemGuid >> SrcSlot >> SrcInvSlot;

```
I understand how bitwise operators work but I'm confused in this situation. Does anyone know what this is doing?

---

### Post by dwhitney67 on 2010-09-15
That is not the bitwise operator, perse, but instead input stream operator that has been defined for the class object that represents the "recv_data".

Can you please post the relevant code that describes this class?

---

### Post by Bachstelze on 2010-09-15
What is it doing, and what were you expecting?

---

### Post by xnerdx on 2010-09-15
I'm sorry I feel like an idiot xD I forgot that > is the bitwise operator :P. What I don't understand still is how the data in recv_data is seperated so that the following variables will know what to take from it. What kind of data should I look for in its class definition?

---

### Post by dwhitney67 on 2010-09-15
> **xnerdx said:**
> I'm sorry I feel like an idiot xD I forgot that > is the bitwise operator :P. What I don't understand still is how the data in recv_data is seperated so that the following variables will know what to take from it. What kind of data should I look for in its class definition?

If say "recv_data" is of class type **Foo**, then you should be looking for something like the following (in Foo.cpp?):
```

Foo& operator>>(WoWGuid& val)
{
   ...
   return *this;
}

Foo& operator>>(int8& val)
{
   ...
   return *this;
}

Foo& operator>>(uint8& val)
{
   ...
   return *this;
}

// or possibly something craftier like
//
template <typename T>
Foo& operator(T& val)
{
   ...
   return *this;
}

```

---

