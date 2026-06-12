---
title: "cant use xargs with my c++ program"
date: 2009-06-13
forum: Programming Talk
---

### Post by monkeyking on 2009-06-13
Hi,

I want to able to use xarg with my program,
like

```

ls */*.txt |xargs ./myprogram

```

I got code like

[PHP]
#include <iostream>
#include <fstream>
#include <cstring>
#include <unistd.h>

#define LENS 10000
#define buf 200

int main(int argc, char **argv){
  char *filename =new char[buf];
  if(argc==2)
    filename = argv[1];
  else
    std::cin.getline(filename,buf);

  printf("#\t%s\n",filename);
  return 0;
}
[/PHP]

I get the filename if I do like

```

echo my_path | ./myprogram
#or
ls my_path | ./myprogram

```

but not

```

ls */*.txt |xargs ./myprogram

```


thanks in advance

---

### Post by soltanis on 2009-06-13
xargs by default feeds your program as many arguments as the shell allows (which in Linux is actually unlimited now, but the program is specified by the posix standard, plus it's useful).

Try the command again, but with

```

xargs -n 1

```

---

### Post by MadCow108 on 2009-06-13
alternative:
as xargs with no parameters just passes on the output as parameters you could write:
```

 for (int i=0; i<argc; i+=1)
  {
  	std::cout << argv[i] << std::endl;
  }

```
and:
ls *.* | xargs -0 ./programm

(-0 necessary for spaces in filenames! also in the version of soltanis)

another addition if you use soltanis+your solution:
your buffer can be to small for the filenames.
As your using c++ use strings:
```

  std::string filename;
  filename.reserve(buf);
  if(argc==2) 
    filename = argv[1]; 
  else 
    std::getline(cin,filename);

```

---

### Post by monkeyking on 2009-06-13
Thanks ppl,
It's working now.

---

