---
title: "Java ArrayIndexOutOfBoundsException"
date: 2007-08-09
forum: Programming Talk
---

### Post by Belathor on 2007-08-09
Hi everyone,

I'm trying to make an array that is the reverse of an inputted array containing 3 integers. I thought that code below would work, but I keep getting the ArrayOutOfBounds exception. I've been going through the loop in my head and I can't see how it is going out of bounds. It looks to me like it should work. reverse[0] = nums[2] -> reverse[1] = nums[1] -> reverse[2] = nums[0]. Shouldn't the for-each loop stop after that? 

Thanks for helping me conceptually understand what I am missing!

```
public int[] reverse3(int[] nums) {
  int[] reverse = new int[3];
  for(int x : nums) {
    reverse[x] = nums[2 - x];
  }
  return reverse;
}
```

---

### Post by Ramses de Norre on 2007-08-09
> **Belathor said:**
> Hi everyone,

I'm trying to make an array that is the reverse of an inputted array containing 3 integers. I thought that code below would work, but I keep getting the ArrayOutOfBounds exception. I've been going through the loop in my head and I can't see how it is going out of bounds. It looks to me like it should work. reverse[0] = nums[2] -> reverse[1] = nums[1] -> reverse[2] = nums[0]. Shouldn't the for-each loop stop after that? 

Thanks for helping me conceptually understand what I am missing!

```
public int[] reverse3(int[] nums) {
  int[] reverse = new int[3];
  for(int x : nums) {
    reverse[x] = nums[2 - x];
  }
  return reverse;
}
```

```
for(int x:nums)
```
Will iterate over the elements of nums, so if nums=={3,4,1}, x will take the values 3, 4 and 1. You have quite a big change of going out of bounds...

---

### Post by Belathor on 2007-08-09
Thanks Ramses! I understand it now.

---

