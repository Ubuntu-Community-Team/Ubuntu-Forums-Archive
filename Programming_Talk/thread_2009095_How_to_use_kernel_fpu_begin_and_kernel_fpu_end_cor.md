---
title: "How to use kernel_fpu_begin and kernel_fpu_end correctly?"
date: 2012-06-23
forum: Programming Talk
---

### Post by geewhan on 2012-06-23
I would like to know how to use the functions, kernel_fpu_begin and kernel_fpu_end, correctly.

I did try to google this, but the other forums were not clear enough for me to understand.

I did try this doing these functions, but I got couple of errors. I think it may have to do with the include header file.
May be it is the wrong one.

The code below is something I tried. 
Any help is really appreciated thanks.

```

#include <asm/i387.h>

static void tcp_vegas_cong_avoid(struct sock *sk, u32 ack, u32 in_flight)
{
	kernel_fpu_begin();

	struct tcp_sock *tp = tcp_sk(sk);
	struct vegas *vegas = inet_csk_ca(sk);
	int target_queue_size;
	double avgRTT_Mult, rtt_Mult; 
	
	target_queue_size = 100;
	avgRTT_Mult = 0.99609375; //(255/256)
	rtt_Mult    = 0.00390625; //(1/256)


	avgRTT = (avgRTT_Mult*avgRtt) + (rtt_Mult*rtt);

	kernel_fpu_end();	
}
```

---

