---
title: "[SOLVED] Compiling boost libaries,help needed."
date: 2008-05-11
forum: Programming Talk
---

### Post by StOoZ on 2008-05-11
I have the following program:
> #include <boost/regex.hpp>
#include <iostream>
#include <string>
using namespace boost;
using namespace std;

int main(int argc, char* argv[])
{
	const boost::regex e("[a-z]+"); //This is the regular expression

	for(int i = 1; i< argc; ++i)
	{
		if (regex_match( std::string(argv[i]), e ))
		{
			std::cout << argv[i] 
				<< " contains lowercase characters.\n";
		}
		else
		{
			std::cout << argv[i] 
				<< " contains no lowercase characters.\n";
		}
	}

}


I've installed the latest boost libs from source,with the default settings,in the compile command line I insert :
> /usr/local/include/boost-1_35

But I get the following error:
> Running "/usr/bin/make  -f Makefile CONF=Debug clean" in /home/guy/NetBeansProjects/Application_5

/usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .clean-conf
make[1]: Entering directory `/home/guy/NetBeansProjects/Application_5'
rm -f -r build/Debug
rm -f dist/Debug/GNU-Linux-x86/application_5
make[1]: Leaving directory `/home/guy/NetBeansProjects/Application_5'

Clean successful. Exit value 0.

Running "/usr/bin/make  -f Makefile CONF=Debug" in /home/guy/NetBeansProjects/Application_5

/usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .build-conf
make[1]: Entering directory `/home/guy/NetBeansProjects/Application_5'
mkdir -p build/Debug/GNU-Linux-x86
g++    -c -g -I/usr/local/include/boost-1_35 -o build/Debug/GNU-Linux-x86/newmain.o newmain.cc
mkdir -p dist/Debug/GNU-Linux-x86
g++     -o dist/Debug/GNU-Linux-x86/application_5 build/Debug/GNU-Linux-x86/newmain.o  
build/Debug/GNU-Linux-x86/newmain.o: In function `boost::basic_regex<char, boost::regex_traits<char, boost::cpp_regex_traits<char> > >::assign(char const*, char const*, unsigned int)':
/usr/local/include/boost-1_35/boost/regex/v4/basic_regex.hpp:262: undefined reference to `boost::basic_regex<char, boost::regex_traits<char, boost::cpp_regex_traits<char> > >::do_assign(char const*, char const*, unsigned int)'
build/Debug/GNU-Linux-x86/newmain.o: In function `perl_matcher':
/usr/local/include/boost-1_35/boost/regex/v4/perl_matcher.hpp:347: undefined reference to `boost::re_detail::perl_matcher<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >, boost::regex_traits<char, boost::cpp_regex_traits<char> > >::construct_init(boost::basic_regex<char, boost::regex_traits<char, boost::cpp_regex_traits<char> > > const&, boost::regex_constants::_match_flags)'
build/Debug/GNU-Linux-x86/newmain.o: In function `bool boost::regex_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >, char, boost::regex_traits<char, boost::cpp_regex_traits<char> > >(__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, __gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, boost::match_results<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > > >&, boost::basic_regex<char, boost::regex_traits<char, boost::cpp_regex_traits<char> > > const&, boost::regex_constants::_match_flags)':
/usr/local/include/boost-1_35/boost/regex/v4/regex_match.hpp:50: undefined reference to `boost::re_detail::perl_matcher<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >, boost::regex_traits<char, boost::cpp_regex_traits<char> > >::match()'
build/Debug/GNU-Linux-x86/newmain.o: In function `boost::cpp_regex_traits<char>::transform(char const*, char const*) const':
/usr/local/include/boost-1_35/boost/regex/v4/cpp_regex_traits.hpp:884: undefined reference to `boost::re_detail::cpp_regex_traits_implementation<char>::transform(char const*, char const*) const'
build/Debug/GNU-Linux-x86/newmain.o: In function `boost::cpp_regex_traits<char>::transform_primary(char const*, char const*) const':
/usr/local/include/boost-1_35/boost/regex/v4/cpp_regex_traits.hpp:888: undefined reference to `boost::re_detail::cpp_regex_traits_implementation<char>::transform_primary(char const*, char const*) const'
build/Debug/GNU-Linux-x86/newmain.o: In function `boost::re_detail::perl_matcher<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >, boost::regex_traits<char, boost::cpp_regex_traits<char> > >::match_match()':
/usr/local/include/boost-1_35/boost/regex/v4/perl_matcher_common.hpp:479: undefined reference to `boost::match_results<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > > >::maybe_assign(boost::match_results<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > > > const&)'
build/Debug/GNU-Linux-x86/newmain.o: In function `boost::re_detail::cpp_regex_traits_implementation<char>::error_string(boost::regex_constants::error_type) const':
/usr/local/include/boost-1_35/boost/regex/v4/cpp_regex_traits.hpp:432: undefined reference to `boost::re_detail::get_default_error_string(boost::regex_constants::error_type)'
/usr/local/include/boost-1_35/boost/regex/v4/cpp_regex_traits.hpp:434: undefined reference to `boost::re_detail::get_default_error_string(boost::regex_constants::error_type)'
build/Debug/GNU-Linux-x86/newmain.o: In function `void boost::re_detail::raise_error<boost::regex_traits_wrapper<boost::regex_traits<char, boost::cpp_regex_traits<char> > > >(boost::regex_traits_wrapper<boost::regex_traits<char, boost::cpp_regex_traits<char> > > const&, boost::regex_constants::error_type)':
/usr/local/include/boost-1_35/boost/regex/pattern_except.hpp:75: undefined reference to `boost::re_detail::raise_runtime_error(std::runtime_error const&)'
build/Debug/GNU-Linux-x86/newmain.o: In function `boost::re_detail::perl_matcher<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >, boost::regex_traits<char, boost::cpp_regex_traits<char> > >::extend_stack()':
/usr/local/include/boost-1_35/boost/regex/v4/perl_matcher_non_recursive.hpp:197: undefined reference to `boost::re_detail::get_mem_block()'
build/Debug/GNU-Linux-x86/newmain.o: In function `boost::re_detail::perl_matcher<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >, boost::regex_traits<char, boost::cpp_regex_traits<char> > >::unwind_extra_block(bool)':
/usr/local/include/boost-1_35/boost/regex/v4/perl_matcher_non_recursive.hpp:976: undefined reference to `boost::re_detail::put_mem_block(void*)'
collect2: ld returned 1 exit status
make[1]: *** [dist/Debug/GNU-Linux-x86/application_5] Error 1
make[1]: Leaving directory `/home/guy/NetBeansProjects/Application_5'
make: *** [.build-impl] Error 2

Build failed. Exit value 2.



any idea how to solve it?

---

### Post by StOoZ on 2008-05-11
problem solved.
How?:
its not enough to only include the libs, linking with dynamic libs (.so) must be done,which by default are located at : /usr/local/lib    with the appropriate lib.
in this case : libboost_regex-gcc41-mt-1_35.so

solved the issue.

---

### Post by Jessehk on 2008-05-11
One of the strongest benefits of the Debian/Ubuntu way is that almost every package is included in the repositories and included in the deb/apt system. Similarly, in my opinion, it's biggest disadvantage is that you are severly restricted if you want to do something outside the confines of that system.

Without looking too intently, it seems that there is an error in the latest boost sources. It's probably nothing **you** did.

My advice would be to downgrade the version of Boost to the one supplied in the repositories (libboost-dev for the header libs and libboost-<whatever>-dev for the others like Regex if I remember correctly).

EDIT: I looked again and I was going to suggest that you try linking to the libraries (if you hadn't already), but then you beat me to it. :)

EDIT2: For future reference, this should be all that's required:
```

gcc -lboost_regex <file>.c -o file

```

---

### Post by StOoZ on 2008-05-11
Thanks.
I already seen that an older version is included in the repositories... the issue is, that since its an older version, asio libs are not included in there, and I really need it for my dev.

---

