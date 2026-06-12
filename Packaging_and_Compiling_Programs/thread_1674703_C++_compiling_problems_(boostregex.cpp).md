---
title: "C++ compiling problems (boost/regex.cpp)"
date: 2011-01-24
forum: Packaging and Compiling Programs
---

### Post by Darkade on 2011-01-24
Hello. While I'm not new to programming I'm just picking up C++ and I've been having problems compiling some simple programs. Right now I've solved them but it was painful looking for the answer I needed, so this is kind of an informative post, but I'm still looking for some advice.

The program I was trying to compile is this
```

#include <iostream>
#include <string>
#include <boost/regex.hpp>  // Boost.Regex lib
#include <boost/config.hpp>


using namespace std;

int main( ) {

   std::string s, sre;
   boost::regex re;

   while(true)
   {
      cout << "Expression: ";
      cin >> sre;
      if (sre == "quit")
      {
         break;
      }
      cout << "String:     ";
      cin >> s;

      try
      {
         // Set up the regular expression for case-insensitivity
         re.assign(sre, boost::regex_constants::icase);
      }
      catch (boost::regex_error& e)
      {
         cout << sre << " is not a valid regular expression: \""
              << e.what() << "\"" << endl;
         continue;
      }
      if (boost::regex_match(s, re))
      {
         cout << re << " matches " << s << endl;
      }
   }
}

```

It was posted as an example in the boost documentation. And the problem I was is posted below, but right now is somewhat unimportant. What is important is that it solved by just adding the  ***-lboost_regex*** to the compiling line so:

This works:```
ivan ~ $  g++ main.cc -o main -lboost_regex
```

this don't ```
ivan ~ $  g++ main.cc -o main 
```

And I really don't understand why. How is one supposed to know that you need to append that tiny option to the compiler. [I googled just for that (-lboost_regex)]("http://www.google.com/search?q=site%3Aboost.org+-lboost_regex&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a#sclient=psy&hl=en&client=firefox-a&hs=HtP&rls=org.mozilla:en-US%3Aofficial&source=hp&q=site:boost.org+%22lboost_regex%22&aq=f&aqi=&aql=&oq=&pbx=1&fp=241062ed1d424d73") in the whole boost site and it's just mentioned in the mailing list, not in the documentation.

I'm really serious about learning C++ but that kind of thing seems cryptic to me. I also tried to compile something with xapian and it needed this option ***-lxapian***. Where can I find this kind of options? Why are they needed? Can someone advice me about this kind of thing?

I know I sound desperate, and that's because I am. I spend at least five hours yesterday trying to compile that, downgrading, upgrading, and compiling by hand the dependencies until I finally found that option. So if you have some pointers to those things I'll really appreciate them.

Thanks, and happy coding.



**ERROR:**
```

Ivan ~/abs $  g++ main.cc -o main
/tmp/cc0thsm4.o:(.gcc_except_table+0x7c): undefined reference to `typeinfo for boost::regex_error'
/tmp/cc0thsm4.o: In function `boost::basic_regex<char, boost::regex_traits<char, boost::cpp_regex_traits<char> > >::assign(char const*, char const*, unsigned int)':
main.cc:(.text._ZN5boost11basic_regexIcNS_12regex_traitsIcNS_16cpp_regex_traitsIcEEEEE6assignEPKcS7_j[boost::basic_regex<char, boost::regex_traits<char, boost::cpp_regex_traits<char> > >::assign(char const*, char const*, unsigned int)]+0x2e): undefined reference to `boost::basic_regex<char, boost::regex_traits<char, boost::cpp_regex_traits<char> > >::do_assign(char const*, char const*, unsigned int)'
/tmp/cc0thsm4.o: In function `bool boost::regex_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >, char, boost::regex_traits<char, boost::cpp_regex_traits<char> > >(__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, __gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, boost::match_results<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > > >&, boost::basic_regex<char, boost::regex_traits<char, boost::cpp_regex_traits<char> > > const&, boost::regex_constants::_match_flags)':
main.cc:(.text._ZN5boost11regex_matchIN9__gnu_cxx17__normal_iteratorIPKcSsEESaINS_9sub_matchIS5_EEEcNS_12regex_traitsIcNS_16cpp_regex_traitsIcEEEEEEbT_SD_RNS_13match_resultsISD_T0_EERKNS_11basic_regexIT1_T2_EENS_15regex_constants12_match_flagsE[bool boost::regex_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >, char, boost::regex_traits<char, boost::cpp_regex_traits<char> > >(__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, __gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, boost::match_results<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > > >&, boost::basic_regex<char, boost::regex_traits<char, boost::cpp_regex_traits<char> > > const&, boost::regex_constants::_match_flags)]+0x80): undefined reference to `boost::re_detail::perl_matcher<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >, boost::regex_traits<char, boost::cpp_regex_traits<char> > >::match()'
/tmp/cc0thsm4.o: In function `boost::re_detail::perl_matcher<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >, boost::regex_traits<char, boost::cpp_regex_traits<char> > >::perl_matcher(__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, __gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, boost::match_results<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > > >&, boost::basic_regex<char, boost::regex_traits<char, boost::cpp_regex_traits<char> > > const&, boost::regex_constants::_match_flags, __gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >)':
main.cc:(.text._ZN5boost9re_detail12perl_matcherIN9__gnu_cxx17__normal_iteratorIPKcSsEESaINS_9sub_matchIS6_EEENS_12regex_traitsIcNS_16cpp_regex_traitsIcEEEEEC2ES6_S6_RNS_13match_resultsIS6_S9_EERKNS_11basic_regexIcSD_EENS_15regex_constants12_match_flagsES6_[_ZN5boost9re_detail12perl_matcherIN9__gnu_cxx17__normal_iteratorIPKcSsEESaINS_9sub_matchIS6_EEENS_12regex_traitsIcNS_16cpp_regex_traitsIcEEEEEC5ES6_S6_RNS_13match_resultsIS6_S9_EERKNS_11basic_regexIcSD_EENS_15regex_constants12_match_flagsES6_]+0x116): undefined reference to `boost::re_detail::perl_matcher<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >, boost::regex_traits<char, boost::cpp_regex_traits<char> > >::construct_init(boost::basic_regex<char, boost::regex_traits<char, boost::cpp_regex_traits<char> > > const&, boost::regex_constants::_match_flags)'
/tmp/cc0thsm4.o: In function `boost::re_detail::perl_matcher<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >, boost::regex_traits<char, boost::cpp_regex_traits<char> > >::unwind_extra_block(bool)':
main.cc:(.text._ZN5boost9re_detail12perl_matcherIN9__gnu_cxx17__normal_iteratorIPKcSsEESaINS_9sub_matchIS6_EEENS_12regex_traitsIcNS_16cpp_regex_traitsIcEEEEE18unwind_extra_blockEb[boost::re_detail::perl_matcher<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >, boost::regex_traits<char, boost::cpp_regex_traits<char> > >::unwind_extra_block(bool)]+0x69): undefined reference to `boost::re_detail::put_mem_block(void*)'
/tmp/cc0thsm4.o: In function `boost::re_detail::perl_matcher<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >, boost::regex_traits<char, boost::cpp_regex_traits<char> > >::match_match()':
main.cc:(.text._ZN5boost9re_detail12perl_matcherIN9__gnu_cxx17__normal_iteratorIPKcSsEESaINS_9sub_matchIS6_EEENS_12regex_traitsIcNS_16cpp_regex_traitsIcEEEEE11match_matchEv[boost::re_detail::perl_matcher<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >, boost::regex_traits<char, boost::cpp_regex_traits<char> > >::match_match()]+0x277): undefined reference to `boost::match_results<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > > >::maybe_assign(boost::match_results<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > > > const&)'
/tmp/cc0thsm4.o: In function `void boost::re_detail::raise_error<boost::regex_traits_wrapper<boost::regex_traits<char, boost::cpp_regex_traits<char> > > >(boost::regex_traits_wrapper<boost::regex_traits<char, boost::cpp_regex_traits<char> > > const&, boost::regex_constants::error_type)':
main.cc:(.text._ZN5boost9re_detail11raise_errorINS_20regex_traits_wrapperINS_12regex_traitsIcNS_16cpp_regex_traitsIcEEEEEEEEvRKT_NS_15regex_constants10error_typeE[void boost::re_detail::raise_error<boost::regex_traits_wrapper<boost::regex_traits<char, boost::cpp_regex_traits<char> > > >(boost::regex_traits_wrapper<boost::regex_traits<char, boost::cpp_regex_traits<char> > > const&, boost::regex_constants::error_type)]+0x4d): undefined reference to `boost::re_detail::raise_runtime_error(std::runtime_error const&)'
/tmp/cc0thsm4.o: In function `boost::re_detail::perl_matcher<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >, boost::regex_traits<char, boost::cpp_regex_traits<char> > >::extend_stack()':
main.cc:(.text._ZN5boost9re_detail12perl_matcherIN9__gnu_cxx17__normal_iteratorIPKcSsEESaINS_9sub_matchIS6_EEENS_12regex_traitsIcNS_16cpp_regex_traitsIcEEEEE12extend_stackEv[boost::re_detail::perl_matcher<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >, boost::regex_traits<char, boost::cpp_regex_traits<char> > >::extend_stack()]+0x36): undefined reference to `boost::re_detail::get_mem_block()'
/tmp/cc0thsm4.o: In function `boost::cpp_regex_traits<char>::transform(char const*, char const*) const':
main.cc:(.text._ZNK5boost16cpp_regex_traitsIcE9transformEPKcS3_[boost::cpp_regex_traits<char>::transform(char const*, char const*) const]+0x38): undefined reference to `boost::re_detail::cpp_regex_traits_implementation<char>::transform(char const*, char const*) const'
/tmp/cc0thsm4.o: In function `boost::cpp_regex_traits<char>::transform_primary(char const*, char const*) const':
main.cc:(.text._ZNK5boost16cpp_regex_traitsIcE17transform_primaryEPKcS3_[boost::cpp_regex_traits<char>::transform_primary(char const*, char const*) const]+0x38): undefined reference to `boost::re_detail::cpp_regex_traits_implementation<char>::transform_primary(char const*, char const*) const'
/tmp/cc0thsm4.o: In function `boost::re_detail::cpp_regex_traits_implementation<char>::error_string(boost::regex_constants::error_type) const':
main.cc:(.text._ZNK5boost9re_detail31cpp_regex_traits_implementationIcE12error_stringENS_15regex_constants10error_typeE[boost::re_detail::cpp_regex_traits_implementation<char>::error_string(boost::regex_constants::error_type) const]+0xa6): undefined reference to `boost::re_detail::get_default_error_string(boost::regex_constants::error_type)'
main.cc:(.text._ZNK5boost9re_detail31cpp_regex_traits_implementationIcE12error_stringENS_15regex_constants10error_typeE[boost::re_detail::cpp_regex_traits_implementation<char>::error_string(boost::regex_constants::error_type) const]+0xfe): undefined reference to `boost::re_detail::get_default_error_string(boost::regex_constants::error_type)'
collect2: ld devolvió el estado de salida 1
ivan ~/abs $  

```

---

### Post by bouncingwilf on 2011-01-24
-lboost_regex includes the  boost library into the linking stage. Without it, references to boost would be unresolved.

Bouncingwilf

---

### Post by ibuclaw on 2011-01-24
-l is a linker option, telling the linker to search for the named library when linking. By default only the standard C++ libraries are linked in (unless specified otherwise with -nostdlib), any other libraries will need to be explicitly added, otherwise the linker will not know about them - hence "undefined reference" to symbols.

---

### Post by Darkade on 2011-01-24
But isn't that what the -I option is for? And where can I find more about those linker options? Thanks

---

### Post by bouncingwilf on 2011-01-25
man ld

Bouncingwilf

---

### Post by poodoopealeoaph on 2011-01-25
I am also very new to programming and I'm not completely sure if compilation is the same between c and c++ so I'm not sure if I can help.... I have noticed that as long as you have gcc installed. If you just run ```
filename.c -c
``` then ```
filename.o -o desired_exe_name
``` then you should be good. Well, that is if c++ compiles the same... hope I was of some sort of help.

---

### Post by ibuclaw on 2011-01-25
> **poodoopealeoaph said:**
> I am also very new to programming and I'm not completely sure if compilation is the same between c and c++
The compilation process is same between C and C++.

---

### Post by bouncingwilf on 2011-01-25
All very similar but please note for C++ you require g++ (get it from the repos)  not gcc. 

Bouncingwilf

---

