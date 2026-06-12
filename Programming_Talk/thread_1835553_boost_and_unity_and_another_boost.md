---
title: "boost and unity and another boost"
date: 2011-08-29
forum: Programming Talk
---

### Post by herrzweiblum on 2011-08-29
So i guess this goes best here:

Am developing for a project that is using boost as a contrib library. Switched from 10.04 to 11.04 lately and get the most weird error message while building a CXX object that is using ```
#include <boost/accumulators/accumulators.hpp>
``` 
btw other boost includes are no problem e.g. ```
#include <boost/math/special_functions/fpclassify.hpp>
```

So, it goes like:
```
include/boost/accumulators/numeric/functional.hpp:190:5:   instantiated from ‘boost::numeric::functional::result_of_divides<mpl_::arg<1>, mpl_::arg<2>, void>’
... this goes on for a while with nested instantiated blah...
... include/boost/accumulators/numeric/functional.hpp:190:5: error: no match for ‘operator/’ in ‘boost::numeric::functional::detail::lvalue_of [with T = mpl_::arg<1>]() / boost::numeric::functional::detail::lvalue_of [with T = mpl_::arg<2>]()’
#or when playing a round a bit with boost includes  
...include/boost/accumulators/statistics/variance.hpp:88:89: error: no type named ‘result_type’ in ‘struct boost::numeric::functional::average<mpl_::arg<1>, unsigned int, void, void>’
```

well I guess this comes with unity and the usage of boost within as I have no such problems with 10.04. I see that CMAKE is using the correct boost headers but it must get confused with the lib.
Does anyone have a piece of advice where to begin to get this straight?

cheers, 
  zweiblum

---

### Post by MadCow108 on 2011-08-29
the hello world example given in the user guide works fine in 11.04
please give a more complete example reproducing your problem

did you upgrade from 10.04 or was it a fresh install?

---

