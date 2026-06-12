---
title: "Programm slower with multiple Threads?"
date: 2009-03-13
forum: Programming Talk
---

### Post by MadMan2k on 2009-03-13
I have written a program in C++ where the computation heavy part boils down to searching for a large number of points for the nearest neighbour in a OctTree.

Therefore I thought I could speed up the computation with distributing the searching loop on several threads. So I have something like this:

```

#pragma omp parallel for
for(int i=0; i < 10000; i++) {
    octTree.get_nearest(p[i]);
}

```

but when I set the thread count to more than 1, the program actually takes longer. Now I am wondering what it could be.

Below is my implementation of the OctTree, if it helps. Generally I pass only references around when I build the Tree, so all data is stored somewhere in arbitary order. Is it probably a caching issue? So that multiple threads result in more cache misses?

```

/* 
 * File:   octtree.cpp
 * Author: pavel
 * 
 * Created on 24. Januar 2009, 11:19
 */

#include "octtree.h"

#include <array>
#include <valarray>
#include <algorithm>
#include <functional>

#include "linalg.h"

using namespace std::placeholders;

/**
 * Distance Comparator
 * compares two points according to their distance to cmp
 * @param cmp comparison point
 * @param a one point
 * @param b another point
 * @return true if a < b
 */
static bool dist_cmp(const valarray<float>* cmp, const valarray<float>* a, const valarray<float>* b) {
    array<float, 3> tmp1, tmp2;

    for (int i = 0; i < 3; i++) {
        tmp1[i] = (*a)[i] - (*cmp)[i];
        tmp2[i] = (*b)[i] - (*cmp)[i];
    }

    return dot(tmp1, tmp1) < dot(tmp2, tmp2);
}

OctTree::OctTree(const list<const valarray<float>*> &data, const Boundings _b, const OctTree *_parent) : b(_b), parent(_parent) {
    is_leaf = false;
    
    if (data.size() == 1) {
        p = data.front();
        is_leaf = true;
        return;
    }

    // Center
    const valarray<float>& center = (b.min + b.max) / 2;

    // Sides
    const valarray<valarray<float>>& s = diag(b.max - b.min);

    // Edges of the Boundings
    valarray<valarray<float>> verts(valarray<float>(3), 8);
    verts[0] = b.min;
    verts[1] = b.min + s[0];
    verts[2] = b.min + s[0] + s[2];
    verts[3] = b.min + s[2];
    verts[4] = b.min + s[1];
    verts[5] = b.min + s[0] + s[1];
    verts[6] = b.max;
    verts[7] = b.min + s[1] + s[2];

    // Create children
    for (int i = 0; i < 8; i++) {
        Boundings c_b(center, verts[i]); // child boundings
        list<const valarray<float>*> c_d;      // child data

        for (list<const valarray<float>*>::const_iterator it = data.begin(); it != data.end(); it++) {
            if (c_b.contains(*(*it))) {
                c_d.push_back(*it);
            }
        }

        childs[i] = c_d.size() == 0 ? NULL : new OctTree(c_d, c_b, this);
    }
}

void OctTree::get_points(list<const valarray<float>*>& pts) const {
    if (is_leaf) {
        pts.push_back(p);
    } else {
        for (int i = 0; i < 8; i++) {
            if(childs[i] != NULL)
                childs[i]->get_points(pts);
        }
    }
}


const valarray<float>* OctTree::get_nearest(const valarray<float>& p) const {
    list<const valarray<float>*> l;
    float r;
    function<bool (const valarray<float>*, const valarray<float>*)>
    cmp = bind(dist_cmp, &p, _1, _2);

    if (is_leaf) {
        // we have only one child
        r = norm2(p - (valarray<float>)(*this->p)[slice(0,3,1)]);

        Boundings b(p + r, p - r);
        walk_up(b, l);

        return *min_element(l.begin(), l.end(), cmp);
    }

    // try to dispatch
    for (int i = 0; i < 8; i++) {
        if (childs[i] != NULL && childs[i]->b.contains(p))
            return childs[i]->get_nearest(p);
    }

    get_points(l);

    // now search with BBox
    r = norm2(p - (**min_element(l.begin(), l.end(), cmp))[slice(0,3,1)]);

    Boundings b(p + r, p -r);

    l.clear();
    walk_up(b, l);

    return *min_element(l.begin(), l.end(), cmp);
}

void OctTree::get_in_bbox(const Boundings& b, list<const valarray<float>*> &pts) const {
    if (is_leaf) {
        if (b.weak_contains(*p)) {
            pts.push_back(p);
        }
        return;
    }

    for (int i = 0; i < 8; i++) {
        if(childs[i] != NULL && childs[i]->b.contains(b))
            childs[i]->get_in_bbox(b, pts);
    }
}

void OctTree::walk_up(const Boundings& b, list<const valarray<float>*>& pts) const {
    if (this->b.encloses(b) || parent == NULL) {
        get_in_bbox(b, pts);
    } else {
        parent->walk_up(b, pts);
    }
}

int OctTree::depth() {
    if (is_leaf) {
        return 1;
    } else {
        int c_d = 0;

        for (int i = 0; i < 8; i++) {
            if(childs[i] != NULL)
                c_d = max(c_d, childs[i]->depth());
        }

        return c_d + 1;
    }
}


```

---

### Post by regala on 2009-03-13
> **MadMan2k said:**
> 
but when I set the thread count to more than 1, the program actually takes longer.


on which machine did you run your program ? (i.e. how many processors/cores do you have ?)

---

### Post by kjohansen on 2009-03-13
There is always some overhead in starting up multithreaded/parallel applications, if the "size" of the problem is too small for the number of processors you have specified you will get worse performance...

---

### Post by the_unforgiven on 2009-03-13
Don't know if I missed something, but the code doesn't look like multi-threaded at all.
You're not creating threads - you're just creating *objects* of the same class and pushing them in the childs list/whatever. And then, in almost all the functions, you're just running through this list of children *sequentially*.

I don't think the OctTree class derives from a threading structure, does it? Neither did I find any thread initialization in the ctor.

That's all I could gather from the snippet of code.

Let me know if I am wrong or have missed something.

---

### Post by MadMan2k on 2009-03-13
> **the_unforgiven said:**
> Don't know if I missed something, but the code doesn't look like multi-threaded at all.
I have a list of points for which I want to know the nearest neighbour from a fixed set of points.
In order to speed up the search the set is organised as an OctTree.

Do separate the work on several threads I just let Thread1 find the neighbours for points 1..n/2 and Thread2 for n/2..n.
(in the code its the #pragma line from openmp)

My machine is a dual-core core2.

---

### Post by the_unforgiven on 2009-03-13
> **MadMan2k said:**
> I have a list of points for which I want to know the nearest neighbour from a fixed set of points.
In order to speed up the search the set is organised as an OctTree.

Do separate the work on several threads I just let Thread1 find the neighbours for points 1..n/2 and Thread2 for n/2..n.
(in the code its the #pragma line from openmp)

My machine is a dual-core core2.

Ah... OpenMP it is..
Need to do more study on it :p

---

