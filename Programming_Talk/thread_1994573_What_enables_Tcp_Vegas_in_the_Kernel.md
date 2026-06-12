---
title: "What enables Tcp_Vegas in the Kernel?"
date: 2012-06-03
forum: Programming Talk
---

### Post by geewhan on 2012-06-03
I would like to know if someone could tell me in the tcp.c file which function/line of code that enables the congestion avoidance algorithm.


I believe that this function/line of code enables the congestion avoidance algorithm, specifically the tcp_reno.
```
tcp_register_congestion_control(&tcp_reno);
```

I ask because I want to enable the tcp_vegas in the Kernel. I assume if that I put tcp_vegas such like this:

```
tcp_register_congestion_control(&tcp_vegas);
```

I would enable tcp_vegas congestion avoidance algorithm in the tcp_vegas.c file, right?

The tcp.c file I am referring to is the one that you can download from the Kernel website.

---

### Post by Bachstelze on 2012-06-03
No. This would just change the type of argument that the function expects, it would not change how that function is actually called (so if you do that your kernel might not even compile).

You seem to be unfamiliar with C, so I think you have a lot of learning to do before you can mess around with the kernel. In any case, this is probably not the right place to ask very technical kernel questions like that, you will have better luck on the kernel mailing-lists.

---

