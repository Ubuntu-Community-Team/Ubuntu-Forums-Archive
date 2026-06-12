---
title: "Laptop fan is making lot of noise."
date: 2014-09-14
forum: New to Ubuntu
---

### Post by Chandrasekhar_Thum on 2014-09-14
Hi Team,

Its been a long while I used Ubuntu. Actually when I was in college. Now I'm almost like a new user. 

I have a question related to Ubuntu installation on my Sony Vaio VPCEA laptor. After installing Ubuntu 14.04 LTS, my laptop (i guess fan) is making lot of noise. This never use to happen with Linux Mint. It use to happen with Ubuntu 13. Can you please let me know if there is any fix/workaround that helps me fix this issue.

PS: Please let me know if there are any quick start tools or commands that can help be jump start with my new OS. Appreciate your help..!

Regards,
-Chandra.

---

### Post by Vladlenin5000 on 2014-09-14
Hi, welcome.

First of all, update the system. There's a good chance that a new kernel already corrected it.

---

### Post by SBMN7 on 2014-09-15
I think you should check your BIOS setting. You can change the CPU fan speed ans also you can restore you BIOS settings from there.

---

### Post by Chandrasekhar_Thum on 2014-09-15
> **SBMN7 said:**
> I think you should check your BIOS setting. You can change the CPU fan speed ans also you can restore you BIOS settings from there.

Thanks for your response. Like I said, I never use to see this issue with my windows machine as well as with Linux Mint. This issue I'm seeing only with Ubuntu.

---

### Post by Chandrasekhar_Thum on 2014-09-15
> **Vladlenin5000 said:**
> Hi, welcome.

First of all, update the system. There's a good chance that a new kernel already corrected it.

Thanks for your response. I'm trying that. Hopefully it resolves the issue, will update the thread accordingly.

---

### Post by Chandrasekhar_Thum on 2014-09-15
> **Vladlenin5000 said:**
> Hi, welcome.

First of all, update the system. There's a good chance that a new kernel already corrected it.

Kernel update didn't help. I still see the same issue.

---

### Post by Impavidus on 2014-09-15
Are there any proprietary drivers available for your hardware? Use the additional drivers tool. Better drivers may reduce energy usage and thereby heat production, and at the same time increase battery life. Maybe Mint installs them automatically.

---

### Post by Chandrasekhar_Thum on 2014-09-16
> **Impavidus said:**
> Are there any proprietary drivers available for your hardware? Use the additional drivers tool. Better drivers may reduce energy usage and thereby heat production, and at the same time increase battery life. Maybe Mint installs them automatically.

Thanks for your reply. I used update center to find the availability of any additional drivers and I don't see any drivers. Sometime But what I noticed is after Kernel update, most of the times, my laptop fan is absolutely silent.

---

### Post by Impavidus on 2014-09-16
Great. And when it isn't silent there is probably a reason for the computer to generate heat. If you are satisfied, could you mark this thread as solved? Click thread tools &#8594; mark as solved.

---

### Post by Mark Phelps on 2014-09-16
>  I used update center to find the availability of any additional drivers and I don't see any drivers. 

That's not how you find them.

Go to Additional Drivers.  Since your has a mobile Radeon video chipset, you should see entries for fglrx drivers there.

---

