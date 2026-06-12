---
title: "tracing call chain, ebp in kernel stack located, but system halted"
date: 2007-12-23
forum: Programming Talk
---

### Post by RaistlinU on 2007-12-23
I am trying to trace the calling chain when a system call happens, I've already located ebp in kernel stack when syscall happens. The tracing loop would be like this:
> 			int i;
			       for (i=1; i<10; i++) {
			      if (((ebp & 0xffffc000) == 0xbfffc000) && (((ebp+sizeof(long)) & 0xffffc000) == 0xbfffc000)) {   
					pc[i] = *((long*)ebp+1);  	  
					ebp = *((long*)ebp);
				} else {
					pc[i] = 0xffffffff;
					break;
				}
			}
when I compiled the kernel and run the intercepting function, system always became halted. 
Please somebody help me with this problem?

---

