---
title: "[c++] Default Construction Confusion"
date: 2009-04-12
forum: Programming Talk
---

### Post by tdrusk on 2009-04-12
I have
```
class InventoryException : public runtime_error
{
    private:
      Inventory item;
      string errorMessage;
    public:
      InventoryException(Inventory, string);
      void showMsg();
};
InventoryException::InventoryException(Inventory item, string errorMessage)
{
    this->item = item;
    this->errorMessage = errorMessage;
}
```

and I get the error
```
'std::runtime_error' : no appropriate default constructor available
```

I'm not sure where I should go from here...

---

### Post by sujoy on 2009-04-12
iirc in c++, if you write a constructor that takes parameter, then you must also write a constructor that doesnt take any parameter (the default constructor)

the default constructor need not be written if you dont write any constructor at all, however, if you do, then you must write the default one too

```

InventoryException::InventoryException()
{
    // do stuffs
}

```

---

### Post by Jiraiya_sama on 2009-04-12
I'm guessing the problem is that you don't have a default constructor. Either make a constructor that accepts no arguments or give your current constructor default values for each argument.
(ex:InventoryException(Inventory = Inventory(), string = ""))

---

### Post by tdrusk on 2009-04-12
> **Jiraiya_sama said:**
> I'm guessing the problem is that you don't have a default constructor. Either make a constructor that accepts no arguments or give your current constructor default values for each argument.
(ex:InventoryException(Inventory = Inventory(), string = ""))

```
class InventoryException : public runtime_error
{
    private:
      Inventory item;
      string errorMessage;
    public:
      InventoryException(Inventory = Inventory(), string = "");
      void showMsg();
};

InventoryException::InventoryException(Inventory item, string errorMessage)
{
    this->item = item;
    this->errorMessage = errorMessage;
}
```

I did as you said and I am still getting the same error... #-o

---

### Post by dribeas on 2009-04-12
> **tdrusk said:**
> I have
```
class InventoryException : public runtime_error
{
   //...
};
InventoryException::InventoryException(Inventory item, string errorMessage)
{
    this->item = item;
    this->errorMessage = errorMessage;
}
```


Your class is inheriting from std::runtime_error, that does not have a default constructor (just like the error tells you). You must pass an argument to the constructor of std::runtime_error in your class initialization list (and now you are at it, initialize all members there:

```

InventoryException::InventoryException( Inventory item, string errorMessage )
    : std::runtime_error( errorMessage ), 
      item( item ), 
      errorMessage( errorMessage ) // is this needed? runtime_error will keep the message
{
}

```

The important part is the std::runtime_error( errorMessage ). If you do not provide an initialization list, the compiler will try to default initialize your bases and your attributes, and that will fail with runtime_error

---

### Post by tdrusk on 2009-04-12
Thanks guys for your help. I started from scratch and realized I was making it more complicated than necessary. :guitar:

---

