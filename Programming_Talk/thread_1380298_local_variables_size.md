---
title: "local variables size"
date: 2010-01-13
forum: Programming Talk
---

### Post by ppradeep on 2010-01-13
error: total size of local objects too large
void basic(float sigma,float ro,float delta,int n,float eps[10000],float Y[10000],int x)
{
int i,j,k,t=1;/*value of x need to be checked*/
float cbar,sum,a,alpha;
double M[10000][10000],b[10000][10000],A[10000][10000],H[10000][10000],C[10000][10000],P[10000],T[10000][10000];

..........
...........
}
int main()
{

basic(sigmar,ro,delta,n,eps,Y2,x);

}

---

### Post by Habbit on 2010-01-13
Well, a 10000x10000 double matrix would use up 8x10000x10000=8E8 bytes, which is more than half a gigabyte. Usually stack space (where local variables reside) is not that big, but orders of magnitude smaller.

Furthermore, you declare _several_ such arrays with a total size of _at least_ 4.8E9 bytes (nearly 5 GB) much more than the 2-4 GiB available to non-address-extension-aware programs in most 32bit architectures, so you wouldn't be able to use that much memory _even_ if you tried to malloc() it.

---

### Post by mikejonesey on 2010-01-14
lol have you heard of vectors?

---

### Post by lavinog on 2010-01-14
It might be better to use malloc

Is this a school assignment?

---

