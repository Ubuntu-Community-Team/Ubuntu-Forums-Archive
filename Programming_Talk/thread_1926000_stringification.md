---
title: "stringification"
date: 2012-02-15
forum: Programming Talk
---

### Post by conradin on 2012-02-15
Hi all, 
I am trying to make a define macro that is a string of flags for the mode of the function open(). What I have, (bellow) seems to set m775 to the correct set of flags, but when the file is written, the permissions are all screwed up. Can someone show me what I'm doing wrong? I want the permissions to be set to 775 when Im done. And yes, my umask is set to allow for this to work.


```
#include <sys/types.h>   //Specified in man 2 open
#include <sys/stat.h>
#include <stdlib.h>
#include <errno.h>  	 //Allows use of error numbers
#include <fcntl.h>       //Specified in man 2 open
#include <stdio.h>

#define  m775   "S_IRWXU |  S_IRWXG  |  S_IROTH |  S_IXOTH"


int main(int argc, char *argv[]){
	char modez[] = m775;
	int fd;
	printf("%s", modez);
	fd = open(argv[1], O_CREAT, modez);
			
     return 0;
}
```

---

### Post by conradin on 2012-02-15
By comparision, (this): totaly works but looks stupid:
```
#include <sys/types.h>   //Specified in man 2 open
#include <sys/stat.h>
#include <stdlib.h>
#include <errno.h>  	 //Allows use of error numbers
#include <fcntl.h>       //Specified in man 2 open
#include <stdio.h>

#define  m775   "S_IRWXU |  S_IRWXG  |  S_IROTH |  S_IXOTH"
#define  m700    S_IRWXU
#define  m070    S_IRWXG
#define  m004    S_IROTH
#define  m001    S_IXOTH

int main(int argc, char *argv[]){
	
	int fd;
	fd = open(argv[1], O_CREAT, m700 | m070 | m004 | m001 );
		
     return 0;
}
```

---

### Post by McNils on 2012-02-15
You are sending the address of modez to open instead of what you really mean.

Here is a simple correct version.
```
#include <sys/types.h>   //Specified in man 2 open                                                                                                                                  
#include <sys/stat.h>                                                                                                                                                               
#include <stdlib.h>                                                                                                                                                                 
#include <errno.h>       //Allows use of error numbers
#include <fcntl.h>       //Specified in man 2 open
#include <stdio.h>

#define  m775   S_IRWXU |  S_IRWXG  |  S_IROTH |  S_IXOTH


int main(int argc, char *argv[]){
        int fd;
        fd = open(argv[1], O_CREAT, m775);
                        
     return 0;
}

```

---

### Post by Bachstelze on 2012-02-15
Well, you are giving open() a string where it expects an integer... What you want is

```
#include <sys/types.h>   //Specified in man 2 open
#include <sys/stat.h>
#include <stdlib.h>
#include <errno.h>  	 //Allows use of error numbers
#include <fcntl.h>       //Specified in man 2 open
#include <stdio.h>

#define  m775   ((S_IRWXU) | (S_IRWXG) | (S_IROTH) | (S_IXOTH))


int main(int argc, char *argv[]){
	mode_t modez = m775;
	int fd;
	printf("%d", m775);
	fd = open(argv[1], O_CREAT, modez);
			
     return 0;
}
```

You can also just do this...

```
fd = open(argv[1], O_CREAT, 0775);
```

---

### Post by Arndt on 2012-02-15
> **McNils said:**
> 
```

#define  m775   S_IRWXU |  S_IRWXG  |  S_IROTH |  S_IXOTH

```

This works, but it is always a good idea to let parentheses be a part of the macro definition:

#define  m775   (S_IRWXU |  S_IRWXG  |  S_IROTH |  S_IXOTH)

---

### Post by dwhitney67 on 2012-02-15
> **conradin said:**
> By comparision, (this): totaly works but looks stupid:
```

#define  m775   "S_IRWXU |  S_IRWXG  |  S_IROTH |  S_IXOTH"

```

Congratulations.  The macro above defines m775 to be a string.  If you had removed the quotes, you would have had better luck.

---

### Post by conradin on 2012-02-15
!! Aw man, I tried something like that the other day, but didnt have the 0 in 775! That does look much better!
Alas, I really should get into using, and understanding macros anyway.
Thank you Everyone!



You can also just do this...

```
fd = open(argv[1], O_CREAT, 0775);
```[/QUOTE]

---

### Post by dwhitney67 on 2012-02-15
> **conradin said:**
> !! Aw man, I tried something like that the other day, but didnt have the 0 in 775! That does look much better!
Alas, I really should get into using, and understanding macros anyway.
Thank you Everyone!



You can also just do this...

```
fd = open(argv[1], O_CREAT, 0775);
```

When you prepend a 0 (zero) before the numeral 775, that number is treated as octal.  Thus:

0775 = 7*64 + 7*8 + 5 = 509 (base 10)

Obviously 509 is different from 775.

---

### Post by ofnuts on 2012-02-15
Am I alone in thinking that defining
```
#define  m775   (S_IRWXU |  S_IRWXG  |  S_IROTH |  S_IXOTH)
```
 isn't terribly helpful for the hoi polloi who don't know their access flags by heart, and that calling this macro "NO_WRITE_RIGHTS_FOR_OTHERS" would be a bit more explicit?

---

### Post by Arndt on 2012-02-15
> **ofnuts said:**
> Am I alone in thinking that defining
```
#define  m775   (S_IRWXU |  S_IRWXG  |  S_IROTH |  S_IXOTH)
```
 isn't terribly helpful for the hoi polloi who don't know their access flags by heart, and that calling this macro "NO_WRITE_RIGHTS_FOR_OTHERS" would be a bit more explicit?

No, I agree. If you know the number is 775 and expect the readers to know it too, why not write that in the first place.

---

