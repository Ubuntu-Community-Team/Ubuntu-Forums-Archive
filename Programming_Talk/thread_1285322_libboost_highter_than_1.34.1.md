---
title: "libboost highter than 1.34.1?"
date: 2009-10-07
forum: Programming Talk
---

### Post by Tom Crusher on 2009-10-07
Who know how to repair this error on Ubuntu 8.04 and how to update libboost to 1.38.0? Or what should add in repository to possiblity install boost on console with command:
[PHP]apt-get install libboost1.38-dev [/PHP]
I have this error when I tryed compile:
[PHP]luascript.o: In function `boost::filesystem::basic_directory_iterator<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >::m_init(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&)':
/usr/local/include/boost/filesystem/operations.hpp:944: undefined reference to `boost::filesystem::detail::not_found_error()'
luascript.o: In function `boost::enable_if<boost::filesystem::is_basic_path<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >, boost::filesystem::file_status>::type boost::filesystem::status<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&)':
/usr/local/include/boost/filesystem/operations.hpp:259: undefined reference to `boost::filesystem::detail::status_api(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, boost::system::error_code&)'
otserv.o: In function `interruption_checker':
/usr/local/include/boost/thread/pthread/thread_data.hpp:81: undefined reference to `boost::detail::get_current_thread_data()'
/usr/local/include/boost/thread/pthread/thread_data.hpp:81: undefined reference to `boost::detail::get_current_thread_data()'
scheduler.o: In function `interruption_checker':
/usr/local/include/boost/thread/pthread/thread_data.hpp:81: undefined reference to `boost::detail::get_current_thread_data()'
/usr/local/include/boost/thread/pthread/thread_data.hpp:81: undefined reference to `boost::detail::get_current_thread_data()'
scheduler.o: In function `~thread_data':
/usr/local/include/boost/thread/detail/thread.hpp:40: undefined reference to `boost::detail::thread_data_base::~thread_data_base()'
/usr/local/include/boost/thread/detail/thread.hpp:40: undefined reference to `boost::detail::thread_data_base::~thread_data_base()'
scheduler.o: In function `thread_data_base':
/usr/local/include/boost/thread/pthread/thread_data.hpp:54: undefined reference to `vtable for boost::detail::thread_data_base'
scheduler.o: In function `thread<boost::_bi::bind_t<void, void (*)(void*), boost::_bi::list1<boost::_bi::value<void*> > > >':
/usr/local/include/boost/thread/detail/thread.hpp:188: undefined reference to `boost::thread::start_thread()'
scheduler.o: In function `interruption_checker':
/usr/local/include/boost/thread/pthread/thread_data.hpp:81: undefined reference to `boost::detail::get_current_thread_data()'
scheduler.o:(.rodata._ZTIN5boost6detail11thread_dataINS_3_bi6bind_tIvPFvPvENS2_5list1INS2_5valueIS4_EEEEEEEE[typeinfo for boost::detail::thread_data<boost::_bi::bind_t<void, void (*)(void*), boost::_bi::list1<boost::_bi::value<void*> > > >]+0x8): undefined reference to `typeinfo for boost::detail::thread_data_base'
scriptmanager.o: In function `boost::enable_if<boost::filesystem::is_basic_path<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >, bool>::type boost::filesystem::exists<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&)':
/usr/local/include/boost/filesystem/operations.hpp:293: undefined reference to `boost::filesystem::detail::status_api(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, boost::system::error_code&)'
tasks.o: In function `interruption_checker':
/usr/local/include/boost/thread/pthread/thread_data.hpp:81: undefined reference to `boost::detail::get_current_thread_data()'
collect2: ld returned 1 exit status  [/PHP]

---

### Post by januzi on 2009-10-07
There was a topic about missing references: [http://ubuntuforums.org/showthread.php?t=825888](http://ubuntuforums.org/showthread.php?t=825888)
You could check that *filesystem*, *detail* and *thread_data_base*[COLOR=#000000][COLOR=#DD0000][/COLOR][/COLOR]

---

### Post by mmix on 2009-10-07
try 1.40.0. from source build.

> 
[color=red]Build System improvements.[/color] Updated Libraries: Accumulators, Asio, Circular Buffer, Foreach, Function, Fusion, Hash, Interprocess, Intrusive, MPL, Program.Options, Proto, Random, Serialization, Unordered, Xpressive. 

---

### Post by dwhitney67 on 2009-10-07
From the error messages, it would appear the code compiled fine.  The issue appears to be a link problem.

Since the OP has provided scant information as to how he is attempting to build his application, I think it would be best to wait to hear from the OP before speculating that a new version of boost will solve the problem.

---

