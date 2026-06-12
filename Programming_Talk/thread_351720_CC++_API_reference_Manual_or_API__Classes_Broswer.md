---
title: "C/C++ API reference Manual or API / Classes Broswer"
date: 2007-02-02
forum: Programming Talk
---

### Post by .::welemski::. on 2007-02-02
Hi,

I have a question. Does anyone know a good doc/class/api browser for c/c++ for linux?
Just like in XCode's help documentation where you just type anything then it will scan through the API reference for a related topic. Say, i'll type in a search box for a "Dictionary", then it will display lots of links for any related resulsts like "NSMutableDictionary", "NSDictionary" etc. Then if clicking to any of the result it will display the class or headers it belongs to and some functions/methods you can use with examples and complete description.

I tried the yelp but some were not there like java/c/c++. Tried KDevelop using it's builtin doc browser but still not as comprehensive as the one found in XCode.

i've download the libstdc++ doc but like I said not as comprehensive as the one found XCode.
I'm looking for a good API reference for c/c++ for me to browser and search offline just like the one found in "Java Doc" which is a very good example.

Mono has good Doc browser , KDevelop has one but you must be connected online and some documents are not as easy as one found on Java doc or in XCode. DevHelp is good but not all API or libraries which is essential for developing were not listed at all.

if you know any good Doc/API browser please post here. I'm still learning to program in linux just dont know where to get a good resources and documentations that is good for browsing offline and is very comprehensive for a newbie like me. :D.

Thanks in advance.

---

### Post by lnostdal on 2007-02-02
i do not think you'll find this .. no one has bothered with integrating all documentation .. there does not exist one unified format or way of documenting projects/apis/libraries

* linux is a separate project from gtk+
* gtk+ is a separate project from linux (it runs on other OSes for instance)
* glibc is a separate project
* java is a separate project
* postgresql is a separate project (it has a C api)
* etc.

i do not find this to be a problem at all because when i work i spend a looong stretch of my time working against or within a single api/doc .. what i mean is each module in my application only interfaces with one (or very few) projects/apis/docs at a time and i spend a lot of time within each module

if you're constantly jumping back and forth between for instance gui (gtk+) and the data-layer (some postgresql/database wrapper-thingy) of your app there is probably a design problem with your application in the first place ..   user-interface and data-access should be separated into two modules, each taking a significant stretch of time for the switch between ways of finding docs to be a problem at all

there might actually be some benefits to this also as not every way of documenting stuff might fit in a good way within one general/unified way of documenting things

---

