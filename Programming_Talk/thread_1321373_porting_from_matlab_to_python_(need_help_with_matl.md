---
title: "porting from matlab to python (need help with matlab reference)"
date: 2009-11-10
forum: Programming Talk
---

### Post by dracule on 2009-11-10
Ok so if anyone can spare a few minutes and can tell me what each of these things are in terms of python (or plain english), that would be FANTASTIC!

```

(this is in a for loop where d is defined as 1-9)
D = load(['digit' num2str(d) '.ascii'],'-ascii');
save(['digit' num2str(d) '.mat'],'D','-mat');

then later in a different function:
digitdata=[]; 
targets=[]; 
load digit0; digitdata = [digitdata; D]; targets = [targets; repmat([1 0 0 0 0 0 0 0 0 0], size(D,1), 1)];  
load digit1; digitdata = [digitdata; D]; targets = [targets; repmat([0 1 0 0 0 0 0 0 0 0], size(D,1), 1)];
load digit2; digitdata = [digitdata; D]; targets = [targets; repmat([0 0 1 0 0 0 0 0 0 0], size(D,1), 1)]; 
(etc....)

digitdata = digitdata/255;
totnum=size(digitdata,1);

```

what exactly is going on here? what does this do:
digitdata = [digitdata; D];
?
is it appending the D object (which im guessing came from the digit1.mat it created earlier) onto digitdata?
just to be clear the .ascii file contains a file of data (1's and 0's about 1000 characters on individual lines)

also what is this doing:
digitdata = digitdata/255;
?
so is size(digitdata,1) equivelent to len(digitdata)
?

ok, now for the next batch...
```

input_set = zeros(xx, length_of, numsets);
(then later in another function)

[total_amount size_of_set set_num]=size(input_set);


```

is total_amount == xx, size_of_set == to length_of, and set_num==numsets
??

Also what does this even do:
input_set = zeros(xx, length_of, numsets);
?

So what is this doing?
input_set(:,:,b);
?
and I have absolutely no clue what is going on here:
```

input_set(:,:,b) = digitdata(randomorder(1+(b-1)*batchsize:b*batchsize), :);

```
I think I can get everything from here. 

Also, in matlab I get a memory error for trying to allocate a 3 dimensional array with 100 x 50000 x 10. I have 8gb of ram and 15 gb page file. 

any help would be appreciated. I can figure most stuff out, and most of this stuff is semantic so I can't look it up online very easily.

---

