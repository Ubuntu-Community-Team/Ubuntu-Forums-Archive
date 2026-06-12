---
title: "learning python, stuck on EOF error"
date: 2010-02-24
forum: Programming Talk
---

### Post by fokuslee on 2010-02-24
Hi im learning python
I just tried to program a fn but i get stuck with Token Error, EOF in multiline statement, 
it must be some syntax error
i didn't end the for loop correctlY?

anyway im desparate
thanks for the help

```
def ArcAccuracyTest(ListofChordVertex, ArcCenter, ArcRadius, TestTol):

    import math
    
    Result = True
    LCV = ListofChordVertex
    AC = ArcCenter
    AR = ArcRadius 
    SumDist = 0
    SecondVertexDist = 0
    
    for m in range(len(LCV)):
        LCVx1 = LCV[m][0]       #Nested 1 level deep
        LCVy1 = LCV[m][1]
        LCVx2 = LCV[(m+1)][0]
        LCVy2 = LCV[(m+1)][1]
        MCx = LCVx1 + (LCVx2-LCVx1)/2 #MC stands for midchord
        MCy = LCVy1 + (LCVy2-LCVy1)/2
        DIST1 = abs(AR-math.hypot((LCVx1-AC[0]),(LCVy1-AC[1])))
        DIST2 = abs(AR-math.hypot((MCx-AC[0]),(MCy-AC[1])))
        DIST3 = abs(AR-math.hypot((LCVx2-AC[0]),(LCVy2-AC[1])))
        SumDist = SumDist + DIST1 + DIST2 + DIST3 -    SecondVertexDist
        SecondVertexDist = DIST3
        m += 1
        
    WeightedSum = SumDist / ((Len(LCV)+(Len(LCV)-1)) ##ok something wrong here, but the idel spits out EOF error. sooo confused

    if WeightedSum > TestTol:
        Result = False
                             
    return WeightedSum
```

---

### Post by raydeen on 2010-02-24
I'm a newbie too and I've run into this when I haven't had my () or [] quite right. Check your code:

```

((Len(LCV)+(Len(LCV)-1))

```

I think it should be 
```

((Len(LCV))+(Len(LCV)-1))

```

Not sure though.

---

### Post by jdong on 2010-02-24
Indeed the problem is at 
```

    WeightedSum = SumDist / ((Len(LCV)+(Len(LCV)-1)) ##ok something wrong here, but the idel spits out EOF error. sooo confused

```


The parentheses on the denominator are unbalanced. You're missing a right parenthesis somewhere (at the very end?), depending on what you meant to code.

---

