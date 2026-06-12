---
title: "perl assistance needed, 2d arrays acting like movie stars"
date: 2012-02-15
forum: Programming Talk
---

### Post by Feydakin on 2012-02-15
Heluu all,

I am in dire need of assistance. I am having some trouble with two 2d arrays, one being passed as an argument to the function and one declared inside the function.

Please take a look at the following two snippets.

```

        my      @ref_table = @{$_[0]};
        my      @full_table;    
```
These are the declarations. As you can see, one is passed (and it is the only argument to the function).

```

        for($k=0; $k < $#{$ref_table[0]}; $k++)
        {
                #For each column in the original data table.
                for($l=0; $l < $#{$full_table[0]}; $l++)
                {
                        #Should the header of the original data table match that of the ranked table...
                        if($full_table[0][$l] eq $ref_table[0][$k])
                        {       

                                #Assign the original data table value to the ranked table.
                               $ref_table[$k] = $full_table[$l];
                                    
                        }
                }
        }
```
My problem is (currently) that I cannot get any matches, even though I have the correct data in the table rows.
For starters, $k will go up to either 0 (exit immediately and $l won't even init) or 7000+ (which is strange since the array is only 16 indices wide).
I have tried multiple ways of getting the width of the arrays (scalar... $#{$x} @x etc) but none seem to work for the time being.
Both arrays are two-dimensional. The assignment of one array to the other is not part of this particular problem, simply a method I would like to try (but haven't gotten that far yet).

I am currently passing the argument to the function like this:
```
        @ranked_table = copyRanked(\@ranked_table);
```

Any help would be greatly appreciated.
/Fey

---

### Post by shawnhcorey on 2012-02-15
There is nothing in `@full_table`. Your code will always skip the inner loop.

---

### Post by Feydakin on 2012-02-16
The @full_table is assigned all the relevant values (and verified). I just did not include that part of the code.

---

### Post by shawnhcorey on 2012-02-16
And you expect us to solve your problems by osmosis?

---

