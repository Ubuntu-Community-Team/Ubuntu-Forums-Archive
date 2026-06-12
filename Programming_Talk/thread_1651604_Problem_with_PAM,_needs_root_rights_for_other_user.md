---
title: "Problem with PAM, needs root rights for other users"
date: 2010-12-23
forum: Programming Talk
---

### Post by ritchie-w on 2010-12-23
Hi,

I am trying to get my PAM function running on kubuntu 10.10, but I failed.

```

	strcpy( userID,(char*) ((const char*) UserIdent.toLatin1()));
	strcpy( upassword,(char*) ((const char*) Password.toLatin1()));

	retval = pam_start(PAM_SERVICENAME, userID, &pam_convert, &pamhandle);
	if (retval == PAM_SUCCESS)
		{
		retval = pam_authenticate(pamhandle, PAM_SILENT );	
		if (retval == PAM_SUCCESS)

```

The function "pam_start" gets PAM_SUCCESS back which is ok, but the function "pam_authenticate" returns "PAM_AUTH_ERR".(Wrong password or 
insuffert rights)

The function is working with the actual logined in user of the desktop, but when I use an other user it fails.

The PAM definition file in /etc/pam.d/ .. looks like :
```

#
# default; standard UN*X access
#
auth    required        pam_unix.so debug
account required        pam_unix.so debug

```

When I run the program with "sudo ", everything works fine. 

Why do I need "root" right to access such functions ? Is there a way to do it without "root" rights.

Thanks for help

R.

---

### Post by dwhitney67 on 2010-12-23
I have the following program in my "sandbox"; perhaps you can check to see if it meets your needs.  Btw, I do not need 'root' privileges to run the program on my system.
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
#include <errno.h>

int main(int argc, char** argv)
{
   const char*            user = (argc > 1 ? argv[1] : getenv("USER"));
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

      res = pam_open_session(pamh, 0);

      if (res == PAM_SUCCESS) {
         fprintf(stdout, "Session open.\n");

         pam_close_session(pamh, 0);
      }
      else {
         fprintf(stderr, "Failed to open pam session: %s (%d)\n", pam_strerror(pamh, errno), errno);
      }
   }
   else {
      fprintf(stderr, "%s.\n", pam_strerror(pamh, errno));
   }

   pam_end(pamh, res);

   return res == PAM_SUCCESS ? 0 : 1;
}

```

---

### Post by ritchie-w on 2010-12-24
Hi,

I am using this program in a x window application with my own conversion function. Does your user, who is executing this command member of "shadow" ?

Did you tried a user who is not the same as execute this program ?

Thanks for help & happy X-mas

R.

---

### Post by dwhitney67 on 2010-12-24
> **ritchie-w said:**
> Hi,

I am using this program in a x window application with my own conversion function. Does your user, who is executing this command member of "shadow" ?

Did you tried a user who is not the same as execute this program ?

Thanks for help & happy X-mas

R.

No to all of you questions.  I have no desire to setup an additional account on my system.

Have you tried the application I posted?  It is the most basic of PAM applications.  If you can get it to work, then afterwards I would suggest that you attempt to try it out for other user accounts, or perhaps expand it to use another conversion function.

---

### Post by ritchie-w on 2010-12-25
Hi,

my function is working fine as well with my own account, even the code is moreless the same.

Because there is no security restrication from the system to read his own parameters. Just try to create a new user like 'test' and try to use your function again. I guess it will not work. Tested with kubuntu 10.10.

But you will need to test the new user on your own account.

Best regards

R.

---

