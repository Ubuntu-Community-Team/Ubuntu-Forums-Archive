---
title: "[SOLVED] Confused on a C point operation, using select()"
date: 2007-11-15
forum: Programming Talk
---

### Post by fyplinux on 2007-11-15
Hi,forks

It is the original example, it runs successfully:

===============
```

#include <stdio.h>
#include <sys/time.h>
#include <sys/types.h>
#include <unistd.h>
int
main(void) {
    fd_set rfds;
    struct timeval tv;
    int retval;
    /* Watch stdin (fd 0) to see when it has input. */
    FD_ZERO(&rfds);
    FD_SET(0, &rfds);
    /* Wait up to five seconds. */
    tv.tv_sec = 5;
    tv.tv_usec = 0;
    retval = select(1, &rfds, NULL, NULL, &tv);
    /* Don't rely on the value of tv now! */
    if (retval == -1)
        perror("select()");
    else if (retval)
        printf("Data is available now.\n");
        /* FD_ISSET(0, &rfds) will be true. */
    else
        printf("No data within five seconds.\n");
    return 0;
}


```

I thought rfds is a point operation, it  might be work like the below code. but it didnt work, there's Segmentation faul.

===============
```

#include <stdio.h>
#include <sys/time.h>
#include <sys/types.h>
#include <unistd.h>
int
main(void) {
    fd_set *rfds;/*.........modified............*/
    struct timeval tv;
    int retval;
    /* Watch stdin (fd 0) to see when it has input. */
    FD_ZERO(rfds);
    FD_SET(0, rfds);
    /* Wait up to five seconds. */
    tv.tv_sec = 5;
    tv.tv_usec = 0;
    retval = select(1, rfds, NULL, NULL, &tv);
    /* Don't rely on the value of tv now! */
    if (retval == -1)
        perror("select()");
    else if (retval)
        printf("Data is available now.\n");
        /* FD_ISSET(0, rfds) will be true. */
    else
        printf("No data within five seconds.\n");
    return 0;
}

```

Could anyone give a detailed explanation, thank you very much.

---

### Post by smartbei on 2007-11-15
The reason you are having a problem is that rfds in your changed program is merely a pointer to a fd_set, and is not set to point at a specific fd_set in memory. It is considered good practice to initialize pointers to NULL for several reasons. In this case it is a good idea because it will remind you that the pointer is not pointing at anything, and that is why you are getting a segmentation fault. What you want to do is something like:

```

#include <stdio.h>
#include <sys/time.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{
	fd_set *rfds = NULL;
	rfds = (* fd_set) malloc(sizeof fd_set); /*CHECK THIS OUT*/
	if (rfds == NULL)
	{
		printf("Couldn't allocate a new fd_set");
		return 0;
	}
	struct timeval tv;
	int retval;

	/* Watch stdin (fd 0) to see when it has input. */
	FD_ZERO(rfds);
	FD_SET(0, rfds);

	/* Wait up to five seconds. */
	tv.tv_sec = 5;
	tv.tv_usec = 0;
	retval = select(1, rfds, NULL, NULL, &tv);

	/* Don't rely on the value of tv now! */
	if (retval == -1)
		perror("select()");
	else if (retval)
		printf("Data is available now.\n");

	/* FD_ISSET(0, rfds) will be true. */
	else
		printf("No data within five seconds.\n");
	
	free(rfds); /*CHECK THIS OUT*/
	return 0;
}

```
The lines with CHECK THIS OUT are the major changes. Notice that I free rfds in the end - sine I am dynamically allocating data, I must also dynamically free the data when I am done using it. Notice also that I check after the malloc call to see that it has actually allocated a space in the memory - if all memory is used it will return NULL (0).

On the same line as the malloc I have (* fd_set), which is a hint for the compiler that the value returned by malloc should be used as a pointer to a fd_set structure.

Hope that cleared it up.

Lastly, please, please, use code tags. See the "#" symbol in the advanced editor/post writer.

EDIT: Note that I have changed the the line with the malloc, it should be (fd_set *) instead of (* fd_Set). Thanks to [aks44]("http://ubuntuforums.org/member.php?u=303900") for pointing this out (via private message).

---

### Post by fyplinux on 2007-11-15
If I test this code:
```

#include <stdio.h>
#include <sys/time.h>
#include <sys/types.h>
#include <unistd.h>

int main(void) {
    fd_set rfds;
   
   printf("%d",rfds);
    FD_ZERO(&rfds);
    printf("%d",rfds);
    FD_SET(0, &rfds);
    printf("%d",rfds);
    return 0;
}
```

I got the result:
001

Does this mean rfds is automatically(implicitly) setted after calling 
 > FD_SET(0, &rfds);??

---

### Post by smartbei on 2007-11-16
Well, you can't really be sure what it is doing since rfds is a structure and not a integer as printf would expect from the "%d". If you want you can track down exactly what it is doing through the header files.

from going through them a bit myself I see that fd_set is actually a struct that has a single field, a array of long ints of length 1024/8*sizeof(long int). (It doesn't actually appear in this fashion - this is after going through several defines).

---

### Post by fyplinux on 2007-11-16
smartbei, thank you very much for your patience

---

