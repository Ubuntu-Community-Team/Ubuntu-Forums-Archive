---
title: "adding a new module in NS-2.35 /ubuntu 12.04 LTS"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by row225 on 2012-07-26
Hi
I'm not sure if i have to post this thread here or in the NS2 website, but i will post on both to see if am lucky to get some help.
i was trying to add a new routing protocol (rumor routing) . i modified the  makefile and after that i tried to compile again. but am having an error message and am not quiet sure what its mean. the error is the one below
 
make: *** No rule to make target `rumor/rumor_packet.o', needed by `ns'.  Stop

is the error with NS2 or Ubuntu?

---

### Post by TheFu on 2012-07-26
NS3 is an installable package in 12.04 and the package manager should handle the required dependencies for you.

NS2 appears to be a fairly complex set of programs with many non-trivial dependencies based on the README file.

Asking for help on the nsnam project site is probably best.  You'll want to have the exact errors shown during compile time and 10 lines above and below available. I suspect your system is missing a dependency, but I don't really know based on the 1 line provided.

---

### Post by row225 on 2012-07-26
> **TheFu said:**
> NS3 is an installable package in 12.04 and the package manager should handle the required dependencies for you.

NS2 appears to be a fairly complex set of programs with many non-trivial dependencies based on the README file.

Asking for help on the nsnam project site is probably best.  You'll want to have the exact errors shown during compile time and 10 lines above and below available. I suspect your system is missing a dependency, but I don't really know based on the 1 line provided.

Yeah but the error just appears on one line for now, am trying to debug it after some readings, I will come back to you! Thanks for your reply! I have ns3 but haven't installed it yet! Was using ns2 until the problems started with the new module.

---

### Post by TheFu on 2012-07-26
ns-allinone-2.35.tar.gz?

---

### Post by row225 on 2012-07-26
> **TheFu said:**
> ns-allinone-2.35.tar.gz?

Yeah! This is the one

---

### Post by row225 on 2012-07-26
i got it right, there is no rumor.packet.cc in the folder, so there is no way of having rumor.packet.o ... so i had to go go back in the makefile.(in) to modify it again. then re-run configure. my bad.
thanks for the help:popcorn:

---

