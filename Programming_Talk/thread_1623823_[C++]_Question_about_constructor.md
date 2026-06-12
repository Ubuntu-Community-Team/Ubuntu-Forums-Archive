---
title: "[C++] Question about constructor"
date: 2010-11-17
forum: Programming Talk
---

### Post by erotavlas on 2010-11-17
Hi,

I have the following class.

```

class Auto {

public:

    enum AUTO_TYPE {SPORT, STANDARD};
    enum PROBLEM_TYPE {COMBUSTION, ELECTRIC};


     Auto(const std::string& autoType_, const std::string& engineType_) {

        // sets the flags
        if (autoType_ == "SPORT")
            autoType = SPORT;
        else (autoType_ == "STANDARD")
            autoType = STANDARD;


        if (engineType_ == "COMBUSTION")
            engineType = COMBUSTION;
        else (engineType_ == "ELECTRIC")
            engineType = ELECTRIC;
      
    }

private:

AUTO_TYPE autoType;
ENGINE_TYPE engineType;

};


```

The private members are initialized by the constructor and they are read from input stream. I would like to know if is a good idea to make the conversion from string type to enum inside the constructor. Is there a better way to do it? 

Thank you

---

### Post by NovaAesa on 2010-11-17
I'd say it's fine to put simple things like that in the constructor (and by that I mean using an initialization list at the start of the constructor). Although, I think passing in the enum type directly to the constructor would be a "cleaner" way of doing things, seeing that your emum types are public.

---

### Post by dwhitney67 on 2010-11-17
> **NovaAesa said:**
> ... I think passing in the enum type directly to the constructor would be a "cleaner" way of doing things, seeing that your emum types are public.

+1.

-------------

@ the OP - With your approach, you did not consider the scenario where one may pass in a string that does not match your expectations.  Consider what would happen if "TRUCK" and "HYBRID" were passed in for the auto-type and engine-type.  Your class would remain uninitialized!

Btw, the enum for ENGINE_TYPE is declared as PROBLEM_TYPE; was that a joke?

Anyhow, consider the following:
```

class Auto
{
public:
   enum AutoType   { SPORT, STANDARD, TRUCK };
   enum EngineType { COMBUSTION, ELECTRIC, HYBRID };

   Auto(AutoType autoType_, EngineType engineType_)
      : autoType(autoType_),
        engineType(engineType_)
   {
      // initialize class above... NOT HERE!
   }

private:
   AutoType   autoType;
   EngineType engineType;
};

```
Note how the constructor is implemented.  Also, never used all-caps to define an enum declaration type.  All-caps are typically used for constants (such as the enum members) or macros.

---

