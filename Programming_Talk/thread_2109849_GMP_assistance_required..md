---
title: "GMP assistance required."
date: 2013-01-28
forum: Programming Talk
---

### Post by Ghostmn on 2013-01-28
I'm getting a segmentation fault with this code

```

mpf_init(PLANCKS_CONSTANT);

mpf_set_str(PLANCKS_CONSTANT, ".00000000000000000000000000000006626", 10);

gmp_printf("Planks Constant  %.*Ff", PLANCKS_CONSTANT);

```What's the proper way of actually initializing a extremely small decimal? I happen to be using C.

---

### Post by Bachstelze on 2013-01-28
And what is the PLANCKS_CONSTANT macro defined as?

---

### Post by Ghostmn on 2013-01-28
> **Bachstelze said:**
> And what is the PLANCKS_CONSTANT macro defined as?


I'm actually just using it as a mpf_t variable. Originally it was a macro though.

---

### Post by Bachstelze on 2013-01-28
> **Ghostmn said:**
> I'm actually just using it as a mpf_t variable. Originally it was a macro though.

Then don't write it in all uppercase.

Your problem is actually with printing, not initialising (if you use the simpler mpf_out_str instead of gmp_printf it works).

---

### Post by Ghostmn on 2013-01-28
> **Bachstelze said:**
> Then don't write it in all uppercase.

Your problem is actually with printing, not initialising (if you use the simpler mpf_out_str instead of gmp_printf it works).

I didn't mean to keep it all uppercase. It's changed now.

Anyways, thank you for the solution.

```


mpf_init(plancks_constant);
mpf_set_str(plancks_constant, ".00000000000000000000000000000006626", 10);
    
mpf_out_str(stdout, 10, 0, plancks_constant);


```

---

### Post by Bachstelze on 2013-01-28
Of course this leaves open the question of why gmp_printf() failed. I do not use it often so I am not sure, double-check he documentation.

---

### Post by Ghostmn on 2013-01-28
> **Bachstelze said:**
> Of course this leaves open the question of why gmp_printf() failed. I do not use it often so I am not sure, double-check he documentation.

I only used gmp_printf because there was a code snippet on wikipedia.

The Docs found on [http://gmplib.org/manual/](http://gmplib.org/manual/)  didn't really give me good examples. The technical jargon of it is unfamiliar to me.

---

