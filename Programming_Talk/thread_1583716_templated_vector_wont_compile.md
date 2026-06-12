---
title: "templated vector wont compile"
date: 2010-09-28
forum: Programming Talk
---

### Post by arkangel on 2010-09-28
template<typename  T>
T dot1(const vector<T> & A,const vector<T> & B){

   vector<T>::iterator it=A.begin();
   vector<T>::iterator itb=B.begin();
....

}

error:
../main.cpp:25: error: expected ‘;’ before ‘it’
../main.cpp:26: error: expected ‘;’ before ‘itb’


What I am doing wrong ...?

---

### Post by GeneralZod on 2010-09-28
In future, please use code tags and give a minimal compileable source file that illustrates the problem :)

```

template<typename T>
 T dot1(const vector<T> & A,const vector<T> & B){
 
 typename vector<T>::const_iterator it=A.begin();
 typename vector<T>::const_iterator itb=B.begin();
 ....
 
 }

```

I'll see if I can dig up an explanatory link for the "typename" stuff; the const_iterator is needed because the vectors are const.

Edit: This will probably do for the "typename" stuff: [http://pages.cs.wisc.edu/~driscoll/typename.html](http://pages.cs.wisc.edu/~driscoll/typename.html) - vector<t>::iterator is a *dependent* type.

---

### Post by arkangel on 2010-10-12
thanks  for the reply. I could compile however I am facing another problem

I am passing a vector and I want to access its elements using an iterator 

```

template<typename T>
T foo(vector<T> const & va ,vector<T> const & vb){

   typename vector<T>::iterator  ia=va.begin();
   typename vector<T>::iterator  ib=vb.begin();
     T sum(0);
    for(;ib!=vb.end();ia++,ib++)  sum+=(*ia)+(*ib);
  

} 


```

this is the canonical recommendation that I found to use iterators, the error 
Description    Resource    Path    Location    Type
conversion from &#8216;__gnu_cxx::__normal_iterator<const unsigned int*, std::vector<unsigned int, std::allocator<unsigned int> > >&#8217; to non-scalar type &#8216;__gnu_cxx::__normal_iterator<unsigned int*, std::vector<unsigned int, std::allocator<unsigned int> > >&#8217; requested    linalg_vector_matrix.cpp.H    /GMRES    line 13    C/C++ Problem



Using []  works ok !       It is clear i am declaring wrong the iterator 

Thanks

---

### Post by spjackson on 2010-10-12
> **arkangel said:**
> 
```

template<typename T>
T foo(vector<T> const & va ,vector<T> const & vb){

   typename vector<T>::iterator  ia=va.begin();
   typename vector<T>::iterator  ib=vb.begin();
     T sum(0);
    for(;ib!=vb.end();ia++,ib++)  sum+=(*ia)+(*ib);
  

} 


```this is the canonical recommendation that I found to use iterators, the error 
Description    Resource    Path    Location    Type
conversion from ‘__gnu_cxx::__normal_iterator<const unsigned int*, std::vector<unsigned int, std::allocator<unsigned int> > >’ to non-scalar type ‘__gnu_cxx::__normal_iterator<unsigned int*, std::vector<unsigned int, std::allocator<unsigned int> > >’ requested    linalg_vector_matrix.cpp.H    /GMRES    line 13    C/C++ Problem


You need a const_iterator for a const container. i.e.

```

   typename vector<T>::const_iterator  ia=va.begin();
   typename vector<T>::const_iterator  ib=vb.begin();

```

---

