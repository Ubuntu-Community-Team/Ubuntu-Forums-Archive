---
title: "GCC program not compiling, incomplete pathway fatal error file/directory not found"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by rlwoltz on 2012-09-19
ok, I'm new to this forum and wasn't sure where to put this but here it goes. I have attempted to download a program that will help me with protein modeling. I was able to build successfully and now I'm trying to run the program from the terminal. I am currently in directory 
source/bin/  

I run my file with the correct options and get this error 
ore.scoring.ScoreFunctionFactory: SCOREFUNCTION PATCH: score12
protocols.jobdist.JobDistributors: Looking for an available job: 1 1  1

ERROR: [ERROR] invalid header input for kill_hairpins file. 
ERROR:: Exit from: src/core/scoring/SS_Killhairpins_Info.cc line: 375
I looked at the SS_Killhairpins_Info.cc and I am now in directory 
source/src/core/scoring/ 
line 375 is a header counter and the forum that assists with this program said to make sure the header file was there. It was there however when I tried to compile the program using
cc SS_Killhairpins_Info.cc
the header file could not be found I looked into this further and discovered that the pathway to the header file looked something like this <src/core/headerfilename.hh>
I know this next step was terrible programming the only thing I could think of. I then changed the pathway to /home/user/.../src/core/headerfilename.hh
and it worked and passed it on however the entire program is about 1.7 gb and i've been trying for about 3 9 hour days to change each one manually but the tree is too large and I've barely made a dent. 
I know that this is probably something super simple because it usually is but I just started programming so I'm not sure what it is. any help would be greatly appreciated. This program has a large community and is stable so it should be working since there is no forum on their website, I did post a thread on their forum as well. I'm also hoping to set up a computer that is similar to the one i'm using with this program so if I can fix the problem by either some sort of easy code or by switching ubuntu version I would like to do that before I initialize anything.

My newest compilation looks like this and this is with about 500+ files changed

[SIZE="1"]In file included from /home/.../source/external/boost_1_46_1/boost/mpl/bind.hpp:25:0,
                 from /home/.../source/external/boost_1_46_1/boost/mpl/lambda.hpp:18,
                 from /home/.../source/external/boost_1_46_1/boost/mpl/apply.hpp:25,
                 from /home/.../source/external/boost_1_46_1 /boost/iterator/iterator_facade.hpp:34,
                 from /home/.../source/external/boost_1_46_1/boost/range/iterator_range_core.hpp:23,
                 from /home/../source/external/boost_1_46_1/boost/range/iterator_range.hpp:13,
                 from /home/../source/external/boost_1_46_1/boost/algorithm/string/erase.hpp:16,
                 from /home/.../source/src/utility/string_util.hh:24,
                 from SS_Killhairpins_Info.cc:30:
/home/.../source/external/boost_1_46_1/boost/mpl/next.hpp:17:36: fatal error: boost/mpl/next_prior.hpp: No such file or directory
compilation terminated.[/SIZE]

-ryan

Ubuntu 12.04 LTS 64bit

---

