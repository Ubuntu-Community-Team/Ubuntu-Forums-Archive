---
title: "C++ compilation problems"
date: 2006-05-08
forum: Packaging and Compiling Programs
---

### Post by ravalox on 2006-05-08
I am trying to develop with C++ on my Ubuntu installation, I installed eclipse and CDT, when I attempt to use g++ I get this massive error message:

```
/usr/bin/g++  Point.cpp Color.cpp Box.cpp -o boxTest
/usr/include/c++/4.0.2/i486-linux-gnu/bits/c++config.h:64: error: expected unqualified-id before ‘namespace’
/usr/include/c++/4.0.2/i486-linux-gnu/bits/c++config.h:68: error: expected namespace-name before ‘;’ token
/usr/include/c++/4.0.2/i486-linux-gnu/bits/c++config.h:68: error: ‘<type error>’ is not a namespace
/usr/include/c++/4.0.2/i486-linux-gnu/bits/c++config.h:64: error: expected unqualified-id before ‘namespace’
/usr/include/c++/4.0.2/i486-linux-gnu/bits/c++config.h:68: error: expected namespace-name before ‘;’ token
/usr/include/c++/4.0.2/i486-linux-gnu/bits/c++config.h:68: error: ‘<type error>’ is not a namespace
/usr/include/c++/4.0.2/bits/localefwd.h:50: error: expected unqualified-id before ‘namespace’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2502: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3969: error: provided for ‘template<class _CharT, class _InIter> class std::money_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2503: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:4104: error: provided for ‘template<class _CharT, class _OutIter> class std::money_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2506: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:1926: error: provided for ‘template<class _CharT, class _InIter> class std::num_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2507: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:2205: error: provided for ‘template<class _CharT, class _OutIter> class std::num_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2509: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3323: error: provided for ‘template<class _CharT, class _OutIter> class std::time_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2510: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3419: error: provided for ‘template<class _CharT, class _OutIter> class std::time_put_byname’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2511: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:2982: error: provided for ‘template<class _CharT, class _InIter> class std::time_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2512: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3295: error: provided for ‘template<class _CharT, class _InIter> class std::time_get_byname’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2533: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:2205: error: provided for ‘template<class _CharT, class _OutIter> class std::num_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2534: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:2205: error: provided for ‘template<class _CharT, class _OutIter> class std::num_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2534: error: template-id ‘use_facet<<expression error> >’ for ‘const int& std::use_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2537: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:1926: error: provided for ‘template<class _CharT, class _InIter> class std::num_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2538: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:1926: error: provided for ‘template<class _CharT, class _InIter> class std::num_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2538: error: template-id ‘use_facet<<expression error> >’ for ‘const int& std::use_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2549: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:4104: error: provided for ‘template<class _CharT, class _OutIter> class std::money_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2550: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:4104: error: provided for ‘template<class _CharT, class _OutIter> class std::money_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2550: error: template-id ‘use_facet<<expression error> >’ for ‘const int& std::use_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2553: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3969: error: provided for ‘template<class _CharT, class _InIter> class std::money_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2554: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3969: error: provided for ‘template<class _CharT, class _InIter> class std::money_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2554: error: template-id ‘use_facet<<expression error> >’ for ‘const int& std::use_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2561: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3323: error: provided for ‘template<class _CharT, class _OutIter> class std::time_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2562: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3323: error: provided for ‘template<class _CharT, class _OutIter> class std::time_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2562: error: template-id ‘use_facet<<expression error> >’ for ‘const int& std::use_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2565: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:2982: error: provided for ‘template<class _CharT, class _InIter> class std::time_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2566: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:2982: error: provided for ‘template<class _CharT, class _InIter> class std::time_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2566: error: template-id ‘use_facet<<expression error> >’ for ‘const int& std::use_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2590: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:2205: error: provided for ‘template<class _CharT, class _OutIter> class std::num_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2590: error: template-id ‘has_facet<<expression error> >’ for ‘bool std::has_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2594: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:1926: error: provided for ‘template<class _CharT, class _InIter> class std::num_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2594: error: template-id ‘has_facet<<expression error> >’ for ‘bool std::has_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2598: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3540: error: provided for ‘template<class _CharT, bool _Intl> class std::moneypunct’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2598: error: template-id ‘has_facet<<expression error> >’ for ‘bool std::has_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2602: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:4104: error: provided for ‘template<class _CharT, class _OutIter> class std::money_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2602: error: template-id ‘has_facet<<expression error> >’ for ‘bool std::has_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2606: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3969: error: provided for ‘template<class _CharT, class _InIter> class std::money_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2606: error: template-id ‘has_facet<<expression error> >’ for ‘bool std::has_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2614: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3323: error: provided for ‘template<class _CharT, class _OutIter> class std::time_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2614: error: template-id ‘has_facet<<expression error> >’ for ‘bool std::has_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2618: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:2982: error: provided for ‘template<class _CharT, class _InIter> class std::time_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2618: error: template-id ‘has_facet<<expression error> >’ for ‘bool std::has_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2629: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3969: error: provided for ‘template<class _CharT, class _InIter> class std::money_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2630: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:4104: error: provided for ‘template<class _CharT, class _OutIter> class std::money_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2633: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:1926: error: provided for ‘template<class _CharT, class _InIter> class std::num_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2634: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:2205: error: provided for ‘template<class _CharT, class _OutIter> class std::num_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2636: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3323: error: provided for ‘template<class _CharT, class _OutIter> class std::time_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2637: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3419: error: provided for ‘template<class _CharT, class _OutIter> class std::time_put_byname’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2638: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:2982: error: provided for ‘template<class _CharT, class _InIter> class std::time_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2639: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3295: error: provided for ‘template<class _CharT, class _InIter> class std::time_get_byname’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2660: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:2205: error: provided for ‘template<class _CharT, class _OutIter> class std::num_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2661: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:2205: error: provided for ‘template<class _CharT, class _OutIter> class std::num_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2661: error: template-id ‘use_facet<<expression error> >’ for ‘const int& std::use_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2664: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:1926: error: provided for ‘template<class _CharT, class _InIter> class std::num_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2665: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:1926: error: provided for ‘template<class _CharT, class _InIter> class std::num_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2665: error: template-id ‘use_facet<<expression error> >’ for ‘const int& std::use_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2676: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:4104: error: provided for ‘template<class _CharT, class _OutIter> class std::money_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2677: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:4104: error: provided for ‘template<class _CharT, class _OutIter> class std::money_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2677: error: template-id ‘use_facet<<expression error> >’ for ‘const int& std::use_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2680: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3969: error: provided for ‘template<class _CharT, class _InIter> class std::money_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2681: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3969: error: provided for ‘template<class _CharT, class _InIter> class std::money_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2681: error: template-id ‘use_facet<<expression error> >’ for ‘const int& std::use_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2688: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3323: error: provided for ‘template<class _CharT, class _OutIter> class std::time_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2689: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3323: error: provided for ‘template<class _CharT, class _OutIter> class std::time_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2689: error: template-id ‘use_facet<<expression error> >’ for ‘const int& std::use_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2692: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:2982: error: provided for ‘template<class _CharT, class _InIter> class std::time_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2693: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:2982: error: provided for ‘template<class _CharT, class _InIter> class std::time_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2693: error: template-id ‘use_facet<<expression error> >’ for ‘const int& std::use_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2717: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:2205: error: provided for ‘template<class _CharT, class _OutIter> class std::num_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2717: error: template-id ‘has_facet<<expression error> >’ for ‘bool std::has_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2721: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:1926: error: provided for ‘template<class _CharT, class _InIter> class std::num_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2721: error: template-id ‘has_facet<<expression error> >’ for ‘bool std::has_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2725: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3540: error: provided for ‘template<class _CharT, bool _Intl> class std::moneypunct’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2725: error: template-id ‘has_facet<<expression error> >’ for ‘bool std::has_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2729: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:4104: error: provided for ‘template<class _CharT, class _OutIter> class std::money_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2729: error: template-id ‘has_facet<<expression error> >’ for ‘bool std::has_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2733: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3969: error: provided for ‘template<class _CharT, class _InIter> class std::money_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2733: error: template-id ‘has_facet<<expression error> >’ for ‘bool std::has_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2741: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:3323: error: provided for ‘template<class _CharT, class _OutIter> class std::time_put’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2741: error: template-id ‘has_facet<<expression error> >’ for ‘bool std::has_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2745: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.0.2/bits/locale_facets.h:2982: error: provided for ‘template<class _CharT, class _InIter> class std::time_get’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2745: error: template-id ‘has_facet<<expression error> >’ for ‘bool std::has_facet(const std::locale&)’ does not match any template declaration
make: *** [default] Error 1
```

---

### Post by treak007 on 2006-05-09
hmmm...are you willing to show some segments of the code b/c that would make error finding a lot easier. From the nature of the errors, it looks like the error resides possibly within your template.

---

