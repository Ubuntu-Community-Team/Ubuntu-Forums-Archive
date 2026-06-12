---
title: "BOOST libraries compilation issues"
date: 2010-03-15
forum: Programming Talk
---

### Post by adambaldwin on 2010-03-15
I have successfully compiled and liked BOOST to my c++ program, however, I am trying to use the transcendental functions in the libraries.  I have not been able to compile the test program transc.cpp that tests these functions.  I have included the mpfr and gmp libraries, and my compile command is 

g++ -Wall -lgmp -lmpfr -g -o Test transc.cpp

I am not sure what is happening; I have a test program that compiles and runs for polynomial functions, but when I call y = sin(x) in the program the compiler tells me the following error:

/usr/include/boost/numeric/interval/transc.hpp: In function 'boost::numeric::interval<T, Policies> boost::numeric::cos(const boost::numeric::interval<T, Policies>&) [with T = double, Policies = boost::numeric::interval_lib::policies<boost::numeric::interval_lib::detail::save_state_unprotected<boost::numeric::interval_lib::rounded_arith_opp<double, boost::numeric::interval_lib::rounding_control<double> > >, boost::numeric::interval_lib::checking_strict<double> >]':
/usr/include/boost/numeric/interval/transc.hpp:88:   instantiated from 'boost::numeric::interval<T, Policies> boost::numeric::sin(const boost::numeric::interval<T, Policies>&) [with T = double, Policies = boost::numeric::interval_lib::policies<boost::numeric::interval_lib::rounded_math<double>, boost::numeric::interval_lib::checking_strict<double> >]'
Asai_n_dim_with_corrections.cpp:1142:   instantiated from here
/usr/include/boost/numeric/interval/transc.hpp:73: error: 'struct boost::numeric::interval_lib::detail::save_state_unprotected<boost::numeric::interval_lib::rounded_arith_opp<double, boost::numeric::interval_lib::rounding_control<double> > >' has no member named 'cos_down'
/usr/include/boost/numeric/interval/transc.hpp:73: error: 'struct boost::numeric::interval_lib::detail::save_state_unprotected<boost::numeric::interval_lib::rounded_arith_opp<double, boost::numeric::interval_lib::rounding_control<double> > >' has no member named 'cos_up'
/usr/include/boost/numeric/interval/transc.hpp:75: error: 'struct boost::numeric::interval_lib::detail::save_state_unprotected<boost::numeric::interval_lib::rounded_arith_opp<double, boost::numeric::interval_lib::rounding_control<double> > >' has no member named 'cos_up'

---

