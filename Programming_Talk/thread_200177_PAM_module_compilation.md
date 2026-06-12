---
title: "PAM module compilation"
date: 2006-06-19
forum: Programming Talk
---

### Post by psih on 2006-06-19
I'm trying to compile my own PAM module, I wrote a simplest ever module, wich always succeeds, and a simplest ever application to use this module. When I call the authentication function from the application, it always responses with PAM_MODULE_UNKNOWN (error 28). So the problem is how to compile the module correctly.

Here are codes:
**PAM module**
```

#include <stdio.h>

#include <security/pam_modules.h>
#include <security/_pam_macros.h>

/* --- authentication management functions --- */

PAM_EXTERN int
pam_sm_authenticate(pam_handle_t *pamh, int flags ,
                    int argc , const char **argv )
{
    return PAM_SUCCESS;
}

/* end of module definition */

#ifdef PAM_STATIC

/* static module data */

struct pam_module _pam_permit_t_modstruct = {
    "pam_permit_t",
    pam_sm_authenticate,
    NULL,
    NULL,
    NULL,
    NULL,
    NULL
};

#endif

```

**application**
```

#include <security/pam_appl.h>
#include <security/pam_misc.h>

#include <stdlib.h>
#include <stdio.h>

static struct pam_conv conv = {
    misc_conv,
    NULL
};

int main(int argc, char *argv[])
{
    pam_handle_t *pamh = NULL;
    int pam_err;

    pam_err = pam_start("test_app", NULL, &conv, &pamh);
    if( pam_err != PAM_SUCCESS)
    {
        printf("pam_start error: %d\n", pam_err);
        return pam_err;
    }
    pam_err = pam_authenticate(pamh, 0);
    if( pam_err != PAM_SUCCESS)
    {
        printf("pam_authenticate error: %d\n", pam_err);
        return pam_err;
    }
}

```

What gcc keys do I have to use? I was trying to do everything with respect to the [Linux-PAM manual](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/), and here is how I compile the module and application:

**module**
```

gcc -fPIC -c pam_permit_t.c
ld -x --shared -o /lib/security/pam_permit_t.so pam_permit_t.o

```

**application**
```

gcc -gstabs -o test_app test_app.c -lpam -lpam_misc -ldl

```

---

