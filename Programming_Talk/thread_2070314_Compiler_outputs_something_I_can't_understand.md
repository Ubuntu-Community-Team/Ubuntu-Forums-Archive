---
title: "Compiler outputs something I can't understand"
date: 2012-10-12
forum: Programming Talk
---

### Post by Dirich on 2012-10-12
Hello,

I just finished porting from c to c++ my code, due to a change in libraries (from lapack to eigen).

NOTE: I have a makefile for the old version of my code, but due to some modification I did I am back to my "manually implemented makefile-like system".
You just need to run "drm" (gcc -o drm DRMmain.c) and it will compile everything on its own and run the program.
I have attached the code and everything that is needed to run it if you wanna check the source.

There seems to be essentially no problem with the syntax, but the compiler gives me the following text after compiling, and I can't understand what is the problem.
Also, do not mind the warnings for zero-length gnu_printf.


Thanks for helping!

```

DRMscripting.cpp: In function ‘void Scripting(int&, int&, realtype&, realtype&, int&, realtype&, adatom*)’:
DRMscripting.cpp:91:25: warning: zero-length gnu_printf format string [-Wformat-zero-length]
DRMscripting.cpp:112:36: warning: zero-length gnu_printf format string [-Wformat-zero-length]
DRMscripting.cpp:14:91: warning: unused variable ‘dname’ [-Wunused-variable]
DRMleads.cpp: In function ‘int Sigma_Leads(MatrixXcomplex&, MatrixXcomplex&, MatrixXcomplex*, MatrixXcomplex*, complextype&, realtype&, adatom*, int&)’:
DRMleads.cpp:21:9: warning: unused variable ‘j’ [-Wunused-variable]
/tmp/cc68qjfU.o: In function `__static_initialization_and_destruction_0(int, int)':
DRMsimulator.cpp:(.text+0x14a9): undefined reference to `std::ios_base::Init::Init()'
DRMsimulator.cpp:(.text+0x14ae): undefined reference to `std::ios_base::Init::~Init()'
/tmp/cc68qjfU.o: In function `std::exception::exception()':
DRMsimulator.cpp:(.text._ZNSt9exceptionC2Ev[_ZNSt9exceptionC5Ev]+0x8): undefined reference to `vtable for std::exception'
/tmp/cc68qjfU.o: In function `std::bad_alloc::bad_alloc()':
DRMsimulator.cpp:(.text._ZNSt9bad_allocC2Ev[_ZNSt9bad_allocC5Ev]+0x16): undefined reference to `vtable for std::bad_alloc'
/tmp/cc68qjfU.o: In function `Eigen::internal::throw_std_bad_alloc()':
DRMsimulator.cpp:(.text._ZN5Eigen8internal19throw_std_bad_allocEv[Eigen::internal::throw_std_bad_alloc()]+0xf): undefined reference to `__cxa_allocate_exception'
DRMsimulator.cpp:(.text._ZN5Eigen8internal19throw_std_bad_allocEv[Eigen::internal::throw_std_bad_alloc()]+0x1e): undefined reference to `std::bad_alloc::~bad_alloc()'
DRMsimulator.cpp:(.text._ZN5Eigen8internal19throw_std_bad_allocEv[Eigen::internal::throw_std_bad_alloc()]+0x2a): undefined reference to `typeinfo for std::bad_alloc'
DRMsimulator.cpp:(.text._ZN5Eigen8internal19throw_std_bad_allocEv[Eigen::internal::throw_std_bad_alloc()]+0x32): undefined reference to `__cxa_throw'
/tmp/cc68qjfU.o:(.eh_frame+0x18b): undefined reference to `__gxx_personality_v0'
/tmp/ccy8eWNO.o: In function `__static_initialization_and_destruction_0(int, int)':
DRMprobleminit.cpp:(.text+0x2c4): undefined reference to `std::ios_base::Init::Init()'
DRMprobleminit.cpp:(.text+0x2c9): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccyNxO1K.o: In function `__static_initialization_and_destruction_0(int, int)':
DRMscripting.cpp:(.text+0xc16): undefined reference to `std::ios_base::Init::Init()'
DRMscripting.cpp:(.text+0xc1b): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccznl0LM.o: In function `__static_initialization_and_destruction_0(int, int)':
DRMleads.cpp:(.text+0x15c8): undefined reference to `std::ios_base::Init::Init()'
DRMleads.cpp:(.text+0x15cd): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccznl0LM.o:(.eh_frame+0x41f): undefined reference to `__gxx_personality_v0'
/tmp/ccPdYa9V.o: In function `Transport_Imaging(Eigen::Matrix<std::complex<double>, -1, -1, 0, -1, -1>&, Eigen::Matrix<std::complex<double>, -1, -1, 0, -1, -1>&, Eigen::Matrix<std::complex<double>, -1, -1, 0, -1, -1>*, Eigen::Matrix<std::complex<double>, -1, -1, 0, -1, -1>*, std::complex<double>&, double&, adatom*, int&, int)':
DRMtransport.cpp:(.text+0x517): undefined reference to `std::basic_ofstream<char, std::char_traits<char> >::basic_ofstream()'
DRMtransport.cpp:(.text+0x541): undefined reference to `std::basic_ofstream<char, std::char_traits<char> >::basic_ofstream()'
DRMtransport.cpp:(.text+0x56b): undefined reference to `std::basic_ofstream<char, std::char_traits<char> >::basic_ofstream()'
DRMtransport.cpp:(.text+0x704): undefined reference to `std::basic_ofstream<char, std::char_traits<char> >::open(char const*, std::_Ios_Openmode)'
DRMtransport.cpp:(.text+0x751): undefined reference to `std::basic_ofstream<char, std::char_traits<char> >::open(char const*, std::_Ios_Openmode)'
DRMtransport.cpp:(.text+0x79e): undefined reference to `std::basic_ofstream<char, std::char_traits<char> >::open(char const*, std::_Ios_Openmode)'
DRMtransport.cpp:(.text+0x7f0): undefined reference to `std::basic_ofstream<char, std::char_traits<char> >::open(char const*, std::_Ios_Openmode)'
DRMtransport.cpp:(.text+0x842): undefined reference to `std::basic_ofstream<char, std::char_traits<char> >::open(char const*, std::_Ios_Openmode)'
/tmp/ccPdYa9V.o:DRMtransport.cpp:(.text+0x894): more undefined references to `std::basic_ofstream<char, std::char_traits<char> >::open(char const*, std::_Ios_Openmode)' follow
/tmp/ccPdYa9V.o: In function `Transport_Imaging(Eigen::Matrix<std::complex<double>, -1, -1, 0, -1, -1>&, Eigen::Matrix<std::complex<double>, -1, -1, 0, -1, -1>&, Eigen::Matrix<std::complex<double>, -1, -1, 0, -1, -1>*, Eigen::Matrix<std::complex<double>, -1, -1, 0, -1, -1>*, std::complex<double>&, double&, adatom*, int&, int)':
DRMtransport.cpp:(.text+0x289c): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x28a8): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
DRMtransport.cpp:(.text+0x28b8): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x28c4): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
DRMtransport.cpp:(.text+0x28d4): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x28e6): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(double)'
DRMtransport.cpp:(.text+0x28ee): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
DRMtransport.cpp:(.text+0x28f6): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
DRMtransport.cpp:(.text+0x2948): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2954): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
DRMtransport.cpp:(.text+0x2964): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2970): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
DRMtransport.cpp:(.text+0x2980): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2992): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(double)'
DRMtransport.cpp:(.text+0x299a): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
DRMtransport.cpp:(.text+0x29a2): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
DRMtransport.cpp:(.text+0x29f4): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2a00): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
DRMtransport.cpp:(.text+0x2a10): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2a1c): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
DRMtransport.cpp:(.text+0x2a2c): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2a3e): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(double)'
DRMtransport.cpp:(.text+0x2a46): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
DRMtransport.cpp:(.text+0x2a4e): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
DRMtransport.cpp:(.text+0x2aff): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2b0b): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
DRMtransport.cpp:(.text+0x2b1b): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2b27): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
DRMtransport.cpp:(.text+0x2b37): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2b49): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(double)'
DRMtransport.cpp:(.text+0x2b51): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
DRMtransport.cpp:(.text+0x2b59): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
DRMtransport.cpp:(.text+0x2bb3): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2bbf): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
DRMtransport.cpp:(.text+0x2bcf): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2bdb): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
DRMtransport.cpp:(.text+0x2beb): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2bfd): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(double)'
DRMtransport.cpp:(.text+0x2c05): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
DRMtransport.cpp:(.text+0x2c0d): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
DRMtransport.cpp:(.text+0x2c67): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2c73): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
DRMtransport.cpp:(.text+0x2c83): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2c8f): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
DRMtransport.cpp:(.text+0x2c9f): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2cb1): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(double)'
DRMtransport.cpp:(.text+0x2cb9): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
DRMtransport.cpp:(.text+0x2cc1): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
DRMtransport.cpp:(.text+0x2e32): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2e44): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(double)'
DRMtransport.cpp:(.text+0x2e54): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2e66): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(float)'
DRMtransport.cpp:(.text+0x2e76): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2e88): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(double)'
DRMtransport.cpp:(.text+0x2e90): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
DRMtransport.cpp:(.text+0x2e98): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
DRMtransport.cpp:(.text+0x2f47): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2f59): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(double)'
DRMtransport.cpp:(.text+0x2f69): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2f7b): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(float)'
DRMtransport.cpp:(.text+0x2f8b): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x2f9d): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(double)'
DRMtransport.cpp:(.text+0x2fa5): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
DRMtransport.cpp:(.text+0x2fad): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
DRMtransport.cpp:(.text+0x3057): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x3069): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(float)'
DRMtransport.cpp:(.text+0x3079): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x308b): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(double)'
DRMtransport.cpp:(.text+0x309b): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x30ad): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(double)'
DRMtransport.cpp:(.text+0x30b5): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
DRMtransport.cpp:(.text+0x30bd): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
DRMtransport.cpp:(.text+0x316c): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x317e): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(float)'
DRMtransport.cpp:(.text+0x318e): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x31a0): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(double)'
DRMtransport.cpp:(.text+0x31b0): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x31c2): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(double)'
DRMtransport.cpp:(.text+0x31ca): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
DRMtransport.cpp:(.text+0x31d2): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
DRMtransport.cpp:(.text+0x32a9): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x32bb): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(double)'
DRMtransport.cpp:(.text+0x32cb): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x32dd): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(float)'
DRMtransport.cpp:(.text+0x32ed): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x32ff): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(double)'
DRMtransport.cpp:(.text+0x3307): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
DRMtransport.cpp:(.text+0x330f): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
DRMtransport.cpp:(.text+0x33c8): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x33da): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(double)'
DRMtransport.cpp:(.text+0x33ea): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x33fc): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(float)'
DRMtransport.cpp:(.text+0x340c): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
DRMtransport.cpp:(.text+0x341e): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(double)'
DRMtransport.cpp:(.text+0x3426): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
DRMtransport.cpp:(.text+0x342e): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
DRMtransport.cpp:(.text+0x346e): undefined reference to `std::basic_ofstream<char, std::char_traits<char> >::close()'
DRMtransport.cpp:(.text+0x347c): undefined reference to `std::basic_ofstream<char, std::char_traits<char> >::close()'
DRMtransport.cpp:(.text+0x348a): undefined reference to `std::basic_ofstream<char, std::char_traits<char> >::close()'
DRMtransport.cpp:(.text+0x349d): undefined reference to `std::basic_ofstream<char, std::char_traits<char> >::close()'
DRMtransport.cpp:(.text+0x34b0): undefined reference to `std::basic_ofstream<char, std::char_traits<char> >::close()'
/tmp/ccPdYa9V.o:DRMtransport.cpp:(.text+0x34c3): more undefined references to `std::basic_ofstream<char, std::char_traits<char> >::close()' follow
/tmp/ccPdYa9V.o: In function `__static_initialization_and_destruction_0(int, int)':
DRMtransport.cpp:(.text+0x3e19): undefined reference to `std::ios_base::Init::Init()'
DRMtransport.cpp:(.text+0x3e1e): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccPdYa9V.o:(.eh_frame+0x3df): undefined reference to `__gxx_personality_v0'
/tmp/ccOrayB7.o: In function `__static_initialization_and_destruction_0(int, int)':
DRMdatastorage.cpp:(.text+0x6f3): undefined reference to `std::ios_base::Init::Init()'
DRMdatastorage.cpp:(.text+0x6f8): undefined reference to `std::ios_base::Init::~Init()'
collect2: ld returned 1 exit status

```

---

### Post by mevun on 2012-10-12
I didn't open your zip file, but it looks like you have not specified the standard c++ library for linking.

That might happen automatically if you use "g++" instead of "gcc".  So try that substitution first.  If it still has problems, then you'll have to figure out how to specify linking with the stdc++ library.

---

### Post by Dirich on 2012-10-13
> **mevun said:**
> I didn't open your zip file, but it looks like you have not specified the standard c++ library for linking.

That might happen automatically if you use "g++" instead of "gcc".  So try that substitution first.  If it still has problems, then you'll have to figure out how to specify linking with the stdc++ library.

gcc is used for DRMmain.c since it's a C file. It calls g++ since the rest of the program I already ported to C++. But indeed, the problem was the linking of stdc++.

In particular, even with g++, I needed to add -lstdc++.

---

