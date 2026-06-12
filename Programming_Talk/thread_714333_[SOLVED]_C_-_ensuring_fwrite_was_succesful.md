---
title: "[SOLVED] C - ensuring fwrite was succesful"
date: 2008-03-03
forum: Programming Talk
---

### Post by S15_88 on 2008-03-03
Hi i'm writing a structure to a binary file, but i'm wondering if it's possible to check whether the write was successful or not.

I have this:
```

if(fwrite(info, sizeof(employeeRecord), 1, writeRecord) > 0)
{
    printf("The Information Has Been Stored\n");
}
else
{
    printf("Error Occured\n");
}     

```

because fwrite returns the number of items written.  But in this case it could write just half the data or something but since it wrote something it would return a number greater than 1.

is there any other way to do this like maybe:
```

if(fwrite(info, sizeof(employeeRecord), 1, writeRecord) == sizeof(employeeRecord)

```
would that make more sense.

Thanks, ALain

---

### Post by aks44 on 2008-03-03
See [http://www.opengroup.org/onlinepubs/7990989775/xsh/fwrite.html](http://www.opengroup.org/onlinepubs/7990989775/xsh/fwrite.html)


If fwrite() doesn't *fully* write an item, that item won't be counted in the return value.

Which means that your above code is perfectly safe**[COLOR="Navy"]*[/COLOR]** as long as your number of items is 1.

A more "generic" approach would be:
```
if (fwrite(items, sizeof(*item), numItems, outputFile) == numItems)
{
  // OK
}
else
{
  // ERROR
};
```

But again, as long as numItems is 1 there is **no difference** with your original code (since the return value can then only be either 0 or 1).



**[COLOR="Navy"](*)[/COLOR]** See the "APPLICATION USAGE" section at the end of the link I gave. They also forgot to mention structure padding as a possible cause of problems.

---

### Post by nanotube on 2008-03-03
and if you /really/ want to make sure everything is correct, and you didn't just happen to write to a bad piece of disk, or a stray gamma ray photon didn't hit your ram and flip a bit just at the wrong moment... you could just read it back and see if your source and destination data match. :)

---

### Post by S15_88 on 2008-03-03
Thanks!

---

### Post by Can+~ on 2008-03-03
As an extra layer, make sure that when doing fopen, it doesn't return NULL. Maybe the user can't write to that file.

---

