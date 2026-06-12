---
title: "GCOV: Cannot Open Graph File"
date: 2010-08-06
forum: Packaging and Compiling Programs
---

### Post by KungFuCharlie on 2010-08-06
I am having trouble using gcov on a large project. Using configure and gcc the gcno and gcda files are generated. But everytime I try to run one of the source files through gcov I get an error stating "filename.gcno:cannot open graph file". I searched around the internet and found different solutions to the problem but none of them fixed it. For example, running gcov from the same directory that I invoked the compiler from, using the -o option to specify a directory|filename, ect. 

Any thoughts as to why this thing is failing?

---

### Post by KungFuCharlie on 2010-08-06
Never mind. It was a failure with configure and not with gcov. Got it all working.

---

### Post by arun.channagiri on 2011-02-08
Hi for my project that .gcda file is not getting created,
 
following is what i get every time i run ? let me know what may be wrong ?
 
 
**developer@hbbtv-browser:~/hbbtv_new/trunk$**** gcov -o . -o ./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/*.o -o ./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/*.lo ./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/*.cpp**
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcno:version '403*', prefer '404*'
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcda:cannot open data file, assuming not executed
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcno:version '403*', prefer '404*'
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcda:cannot open data file, assuming not executed
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcno:version '403*', prefer '404*'
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcda:cannot open data file, assuming not executed
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcno:version '403*', prefer '404*'
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcda:cannot open data file, assuming not executed
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcno:version '403*', prefer '404*'
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcda:cannot open data file, assuming not executed
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcno:version '403*', prefer '404*'
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcda:cannot open data file, assuming not executed
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcno:version '403*', prefer '404*'
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcda:cannot open data file, assuming not executed
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcno:version '403*', prefer '404*'
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcda:cannot open data file, assuming not executed
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcno:version '403*', prefer '404*'
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcda:cannot open data file, assuming not executed
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcno:version '403*', prefer '404*'
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcda:cannot open data file, assuming not executed
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcno:version '403*', prefer '404*'
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcda:cannot open data file, assuming not executed
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcno:version '403*', prefer '404*'
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcda:cannot open data file, assuming not executed
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcno:version '403*', prefer '404*'
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcda:cannot open data file, assuming not executed
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcno:version '403*', prefer '404*'
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcda:cannot open data file, assuming not executed
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcno:version '403*', prefer '404*'
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcda:cannot open data file, assuming not executed
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcno:version '403*', prefer '404*'
./BUILD/PCLINUX/hbbtvjs/plugins/src/channel/nphbbtvjs_la-ChannelConfig.gcda:cannot open data file, assuming not executed
File 'src/channel/JSChannelConfig.h'
Lines executed:0.00% of 2
src/channel/JSChannelConfig.h:creating 'JSChannelConfig.h.gcov'
src/channel/JSChannelConfig.h:cannot open source file
File 'src/channel/ChannelConfig.cpp'
Lines executed:0.00% of 22
src/channel/ChannelConfig.cpp:creating 'ChannelConfig.cpp.gcov'
src/channel/ChannelConfig.cpp:cannot open source file
File 'src/channel/JSChannelList.h'
Lines executed:0.00% of 3
src/channel/JSChannelList.h:creating 'JSChannelList.h.gcov'
src/channel/JSChannelList.h:cannot open source file
File './common/PluginBase.h'
Lines executed:0.00% of 2
./common/PluginBase.h:creating 'PluginBase.h.gcov'
./common/PluginBase.h:cannot open source file

---

