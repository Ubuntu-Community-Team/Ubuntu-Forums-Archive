---
title: "How much RAM is enough and safe for Ubuntu CLI 24/7 Server?"
date: 2024-11-10
forum: New to Ubuntu
---

### Post by ken-91283 on 2024-11-10
New to Linux.

How to properly setting up a 24/7 non-stop server running CLI Ubuntu and a few self-developed applications to achieve best-practice up time?   May be one hangup reboot per 12 to 24 months, if possible.

1. CLI version is more stable than GUI version, right?

2. Any rule of thumb best-practice on how much RAM?  How to read 'top' command and calculate amount of RAM so that it has enough safty margin.  

3. Should we run the system at full load for, may be, a few days and observe the top command output.  Presumably, many software modules (inside Ubuntu and our application) use dynamic memory allocation and release and RAM usage is variable???   Used RAM should not be growing too much over days or else may be memory leakage (not released)?

4. How to interface with UPS, to signal AC power loss and perform orderly shutdown?

5. What hardware is more suitable?  The server handle small number of bytes per seconds.  Intel N100, Intel low-thermal power desktop (not affect by 13rd and 14th generatio issues) CPU (i3, i5, etc, may be 1xx to 2xx USD for CPU), ARM CPU?

6. Any pointers to information on middleware, utility, etc. that you recommend for the above use case?

Many thanks

---

### Post by grahammechanical on 2024-11-10
> 1. CLI version is more stable than GUI version, right?

Why do you say that? What experience of Linux/Ubuntu do you have so that you can claim that Desktop Ubuntu is not as stable as Server Ubuntu? As far as I know Ubuntu server is released as a Long Term Support (LTS) every two years just like Ubuntu desktop. Long Term Support versions get 5 years support. 

The ubuntu developers bring out new versions of Ubuntu (desktop & sever) every 6 months after a 26 week development period. These Standard support versions are supported for 9 months and it is in them that the Ubuntu developers bring in new software. So that by the time the next LTS version is released we have a stable operating system.

By the way you should be aware of the fact that the latest Ubuntu LTS version is Ubuntu 24.04 LTS. Supported up to April 2029. Your other questions are beyond my expertise. In my opinion they should be asked as separate questions in separate threads. To avoid confusion as to which posts are replying to which question.

Regards

---

### Post by ActionParsnip on 2024-11-11
Just as stable. A GUI adds more services and running applications but why/how would it be more or less stable?
Here is the official Ubuntu requirements doc:
[https://ubuntu.com/server/docs/system-requirements](https://ubuntu.com/server/docs/system-requirements)

---

### Post by Topsiho on 2024-11-22
Though I am not able to answer the questions of the OP, I think, logically, that adding any unnecessary software to any server adds to it's potential instability and insecurity, and should be avoided. And that a GUI can offer only limited options as compared to what one can do with the CLI, as any GUI can provide only a tiny selection of the capabilities of the CLI.

Topsiho

---

