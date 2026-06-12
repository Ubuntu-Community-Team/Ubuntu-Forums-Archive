---
title: "problems calling template function pointer"
date: 2008-09-20
forum: Programming Talk
---

### Post by monkeyking on 2008-09-20
Hi, I've been building a generic matrix template and a  generic array template container.

I've made a generic apply function that I supply with a Matrix and a pointer to a funcion that then calculates the value for each row/column. This is working and looks like this.

[PHP]
//this is the function that I'm pointer to
template<typename T>
T sum(const Array<T> &a){ // a simple function that return the sum of an Array
  T res=0;
  for(int i=0  ;  i<a.length()  ;  i++)
    res  +=  a(i);
  return res;
}

//this is the apply function that calls above
template<typename T>
Array<T> apply(Matrix<T> &m,int doRow,T (*fun)(const Array<T>&)){
  if(doRow==1){
    Array<T> retA(m.x());
    for (int i=0  ;  i<m.x()  ;  i++){
      Array<T> r = getrow(m,i);
      retA(i) = (*fun)(r);
    } 
    return  retA;
  }else if(doRow==2){
    Array<T> retA(m.y());
    for (int i=0  ;  i<m.y()  ;  i++){
      Array<T> r = getcol(m,i);
      retA(i) = (*fun)(r);
    } 
    return  retA;

  }
}
int main(){
 Matrix(int) r(10,10);
 Array<int> var = apply(r,1,&sum<int>);
}
[/PHP]
Now this works perfecttly,
but now I want to do even more simple one,
I want to call a function on each entry of the matrix,
this looks like

[PHP]
//very simple function 
//that I'd like to call from a template context
int myAdder(int input){ //this will only work if I pass input as a parameter
  return (input +50);
}


//this one returns a Matrix of same dim as input Matrix
template<typename T>
Matrix<T> sapply( Matrix<T> &m,T (*fun)(const T&)){
  Matrix<T> retM(m.x(),m.y());
  for (int i=0  ;  i<m.x()  ;  i++)
    for (int j=0  ;  j<m.x()  ;  j++){
      T var =  (*fun)(m(i,j));
      retM(i,j) =var;
    }
  return  retM;
}
int main(){
 Matrix<int> r51 = sapply(r,&myAdder);
}
[/PHP]

This code works perfectly, but only if my function pointer points to a function, that has it's argument given as a reference?

can someone Eleborate on why this is so.


thanks in advance

---

### Post by dribeas on 2008-09-20
> **monkeyking said:**
> This code works perfectly, but only if my function pointer points to a function, that has it's argument given as a reference?

can someone Eleborate on why this is so.

The function signatures are not the same.

```

int f1( int i );
int f2( int const & i );

int (*pf1)( int ) = f1;
int (*pf2)( int const & ) = f2;
int (*error)( int const & ) = f1; // f1 signature is int (*)(int)

```

For the compiler there are differences. For f1() it must copy the int value into 'i' (usually through the stack) while for f2() it generates a hidden pointer into the given parameter and autotically dereferences it inside f2(). Even if you can call in your code both functions in the same use cases, for the compiler they are different.

---

