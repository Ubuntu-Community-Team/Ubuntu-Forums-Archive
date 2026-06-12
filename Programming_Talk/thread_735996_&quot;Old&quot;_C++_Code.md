---
title: "&quot;Old&quot; C++ Code"
date: 2008-03-26
forum: Programming Talk
---

### Post by algatt on 2008-03-26
Hello,

I am trying to compile some C++ code ([http://www.cse.ust.hk/~yike/prtree/](http://www.cse.ust.hk/~yike/prtree/)) but it cannot compile, and I think it's mainly because the code is somewhat old. Is there a way to compile code for the year it was created on - I think 2002.

Thanks.

---

### Post by CptPicard on 2008-03-26
Umm no, code doesn't rot like that and the C++ standard doesn't evolve that quickly... :) care to give your compiler errors?

---

### Post by algatt on 2008-03-26
Hmm... There are far too many errors in the code ~300 errors!

The code I am trying to compile is a PR-Tree index (related to R-Tree), but it uses the TPIE library ([http://www.cs.duke.edu/TPIE/](http://www.cs.duke.edu/TPIE/)). The errors are on all sides.

There are some errors in the include files (TPIE) such as

```
../include/vararray.H: In member function ‘VarArray2D<T>& VarArray2D<T>::operator=(const VarArray2D<T>&)’:
../include/vararray.H:205: error: invalid types ‘int[int]’ for array subscript
../include/vararray.H:205: error: invalid types ‘int[int]’ for array subscript
../include/vararray.H: In member function ‘VarArray3D<T>& VarArray3D<T>::operator=(const VarArray3D<T>&)’:
../include/vararray.H:288: error: invalid types ‘int[int]’ for array subscript
../include/vararray.H:288: error: invalid types ‘int[int]’ for array subscript
../include/vararray.H:288: error: invalid types ‘int[int]’ for array subscript
../include/logstream.H: At global scope:
../include/logstream.H:66: error: declaration of ‘operator<<’ as non-function
../include/logstream.H:66: error: expected ‘;’ before ‘<’ token
```

and also on the PR-Tree side such as:

```
./ami_PRtree.H:134: error: ‘typedef class AMI_stream_single<box_type<double, 2u> > PRtree<double, 2u, BTE_collection_mmap<unsigned int> >::stream_t’ is private
build_PRtree.C:26: error: within this context
./ami_PRtree.H:134: error: ‘typedef class AMI_stream_single<box_type<double, 2u> > PRtree<double, 2u, BTE_collection_mmap<unsigned int> >::stream_t’ is private
build_PRtree.C:26: error: within this context
./ami_PRtree.H:134: error: ‘typedef class AMI_stream_single<box_type<double, 2u> > PRtree<double, 2u, BTE_collection_mmap<unsigned int> >::stream_t’ is private
build_PRtree.C:51: error: within this context
```


Last small thing, one error was about not finding **hash_set** and I added **ext/** in front (hope did well). 

Thanks!

---

