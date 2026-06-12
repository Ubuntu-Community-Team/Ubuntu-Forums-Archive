---
title: "make issue with head file dependency with gcc 4.6.1 on ubuntu 11.10"
date: 2011-11-16
forum: Packaging and Compiling Programs
---

### Post by dx_z on 2011-11-16
I will highly appreciate if any expert can help me on this.

The issue is that the make command cannot detect changes in head file. For example, if I touch "test.h", make command will not recompile. 

This works with gcc 4.5.4 on the same OS.

Thanks a lot!

--test.h--
#include <iostream>
void hello()
{
	std::cout << "Hello\n";
}

--test.cc--
#include "test.h"
int main()
{
	hello();
}

--Makefile--
sources := test.cc						
objects := test.o
depends := test.d
main  := test

all : $(main)
obj : $(objects) 

$(main) : % : %.o 
	@echo "     " compile $< : -o $@ 
	@$(CXX) $< -o $@  -L$(LIB_DIR) -lcommon $(LDFLAGS) $(LDLIBS) $(STATIC)
 
clean :
	-rm -rf $(objects) $(depends) $(main)

%.o : %.cc
	@echo "     " compile $<
	@$(CXX) -c $(CPPFLAGS) $(CXXFLAGS) -MMD -MP -MF"$(@:%.o=%.d)" -MT"$(@:%.o=%.d)" $< -o $@

ifneq ($(MAKECMDGOALS),clean)
-include $(depends)
endif

---

