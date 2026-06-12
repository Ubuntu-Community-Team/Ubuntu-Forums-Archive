---
title: "Motivation and theory behind linux suspend"
date: 2006-07-18
forum: Programming Talk
---

### Post by acojlo on 2006-07-18
Hi,

Why is it so hard to enable suspend on a laptop? I've read in kernel documentation the drivers do not have current acpi specification quality. But - my personal opinion is suspend2ram and suspend2disk are fantastic possibilities of my hardware.

Some people like to travel. Imagine the man or, better the girl of your dreams, sitting at the railway station with laptop on her fancy knees. Official speaker announces train departure and she must enter the train. She is using the Linux and she must use shutdown. It lasts - about minute. It lasts another minute to turn on when she is in the train. Do you want her to be frustrated and stop working at laptop and thus enable herself to start chating with some guy about linux frustration? Imagine, they can continue by marriage and linux bad experience. She want be yours at that stage? ;)

How much is Linux as a operating system energy eficient when it does not support well suspend s3 and hibernate states? How much does it affect the energy consumption level and deffect the quality of life on individuals (because they lack the money they spent on electical energy)? Well, not much - some one can argue - because when you use linux you go shutdown - thus no energy consumption? :)

Linux is able to shutdown the computer. So if it is able to shutdown why it is not able to prepare some files on the hard disk and then shutdown? After all, it is preparing some files on the hard disk before every shutdown? It is not logical to me, it is just like a not too much motivation for the task. From my personal experience, when I press Hibernation button - computer starts preparing for the hibernation and then - puf - it stays turned on with no activity. My keyboard leds can blink after that (caps on off).

After all, having in mind the previous paragraph, if Linux is able to shutdown and theoreticaly to suspend2disk why it is not able to enter S3 state (prepare the files in RAM)?

Cheers!

---

### Post by Engnome on 2006-07-18
[QUOTE=Linus Torvalds]"Modern PCs are horrible. ACPI is a complete design disaster in every way. But we're kind of stuck with it. If any Intel people are listening to this and you had anything to do with ACPI, shoot yourself now, before you reproduce." [/QUOTE]

[QUOTE=Linus Torvalds]"The fact that ACPI was designed by a group of monkeys high on LSD, and is some of the worst designs in the industry obviously makes running it at _any_ point pretty damn ugly. "[/QUOTE]

An explanation direct from the semi-god himself.

---

### Post by acojlo on 2006-07-19
> **Engnome said:**
> An explanation direct from the semi-god himself.

Do you maybe know what is the way if I want to enable better acpi support for my laptop under linux? After all the laptop is shipped all around the world, so I am not only one who use this model? Maybe dmidecode data may help?

---

