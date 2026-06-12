---
title: "how to use codecvt from GNU libstdc++?"
date: 2007-06-24
forum: Programming Talk
---

### Post by baritono on 2007-06-24
I'm trying to use std::codecvt from the C++ standard library. And I found this snippet from GNU libstdc++ official documentation (from [http://gcc.gnu.org/onlinedocs/libstdc++/22_locale/codecvt.html](http://gcc.gnu.org/onlinedocs/libstdc++/22_locale/codecvt.html))

  typedef codecvt_base::result                  result;
  typedef unsigned short                        unicode_t;
  typedef unicode_t                             int_type;
  typedef char                                  ext_type;
  typedef encoding_state                          state_type;
  typedef codecvt<int_type, ext_type, state_type> unicode_codecvt;

  const ext_type*       e_lit = "black pearl jasmine tea";
  int                   size = strlen(e_lit);
  int_type              i_lit_base[24] = 
  { 25088, 27648, 24832, 25344, 27392, 8192, 28672, 25856, 24832, 29184, 
    27648, 8192, 27136, 24832, 29440, 27904, 26880, 28160, 25856, 8192, 29696,
    25856, 24832, 2560
  };
  const int_type*       i_lit = i_lit_base;
  const ext_type*       efrom_next;
  const int_type*       ifrom_next;
  ext_type*             e_arr = new ext_type[size + 1];
  ext_type*             eto_next;
  int_type*             i_arr = new int_type[size + 1];
  int_type*             ito_next;

  // construct a locale object with the specialized facet.
  locale                loc(locale::classic(), new unicode_codecvt);
  // sanity check the constructed locale has the specialized facet.
  VERIFY( has_facet<unicode_codecvt>(loc) );
  const unicode_codecvt& cvt = use_facet<unicode_codecvt>(loc); 
  // convert between const char* and unicode strings
  unicode_codecvt::state_type state01("UNICODE", "ISO_8859-1");
  initialize_state(state01);
  result r1 = cvt.in(state01, e_lit, e_lit + size, efrom_next, 
                     i_arr, i_arr + size, ito_next);
  VERIFY( r1 == codecvt_base:: ok );
  VERIFY( !int_traits::compare(i_arr, i_lit, size) ); 
  VERIFY( efrom_next == e_lit + size );
  VERIFY( ito_next == i_arr + size );

I encapsulate it with a main() and
#include <cassert>
#include <locale>
using namespace std;

#define VERIFY(x) assert(x)

but it does not work! g++ says
convert.cpp: In function 'int main()'
convert.cpp:38: error: variable 'std::__enc_traits state01' has initializer but incomplete type

seems that the header <locale> contains only a forward declaration for std::__enc_traits, but where can I find the complete definition, which header should I include? can anybody help me?

$ g++ --version
g++ (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
...
$ g++ -dumpmachine
i486-linux-gnu

---

