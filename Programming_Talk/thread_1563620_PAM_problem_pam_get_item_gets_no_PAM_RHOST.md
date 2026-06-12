---
title: "PAM problem: pam_get_item gets no PAM_RHOST"
date: 2010-08-29
forum: Programming Talk
---

### Post by ritchie-w on 2010-08-29
Hi,

does somebody knows, what's wrong with 
```

if( pam_get_item(pamhandle,PAM_RHOST,(const void **) &hostname) == PAM_SUCCESS)


```

I get PAM_SUCCESS, but the pointer is zero !

Thanks for help

R.

---

