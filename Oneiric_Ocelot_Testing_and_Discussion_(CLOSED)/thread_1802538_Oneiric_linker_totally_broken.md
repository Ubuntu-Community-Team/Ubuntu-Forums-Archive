---
title: "Oneiric linker totally broken"
date: 2011-07-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by genjix on 2011-07-12
My app keeps spawning loads of boost linker messages under oneiric,

```

/usr/include/boost/system/error_code.hpp:208: undefined reference to `boost::system::get_system_category()'
/usr/include/boost/system/error_code.hpp:209: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:214: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:215: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:216: undefined reference to `boost::system::get_system_category()'

```

```
g++ -lcrypto -lboost_system -lboost_thread  -o bin/tests/nettest ./obj/network.o ./obj/dialect.o ./obj/channel.o obj/serializer.o obj/logger.o obj/nettest.o obj/kernel.o obj/storage.o obj/sha256.o obj/types.o
```

That's the linker command.

Works totally fine in Natty, but not in Oneiric.


EDIT: Thanks to chriscoulson. Reorder of the arguments to put the linked libs at the end of the command and it works:
g++ obj/*.o -lboost_thread -lboost_system -lcrypto

---

### Post by Perfect Storm on 2011-07-12
Moved to Ubuntu 11.10 development forum.

---

### Post by genjix on 2011-07-12
Full output. As you can see those symbols are defined,

```
genjix|~/cb$ make net
g++ -lcrypto -lboost_thread /usr/lib/libboost_system.so.1.42.0 -o bin/tests/nettest ./obj/network.o ./obj/dialect.o ./obj/channel.o obj/serializer.o obj/logger.o obj/nettest.o obj/kernel.o obj/storage.o obj/sha256.o obj/types.o 
./obj/network.o: In function `__static_initialization_and_destruction_0':
/usr/include/boost/system/error_code.hpp:208: undefined reference to `boost::system::get_system_category()'
/usr/include/boost/system/error_code.hpp:209: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:214: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:215: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:216: undefined reference to `boost::system::get_system_category()'
./obj/network.o: In function `error_code':
/usr/include/boost/system/error_code.hpp:315: undefined reference to `boost::system::get_system_category()'
./obj/network.o: In function `boost::asio::error::get_system_category()':
/usr/include/boost/asio/error.hpp:218: undefined reference to `boost::system::get_system_category()'
./obj/network.o: In function `~posix_thread':
/usr/include/boost/asio/detail/posix_thread.hpp:69: undefined reference to `pthread_detach'
./obj/network.o: In function `boost::asio::detail::posix_thread::join()':
/usr/include/boost/asio/detail/posix_thread.hpp:77: undefined reference to `pthread_join'
./obj/network.o: In function `posix_tss_ptr':
/usr/include/boost/asio/detail/posix_tss_ptr.hpp:47: undefined reference to `pthread_key_create'
./obj/network.o: In function `~posix_tss_ptr':
/usr/include/boost/asio/detail/posix_tss_ptr.hpp:61: undefined reference to `pthread_key_delete'
./obj/network.o: In function `boost::asio::detail::posix_tss_ptr<boost::asio::detail::call_stack<boost::asio::detail::task_io_service<boost::asio::detail::epoll_reactor<false> > >::context>::operator boost::asio::detail::call_stack<boost::asio::detail::task_io_service<boost::asio::detail::epoll_reactor<false> > >::context*() const':
/usr/include/boost/asio/detail/posix_tss_ptr.hpp:67: undefined reference to `pthread_getspecific'
./obj/network.o: In function `boost::asio::detail::posix_tss_ptr<boost::asio::detail::call_stack<boost::asio::detail::task_io_service<boost::asio::detail::epoll_reactor<false> > >::context>::operator=(boost::asio::detail::call_stack<boost::asio::detail::task_io_service<boost::asio::detail::epoll_reactor<false> > >::context*)':
/usr/include/boost/asio/detail/posix_tss_ptr.hpp:73: undefined reference to `pthread_setspecific'
./obj/network.o: In function `posix_tss_ptr':
/usr/include/boost/asio/detail/posix_tss_ptr.hpp:47: undefined reference to `pthread_key_create'
./obj/network.o: In function `~posix_tss_ptr':
/usr/include/boost/asio/detail/posix_tss_ptr.hpp:61: undefined reference to `pthread_key_delete'
./obj/network.o: In function `boost::asio::detail::posix_tss_ptr<boost::asio::detail::call_stack<boost::asio::detail::strand_service::strand_impl>::context>::operator boost::asio::detail::call_stack<boost::asio::detail::strand_service::strand_impl>::context*() const':
/usr/include/boost/asio/detail/posix_tss_ptr.hpp:67: undefined reference to `pthread_getspecific'
./obj/network.o: In function `boost::asio::detail::posix_tss_ptr<boost::asio::detail::call_stack<boost::asio::detail::strand_service::strand_impl>::context>::operator=(boost::asio::detail::call_stack<boost::asio::detail::strand_service::strand_impl>::context*)':
/usr/include/boost/asio/detail/posix_tss_ptr.hpp:73: undefined reference to `pthread_setspecific'
./obj/dialect.o: In function `__static_initialization_and_destruction_0':
/usr/include/boost/system/error_code.hpp:208: undefined reference to `boost::system::get_system_category()'
/usr/include/boost/system/error_code.hpp:209: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:214: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:215: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:216: undefined reference to `boost::system::get_system_category()'
./obj/channel.o: In function `__static_initialization_and_destruction_0':
/usr/include/boost/system/error_code.hpp:208: undefined reference to `boost::system::get_system_category()'
/usr/include/boost/system/error_code.hpp:209: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:214: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:215: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:216: undefined reference to `boost::system::get_system_category()'
obj/serializer.o: In function `__static_initialization_and_destruction_0':
/usr/include/boost/system/error_code.hpp:208: undefined reference to `boost::system::get_system_category()'
/usr/include/boost/system/error_code.hpp:209: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:214: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:215: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:216: undefined reference to `boost::system::get_system_category()'
obj/nettest.o: In function `__static_initialization_and_destruction_0':
/usr/include/boost/system/error_code.hpp:208: undefined reference to `boost::system::get_system_category()'
/usr/include/boost/system/error_code.hpp:209: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:214: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:215: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:216: undefined reference to `boost::system::get_system_category()'
obj/kernel.o: In function `__static_initialization_and_destruction_0':
/usr/include/boost/system/error_code.hpp:208: undefined reference to `boost::system::get_system_category()'
/usr/include/boost/system/error_code.hpp:209: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:214: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:215: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:216: undefined reference to `boost::system::get_system_category()'
obj/storage.o: In function `__static_initialization_and_destruction_0':
/usr/include/boost/system/error_code.hpp:208: undefined reference to `boost::system::get_system_category()'
/usr/include/boost/system/error_code.hpp:209: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:214: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:215: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:216: undefined reference to `boost::system::get_system_category()'
obj/sha256.o: In function `libbitcoin::generate_sha256_hash(std::vector<unsigned char, std::allocator<unsigned char> > const&)':
/home/genjix/libbitcoin/./src/util/sha256.cpp:13: undefined reference to `SHA256_Init'
/home/genjix/libbitcoin/./src/util/sha256.cpp:14: undefined reference to `SHA256_Update'
/home/genjix/libbitcoin/./src/util/sha256.cpp:15: undefined reference to `SHA256_Final'
/home/genjix/libbitcoin/./src/util/sha256.cpp:16: undefined reference to `SHA256_Init'
/home/genjix/libbitcoin/./src/util/sha256.cpp:17: undefined reference to `SHA256_Update'
/home/genjix/libbitcoin/./src/util/sha256.cpp:18: undefined reference to `SHA256_Final'
obj/sha256.o: In function `__static_initialization_and_destruction_0':
/usr/include/boost/system/error_code.hpp:208: undefined reference to `boost::system::get_system_category()'
/usr/include/boost/system/error_code.hpp:209: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:214: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:215: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:216: undefined reference to `boost::system::get_system_category()'
obj/types.o: In function `__static_initialization_and_destruction_0':
/usr/include/boost/system/error_code.hpp:208: undefined reference to `boost::system::get_system_category()'
/usr/include/boost/system/error_code.hpp:209: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:214: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:215: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:216: undefined reference to `boost::system::get_system_category()'
collect2: ld returned 1 exit status
make: *** [bin/tests/nettest] Error 1
genjix|~/cb$ nm -D /usr/lib/libboost_system.so.1.42.0 
                 w _Jv_RegisterClasses
                 U _Unwind_Resume
0000000000001d40 W _ZN5boost6system14error_categoryD0Ev
0000000000001cc0 W _ZN5boost6system14error_categoryD1Ev
0000000000001cc0 W _ZN5boost6system14error_categoryD2Ev
0000000000001450 T _ZN5boost6system19get_system_categoryEv
00000000000014c0 T _ZN5boost6system20get_generic_categoryEv
0000000000203090 B _ZN5boost6system6throwsE
0000000000001d20 W _ZNK5boost6system14error_category10equivalentERKNS0_10error_codeEi
0000000000001ce0 W _ZNK5boost6system14error_category10equivalentEiRKNS0_15error_conditionE
0000000000001cd0 W _ZNK5boost6system14error_category23default_error_conditionEi
                 U _ZNSsC1EPKcRKSaIcE
                 U _ZNSsC1ERKSs
                 U _ZNSsD1Ev
0000000000202cd0 V _ZTIN5boost12noncopyable_11noncopyableE
0000000000202cb0 V _ZTIN5boost6system14error_categoryE
00000000000020a0 V _ZTSN5boost12noncopyable_11noncopyableE
0000000000002080 V _ZTSN5boost6system14error_categoryE
                 U _ZTVN10__cxxabiv117__class_type_infoE
                 U _ZTVN10__cxxabiv120__si_class_type_infoE
0000000000202c60 V _ZTVN5boost6system14error_categoryE
                 U _ZdlPv
0000000000203078 A __bss_start
                 U __cxa_atexit
                 w __cxa_finalize
                 U __cxa_guard_abort
                 U __cxa_guard_acquire
                 U __cxa_guard_release
                 U __cxa_pure_virtual
                 w __gmon_start__
                 U __gxx_personality_v0
                 U __stack_chk_fail
0000000000203078 A _edata
0000000000203100 A _end
0000000000001d98 T _fini
00000000000010f0 T _init
                 U strerror_r

```

---

### Post by chrisccoulson on 2011-07-12
For starters, you're calling the linker incorrectly. You need to specify libraries after objects, eg:

```
g++ -o bin/tests/nettest ./obj/network.o ./obj/dialect.o ./obj/channel.o obj/serializer.o obj/logger.o obj/nettest.o obj/kernel.o obj/storage.o obj/sha256.o obj/types.o -lcrypto -lboost_thread /usr/lib/libboost_system.so.1.42.0
```

If that doesn't work, then you'd need to post some code. It's unlikely that there is anything wrong with the linker - after all, we're using the same linker to link 10,000s of source packages already. If the linker was totally broken, we'd have known about it a long time ago ;)

---

### Post by genjix on 2011-07-12
> **chrisccoulson said:**
> For starters, you're calling the linker incorrectly. You need to specify libraries after objects, eg:

```
g++ -o bin/tests/nettest ./obj/network.o ./obj/dialect.o ./obj/channel.o obj/serializer.o obj/logger.o obj/nettest.o obj/kernel.o obj/storage.o obj/sha256.o obj/types.o -lcrypto -lboost_thread /usr/lib/libboost_system.so.1.42.0
```

If that doesn't work, then you'd need to post some code. It's unlikely that there is anything wrong with the linker - after all, we're using the same linker to link 10,000s of source packages already. If the linker was totally broken, we'd have known about it a long time ago ;)

Thanks. That's strange as I've never had to do that before :) Was working in Natty the other way.

---

### Post by chrisccoulson on 2011-07-12
> **genjix said:**
> Thanks. That's strange as I've never had to do that before :) Was working in Natty the other way.

I think it only worked by pure luck in Natty because the linker unconditionally linked all libraries specified on the command line (regardless of whether you were using any symbols from them). It has stopped working now because we pass "--as-needed" to the linker by default.

---

### Post by genjix on 2011-07-12
How about linking bitcoin
```
g++ obj/nogui/util.o obj/nogui/script.o obj/nogui/db.o obj/nogui/net.o obj/nogui/irc.o obj/nogui/keystore.o obj/nogui/main.o obj/nogui/wallet.o obj/nogui/rpc.o obj/nogui/init.o cryptopp/obj/sha.o cryptopp/obj/cpu.o  -lboost_system -lboost_filesystem -lboost_program_options -lboost_thread -ldb_cxx -lssl -lcrypto  -lgthread-2.0 -lz -ldl -lpthread  -o bitcoind
```

Get these errors:
```
obj/nogui/util.o: In function `GetDataDir(char*)':
util.cpp:(.text+0x885): undefined reference to `boost::filesystem3::path::wchar_t_codecvt_facet()'
util.cpp:(.text+0x8b3): undefined reference to `boost::filesystem3::detail::create_directory(boost::filesystem3::path const&, boost::system::error_code*)'
obj/nogui/util.o: In function `GetConfigFile()':
util.cpp:(.text+0x18f5): undefined reference to `boost::filesystem3::path::wchar_t_codecvt_facet()'
util.cpp:(.text+0x193e): undefined reference to `boost::filesystem3::path::root_directory() const'
util.cpp:(.text+0x1977): undefined reference to `boost::filesystem3::path::wchar_t_codecvt_facet()'
util.cpp:(.text+0x19c2): undefined reference to `boost::filesystem3::path::operator/=(boost::filesystem3::path const&)'
obj/nogui/util.o: In function `GetPidFile()':
util.cpp:(.text+0x1bf5): undefined reference to `boost::filesystem3::path::wchar_t_codecvt_facet()'
util.cpp:(.text+0x1c3e): undefined reference to `boost::filesystem3::path::root_directory() const'
util.cpp:(.text+0x1c77): undefined reference to `boost::filesystem3::path::wchar_t_codecvt_facet()'
util.cpp:(.text+0x1cc2): undefined reference to `boost::filesystem3::path::operator/=(boost::filesystem3::path const&)'
obj/nogui/util.o: In function `ReadConfigFile(std::map<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::less<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<std::pair<std::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >&, std::map<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::vector<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >, std::less<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<std::pair<std::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::vector<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > > > >&)':
util.cpp:(.text+0x256d): undefined reference to `boost::filesystem3::path::wchar_t_codecvt_facet()'
obj/nogui/util.o: In function `_GLOBAL__sub_I_mapArgs':
util.cpp:(.text.startup+0x42): undefined reference to `boost::system::generic_category()'
util.cpp:(.text.startup+0x50): undefined reference to `boost::system::generic_category()'
util.cpp:(.text.startup+0x5c): undefined reference to `boost::system::system_category()'

```

---

### Post by SevenMachines on 2011-07-12
Cant remember offhand but i vaguely remember something about the move from boost 1.42 to 1.46 (i think?) involving boost::filesystem defaulting from version 2 to version 3. you can change this by defining 
BOOST_FILESYSTEM_VERSION as version 2 on the command line. Best have a look at /usr/include/boost/filesytem/path.hpp and the new boost documentation.

---

