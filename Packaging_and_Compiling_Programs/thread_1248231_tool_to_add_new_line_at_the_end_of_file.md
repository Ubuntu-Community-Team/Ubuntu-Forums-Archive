---
title: "tool to add new line at the end of file"
date: 2009-08-23
forum: Packaging and Compiling Programs
---

### Post by cpthk on 2009-08-23
Hi:

I am trying to compile a code in ubuntu, the code was from windows. GCC gave me thousands of warning that "no newline at the end of the file". I know I only need to add a newline for each file, but the thing is I have thousand of source files here, adding for each file is probably not a good move. Is there any tool either in ubuntu or windows that does that for me? Or is there any environment variable for GCC to ignore those warnings?

Thanks.

---

### Post by unutbu on 2009-08-25
This will add a newline to the end of each *.c file :
```

find . -name "*.c" -exec sed -i '$a\\' {} ";"
```

Also, if you install the tofrodos package, then the command
```

find . -name "*.c" -exec fromdos {} ";"
```

could be used to convert all DOS CR/LF line endings to unix LFs.

---

