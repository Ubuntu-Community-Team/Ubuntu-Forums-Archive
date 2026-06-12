---
title: "Boost C++ Library Full Of Errors"
date: 2013-07-05
forum: New to Ubuntu
---

### Post by redmask on 2013-07-05
I just installed the C++ boost library (for socket programing and such)

using this command:
sudo apt-get install libboost-all-dev

I tryed to copy all of the errors but it crashed terminal the first time.

here is what terminal could fit:
```

cleint.cpp:(.text._ZN5boost16exception_detail10clone_implINS0_19error_info_injectorINS_6system12system_errorEEEED2Ev[_ZN5boost16exception_detail10clone_implINS0_19error_info_injectorINS_6system12system_errorEEEED5Ev]+0x4f): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `boost::exception_detail::clone_impl<boost::exception_detail::error_info_injector<boost::system::system_error> >::~clone_impl()':
cleint.cpp:(.text._ZN5boost16exception_detail10clone_implINS0_19error_info_injectorINS_6system12system_errorEEEED0Ev[boost::exception_detail::clone_impl<boost::exception_detail::error_info_injector<boost::system::system_error> >::~clone_impl()]+0x26): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `boost::asio::detail::epoll_reactor::descriptor_state* boost::asio::detail::object_pool_access::create<boost::asio::detail::epoll_reactor::descriptor_state>()':
cleint.cpp:(.text._ZN5boost4asio6detail18object_pool_access6createINS1_13epoll_reactor16descriptor_stateEEEPT_v[boost::asio::detail::epoll_reactor::descriptor_state* boost::asio::detail::object_pool_access::create<boost::asio::detail::epoll_reactor::descriptor_state>()]+0x10): undefined reference to `operator new(unsigned int)'
cleint.cpp:(.text._ZN5boost4asio6detail18object_pool_access6createINS1_13epoll_reactor16descriptor_stateEEEPT_v[boost::asio::detail::epoll_reactor::descriptor_state* boost::asio::detail::object_pool_access::create<boost::asio::detail::epoll_reactor::descriptor_state>()]+0x2d): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `boost::asio::detail::posix_tss_ptr<boost::asio::detail::call_stack<boost::asio::detail::task_io_service>::context>::~posix_tss_ptr()':
cleint.cpp:(.text._ZN5boost4asio6detail13posix_tss_ptrINS1_10call_stackINS1_15task_io_serviceEE7contextEED2Ev[_ZN5boost4asio6detail13posix_tss_ptrINS1_10call_stackINS1_15task_io_serviceEE7contextEED5Ev]+0xf): undefined reference to `pthread_key_delete'
/tmp/ccOrHIg8.o: In function `boost::asio::io_service::service* boost::asio::detail::service_registry::create<boost::asio::detail::task_io_service>(boost::asio::io_service&)':
cleint.cpp:(.text._ZN5boost4asio6detail16service_registry6createINS1_15task_io_serviceEEEPNS0_10io_service7serviceERS5_[boost::asio::io_service::service* boost::asio::detail::service_registry::create<boost::asio::detail::task_io_service>(boost::asio::io_service&)]+0x10): undefined reference to `operator new(unsigned int)'
cleint.cpp:(.text._ZN5boost4asio6detail16service_registry6createINS1_15task_io_serviceEEEPNS0_10io_service7serviceERS5_[boost::asio::io_service::service* boost::asio::detail::service_registry::create<boost::asio::detail::task_io_service>(boost::asio::io_service&)]+0x34): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `void boost::checked_delete<boost::asio::io_service>(boost::asio::io_service*)':
cleint.cpp:(.text._ZN5boost14checked_deleteINS_4asio10io_serviceEEEvPT_[void boost::checked_delete<boost::asio::io_service>(boost::asio::io_service*)]+0x1a): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `void boost::checked_delete<boost::asio::io_service::work>(boost::asio::io_service::work*)':
cleint.cpp:(.text._ZN5boost14checked_deleteINS_4asio10io_service4workEEEvPT_[void boost::checked_delete<boost::asio::io_service::work>(boost::asio::io_service::work*)]+0x1a): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `void boost::checked_delete<boost::asio::detail::posix_thread>(boost::asio::detail::posix_thread*)':
cleint.cpp:(.text._ZN5boost14checked_deleteINS_4asio6detail12posix_threadEEEvPT_[void boost::checked_delete<boost::asio::detail::posix_thread>(boost::asio::detail::posix_thread*)]+0x1a): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `boost::asio::detail::posix_tss_ptr<boost::asio::detail::call_stack<boost::asio::detail::strand_service::strand_impl>::context>::~posix_tss_ptr()':
cleint.cpp:(.text._ZN5boost4asio6detail13posix_tss_ptrINS1_10call_stackINS1_14strand_service11strand_implEE7contextEED2Ev[_ZN5boost4asio6detail13posix_tss_ptrINS1_10call_stackINS1_14strand_service11strand_implEE7contextEED5Ev]+0xf): undefined reference to `pthread_key_delete'
/tmp/ccOrHIg8.o: In function `void boost::asio::detail::object_pool_access::destroy<boost::asio::detail::epoll_reactor::descriptor_state>(boost::asio::detail::epoll_reactor::descriptor_state*)':
cleint.cpp:(.text._ZN5boost4asio6detail18object_pool_access7destroyINS1_13epoll_reactor16descriptor_stateEEEvPT_[void boost::asio::detail::object_pool_access::destroy<boost::asio::detail::epoll_reactor::descriptor_state>(boost::asio::detail::epoll_reactor::descriptor_state*)]+0x1a): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `boost::asio::io_service::service* boost::asio::detail::service_registry::create<boost::asio::detail::epoll_reactor>(boost::asio::io_service&)':
cleint.cpp:(.text._ZN5boost4asio6detail16service_registry6createINS1_13epoll_reactorEEEPNS0_10io_service7serviceERS5_[boost::asio::io_service::service* boost::asio::detail::service_registry::create<boost::asio::detail::epoll_reactor>(boost::asio::io_service&)]+0x10): undefined reference to `operator new(unsigned int)'
cleint.cpp:(.text._ZN5boost4asio6detail16service_registry6createINS1_13epoll_reactorEEEPNS0_10io_service7serviceERS5_[boost::asio::io_service::service* boost::asio::detail::service_registry::create<boost::asio::detail::epoll_reactor>(boost::asio::io_service&)]+0x34): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `boost::detail::shared_count::shared_count<void*, boost::asio::detail::socket_ops::noop_deleter>(void*, boost::asio::detail::socket_ops::noop_deleter)':
cleint.cpp:(.text._ZN5boost6detail12shared_countC2IPvNS_4asio6detail10socket_ops12noop_deleterEEET_T0_[_ZN5boost6detail12shared_countC5IPvNS_4asio6detail10socket_ops12noop_deleterEEET_T0_]+0x19): undefined reference to `operator new(unsigned int)'
cleint.cpp:(.text._ZN5boost6detail12shared_countC2IPvNS_4asio6detail10socket_ops12noop_deleterEEET_T0_[_ZN5boost6detail12shared_countC5IPvNS_4asio6detail10socket_ops12noop_deleterEEET_T0_]+0x43): undefined reference to `__cxa_end_catch'
cleint.cpp:(.text._ZN5boost6detail12shared_countC2IPvNS_4asio6detail10socket_ops12noop_deleterEEET_T0_[_ZN5boost6detail12shared_countC5IPvNS_4asio6detail10socket_ops12noop_deleterEEET_T0_]+0x55): undefined reference to `__cxa_begin_catch'
cleint.cpp:(.text._ZN5boost6detail12shared_countC2IPvNS_4asio6detail10socket_ops12noop_deleterEEET_T0_[_ZN5boost6detail12shared_countC5IPvNS_4asio6detail10socket_ops12noop_deleterEEET_T0_]+0x6c): undefined reference to `__cxa_rethrow'
/tmp/ccOrHIg8.o: In function `boost::asio::detail::resolver_service<boost::asio::ip::tcp>::resolve(boost::shared_ptr<void>&, boost::asio::ip::basic_resolver_query<boost::asio::ip::tcp> const&, boost::system::error_code&)':
cleint.cpp:(.text._ZN5boost4asio6detail16resolver_serviceINS0_2ip3tcpEE7resolveERNS_10shared_ptrIvEERKNS3_20basic_resolver_queryIS4_EERNS_6system10error_codeE[boost::asio::detail::resolver_service<boost::asio::ip::tcp>::resolve(boost::shared_ptr<void>&, boost::asio::ip::basic_resolver_query<boost::asio::ip::tcp> const&, boost::system::error_code&)]+0x39): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::c_str() const'
cleint.cpp:(.text._ZN5boost4asio6detail16resolver_serviceINS0_2ip3tcpEE7resolveERNS_10shared_ptrIvEERKNS3_20basic_resolver_queryIS4_EERNS_6system10error_codeE[boost::asio::detail::resolver_service<boost::asio::ip::tcp>::resolve(boost::shared_ptr<void>&, boost::asio::ip::basic_resolver_query<boost::asio::ip::tcp> const&, boost::system::error_code&)]+0x5b): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::c_str() const'
cleint.cpp:(.text._ZN5boost4asio6detail16resolver_serviceINS0_2ip3tcpEE7resolveERNS_10shared_ptrIvEERKNS3_20basic_resolver_queryIS4_EERNS_6system10error_codeE[boost::asio::detail::resolver_service<boost::asio::ip::tcp>::resolve(boost::shared_ptr<void>&, boost::asio::ip::basic_resolver_query<boost::asio::ip::tcp> const&, boost::system::error_code&)]+0x90): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
cleint.cpp:(.text._ZN5boost4asio6detail16resolver_serviceINS0_2ip3tcpEE7resolveERNS_10shared_ptrIvEERKNS3_20basic_resolver_queryIS4_EERNS_6system10error_codeE[boost::asio::detail::resolver_service<boost::asio::ip::tcp>::resolve(boost::shared_ptr<void>&, boost::asio::ip::basic_resolver_query<boost::asio::ip::tcp> const&, boost::system::error_code&)]+0x9b): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
cleint.cpp:(.text._ZN5boost4asio6detail16resolver_serviceINS0_2ip3tcpEE7resolveERNS_10shared_ptrIvEERKNS3_20basic_resolver_queryIS4_EERNS_6system10error_codeE[boost::asio::detail::resolver_service<boost::asio::ip::tcp>::resolve(boost::shared_ptr<void>&, boost::asio::ip::basic_resolver_query<boost::asio::ip::tcp> const&, boost::system::error_code&)]+0x13b): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
cleint.cpp:(.text._ZN5boost4asio6detail16resolver_serviceINS0_2ip3tcpEE7resolveERNS_10shared_ptrIvEERKNS3_20basic_resolver_queryIS4_EERNS_6system10error_codeE[boost::asio::detail::resolver_service<boost::asio::ip::tcp>::resolve(boost::shared_ptr<void>&, boost::asio::ip::basic_resolver_query<boost::asio::ip::tcp> const&, boost::system::error_code&)]+0x14a): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
cleint.cpp:(.text._ZN5boost4asio6detail16resolver_serviceINS0_2ip3tcpEE7resolveERNS_10shared_ptrIvEERKNS3_20basic_resolver_queryIS4_EERNS_6system10error_codeE[boost::asio::detail::resolver_service<boost::asio::ip::tcp>::resolve(boost::shared_ptr<void>&, boost::asio::ip::basic_resolver_query<boost::asio::ip::tcp> const&, boost::system::error_code&)]+0x16f): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
/tmp/ccOrHIg8.o:cleint.cpp:(.text._ZN5boost4asio6detail16resolver_serviceINS0_2ip3tcpEE7resolveERNS_10shared_ptrIvEERKNS3_20basic_resolver_queryIS4_EERNS_6system10error_codeE[boost::asio::detail::resolver_service<boost::asio::ip::tcp>::resolve(boost::shared_ptr<void>&, boost::asio::ip::basic_resolver_query<boost::asio::ip::tcp> const&, boost::system::error_code&)]+0x17e): more undefined references to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()' follow
/tmp/ccOrHIg8.o: In function `boost::asio::ip::basic_resolver_query<boost::asio::ip::tcp>::host_name() const':
cleint.cpp:(.text._ZNK5boost4asio2ip20basic_resolver_queryINS1_3tcpEE9host_nameEv[boost::asio::ip::basic_resolver_query<boost::asio::ip::tcp>::host_name() const]+0x17): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
/tmp/ccOrHIg8.o: In function `boost::asio::ip::basic_resolver_query<boost::asio::ip::tcp>::service_name() const':
cleint.cpp:(.text._ZNK5boost4asio2ip20basic_resolver_queryINS1_3tcpEE12service_nameEv[boost::asio::ip::basic_resolver_query<boost::asio::ip::tcp>::service_name() const]+0x17): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
/tmp/ccOrHIg8.o: In function `boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>::~basic_resolver_entry()':
cleint.cpp:(.text._ZN5boost4asio2ip20basic_resolver_entryINS1_3tcpEED2Ev[_ZN5boost4asio2ip20basic_resolver_entryINS1_3tcpEED5Ev]+0x13): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
cleint.cpp:(.text._ZN5boost4asio2ip20basic_resolver_entryINS1_3tcpEED2Ev[_ZN5boost4asio2ip20basic_resolver_entryINS1_3tcpEED5Ev]+0x21): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
cleint.cpp:(.text._ZN5boost4asio2ip20basic_resolver_entryINS1_3tcpEED2Ev[_ZN5boost4asio2ip20basic_resolver_entryINS1_3tcpEED5Ev]+0x37): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
/tmp/ccOrHIg8.o: In function `boost::asio::ip::basic_resolver_iterator<boost::asio::ip::tcp>::create(addrinfo*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)':
cleint.cpp:(.text._ZN5boost4asio2ip23basic_resolver_iteratorINS1_3tcpEE6createEP8addrinfoRKSsS8_[boost::asio::ip::basic_resolver_iterator<boost::asio::ip::tcp>::create(addrinfo*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)]+0x69): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
cleint.cpp:(.text._ZN5boost4asio2ip23basic_resolver_iteratorINS1_3tcpEE6createEP8addrinfoRKSsS8_[boost::asio::ip::basic_resolver_iterator<boost::asio::ip::tcp>::create(addrinfo*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)]+0x91): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator=(char const*)'
cleint.cpp:(.text._ZN5boost4asio2ip23basic_resolver_iteratorINS1_3tcpEE6createEP8addrinfoRKSsS8_[boost::asio::ip::basic_resolver_iterator<boost::asio::ip::tcp>::create(addrinfo*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)]+0x9d): undefined reference to `operator new(unsigned int)'
cleint.cpp:(.text._ZN5boost4asio2ip23basic_resolver_iteratorINS1_3tcpEE6createEP8addrinfoRKSsS8_[boost::asio::ip::basic_resolver_iterator<boost::asio::ip::tcp>::create(addrinfo*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)]+0x1c0): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
cleint.cpp:(.text._ZN5boost4asio2ip23basic_resolver_iteratorINS1_3tcpEE6createEP8addrinfoRKSsS8_[boost::asio::ip::basic_resolver_iterator<boost::asio::ip::tcp>::create(addrinfo*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)]+0x1cc): undefined reference to `operator delete(void*)'
cleint.cpp:(.text._ZN5boost4asio2ip23basic_resolver_iteratorINS1_3tcpEE6createEP8addrinfoRKSsS8_[boost::asio::ip::basic_resolver_iterator<boost::asio::ip::tcp>::create(addrinfo*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)]+0x1f2): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
/tmp/ccOrHIg8.o: In function `boost::asio::io_service::service* boost::asio::detail::service_registry::create<boost::asio::ip::resolver_service<boost::asio::ip::tcp> >(boost::asio::io_service&)':
cleint.cpp:(.text._ZN5boost4asio6detail16service_registry6createINS0_2ip16resolver_serviceINS4_3tcpEEEEEPNS0_10io_service7serviceERS8_[boost::asio::io_service::service* boost::asio::detail::service_registry::create<boost::asio::ip::resolver_service<boost::asio::ip::tcp> >(boost::asio::io_service&)]+0x10): undefined reference to `operator new(unsigned int)'
cleint.cpp:(.text._ZN5boost4asio6detail16service_registry6createINS0_2ip16resolver_serviceINS4_3tcpEEEEEPNS0_10io_service7serviceERS8_[boost::asio::io_service::service* boost::asio::detail::service_registry::create<boost::asio::ip::resolver_service<boost::asio::ip::tcp> >(boost::asio::io_service&)]+0x34): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>::basic_resolver_entry(boost::asio::ip::basic_endpoint<boost::asio::ip::tcp> const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)':
cleint.cpp:(.text._ZN5boost4asio2ip20basic_resolver_entryINS1_3tcpEEC2ERKNS1_14basic_endpointIS3_EERKSsSA_[_ZN5boost4asio2ip20basic_resolver_entryINS1_3tcpEEC5ERKNS1_14basic_endpointIS3_EERKSsSA_]+0x2d): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
cleint.cpp:(.text._ZN5boost4asio2ip20basic_resolver_entryINS1_3tcpEEC2ERKNS1_14basic_endpointIS3_EERKSsSA_[_ZN5boost4asio2ip20basic_resolver_entryINS1_3tcpEEC5ERKNS1_14basic_endpointIS3_EERKSsSA_]+0x45): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
cleint.cpp:(.text._ZN5boost4asio2ip20basic_resolver_entryINS1_3tcpEEC2ERKNS1_14basic_endpointIS3_EERKSsSA_[_ZN5boost4asio2ip20basic_resolver_entryINS1_3tcpEEC5ERKNS1_14basic_endpointIS3_EERKSsSA_]+0x57): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
/tmp/ccOrHIg8.o: In function `boost::asio::detail::service_base<boost::asio::ip::resolver_service<boost::asio::ip::tcp> >::~service_base()':
cleint.cpp:(.text._ZN5boost4asio6detail12service_baseINS0_2ip16resolver_serviceINS3_3tcpEEEED2Ev[_ZN5boost4asio6detail12service_baseINS0_2ip16resolver_serviceINS3_3tcpEEEED5Ev]+0x2d): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `boost::asio::detail::service_base<boost::asio::ip::resolver_service<boost::asio::ip::tcp> >::~service_base()':
cleint.cpp:(.text._ZN5boost4asio6detail12service_baseINS0_2ip16resolver_serviceINS3_3tcpEEEED0Ev[_ZN5boost4asio6detail12service_baseINS0_2ip16resolver_serviceINS3_3tcpEEEED5Ev]+0x18): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>::basic_resolver_entry(boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> const&)':
cleint.cpp:(.text._ZN5boost4asio2ip20basic_resolver_entryINS1_3tcpEEC2ERKS4_[_ZN5boost4asio2ip20basic_resolver_entryINS1_3tcpEEC5ERKS4_]+0x30): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
cleint.cpp:(.text._ZN5boost4asio2ip20basic_resolver_entryINS1_3tcpEEC2ERKS4_[_ZN5boost4asio2ip20basic_resolver_entryINS1_3tcpEEC5ERKS4_]+0x4d): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
cleint.cpp:(.text._ZN5boost4asio2ip20basic_resolver_entryINS1_3tcpEEC2ERKS4_[_ZN5boost4asio2ip20basic_resolver_entryINS1_3tcpEEC5ERKS4_]+0x5f): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
/tmp/ccOrHIg8.o: In function `std::vector<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>, std::allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> > >::_M_insert_aux(__gnu_cxx::__normal_iterator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*, std::vector<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>, std::allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> > > >, boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> const&)':
cleint.cpp:(.text._ZNSt6vectorIN5boost4asio2ip20basic_resolver_entryINS2_3tcpEEESaIS5_EE13_M_insert_auxEN9__gnu_cxx17__normal_iteratorIPS5_S7_EERKS5_[std::vector<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>, std::allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> > >::_M_insert_aux(__gnu_cxx::__normal_iterator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*, std::vector<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>, std::allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> > > >, boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> const&)]+0x333): undefined reference to `__cxa_end_catch'
cleint.cpp:(.text._ZNSt6vectorIN5boost4asio2ip20basic_resolver_entryINS2_3tcpEEESaIS5_EE13_M_insert_auxEN9__gnu_cxx17__normal_iteratorIPS5_S7_EERKS5_[std::vector<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>, std::allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> > >::_M_insert_aux(__gnu_cxx::__normal_iterator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*, std::vector<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>, std::allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> > > >, boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> const&)]+0x345): undefined reference to `__cxa_begin_catch'
cleint.cpp:(.text._ZNSt6vectorIN5boost4asio2ip20basic_resolver_entryINS2_3tcpEEESaIS5_EE13_M_insert_auxEN9__gnu_cxx17__normal_iteratorIPS5_S7_EERKS5_[std::vector<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>, std::allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> > >::_M_insert_aux(__gnu_cxx::__normal_iterator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*, std::vector<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>, std::allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> > > >, boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> const&)]+0x3cb): undefined reference to `__cxa_rethrow'
/tmp/ccOrHIg8.o: In function `boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>::operator=(boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> const&)':
cleint.cpp:(.text._ZN5boost4asio2ip20basic_resolver_entryINS1_3tcpEEaSERKS4_[boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>::operator=(boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> const&)]+0x2f): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator=(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
cleint.cpp:(.text._ZN5boost4asio2ip20basic_resolver_entryINS1_3tcpEEaSERKS4_[boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>::operator=(boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> const&)]+0x4c): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator=(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
/tmp/ccOrHIg8.o: In function `boost::asio::io_service::service* boost::asio::detail::service_registry::create<boost::asio::stream_socket_service<boost::asio::ip::tcp> >(boost::asio::io_service&)':
cleint.cpp:(.text._ZN5boost4asio6detail16service_registry6createINS0_21stream_socket_serviceINS0_2ip3tcpEEEEEPNS0_10io_service7serviceERS8_[boost::asio::io_service::service* boost::asio::detail::service_registry::create<boost::asio::stream_socket_service<boost::asio::ip::tcp> >(boost::asio::io_service&)]+0x10): undefined reference to `operator new(unsigned int)'
cleint.cpp:(.text._ZN5boost4asio6detail16service_registry6createINS0_21stream_socket_serviceINS0_2ip3tcpEEEEEPNS0_10io_service7serviceERS8_[boost::asio::io_service::service* boost::asio::detail::service_registry::create<boost::asio::stream_socket_service<boost::asio::ip::tcp> >(boost::asio::io_service&)]+0x34): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `boost::detail::shared_count::shared_count<std::vector<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>, std::allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> > > >(std::vector<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>, std::allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> > >*)':
cleint.cpp:(.text._ZN5boost6detail12shared_countC2ISt6vectorINS_4asio2ip20basic_resolver_entryINS5_3tcpEEESaIS8_EEEEPT_[_ZN5boost6detail12shared_countC5ISt6vectorINS_4asio2ip20basic_resolver_entryINS5_3tcpEEESaIS8_EEEEPT_]+0x18): undefined reference to `operator new(unsigned int)'
cleint.cpp:(.text._ZN5boost6detail12shared_countC2ISt6vectorINS_4asio2ip20basic_resolver_entryINS5_3tcpEEESaIS8_EEEEPT_[_ZN5boost6detail12shared_countC5ISt6vectorINS_4asio2ip20basic_resolver_entryINS5_3tcpEEESaIS8_EEEEPT_]+0x3b): undefined reference to `__cxa_end_catch'
cleint.cpp:(.text._ZN5boost6detail12shared_countC2ISt6vectorINS_4asio2ip20basic_resolver_entryINS5_3tcpEEESaIS8_EEEEPT_[_ZN5boost6detail12shared_countC5ISt6vectorINS_4asio2ip20basic_resolver_entryINS5_3tcpEEESaIS8_EEEEPT_]+0x4d): undefined reference to `__cxa_begin_catch'
cleint.cpp:(.text._ZN5boost6detail12shared_countC2ISt6vectorINS_4asio2ip20basic_resolver_entryINS5_3tcpEEESaIS8_EEEEPT_[_ZN5boost6detail12shared_countC5ISt6vectorINS_4asio2ip20basic_resolver_entryINS5_3tcpEEESaIS8_EEEEPT_]+0x5d): undefined reference to `__cxa_rethrow'
/tmp/ccOrHIg8.o: In function `std::vector<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>, std::allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> > >::_M_check_len(unsigned int, char const*) const':
cleint.cpp:(.text._ZNKSt6vectorIN5boost4asio2ip20basic_resolver_entryINS2_3tcpEEESaIS5_EE12_M_check_lenEjPKc[std::vector<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>, std::allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> > >::_M_check_len(unsigned int, char const*) const]+0x36): undefined reference to `std::__throw_length_error(char const*)'
/tmp/ccOrHIg8.o: In function `boost::asio::detail::service_base<boost::asio::stream_socket_service<boost::asio::ip::tcp> >::~service_base()':
cleint.cpp:(.text._ZN5boost4asio6detail12service_baseINS0_21stream_socket_serviceINS0_2ip3tcpEEEED2Ev[_ZN5boost4asio6detail12service_baseINS0_21stream_socket_serviceINS0_2ip3tcpEEEED5Ev]+0x2d): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `boost::asio::detail::service_base<boost::asio::stream_socket_service<boost::asio::ip::tcp> >::~service_base()':
cleint.cpp:(.text._ZN5boost4asio6detail12service_baseINS0_21stream_socket_serviceINS0_2ip3tcpEEEED0Ev[_ZN5boost4asio6detail12service_baseINS0_21stream_socket_serviceINS0_2ip3tcpEEEED5Ev]+0x18): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `__gnu_cxx::new_allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> >::deallocate(boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*, unsigned int)':
cleint.cpp:(.text._ZN9__gnu_cxx13new_allocatorIN5boost4asio2ip20basic_resolver_entryINS3_3tcpEEEE10deallocateEPS6_j[__gnu_cxx::new_allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> >::deallocate(boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*, unsigned int)]+0xd): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `void boost::checked_delete<std::vector<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>, std::allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> > > >(std::vector<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>, std::allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> > >*)':
cleint.cpp:(.text._ZN5boost14checked_deleteISt6vectorINS_4asio2ip20basic_resolver_entryINS3_3tcpEEESaIS6_EEEEvPT_[void boost::checked_delete<std::vector<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>, std::allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> > > >(std::vector<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>, std::allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> > >*)]+0x1a): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `__gnu_cxx::new_allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> >::allocate(unsigned int, void const*)':
cleint.cpp:(.text._ZN9__gnu_cxx13new_allocatorIN5boost4asio2ip20basic_resolver_entryINS3_3tcpEEEE8allocateEjPKv[__gnu_cxx::new_allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> >::allocate(unsigned int, void const*)]+0x1c): undefined reference to `std::__throw_bad_alloc()'
cleint.cpp:(.text._ZN9__gnu_cxx13new_allocatorIN5boost4asio2ip20basic_resolver_entryINS3_3tcpEEEE8allocateEjPKv[__gnu_cxx::new_allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> >::allocate(unsigned int, void const*)]+0x31): undefined reference to `operator new(unsigned int)'
/tmp/ccOrHIg8.o: In function `boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>* std::__uninitialized_copy<false>::__uninit_copy<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*, boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*>(boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*, boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*, boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*)':
cleint.cpp:(.text._ZNSt20__uninitialized_copyILb0EE13__uninit_copyIPN5boost4asio2ip20basic_resolver_entryINS4_3tcpEEES8_EET0_T_SA_S9_[boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>* std::__uninitialized_copy<false>::__uninit_copy<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*, boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*>(boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*, boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*, boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*)]+0x50): undefined reference to `__cxa_end_catch'
cleint.cpp:(.text._ZNSt20__uninitialized_copyILb0EE13__uninit_copyIPN5boost4asio2ip20basic_resolver_entryINS4_3tcpEEES8_EET0_T_SA_S9_[boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>* std::__uninitialized_copy<false>::__uninit_copy<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*, boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*>(boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*, boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*, boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*)]+0x62): undefined reference to `__cxa_begin_catch'
cleint.cpp:(.text._ZNSt20__uninitialized_copyILb0EE13__uninit_copyIPN5boost4asio2ip20basic_resolver_entryINS4_3tcpEEES8_EET0_T_SA_S9_[boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>* std::__uninitialized_copy<false>::__uninit_copy<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*, boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*>(boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*, boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*, boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>*)]+0x79): undefined reference to `__cxa_rethrow'
/tmp/ccOrHIg8.o: In function `boost::detail::sp_counted_impl_p<std::vector<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>, std::allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> > > >::~sp_counted_impl_p()':
cleint.cpp:(.text._ZN5boost6detail17sp_counted_impl_pISt6vectorINS_4asio2ip20basic_resolver_entryINS4_3tcpEEESaIS7_EEED2Ev[_ZN5boost6detail17sp_counted_impl_pISt6vectorINS_4asio2ip20basic_resolver_entryINS4_3tcpEEESaIS7_EEED5Ev]+0x2d): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `boost::detail::sp_counted_impl_p<std::vector<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>, std::allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> > > >::~sp_counted_impl_p()':
cleint.cpp:(.text._ZN5boost6detail17sp_counted_impl_pISt6vectorINS_4asio2ip20basic_resolver_entryINS4_3tcpEEESaIS7_EEED0Ev[_ZN5boost6detail17sp_counted_impl_pISt6vectorINS_4asio2ip20basic_resolver_entryINS4_3tcpEEESaIS7_EEED5Ev]+0x18): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `boost::detail::sp_counted_impl_pd<void*, boost::asio::detail::socket_ops::noop_deleter>::~sp_counted_impl_pd()':
cleint.cpp:(.text._ZN5boost6detail18sp_counted_impl_pdIPvNS_4asio6detail10socket_ops12noop_deleterEED2Ev[_ZN5boost6detail18sp_counted_impl_pdIPvNS_4asio6detail10socket_ops12noop_deleterEED5Ev]+0x2d): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `boost::detail::sp_counted_impl_pd<void*, boost::asio::detail::socket_ops::noop_deleter>::~sp_counted_impl_pd()':
cleint.cpp:(.text._ZN5boost6detail18sp_counted_impl_pdIPvNS_4asio6detail10socket_ops12noop_deleterEED0Ev[_ZN5boost6detail18sp_counted_impl_pdIPvNS_4asio6detail10socket_ops12noop_deleterEED5Ev]+0x18): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `boost::asio::stream_socket_service<boost::asio::ip::tcp>::~stream_socket_service()':
cleint.cpp:(.text._ZN5boost4asio21stream_socket_serviceINS0_2ip3tcpEED2Ev[_ZN5boost4asio21stream_socket_serviceINS0_2ip3tcpEED5Ev]+0x2d): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o:cleint.cpp:(.text._ZN5boost4asio21stream_socket_serviceINS0_2ip3tcpEED0Ev[_ZN5boost4asio21stream_socket_serviceINS0_2ip3tcpEED5Ev]+0x18): more undefined references to `operator delete(void*)' follow
/tmp/ccOrHIg8.o:(.rodata._ZTVN5boost4asio6detail12service_baseINS0_21stream_socket_serviceINS0_2ip3tcpEEEEE[vtable for boost::asio::detail::service_base<boost::asio::stream_socket_service<boost::asio::ip::tcp> >]+0x10): undefined reference to `__cxa_pure_virtual'
/tmp/ccOrHIg8.o: In function `boost::asio::ip::resolver_service<boost::asio::ip::tcp>::~resolver_service()':
cleint.cpp:(.text._ZN5boost4asio2ip16resolver_serviceINS1_3tcpEED2Ev[_ZN5boost4asio2ip16resolver_serviceINS1_3tcpEED5Ev]+0x3c): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `boost::asio::ip::resolver_service<boost::asio::ip::tcp>::~resolver_service()':
cleint.cpp:(.text._ZN5boost4asio2ip16resolver_serviceINS1_3tcpEED0Ev[_ZN5boost4asio2ip16resolver_serviceINS1_3tcpEED5Ev]+0x18): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o:(.rodata._ZTVN5boost4asio6detail12service_baseINS0_2ip16resolver_serviceINS3_3tcpEEEEE[vtable for boost::asio::detail::service_base<boost::asio::ip::resolver_service<boost::asio::ip::tcp> >]+0x10): undefined reference to `__cxa_pure_virtual'
/tmp/ccOrHIg8.o:(.rodata._ZTVN5boost6detail15sp_counted_baseE[vtable for boost::detail::sp_counted_base]+0x10): undefined reference to `__cxa_pure_virtual'
/tmp/ccOrHIg8.o:(.rodata._ZTVN5boost6detail15sp_counted_baseE[vtable for boost::detail::sp_counted_base]+0x18): undefined reference to `__cxa_pure_virtual'
/tmp/ccOrHIg8.o:(.rodata._ZTVN5boost4asio6detail12service_baseINS1_13epoll_reactorEEE[vtable for boost::asio::detail::service_base<boost::asio::detail::epoll_reactor>]+0x10): undefined reference to `__cxa_pure_virtual'
/tmp/ccOrHIg8.o: In function `boost::asio::detail::task_io_service::~task_io_service()':
cleint.cpp:(.text._ZN5boost4asio6detail15task_io_serviceD2Ev[_ZN5boost4asio6detail15task_io_serviceD5Ev]+0x58): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `boost::asio::detail::task_io_service::~task_io_service()':
cleint.cpp:(.text._ZN5boost4asio6detail15task_io_serviceD0Ev[_ZN5boost4asio6detail15task_io_serviceD5Ev]+0x18): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o:(.rodata._ZTVN5boost4asio6detail12service_baseINS1_15task_io_serviceEEE[vtable for boost::asio::detail::service_base<boost::asio::detail::task_io_service>]+0x10): undefined reference to `__cxa_pure_virtual'
/tmp/ccOrHIg8.o:(.rodata._ZTVN5boost16exception_detail10clone_baseE[vtable for boost::exception_detail::clone_base]+0x8): undefined reference to `__cxa_pure_virtual'
/tmp/ccOrHIg8.o:(.rodata._ZTVN5boost16exception_detail10clone_baseE[vtable for boost::exception_detail::clone_base]+0xc): undefined reference to `__cxa_pure_virtual'
/tmp/ccOrHIg8.o:(.rodata._ZTVN5boost9exceptionE[vtable for boost::exception]+0x8): undefined reference to `__cxa_pure_virtual'
/tmp/ccOrHIg8.o:(.rodata._ZTVN5boost9exceptionE[vtable for boost::exception]+0xc): undefined reference to `__cxa_pure_virtual'
/tmp/ccOrHIg8.o:(.rodata._ZTVN5boost4asio10io_service7serviceE[vtable for boost::asio::io_service::service]+0x10): more undefined references to `__cxa_pure_virtual' follow
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost6detail17sp_counted_impl_pISt6vectorINS_4asio2ip20basic_resolver_entryINS4_3tcpEEESaIS7_EEEE[typeinfo for boost::detail::sp_counted_impl_p<std::vector<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp>, std::allocator<boost::asio::ip::basic_resolver_entry<boost::asio::ip::tcp> > > >]+0x0): undefined reference to `vtable for __cxxabiv1::__si_class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost4asio6detail14typeid_wrapperINS0_21stream_socket_serviceINS0_2ip3tcpEEEEE[typeinfo for boost::asio::detail::typeid_wrapper<boost::asio::stream_socket_service<boost::asio::ip::tcp> >]+0x0): undefined reference to `vtable for __cxxabiv1::__class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost4asio6detail14typeid_wrapperINS0_2ip16resolver_serviceINS3_3tcpEEEEE[typeinfo for boost::asio::detail::typeid_wrapper<boost::asio::ip::resolver_service<boost::asio::ip::tcp> >]+0x0): undefined reference to `vtable for __cxxabiv1::__class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost6detail18sp_counted_impl_pdIPvNS_4asio6detail10socket_ops12noop_deleterEEE[typeinfo for boost::detail::sp_counted_impl_pd<void*, boost::asio::detail::socket_ops::noop_deleter>]+0x0): undefined reference to `vtable for __cxxabiv1::__si_class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost4asio6detail14typeid_wrapperINS1_13epoll_reactorEEE[typeinfo for boost::asio::detail::typeid_wrapper<boost::asio::detail::epoll_reactor>]+0x0): undefined reference to `vtable for __cxxabiv1::__class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost4asio6detail14typeid_wrapperINS1_15task_io_serviceEEE[typeinfo for boost::asio::detail::typeid_wrapper<boost::asio::detail::task_io_service>]+0x0): undefined reference to `vtable for __cxxabiv1::__class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost16exception_detail10clone_implINS0_19error_info_injectorINS_6system12system_errorEEEEE[typeinfo for boost::exception_detail::clone_impl<boost::exception_detail::error_info_injector<boost::system::system_error> >]+0x0): undefined reference to `vtable for __cxxabiv1::__vmi_class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost16exception_detail19error_info_injectorINS_6system12system_errorEEE[typeinfo for boost::exception_detail::error_info_injector<boost::system::system_error>]+0x0): undefined reference to `vtable for __cxxabiv1::__vmi_class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost4asio21stream_socket_serviceINS0_2ip3tcpEEE[typeinfo for boost::asio::stream_socket_service<boost::asio::ip::tcp>]+0x0): undefined reference to `vtable for __cxxabiv1::__si_class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost4asio6detail12service_baseINS0_21stream_socket_serviceINS0_2ip3tcpEEEEE[typeinfo for boost::asio::detail::service_base<boost::asio::stream_socket_service<boost::asio::ip::tcp> >]+0x0): undefined reference to `vtable for __cxxabiv1::__si_class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost4asio2ip16resolver_serviceINS1_3tcpEEE[typeinfo for boost::asio::ip::resolver_service<boost::asio::ip::tcp>]+0x0): undefined reference to `vtable for __cxxabiv1::__si_class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost4asio6detail12service_baseINS0_2ip16resolver_serviceINS3_3tcpEEEEE[typeinfo for boost::asio::detail::service_base<boost::asio::ip::resolver_service<boost::asio::ip::tcp> >]+0x0): undefined reference to `vtable for __cxxabiv1::__si_class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost6detail15sp_counted_baseE[typeinfo for boost::detail::sp_counted_base]+0x0): undefined reference to `vtable for __cxxabiv1::__class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost4asio6detail13epoll_reactorE[typeinfo for boost::asio::detail::epoll_reactor]+0x0): undefined reference to `vtable for __cxxabiv1::__si_class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost4asio6detail12service_baseINS1_13epoll_reactorEEE[typeinfo for boost::asio::detail::service_base<boost::asio::detail::epoll_reactor>]+0x0): undefined reference to `vtable for __cxxabiv1::__si_class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost4asio6detail15task_io_serviceE[typeinfo for boost::asio::detail::task_io_service]+0x0): undefined reference to `vtable for __cxxabiv1::__si_class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost4asio6detail12service_baseINS1_15task_io_serviceEEE[typeinfo for boost::asio::detail::service_base<boost::asio::detail::task_io_service>]+0x0): undefined reference to `vtable for __cxxabiv1::__si_class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost4asio5error6detail12ssl_categoryE[typeinfo for boost::asio::error::detail::ssl_category]+0x0): undefined reference to `vtable for __cxxabiv1::__si_class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost4asio5error6detail13misc_categoryE[typeinfo for boost::asio::error::detail::misc_category]+0x0): more undefined references to `vtable for __cxxabiv1::__si_class_type_info' follow
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost6system12system_errorE[typeinfo for boost::system::system_error]+0x8): undefined reference to `typeinfo for std::runtime_error'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost16exception_detail10clone_baseE[typeinfo for boost::exception_detail::clone_base]+0x0): undefined reference to `vtable for __cxxabiv1::__class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost9exceptionE[typeinfo for boost::exception]+0x0): undefined reference to `vtable for __cxxabiv1::__class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost4asio10io_service7serviceE[typeinfo for boost::asio::io_service::service]+0x0): undefined reference to `vtable for __cxxabiv1::__vmi_class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost6system14error_categoryE[typeinfo for boost::system::error_category]+0x0): undefined reference to `vtable for __cxxabiv1::__si_class_type_info'
/tmp/ccOrHIg8.o: In function `boost::exception_detail::clone_impl<boost::exception_detail::error_info_injector<boost::system::system_error> >::clone() const':
cleint.cpp:(.text._ZNK5boost16exception_detail10clone_implINS0_19error_info_injectorINS_6system12system_errorEEEE5cloneEv[boost::exception_detail::clone_impl<boost::exception_detail::error_info_injector<boost::system::system_error> >::clone() const]+0x18): undefined reference to `operator new(unsigned int)'
cleint.cpp:(.text._ZNK5boost16exception_detail10clone_implINS0_19error_info_injectorINS_6system12system_errorEEEE5cloneEv[boost::exception_detail::clone_impl<boost::exception_detail::error_info_injector<boost::system::system_error> >::clone() const]+0x4a): undefined reference to `operator delete(void*)'
/tmp/ccOrHIg8.o: In function `boost::exception_detail::clone_impl<boost::exception_detail::error_info_injector<boost::system::system_error> >::rethrow() const':
cleint.cpp:(.text._ZNK5boost16exception_detail10clone_implINS0_19error_info_injectorINS_6system12system_errorEEEE7rethrowEv[boost::exception_detail::clone_impl<boost::exception_detail::error_info_injector<boost::system::system_error> >::rethrow() const]+0x18): undefined reference to `__cxa_allocate_exception'
cleint.cpp:(.text._ZNK5boost16exception_detail10clone_implINS0_19error_info_injectorINS_6system12system_errorEEEE7rethrowEv[boost::exception_detail::clone_impl<boost::exception_detail::error_info_injector<boost::system::system_error> >::rethrow() const]+0x42): undefined reference to `__cxa_throw'
cleint.cpp:(.text._ZNK5boost16exception_detail10clone_implINS0_19error_info_injectorINS_6system12system_errorEEEE7rethrowEv[boost::exception_detail::clone_impl<boost::exception_detail::error_info_injector<boost::system::system_error> >::rethrow() const]+0x4c): undefined reference to `__cxa_free_exception'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost4asio6detail10socket_ops12noop_deleterE[typeinfo for boost::asio::detail::socket_ops::noop_deleter]+0x0): undefined reference to `vtable for __cxxabiv1::__class_type_info'
/tmp/ccOrHIg8.o:(.rodata._ZTIN5boost12noncopyable_11noncopyableE[typeinfo for boost::noncopyable_::noncopyable]+0x0): undefined reference to `vtable for __cxxabiv1::__class_type_info'
/tmp/ccOrHIg8.o:(.eh_frame+0x40f): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```

for the record here is my C++ code (a test):
```

#include <cstdlib>
#include <cstring>
#include <iostream>
#include <boost/asio.hpp>

using boost::asio::ip::tcp;

enum { max_length = 1024 };

int main(int argc, char* argv[])
{
  try
  {
    if (argc != 3)
    {
      std::cerr << "Usage: blocking_tcp_echo_client <host> <port>\n";
      return 1;
    }

    boost::asio::io_service io_service;

    tcp::resolver resolver(io_service);
    tcp::resolver::query query(tcp::v4(), argv[1], argv[2]);
    tcp::resolver::iterator iterator = resolver.resolve(query);

    tcp::socket s(io_service);
    s.connect(*iterator);

    using namespace std; // For strlen.
    std::cout << "Enter message: ";
    char request[max_length];
    std::cin.getline(request, max_length);
    size_t request_length = strlen(request);
    boost::asio::write(s, boost::asio::buffer(request, request_length));

    char reply[max_length];
    size_t reply_length = boost::asio::read(s,
        boost::asio::buffer(reply, request_length));
    std::cout << "Reply is: ";
    std::cout.write(reply, reply_length);
    std::cout << "\n";
  }
  catch (std::exception& e)
  {
    std::cerr << "Exception: " << e.what() << "\n";
  }

  return 0;
}


```

What the heck happened?

---

