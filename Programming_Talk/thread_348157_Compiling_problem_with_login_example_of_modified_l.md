---
title: "Compiling problem with login example of modified libjingle from tapioca"
date: 2007-01-28
forum: Programming Talk
---

### Post by papayiya on 2007-01-28
Hi,

When compiling the login example (of the modified libjingle from Tapioca) I get the following error below.  Does anyone know how I could fix this or what I'm doing wrong.

Thanks,
George

root@papayiya-laptop:/root/dev/temp/libjingle
-tapioca/talk/examples/login# make
if /bin/sh ../../../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../../..  -DPOSIX    -MT xmppauth.lo -MD -MP -MF ".deps/xmppauth.Tpo" -c -o xmppauth.lo xmppauth.cc; \
        then mv -f ".deps/xmppauth.Tpo" ".deps/xmppauth.Plo"; else rm -f ".deps/xmppauth.Tpo"; exit 1; fi
../../../talk/base/xmpppassword.h: In member function 'virtual std::string buzz::EmptyXmppPasswordImpl::UrlEncode() const':
../../../talk/base/xmpppassword.h:54: error: return type 'struct std::string' is incomplete
../../../talk/base/xmpppassword.h: In member function 'std::string buzz::XmppPassword::UrlEncode() const':
../../../talk/base/xmpppassword.h:72: error: return type 'struct std::string' is incomplete
../../../talk/base/xmpppassword.h:72: error: invalid use of undefined type 'struct std::string'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/bits/stringfwd.h:56: error: declaration of 'struct std::string'
../../../talk/base/xmpppassword.h: In member function 'void buzz::FormatXmppPassword::Append(const std::string&)':
../../../talk/base/xmpppassword.h:91: error: invalid use of undefined type 'const struct std::basic_string<char, std::char_traits<char>, std::allocator<char> >'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/bits/stringfwd.h:56: error: declaration of 'const struct std::basic_string<char, std::char_traits<char>, std::allocator<char> >'
../../../talk/base/xmpppassword.h:91: error: invalid use of undefined type 'const struct std::basic_string<char, std::char_traits<char>, std::allocator<char> >'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/bits/stringfwd.h:56: error: declaration of 'const struct std::basic_string<char, std::char_traits<char>, std::allocator<char> >'
make: *** [xmppauth.lo] Error 1
root@papayiya-laptop:/root/dev/temp/libjingle-tapioca/talk/examples/login#

---

