---
title: "Implementing the LOGIN command in C/C++"
date: 2009-11-11
forum: Programming Talk
---

### Post by 5four on 2009-11-11
Hello everybody, i would really appreciate some help *implementing the login command under C/C++.*

This is a project i need to work on for my college and i have absolutely no idea where to start. I have medium C programming skills, but it's my first encounter with Linux, more specific UBUNTU. 

I'm guessing i need to read from the command line 2 strings (user&pass) then read and compare with records from user/password folders ?

Any tips will be appreciated!
Thanks in advance!

---

### Post by dwhitney67 on 2009-11-11
I presume that you have a C++ book readily available...

Read the section of the book that covers input and output to/from the terminal.

Prompt the user for their username, capture the input, and then repeat for the password.

If you would rather not have the password echoed to the terminal when the user types it in, use tcgetattr() and tcsetattr() to control the terminal.

To build your program, use 'g++'.  If you haven't got it installed, run:
```

sudo apt-get install build-essential

```
Typical way to use 'g++':
```

g++ MyProgram.cpp -o myprog

```

---

### Post by 5four on 2009-11-11
Thanks for the reply! 

I know how to capture I/O (decided to go with C instead of C++) but i have no idea what to do after, more exactly how do i compare those strings with the user/encrypted pass from Ubuntu's user list ...

---

### Post by Arndt on 2009-11-11
> **5four said:**
> Thanks for the reply! 

I know how to capture I/O (decided to go with C instead of C++) but i have no idea what to do after, more exactly how do i compare those strings with the user/encrypted pass from Ubuntu's user list ...

That may be hard to find out if no one told you: the function is called 'crypt'.

---

### Post by MadCow108 on 2009-11-11
edit: was wrong

---

### Post by 5four on 2009-11-14
I came up with the following code. The program works correctly when verifying if user exists or not, but i get "Login incorrect." no matter what password i insert. There is something wrong with that crypt() verification.

Anybody got a clue? Thanks.

```

/* gcc -lscrypt */
#include <pwd.h> /*  'struct passwd', getpwnam(). */
#include <sys/types.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>   /* strcmp()      */ 

char user[21];
char * password;
char * crypt(const char *password, const char *salt);
char salt[2];

struct passwd* user_info;

void main()
{
printf("User name: "); fflush(stdin);
fgets(user, 20, stdin);

if (strchr(user, '\n'))
    (*(strchr(user, '\n'))) = '\0';

user_info = getpwnam(user);
if (!user_info) {
    printf("User does not exist.\n");
    exit(1);
}

password = getpass("Password: ");
strncpy(salt, user_info->pw_passwd, 2);

if (strcmp(user_info->pw_passwd, crypt(password,salt)) != 0) {
    printf("Login incorrect.\n");
    exit(1);
}

printf("Login successful.\n"); 

}

```

---

### Post by dwhitney67 on 2009-11-14
I assume you are running your application under Ubuntu...

I do not know if you are aware of this, but the user's password is no longer (and it has been this way for quite some time) stored in /etc/passwd.

getpwnam() is looking only in /etc/passwd for the user's information.  The user's password is marked with an 'x'; the encrypted password is located in /etc/shadow.

I do not believe crypt() was used to create the encrypted password.  You need to look at PAM:  [http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/Linux-PAM_ADG.html](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/Linux-PAM_ADG.html)

You may also need to get the PAM development package:
```

sudo apt-get install libpam-dev

```

---

### Post by Arndt on 2009-11-14
> **dwhitney67 said:**
> I assume you are running your application under Ubuntu...

I do not know if you are aware of this, but the user's password is no longer (and it has been this way for quite some time) stored in /etc/passwd.

getpwnam() is looking only in /etc/passwd for the user's information.  The user's password is marked with an 'x'; the encrypted password is located in /etc/shadow.

I do not believe crypt() was used to create the encrypted password.  You need to look at PAM:  [http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/Linux-PAM_ADG.html](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/Linux-PAM_ADG.html)

You may also need to get the PAM development package:
```

sudo apt-get install libpam-dev

```

Look at the manual page for shadow(5) for some more information.

---

### Post by dwhitney67 on 2009-11-14
> **Arndt said:**
> Look at the manual page for shadow(5) for some more information.

Yes, it appears that crypt is used.

However, to authenticate a user, PAM is the easiest to use.  Here's an example (which I obtained via inspiration from the PAM application developer's page):
```

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
To build:
```

gcc password.c -lpam -lpam_misc

```

P.S.  The app above could be modified to permit no args to be passed to the application.  In such an event, PAM prompts for the user-id, and of course, the password.

---

