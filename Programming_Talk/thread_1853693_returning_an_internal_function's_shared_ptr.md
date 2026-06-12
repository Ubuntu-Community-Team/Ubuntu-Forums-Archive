---
title: "returning an internal function's shared_ptr"
date: 2011-10-02
forum: Programming Talk
---

### Post by jebsector on 2011-10-02
I have a function that returns a reference to an object that is created within the method as follows:

(class myItems)
```

boost::shared_ptr<item> anItem::getItem(int32 a) {
   boost::shared_ptr<item> anItem(new item());
   ...
   anItem->a = struct[spot]->a;
   anItem->b = struct[spot]->b;
   return anItem;
}

```

The following code results in a segfault as I'm assuming the method getItem has anItem go out of scope before returning it, and destroys the object.  It happens exactly as getItem returns:

```

  myItems a; ...
  boost::shared_ptr<item> foundI = a->getItem(0);

```

My question is, how can I return anItem from getItem, with maintaining a valid reference to the internal function variable and thereby returning that to the caller?  I know I can use a class member but I want to avoid that if possible..

---

### Post by jebsector on 2011-10-02
update:  I also tried allocating new on the return, with no difference.  Here is the actual method:

```

struct IntLookup {
    int32 data;
    int64 pointer; //pointer will be non-zero for actual items
};
typedef boost::shared_ptr<IntLookup> idxLookup;
...

idxLookup idx_utility::getItem(const int32 item) {
idxLookup idxl(new IntLookup());
...
return idxLookup(new IntLookup()); //fails w/ segfault
return idxLookup(new IntLookup(idxl));  //fails w/ segfault
return idxl;  //fails w/ segfault

```

---

### Post by karlson on 2011-10-02
> **jebsector said:**
> 
My question is, how can I return anItem from getItem, with maintaining a valid reference to the internal function variable and thereby returning that to the caller?  I know I can use a class member but I want to avoid that if possible..

I would suggest you pass in the shared_ptr by reference and return void.

---

### Post by jebsector on 2011-10-02
Ah - what a bunch of garbage.  The segfault was actually happening earlier than that, it just wasn't printing out until the method returned.

It was because I was assigning idxl = in[pointer];
when I should have been doing idxl->pointer = in[pointer]->pointer, 
or to quicken it up, int64 numitems = in[pointer]->pointer;

After I made that change it got rid of the segfault.

Now all three versions return correctly.  Thanks,

---

