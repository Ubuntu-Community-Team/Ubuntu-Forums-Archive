---
title: "GMP precision problem"
date: 2010-11-07
forum: Programming Talk
---

### Post by Phil991 on 2010-11-07
Hi ! 

I'm trying to use GMP (GNU Multiprecision Library). With integers it's ok but i get a problem with float type.

The code : 

#include <gmp.h>

void main() {

mpf_t sunMass;
mpf_init (sunMass);
mpf_set_d (sunMass, 1.989e30);
gmp_printf("sunMass = %Ff\n", sunMass);
}

Output : 
1988999999999999901910000000000

Strange isn't it?

with Gravitational constant : 
mpf_init (G);
mpf_set_d (G, 0.000000000667428 );

Output : 0.000000000667428000000000024141

What's happening?

I'm on Linux Ubuntu 10.10 and GCC 4.4.5.

Thanks !

---

### Post by Tony Flury on 2010-11-07
probably because you are passing it a float initially and that is limited precision, so the library has faithfully recreated the actual number that you passed it - complete with its precission error

Edit - if you want it to work properly - initialise it with integers and then divide using the library routines, thus ensuring appropriate precission is maintained : 

```

mpf_set_d (sunMass, 1989);
// Divide sunMass by 1000 and multiply by 1e30 - not sure how that works in this library.

```

---

