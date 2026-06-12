---
title: "Error while compiling the kernel"
date: 2016-11-02
forum: Programming Talk
---

### Post by thinker1 on 2016-11-02
Greetings and salutations:

I am trying to compile the Ubuntu linux kernel based on the instructions from this page

[https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

I got all the way to the following command

fakeroot debian/rules binary-headers binary-generic

I get the following errors:

/home/adil/ubuntu-precise/arch/x86/kvm/svm.c: In function ‘svm_vcpu_run’:
/home/adil/ubuntu-precise/arch/x86/kvm/svm.c:3707:18: error: invalid character ' ' in raw string delimiter
   "push %%"R"bp; \n\t"
                  ^
/home/adil/ubuntu-precise/arch/x86/kvm/svm.c:3707:3: error: stray ‘R’ in program
   "push %%"R"bp; \n\t"
   ^
/home/adil/ubuntu-precise/arch/x86/kvm/svm.c:3708:33: error: invalid character ' ' in raw string delimiter
   "mov %c[rbx](%[svm]), %%"R"bx \n\t"
                                 ^
....


When I looked in the file svm.c, I see the following code

        asm volatile (
                "push %%"R"bp; \n\t"
                "mov %c[rbx](%[svm]), %%"R"bx \n\t"
                "mov %c[rcx](%[svm]), %%"R"cx \n\t"
                "mov %c[rdx](%[svm]), %%"R"dx \n\t"
                "mov %c[rsi](%[svm]), %%"R"si \n\t"
                "mov %c[rdi](%[svm]), %%"R"di \n\t"
                "mov %c[rbp](%[svm]), %%"R"bp \n\t"

....

So apparently this is assembly code and my guess is that I am not linking the right libraries. 

Any help will be greatly appreciated

Thanks!

---

