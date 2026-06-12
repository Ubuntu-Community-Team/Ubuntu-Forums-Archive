---
title: "Math.floor() in Java not working. Why?"
date: 2014-01-30
forum: Programming Talk
---

### Post by Wiking on 2014-01-30
Hi, I'm trying to do some calculations where I want to round down. Before I was using Int division where it truncates the decimal, but now I have to use float variables to allow decimals. However, I tried using Math.floor to round down but it doesn't work. 

For example if 50.00 / 2 = 2.5 , I want it to be 2. But the system keeps printing out 2.5.

But for some reason it just stays the same. 

Both* change *and *holder *variables are float.

Any help would be greatly appreciated.

```
 //Calculating change        
            change = 100 - price;
          //Converting change to decimal using float variable for Output
           changeOut = change;
          //changeOut *= 100;
        
        // testing ouput
        System.out.println(changeOut);
        System.out.println(change);
        
        //Calculating how many $20 bills
**        Math.floor(holder = change / 20);**
        System.out.println(holder);
**        Math.floor(holder);**
        System.out.println(holder);
        coins = holder * 20;
        System.out.println(coins);
```

thanks

---

### Post by Wiking on 2014-01-30
Had something to do with arguments

```
 holder = Math.floor(holder);
```

works

---

