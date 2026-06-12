---
title: "Configuring Eclipse to use Boost Libraries"
date: 2010-10-14
forum: Programming Talk
---

### Post by swarajban on 2010-10-14
I  am working on a C++ project where I'd like to use boost's serialization  libraries. I downloaded and installed the latest boost libraries from  boost's home page. 

When I tried to compile and run the one of boost's demo serialization examples, I got all sorts of errors that looked like this: 


```

  /usr/local/include/boost/archive/text_iarchive.hpp:140: undefined reference to `boost::archive::detail::shared_ptr_helper::shared_ptr_helper()'
./demo.o: In function `~text_iarchive':
/usr/local/include/boost/archive/text_iarchive.hpp:142: undefined reference to `boost::archive::detail::shared_ptr_helper::~shared_ptr_helper()'
/usr/local/include/boost/archive/text_iarchive.hpp:142: undefined reference to `boost::archive::detail::shared_ptr_helper::~shared_ptr_helper()'
./demo.o: In function `extended_type_info_typeid':
/usr/local/include/boost/serialization/extended_type_info_typeid.hpp:87: undefined reference to `boost::serialization::typeid_system::extended_type_info_typeid_0::extended_type_info_typeid_0(char const*)'
/usr/local/include/boost/serialization/extended_type_info_typeid.hpp:89: undefined reference to `boost::serialization::typeid_system::extended_type_info_typeid_0::type_register(std::type_info const&)'
/usr/local/include/boost/serialization/extended_type_info_typeid.hpp:90: undefined reference to `boost::serialization::extended_type_info::key_register() const'
/usr/local/include/boost/serialization/extended_type_info_typeid.hpp:90: undefined reference to `boost::serialization::typeid_system::extended_type_info_typeid_0::~extended_type_info_typeid_0()'
./demo.o: In function `~extended_type_info_typeid':
/usr/local/include/boost/serialization/extended_type_info_typeid.hpp:93: undefined reference to `boost::serialization::extended_type_info::key_unregister() const'
/usr/local/include/boost/serialization/extended_type_info_typeid.hpp:94: undefined reference to `boost::serialization::typeid_system::extended_type_info_typeid_0::type_unregister()'
/usr/local/include/boost/serialization/extended_type_info_typeid.hpp:94: undefined reference to `boost::serialization::typeid_system::extended_type_info_typeid_0::~extended_type_info_typeid_0()'
/usr/local/include/boost/serialization/extended_type_info_typeid.hpp:94: undefined reference to `boost::serialization::typeid_system::extended_type_info_typeid_0::~extended_type_info_typeid_0()'
/usr/local/include/boost/serialization/extended_type_info_typeid.hpp:93: undefined reference to `boost::serialization::extended_type_info::key_unregister() const'
/usr/local/include/boost/serialization/extended_type_info_typeid.hpp:94: undefined reference to `boost::serialization::typeid_system::extended_type_info_typeid_0::type_unregister()'
/usr/local/include/boost/serialization/extended_type_info_typeid.hpp:94: undefined reference to `boost::serialization::typeid_system::extended_type_info_typeid_0::~extended_type_info_typeid_0()'
/usr/local/include/boost/serialization/extended_type_info_typeid.hpp:94: undefined reference to `boost::serialization::typeid_system::extended_type_info_typeid_0::~extended_type_info_typeid_0()'
/usr/local/include/boost/serialization/extended_type_info_typeid.hpp:93: undefined reference to `boost::serialization::extended_type_info::key_unregister() const'
/usr/local/include/boost/serialization/extended_type_info_typeid.hpp:94: undefined reference to `boost::serialization::typeid_system::extended_type_info_typeid_0::type_unregister()'
/usr/local/include/boost/serialization/extended_type_info_typeid.hpp:94: undefined reference to `boost::serialization::typeid_system::extended_type_info_typeid_0::~extended_type_info_typeid_0()'
/usr/local/include/boost/serialization/extended_type_info_typeid.hpp:94: undefined reference to `boost::serialization::typeid_system::extended_type_info_typeid_0::~extended_type_info_typeid_0()'
```I am using Eclipse CDT in Ubuntu 10.04 for my project,  and have already tried adding 'boost_serialization' to the libraries  option in my project's gcc linker settings. What else could I be doing  wrong? 

Thanks, 
Swaraj

---

### Post by dwhitney67 on 2010-10-14
You've posted a good question that I wish I could answer.

Last weekend I upgraded my system from 9.10 to 10.04; the Boost 1.40 development package is installed, but the libraries are missing.

To confirm, I did the following:
```

sudo apt-get remove libboost-dev
sudo apt-get install libboost-dev

```
Unless things have changed, I would say that someone goofed in building the Boost package.  Then on the other hand, it could be related to the upgrade from 9.10 to 10.04.

---

### Post by spjackson on 2010-10-14
> **dwhitney67 said:**
> You've posted a good question that I wish I could answer.

Last weekend I upgraded my system from 9.10 to 10.04; the Boost 1.40 development package is installed, but the libraries are missing.

To confirm, I did the following:
```

sudo apt-get remove libboost-dev
sudo apt-get install libboost-dev

```Unless things have changed, I would say that someone goofed in building the Boost package.  Then on the other hand, it could be related to the upgrade from 9.10 to 10.04.
I think libboost1.40-all-dev gives you everything.

---

### Post by dwhitney67 on 2010-10-14
> **spjackson said:**
> I think libboost1.40-all-dev gives you everything.

Your thoughts are correct.  Thank you.

Now to attempt to help the OP...

---

### Post by dwhitney67 on 2010-10-14
> **swarajban said:**
> What else could I be doing  wrong? 


It's been awhile since I worked with Eclipse.  But from the command line, the following command works for the serialization demo I first came across in Boost 1.36 (??):
```

g++ demo_xml.cpp -lboost_serialization

```
So, it seems that you have the correct library.  Now whether you are specifying the library correctly within Eclipse is the issue, I suppose.

---

### Post by swarajban on 2010-10-14
Thanks for all the feedback, but it looks like I am still stuck. @dwhitney67, when I ran the command you specified directly from the command line, I get all the same errors so I know it's not just an Eclipse setup problem. Do you think downgrading my boost version will help fix these problems? And if so, can someone walk me through uninstalling my current boost libraries?

Thanks again

---

### Post by dwhitney67 on 2010-10-14
> **swarajban said:**
> Thanks for all the feedback, but it looks like I am still stuck. @dwhitney67, when I ran the command you specified directly from the command line, I get all the same errors so I know it's not just an Eclipse setup problem. Do you think downgrading my boost version will help fix these problems? And if so, can someone walk me through uninstalling my current boost libraries?

Thanks again

If the boost library files are installed in /usr/local/include and /usr/local/lib, it should be a breeze to uninstall.  Just use the brute-force approach if you cannot figure out how to use the Makefile that came with the Boost source code itself.

As for my system setup, I am using the 32-bit version of Ubuntu 10.04, and with spjackson's advice, I was able to install Boost 1.40.

---

### Post by swarajban on 2010-10-14
Thank you everyone for all your help. I finally got my problem solved, though my solution is fairly anti-climactic, and probably not that informative. I had tried to install the boost libraries manually, by downloading them from boost's website directly, and found that all the libraries had been installed in /usr/local/lib, and /usr/local/include/boost/ . After repeatedly running into my original errors, I decided to see if the Synaptic Package Manager could do a 'better' job of installing the boost libraries. I selected 'libboost1.40-all-dev' to install everything, but still nothing was working. Finally, I decided to start fresh so manually deleted the boost/ directory in /usr/local/include, and I deleted all the libboost files in /usr/local/lib. I then marked all the boost libraries for complete removal to remove everything. Once all the boost libraries were uninstalled, I went back to the Synaptic Package Manager, selected 'libboost1.40-all-dev' one more time. I am not sure what exactly changed when I re-installed the libraries again, but everything started to work again. I first tested from the command line, and tried to compile the demo.cpp from boost's website one more time with the following command:
```

g++ demo.cpp -lboost_serialization
```and it compiled immediately. Running the executable displayed exactly the results I was looking for. Furthermore, I moved the file back into my Eclipse project, added 'boost_serialization' to the Linker libraries, and tried to build the project. Everything worked perfectly again, as I could build the project and run the example code. I don't really have an explanation for why this fixed my problem, but to anyone else experiencing similar problems, the best advice I can give is to NOT install the boost libraries directly, but rather have the Synaptic Package Manager handle everything.

Thanks again everyone, you've been extremely helpful.

---

