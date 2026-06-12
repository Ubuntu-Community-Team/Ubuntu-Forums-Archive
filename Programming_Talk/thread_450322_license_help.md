---
title: "license help"
date: 2007-05-21
forum: Programming Talk
---

### Post by oly on 2007-05-21
hi, i have been writing a program in python which i wish to release soon, however i am unsure which license to use, can anyone lend some insight.

basically i want the code to remain open and any changes / forks to it to be released and made available, if anyone was to sell or make a profit from it commercially thats fine as long as i got something out of it, basically so some one is not making money out of all the work and time i have put into the application with out some return.

similar position to a lot really, i spend a lot of my free time coding and do not earn much money.

what license closely matches these requirement, and is there anything else i should be thinking about ?

The program by the way is a bit like swat but closer to  sme server manager.

---

### Post by pmasiar on 2007-05-21
> **oly said:**
> hi, i have been writing a program in python which i wish to release soon, however i am unsure which license to use, can anyone lend some insight. (skip)

The program by the way is a bit like swat but closer to  sme server manager.

Looks like license of Python is too free for your needs: [http://python.org/psf/license/](http://python.org/psf/license/) Best bet IMHO will be to use double license like MySQL: (1) GPL, forcing everyone release changes back, and (2) proprietary license for people who wants to pay for non-GPL license.

Unfortunately GPL does not allow you to prevent anyone from charging for any services related to your code - it only forces others to release code changes. But since *you* are the best expert in your code, if anyone want to pay for services, why whey would hire someone else?

---

### Post by oly on 2007-05-21
good point, i was thinking GPL initally, but i know from a company that supports linux servers that they are intrested in my project. so it seems others might be as well which is why i started developing it.

probably will put it under GPL just wanted to know what else is available

---

### Post by pmasiar on 2007-05-21
> **oly said:**
> probably will put it under GPL just wanted to know what else is available


MIT, BSD and APACHE licenses are more "free" - they let the code be used without returning changes back to the community.

[http://opensource.org/](http://opensource.org/) and [http://www.fsf.org/](http://www.fsf.org/) link to many "approved" licenses, check them out. Big projects (like Python, Mozilla etc) often have own license. But without consulting a lawyer, it is not simple to decide. As a copyright owner, you can use 2 licenses, so GPL + proprietary seems as best way to me. GPL gives you most compatibility with code from other people.

IMHO, IANAL, YMMV of course.

---

### Post by winch on 2007-05-21
GPL prevents distribution of binaries without also making the source availible on request. That is different to forcing people to release changes.

If you never distribute the program or only distribute it to people who won't request or distribute the source you can modify a GPLed program all you want and never release your changes.

---

### Post by pmasiar on 2007-05-21
> **winch said:**
> GPL prevents distribution of binaries without also making the source availible on request. That is different to forcing people to release changes.

You are correct of course - this is what I had in mind. 

I just wanted to compare GPL with MIT/BSD licenses, which do not require releasing changes at all.

And I said IANAL :-)

---

### Post by oly on 2007-05-22
is it possibly to just switch licenses at a later date ?

so if i release under gpl and then a year down the line find another license which is more suited to my needs, is it possibly to just start releasing under the new license. ?

---

### Post by Mathiasdm on 2007-05-22
It would be possible to change the license as long as you have permission from all the contributors to the code.
Also, if someone else has a version under the GPL license, he can still distribute that version under that license.

---

### Post by pmasiar on 2007-05-22
> **oly said:**
> so if i release under gpl and then a year down the line find another license which is more suited to my needs, is it possibly to just start releasing under the new license. ?

Yes, you can change license to your own code (code you own copyright) at any time, or release it under multiple licenses in parallel.
You may want to accept outside patches only if copyright is assigned to you to have this flexibility later. Some people might not like it and not contribute tho - GPL is golden standard and anything else is suspicious. So be careful what message you will send to developer community.

---

