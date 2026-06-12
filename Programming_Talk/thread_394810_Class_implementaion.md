---
title: "Class implementaion"
date: 2007-03-27
forum: Programming Talk
---

### Post by nano2 on 2007-03-27
Hi ,

Has anyone a class implementation that will build up th followingc lass with the following values :
build up  a classification class where  the user will call the object createprog  like so to progate  the values into the class.

the class will have any of these values startday, endday starttime endtime and a type 
 
Createprog 24214155, 154151555435, TYPE0

At runtime the 
Createprog Monday Sunday 0 86400 TYPE1

Createprog Monday Friday 28800 64801 TYPE2
Createprog 24214155, 154151555435, TYPE3

In c it would look like  so 

typedef enum {TYPE0,TYPE1, TYPE2,TYPE3} ClassType;
struct Classification {
    int startDate;
    int endDate;
    ClassType type;
};


Createprog Monday Sunday 0 86400 "type1"

Createprog Monday Friday 28800 64801 "type3"

---

### Post by Tomosaur on 2007-03-27
```

class Classification{
  static int startDate;
  static int endDate;
  static ClassType type;

  public void Classification(int s_date, int _date, ClassType t){
    startDate = s_date;
    endDate = e_date;
    type = t;
  }
}

```
Like that?

---

### Post by nano2 on 2007-03-28
the method can be called like so inserting values for variables at runtime :

createprog [ startday, endday, starttime, endtime,type]
createprog[startday, endday,offsetstarttime,offsetendtime,type]
Createprog[startDatetime,endDatetime,type]

so therefore that definition wouldn't work ????????????????????????????

---

### Post by Tomosaur on 2007-03-28
Then your C code was wrong, you didn't mention anything about times, just dates. In any case, modifying that class is trivial.

---

### Post by nano2 on 2007-03-28
Sorry my mistake ... have you any suggestions how it might be done ?

---

