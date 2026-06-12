---
title: "User Authentication (C/C++)"
date: 2010-06-12
forum: Programming Talk
---

### Post by beattyml1 on 2010-06-12
I want to write a program that will authenticate a user, and then launch a process as that user if authentication succeeds.  How do I go about doing this?

---

### Post by dwhitney67 on 2010-06-12
Use PAM.

Example:
```

//
// To build:
//
//      gcc pam_password.c -lpam -lpam_misc
//
// To get PAM development library:
//
//      sudo apt-get install libpam-dev
//
//
#include <security/pam_appl.h>
#include <security/pam_misc.h>
#include <stdio.h>

int main(int argc, char** argv)
{
   if (argc < 2) {
      fprintf(stderr, "Usage: %s <username>\n", argv[0]);
      return 1;
   }

   const char*            user = argv[1];
   static struct pam_conv pam_conversation = { misc_conv, NULL };
   pam_handle_t*          pamh;

   int res = pam_start(argv[0], user, &pam_conversation, &pamh);

   if (res == PAM_SUCCESS) {
      res = pam_authenticate(pamh, 0);
   }

   if (res == PAM_SUCCESS) {
      res = pam_acct_mgmt(pamh, 0);
   }

   if (res == PAM_SUCCESS) {
      fprintf(stdout, "Authenticated.\n");
   }
   else {
      fprintf(stdout, "Not Authenticated.\n");
   }

   pam_end(pamh, res);

   return res == PAM_SUCCESS ? 0 : 1;
}

```
You would want to do the "something" if 'res' equals PAM_SUCCESS after calling pam_acct_mgmt().

---

### Post by beattyml1 on 2010-06-12
Thanks, that helps a lot, but I can't seem to get it to build. 
I installed the package that you told me to and cut and pasted the code you gave me into, and when I try to build it it doesn't work.


```
gcc -c auth.c
```
exits succesfully, however

```
gcc -o auth auth.c
```

produces the following output

```

/tmp/ccM6nBO9.o: In function `main':
auth.c:(.text+0x65): undefined reference to `pam_start'
auth.c:(.text+0x84): undefined reference to `pam_authenticate'
auth.c:(.text+0xa3): undefined reference to `pam_acct_mgmt'
auth.c:(.text+0x114): undefined reference to `pam_end'
/tmp/cc6jL8vt.o:(.data+0x0): undefined reference to `misc_conv'
collect2: ld returned 1 exit status

```

Any ideas what is wrong?

---

### Post by dwhitney67 on 2010-06-12
Hmmm; that's odd.  My code has the instructions to compile it, but somehow I guess I neglected to post/copy it.  I've updated my earlier post to include it now.

For your needs, this is what is needed:
```

gcc YourProgram.c -lpam -lpam_misc

```

---

### Post by beattyml1 on 2010-06-13
Thanks, I got it to compile, but how would I go about changing this if I needed to do this with a GUI/I want to pass it the password from my program?

---

### Post by hakermania on 2010-06-13
> **beattyml1 said:**
> Thanks, I got it to compile, but how would I go about changing this if I needed to do this with a GUI/I want to pass it the password from my program?
just make 2 executables.The one that the friend above provided you and this one links to your GUI application E.g. mean {if pam = PAM_SUCCESSFUL system("/usr/share/myprogram/myGUIprogram"); else system("echo Not authenticated,aborting; sleep 2") 
system is provided in stdlib.h

---

### Post by beattyml1 on 2010-06-13
I think you misunderstood my question I want to present the user with a GUI login prompt with username and password, and once I get these I want to use this information that is now in my program to authenticate the user.  The user cannot use the command line to enter the password.  

How would I accomplish this?

---

