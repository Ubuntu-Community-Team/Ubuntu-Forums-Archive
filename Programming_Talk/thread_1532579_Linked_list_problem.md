---
title: "Linked list problem"
date: 2010-07-16
forum: Programming Talk
---

### Post by esmeco on 2010-07-16
I'm doing some exercises as preparation for exams and I've came across this particular exercise which I'm stuck at the algorithm.
To sum it up,there's a linked list that represents an inquiry in various districts.Each answer was stored in the linked list.
So,there's a linked list of districts(type dno) and each district has a second linked list that stores all the answers in that particular district(type rno).All districts are alphabetically sorted.
Here are the given structures:

```

typedef struct dist dno,*dpno;
typedef struct ans rno,*rpno;

struct dist
{
   char name[100];
   dpno next;
   rpno ans;
};

struct ans
{
  char c;
 rpno next;
};


```
This exercise,requires me to write a a function in C language that determines if a district is out of place on the linked list (not abiding the alphabetical order).The function is supposed to find that particular district(assuming there's only one district out of place) and put it on the correct order on the list.I'm not supposed to request memory allocation,just switch node position.
The algorithm is really bugging me as I have no clue on how should I approach this.

---

### Post by nvteighen on 2010-07-16
> **esmeco said:**
> I'm doing some exercises as preparation for exams and I've came across this particular exercise which I'm stuck at the algorithm.
To sum it up,there's a linked list that represents an inquiry in various districts.Each answer was stored in the linked list.
So,there's a linked list of districts(type dno) and each district has a second linked list that stores all the answers in that particular district(type rno).All districts are alphabetically sorted.
Here are the given structures:

```

typedef struct dist dno,*dpno;
typedef struct ans rno,*rpno;

struct dist
{
   char name[100];
   dpno next;
   rpno ans;
};

struct ans
{
  char c;
 rpno next;
};


```
This exercise,requires me to write a a function in C language that determines if a district is out of place on the linked list (not abiding the alphabetical order).The function is supposed to find that particular district(assuming there's only one district out of place) and put it on the correct order on the list.I'm not supposed to request memory allocation,just switch node position.
The algorithm is really bugging me as I have no clue on how should I approach this.

The first you have to do is to change that horrible typedefs to something much clearer. Such an approach is totally unclear and is surely confusing you a lot.

Wouldn't be this much more senseful and explicit:
```

typedef struct dist dist;
typedef struct ans ans;

struct dist
{
   char name[100];
   dist *next;
   ans *answer;
};

struct ans
{
  char c;
  ans *next;
};

```

Now, please segment the task into smaller parts. You first have to find the mislocated entry, right? Write a reliable way to find it first before thinking on the sorting algorithm.

---

### Post by esmeco on 2010-07-16
Well,it really is not that clear,but since the structures were already defined like that in the exercise header, I just stuck with them.

---

### Post by esmeco on 2010-07-16
I thought about how to find the misplaced entry first before the algorithm,but it's proving to be quite a challenge.
I think I'll have different cases depending if the entry is found misplaced 1st on the list,on the middle of the list and on the end of the list...Am I right?

---

### Post by howlingmadhowie on 2010-07-17
> **esmeco said:**
> I thought about how to find the misplaced entry first before the algorithm,but it's proving to be quite a challenge.
I think I'll have different cases depending if the entry is found misplaced 1st on the list,on the middle of the list and on the end of the list...Am I right?

well, there are different ways to sort lists. one of the easiest ways would be like this in pseudocode:

```

function sortOneItem(aList, start) {
  positionOfLowestItem=start
  for(i=(start+1); i<aList.length; i++) {
    if(aList[i].isAlphabetiacallyBefore(aList[positionOfLowestItem])) {
      positionOfLowestItem=i;
    }
  }
  if(positionOfLowestItem==start) {
    return "done";
  } else {
    aList.swap(start, positionOfLowestItem);
    return aList;
  }
}

function sortList(aList) {
  for(i=0; i<aList.length; i++) {
    while(true) {
      aListReturnValue=sortOneItem(aList, i);
      if(aListReturnValue=="done") {
        break;
      } else {
        aList=aListReturnValue;
      }
    }
  }
  return aList;
}

```

this should do it.  there are lots of functions i haven't written, like "isAlphabeticallyBefore" and "swap", but the structure may well be clearer now.

---

### Post by esmeco on 2010-07-17
But how can I determine which entry is misplaced?

---

### Post by dwhitney67 on 2010-07-17
> **esmeco said:**
> But how can I determine which entry is misplaced?

The same way you would if you were staring at with your own two eyes; you look at the current entry and compare it with the previous.

A -> B -> C -> F -> D

Bingo... D is out of place, because it should come before F.

---

### Post by esmeco on 2010-07-17
How about if F is in the beggining of the list like this:

F -> A -> B -> C -> D

I can't compare with the previous entry because it's the beginning of the list. And if 'A' is the current entry, if I compare it with the previous, 'A' is out of place because it should come before F,which is wrong because,in fact, 'F' is the one out of place.
How should I approach this particular situation?

---

### Post by Bachstelze on 2010-07-17
> **esmeco said:**
> How about if F is in the beggining of the list like this:

F -> A -> B -> C -> D

I can't compare with the previous entry because it's the beginning of the list. And if 'A' is the current entry, if I compare it with the previous, 'A' is out of place because it should come before F,which is wrong because,in fact, 'F' is the one out of place.
How should I approach this particular situation?

"Out of place" is ambiguous. You can say that F is out of place because it should be after A, B, C, D, or that A, B, C, D are out of place because they should be before F.  You have to settle some sort of convention, for example by saying that in case of conflict, you consider that the one with the "highest" letter is the one that is out-of-place.

---

### Post by Can+~ on 2010-07-17
> **esmeco said:**
> How about if F is in the beggining of the list like this:

F -> A -> B -> C -> D

I can't compare with the previous entry because it's the beginning of the list. And if 'A' is the current entry, if I compare it with the previous, 'A' is out of place because it should come before F,which is wrong because,in fact, 'F' is the one out of place.
How should I approach this particular situation?

You stopped at the first iteration and called it wrong. See for yourself:

```

F -> A -> B -> C -> D; A > F? No, swap them
     ^
A -> F -> B -> C -> D; B > F? No, swap them
          ^
A -> B -> F -> C -> D; C > F? No, swap them
               ^
A -> B -> C -> F -> D; D < F? No, swap them
                    ^
A -> B -> C -> D -> F; End reached.
                    ^
```

---

