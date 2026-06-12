---
title: "create symlinks of icons with cmake"
date: 2011-07-23
forum: Programming Talk
---

### Post by Jonas thomas on 2011-07-23
I'm trying to symlink icons in a source tree into the bin file with the executable.
This cmake stuff is sort of new to me. I managed to to this for an indivdual file, but I was hoping to symlink contents of a folder into another in one command. 

It seems like from/*.*  to /*.* doesn't work

Is that possible to do this in one shot or do I need to build a for e 
ach loop and do this with indivdual files.
```
if("${CMAKE_EXTRA_GENERATOR}" STREQUAL "CodeBlocks")
   if(UNIX)
      	#JT
      	#The local bin directory was created when the src directory was added
      	#may want to invoke RUNINPLACE from the command line
        message ("Adding symlinks to /bin to enable for RUNINPLACE")   
      	
	execute_process(COMMAND ${CMAKE_COMMAND} -E create_symlink
	${CMAKE_SOURCE_DIR}/icons/arc.png

        ${CMAKE_BINARY_DIR}/bin/arc.png)
        message("${CMAKE_BINARY_DIR}")


    endif()
endif()

```

---

