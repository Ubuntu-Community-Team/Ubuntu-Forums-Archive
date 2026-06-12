---
title: "[C++] class definition"
date: 2010-11-15
forum: Programming Talk
---

### Post by erotavlas on 2010-11-15
Hi,

I have a problem inside a class definition. I get the following compile error, [HTML]In constructor `Auto::Iterator::Iterator(const Auto&) expected primary-expression before '=' token|[/HTML] but I can't understand where is the error.


```
class Auto {

public:


    
    typedef std::map<std::vector<std::string>, float> AutoMap;

private:
    AutoMap myAutoMap;

public:

       class Iterator {
    private:
        typedef AutoMap::const_iterator iter;
        const Auto* myAuto;

    public:
        Iterator(const Auto& myAuto_) {
            myAuto = &myAuto_;
            iter = myAuto->myAutoMap.begin();
        }
     };

friend class Iterator;


/*...*/

};
```

Thank you

---

### Post by GeneralZod on 2010-11-15
> **erotavlas said:**
> Hi,

I have a problem inside a class definition. I get the following compile error, [HTML]In constructor `Auto::Iterator::Iterator(const Auto&) expected primary-expression before '=' token|[/HTML] but I can't understand where is the error.


```

       class Iterator {
...
        typedef AutoMap::const_iterator iter;
...

    public:
        Iterator(const Auto& myAuto_) {
...   
            iter = myAuto->myAutoMap.begin();
        }
     };

```


"iter" is a type, not an object, so can't be the target of an assignment.

---

### Post by erotavlas on 2010-11-15
> **GeneralZod said:**
> "iter" is a type, not an object, so can't be the target of an assignment.

Ok, you are right...
The following code is correct because the class Auto is a template? 
Correct me If I say a ********...

```

template <typename I = Vector, typename T = float>
class Auto {

public:

   
    typedef std::map<I, T> AutoMap;

private:
    AutoMap myAutoMap;

public:

       class Iterator {
    private:
        typename AutoMap::const_iterator iter;
        const Auto<I,T>* myAuto;

    public:
        Iterator(const Auto& myAuto_) {
            myAuto = &myAuto_;
            iter = myAuto->myAutoMap.begin();
        }
     };

friend class Iterator;


/*...*/

};
```

---

