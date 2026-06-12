---
title: "G++ template class problem"
date: 2007-09-22
forum: Programming Talk
---

### Post by mortykun on 2007-09-22
I figured out the problem.  The g++/gcc compiler does not automatically type cast return types to references in a function call.

I.E.

```


void Func(dataType &t);

// if i called the above method like this, and GetDataType() returned a instance of dataType, it would not auto reference that return varible

{
   Func(GetDataType());
}


```

I concede that this was plainly my own mistake, as I should never do something like that.  I guess what threw me for a long while was that this works on three other compilers.  Live and learn.


---- end of edit


I wrote a generic auditing base object in c++.  I then extended this object with a template class.
Anyway, this piece of code runs on unix and windows, and it compiles with three different c++ compilers (Xlc, msc, borland).  We are trying to port our unix/windows servers to run on linux, but it seems to me that  the g++ compiler croaks itself when it hits polymorphic template classes.

Below is a simplified version of what I am doing.

```

class DataBuilder;

class TableBase
{
public:
   virtual void insert(DataBuilder *table);
};

template <class TableClass,
                 class TableStruct,
                 class TableKey,
                 class  TableSelectAll>
class GenericTable : public TableBase
{
    void insert(DataBuilder *table)
    {
        TableClass  rec = (TableClass *) table->DeriveObject();
 
        GenericAudit<TableClass, TableKey> ga;
   
        ga.Insert(&rec);  // this method gets the before image, and calls the bellow class
   }
};

class DiffAudit
{
    public:
       template<TableClass,  TableKey>
      void Audit(TableClass *before,
                       TableClass  *after,
                       TableKey *key,
                       const char *userId)
     {
          .... code here, but it is this method that gets poached.
     }
};


```

The problem that seems to be happening is that the g++ compiler is adding pointer references into my generated template code.  Why would it be doing this? 

Has anyone else ever experienced something like this before with the g++ compiler?  Some of errors I got are below

> 

Bbd::StonedPlug::DiffAudit::Audit(**TableClass*, TableClass*, TableKey&, const char***) [with TableClass = Bbd::Workflow::cAreaCodes, TableKey = Bbd::Workflow::sAreaCodesKey]

DiffAudit::Audit(**Bbd::Workflow::cAreaCodes*&**, Bbd::Workflow::cAreaCodes*, Bbd::Workflow::sAreaCodesKey, const char*)?



The code compiles under three other compilers, so I know it is either some kind compiler switch, or compiler bug that is causing this?

It's almost like the compiler is mangling one of the template classes but not the other. Then when it tries to link the template classes together it cannot resolve the symbols?      

Any ideas?

---

### Post by glok_twen on 2007-09-22
if you haven't already i'd also post this on codeguru.com

---

### Post by Lux Perpetua on 2007-09-22
It would help if you could post the **first compilation error** in its entirety. (What you posted is not even one complete error and is essentially useless.) The error message usually tells you what line the error occurred on, so it would also help if you pointed out the relevant line(s) in your program.

---

### Post by mortykun on 2007-09-25
thanks, will check out codeguru.com

---

