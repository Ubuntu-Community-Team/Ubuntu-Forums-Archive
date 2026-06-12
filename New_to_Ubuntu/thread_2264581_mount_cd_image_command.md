---
title: "mount cd image command"
date: 2015-02-08
forum: New to Ubuntu
---

### Post by anif726 on 2015-02-08
hello every one ... i am very new to ubuntu OS ,,, this forum help me a lot... thanks

but i have one question that i didn't understand ...

when i want t install vmware tools and the cd image didn't mount on ubuntu dekstop... we must use command line... it said something like this

" in ubuntu guest"

what this means?

1. run command in terminal { host }

2. run command in terminal { guest session }

3. run command in vmware workstation black window [ but in this window i can't type anything ... when i press keypad it keep load the same order.. ]

thank you

i am using ubuntu 12.04 64 bit

---

### Post by yancek on 2015-02-08
I haven't used VMWare but when it says Ubuntu guest, that means running Ubuntu inside the virtual software.  Ubuntu host is what you have installed to your hardware which you say is Ubuntu 12.04.  So you install VMWare and then boot an iso or a CD with a bootable image inside VMWare.  I've actually only used VirtualBox but I would expect it to be similar.

---

### Post by sandyd on 2015-02-08
> **anif726 said:**
> hello every one ... i am very new to ubuntu OS ,,, this forum help me a lot... thanks

but i have one question that i didn't understand ...

when i want t install vmware tools and the cd image didn't mount on ubuntu dekstop... we must use command line... it said something like this

" in ubuntu guest"

what this means?

1. run command in terminal { host }

2. run command in terminal { guest session }

3. run command in vmware workstation black window [ but in this window i can't type anything ... when i press keypad it keep load the same order.. ]

thank you

i am using ubuntu 12.04 64 bit
With virtualization, there are two main OS systems that will be refered to:

"Host" refers to the system that you are running the virtualization system on. Sometimes this "Host" may be virtualized as well, if your doing slabbing
"Guest" refers the system that is being virtualized or run on the "Host"

---

### Post by anif726 on 2015-02-09
thanks for that answer.. i got some knowledge.... so the answer is no 3... but i can't type anything in that machine.. it keep load same things when i press any key like screenshot... any solution?

---

### Post by sandyd on 2015-02-09
> **anif726 said:**
> thanks for that answer.. i got some knowledge.... so the answer is no 3... but i can't type anything in that machine.. it keep load same things when i press any key like screenshot... any solution?

Have you installed Ubuntu yet?
You need to set the VM to boot from the Ubuntu ISO, install, then install the guest additions inside Ubuntu.

---

### Post by anif726 on 2015-02-11
nop.. that also new to me.. because mst of website did not mention that... and for now i am still searching for that location file in my ubuntu .... :((

---

### Post by anif726 on 2015-02-11
sorry ... stiil try to boot... same things appear

---

### Post by anif726 on 2015-02-11
i think i can ask this question here,,,, what is the problem with this error.... thanks and sorry

# Could not detect which operating system is in this disc image.  # You will need to specify which operating system will be installed"

---

