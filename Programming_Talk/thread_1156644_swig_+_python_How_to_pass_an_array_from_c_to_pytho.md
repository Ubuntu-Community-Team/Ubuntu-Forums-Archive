---
title: "swig + python: How to pass an array from c to python?"
date: 2009-05-11
forum: Programming Talk
---

### Post by 3togo on 2009-05-11
I could get an item but not an array. Pls help.
 
swig -c++ -python nodes.i
g++ -shared -fPIC nodes.cpp nodes_wrap.cxx -lpython2.6 -I /usr/include/python2.6/ -o _nodes.so
python
>import nodes
>a=nodes.get()
>print "[%d:%f]"%(a.index,a.value)
[5:1.100000]

My problem is that "a" is indeed a pointer to 5-dimension array. How can I retrieve the rest of the values assuming that I can't modify the content of nodes.cpp. Only nodes.i could be modified.

/*nodes.cpp*/
[PHP]struct FeatureNode {
  int index;
  float value;
};

FeatureNode jj[5];
FeatureNode* get() {
    for(int i=0;i<5;i++) {
        jj[i].index=(i+1)*5;
        jj[i].value=1.1*(i+1);
        }

     return (&jj[0]);
}
[/PHP]
/* nodes.i */
[PHP]%module nodes
%{
struct FeatureNode {
      int index;
      float value;
    };
extern    FeatureNode jj[5];
extern    FeatureNode* get();
%}

struct FeatureNode {
      int index;
      float value;
    };
extern    FeatureNode jj[5];
extern    FeatureNode* get();[/PHP]

---

