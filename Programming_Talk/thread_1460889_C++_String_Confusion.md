---
title: "C++ String Confusion"
date: 2010-04-23
forum: Programming Talk
---

### Post by MrStill on 2010-04-23
I am working on compiling a list of arguments into an array and passing them to the execv(const char* path, char *const args[]) function.

```
   	        ...
                const char* args[count];
		for(x = 0; x < count; x++){
			args[x] = argmnts[x];
		}
		while(dirs != NULL){
			strcpy(readyCommand, "");
			strcpy(readyCommand, dirs);
			strcat(readyCommand, "/");
			strcat(readyCommand, command);
			execv(readyCommand, args);
			dirs = strtok(NULL, ":");
		}
                ...
```

The issue I am having is that my args are of type const char* and are stored in an array const char *args[]. When I try to compile, I get an error:

```

nutshell.y:67: error: invalid conversion from ‘const char**’ to ‘char* const*’
nutshell.y:67: error:   initializing argument 2 of ‘int execv(const char*, char* const*)’

```

I have attempted to call my args array as type char *const; however, this moved my conversion error up to the line where I load the array with arguments. I am not very good with C strings so I can't say that I really understand the difference between types const char* and char *const. Any advise?

Thanks
Joseph

---

### Post by gmargo on 2010-04-23
I was able to make the error go away by casting it.
```

execv(readyCommand, (char * const *)args);

```> the difference between types const char* and char *constCheck out the **cdecl** tool (Install the **cdecl** package if needed.)

```

$ cdecl explain "const char * args[]"
declare args as array of pointer to const char

$ cdecl explain "const char ** a"
declare a as pointer to pointer to const char

$ cdecl explain "char * const * a"
declare a as pointer to const pointer to char

```

---

