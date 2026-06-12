---
title: "Full drive encryption with to releases of Ubuntu"
date: 2014-04-03
forum: New to Ubuntu
---

### Post by pgte3 on 2014-04-03
If I install 14.04 LTS and opt for full drive encryption, will I be able to then install another release of Unbutu on the same disk? How does that work?

---

### Post by sudodus on 2014-04-03
I would not do that. Instead I suggest

- either full drive encryption for example according to the following description (actually instructions for testing, but good also for installing)

[http://iso.qa.ubuntu.com/qatracker/testcases/1439/info](http://iso.qa.ubuntu.com/qatracker/testcases/1439/info)

- or encrypted home directory (so that the drive is available for normal management of partitions).

-o-

But maybe someone knows a good way to dual boot with full drive encryption. In that case, let us hope that person will find your thread and help you :-)

---

### Post by Double.J on 2014-04-03
Hi there!

yup I don't really recommend this either. Having just your personal data encrypted is good enough. For one encryption doesn't make any difference if the system is running and reduces your ability to fix it. You also have to erase a while drive and start over to encrypt.

i did it back around '10/'11 using windows - encrypt disk with true-crypt, and use easy bcd to then chain boot grub. I can't find the guide I used back then, but it was a total pain that took about 4 days to get properly set up and then 6/8 months later I needed to update grub after an update and couldn't use a live installer to do it. Had to reformat the whole drive and start over. It was really not worth it.

to be honest you don't even need encrypt /home! Given that if your machine is running, the information is unencrypted and available, you're better off just keeping your super sensitive info in an encrypted folder and using split to make sure all the pieces of the folder are in different places, heck you can change the file extension at the same time so they just blend into your system. .conf or .txt anyone?

just remember where you put them and what the password was!

encryption can be a great tool, but it can also be a great way to loose a lot of data. Few hone users really need it, For those that are concerned, the /home or encrypted file are probably best.

---

