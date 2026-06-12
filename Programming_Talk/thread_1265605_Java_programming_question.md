---
title: "Java programming question"
date: 2009-09-13
forum: Programming Talk
---

### Post by nathang1392 on 2009-09-13
i am writting a program in java. i am very new to everything so my question may seem very simple to most of you. i am using a boolean statement and am trying to make the statement figure out if some user input fits in between two numbers. 
eg: 
boolean isRate = exercisedHeartRate > lowerEnd and < upperEnd;
but clearly this isnt a correct statement. how would i make this correct?

---

### Post by Reiger on 2009-09-13
The && operator is the boolean and operator; ^ in logic.

---

### Post by froggyswamp on 2009-09-13
> **nathang1392 said:**
> 
boolean isRate = exercisedHeartRate > lowerEnd and < upperEnd;

```

boolean isRate = exercisedHeartRate > lowerEnd && exercisedHeartRate < upperEnd;

```

---

