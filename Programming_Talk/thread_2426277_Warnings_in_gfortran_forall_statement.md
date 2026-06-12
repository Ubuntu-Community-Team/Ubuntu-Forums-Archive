---
title: "Warnings in gfortran forall statement"
date: 2019-09-06
forum: Programming Talk
---

### Post by Dedalo on 2019-09-06
Hi. I am using the forall statement in a way which causes a warning. I am constructing a scalar, which is formed from the sum of some elements in an array. The forall statement requires to have an array at the both sides of the equality in order to have no warnings.



```

       forall(k=1:kmax)
        rsum=0.d0
        forall(j=ndet/4+1:ndet/2)
         rsum=rsum+ds(irtm,j)*sourceay(k,j-ndet/4)
        end forall
        rI(1,k)=rsum
       end forall

```

My question is if it is okey to use the forall statement in this way, or if could cause some trouble.
This is the warning it gives: 

```

*         rsum=0.d0*
*        1*
*Warning: The FORALL with index &#8216;k&#8217; is not used on the left side of the assignment at (1) and so might cause multiple assignment to this object*
*ptdrtev0.6.53.f90:2399:9:*

*          rsum=ds(irtm,j)*sourceay(k,j-ndet/4)*
*         1*
*Warning: The FORALL with index &#8216;k&#8217; is not used on the left side of the assignment at (1) and so might cause multiple assignment to this object*
[I]ptdrtev0.6.53.f90:2399:9:
[/I]
```

---

